---
title: _calloc_dbg | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _calloc_dbg
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- _calloc_dbg
- calloc_dbg
dev_langs:
- C++
helpviewer_keywords:
- _calloc_dbg function
- calloc_dbg function
ms.assetid: 7f62c42b-eb9f-4de5-87d0-df57036c87de
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2759c19fb88b820fc346b5cf35e97522b7e74cb6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32396773"
---
# <a name="callocdbg"></a>_calloc_dbg

디버깅 헤더에 대한 추가 공간이 있는 힙에서 다수의 메모리 블록을 할당하고 버퍼를 덮어씁니다(디버그 버전에만 해당).

## <a name="syntax"></a>구문

```C
void *_calloc_dbg(
   size_t num,
   size_t size,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>매개 변수

*번호*<br/>
요청된 메모리 블록 수입니다.

*size*<br/>
요청된 각 메모리 블록 크기입니다(바이트).

*blockType*<br/>
요청 된 메모리 블록의 형식: **_CLIENT_BLOCK** 또는 **_NORMAL_BLOCK**합니다.

할당 블록 형식과 이러한 형식의 사용 방법에 대한 자세한 내용은 [디버그 힙의 블록 형식](/visualstudio/debugger/crt-debug-heap-details)을 참조하세요.

*filename*<br/>
할당 작업을 요청한 소스 파일의 이름에 대 한 포인터 또는 **NULL**합니다.

*linenumber*<br/>
할당 작업이 요청 된 소스 파일의 줄 번호 또는 **NULL**합니다.

*filename* 및 *linenumber* 매개 변수를만 사용할 때 **_calloc_dbg** 명시적으로 호출 되었거나 또는 [_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md)전처리기 상수가 정의 된 합니다.

## <a name="return-value"></a>반환 값

성공적으로 완료 되 면이 함수 마지막 할당 된 메모리 블록의 사용자 부분에 대 한 포인터를 반환, 새 처리기 함수를 호출 하거나 반환 **NULL**합니다. 반환 동작에 대한 자세한 내용은 설명 부분을 참조하세요. 새 처리기 함수를 사용하는 방법에 대한 자세한 내용은 [calloc](calloc.md) 함수를 참조하세요.

## <a name="remarks"></a>설명

**_calloc_dbg** 의 디버그 버전이 [calloc](calloc.md) 함수입니다. 때 [_DEBUG](../../c-runtime-library/debug.md) 를 정의 하지 않은를 호출할 때마다 **_calloc_dbg** 에 대 한 호출으로 줄어듭니다 **calloc**합니다. 둘 다 **calloc** 및 **_calloc_dbg** 할당 *번호* 기본 힙에서 메모리 블록 하지만 **_calloc_dbg** 몇 가지 디버깅을 제공 합니다. 기능:

- 누수를 테스트하기 위해 블록의 사용자 부분 양쪽에서 버퍼 제공.

- 특정 할당 형식을 추적하기 위해 블록 형식 매개 변수 제공.

- *filename*/*linenumber* 정보로 할당 요청의 원점을 확인 하 합니다.

**_calloc_dbg** 각 메모리 블록에는 요청 된 것 보다 약간 더 많은 공간을 할당 *크기*합니다. 디버그 힙 관리자는 추가 공간을 사용하여 디버그 메모리 블록을 연결하고 응용 프로그램에 디버그 헤더 정보를 제공하고 버퍼를 덮어씁니다. 블록이 할당되면 블록의 사용자 부분은 값 0xCD로 채워지고 각 덮어쓰기 버퍼는 0xFD로 채워집니다.

**_calloc_dbg** 설정 **errno** 를 **ENOMEM** 메모리 할당에 실패 하면 **EINVAL** (앞에서 언급 한 오버 헤드 포함) 필요한 메모리 양을 초과 하는 경우 반환 되 **_HEAP_MAXREQ**합니다. 이 오류 및 다른 오류 코드에 대한 자세한 내용은 [errno, _doserrno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조하세요.

기본 힙의 디버그 버전에서 메모리 블록을 할당, 초기화 및 관리하는 방법에 대한 자세한 내용은 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)를 참조하세요. 응용 프로그램의 디버그 빌드에서 표준 힙 함수를 호출하는 것과 해당 함수의 디버그 버전을 호출하는 것의 차이에 대한 자세한 내용은 [힙 할당 함수의 디버그 버전](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)을 참조하세요.

## <a name="requirements"></a>요구 사항

|루틴|필수 헤더|
|-------------|---------------------|
|**_calloc_dbg**|\<crtdbg.h>|

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_callocd.c
// This program uses _calloc_dbg to allocate space for
// 40 long integers. It initializes each element to zero.

#include <stdio.h>
#include <malloc.h>
#include <crtdbg.h>

int main( void )
{
    long *bufferN, *bufferC;

    // Call _calloc_dbg to include the filename and line number
    // of our allocation request in the header and also so we can
    // allocate CLIENT type blocks specifically
    bufferN = (long *)_calloc_dbg( 40, sizeof(long), _NORMAL_BLOCK, __FILE__, __LINE__ );
    bufferC = (long *)_calloc_dbg( 40, sizeof(long), _CLIENT_BLOCK, __FILE__, __LINE__ );
    if( bufferN != NULL && bufferC != NULL )
        printf( "Allocated memory successfully\n" );
    else
        printf( "Problem allocating memory\n" );

    / _free_dbg must be called to free CLIENT type blocks
    free( bufferN );
    _free_dbg( bufferC, _CLIENT_BLOCK );
}
```

```Output
Allocated memory successfully
```

## <a name="see-also"></a>참고자료

[디버그 루틴](../../c-runtime-library/debug-routines.md)<br/>
[calloc](calloc.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
[_DEBUG](../../c-runtime-library/debug.md)<br/>

---
title: remove, _wremove | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wremove
- remove
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- remove
- _wremove
- _tremove
dev_langs:
- C++
helpviewer_keywords:
- tremove function
- _wremove function
- files [C++], deleting
- _tremove function
- files [C++], removing
- wremove function
- remove function
ms.assetid: b6345ec3-3289-4645-93a4-28b9e478cc19
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 36cdc09107a66067b358cb2fd72ec9bd1b2b30a1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32406435"
---
# <a name="remove-wremove"></a>remove, _wremove

파일을 삭제합니다.

## <a name="syntax"></a>구문

```C
int remove(
   const char *path
);
int _wremove(
   const wchar_t *path
);
```

### <a name="parameters"></a>매개 변수

*path*<br/>
제거할 파일의 경로입니다.

## <a name="return-value"></a>반환 값

파일이 삭제되면 이러한 함수 각각이 0을 반환합니다. 그렇지 않으면-1을 반환 하 고 설정 **errno** 하도록 **EACCES** 읽기 전용 파일을 지정 하는 경로 또는 파일을 열면, 나타내기 위해 또는 **ENOENT** 임을 나타내는 파일 이름 또는 경로 찾을 수 없거나 경로가 디렉터리를 지정 합니다.

이러한 반환 코드 및 기타 반환 코드에 대한 자세한 내용은  [_doserrno, errno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)을 참조하세요.

## <a name="remarks"></a>설명

**remove** 함수는 *path*로 지정된 파일을 삭제합니다. **_wremove** 의 와이드 문자 버전이 **_remove**; *경로* 인수를 **_wremove** 는 와이드 문자 문자열입니다. **_wremove** 및 **_remove** 동일 하 게 작동 합니다. 삭제하기 전에 파일에 대한 모든 핸들을 닫아야 합니다.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tremove**|**remove**|**remove**|**_wremove**|

## <a name="requirements"></a>요구 사항

|루틴|필수 헤더|
|-------------|---------------------|
|**remove**|\<stdio.h> 또는 \<io.h>|
|**_wremove**|\<stdio.h> 또는 \<wchar.h>|

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

모든 버전의 [C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)입니다.

## <a name="example"></a>예제

```C
// crt_remove.c
/* This program uses remove to delete crt_remove.txt */

#include <stdio.h>

int main( void )
{
   if( remove( "crt_remove.txt" ) == -1 )
      perror( "Could not delete 'CRT_REMOVE.TXT'" );
   else
      printf( "Deleted 'CRT_REMOVE.TXT'\n" );
}
```

### <a name="input-crtremovetxt"></a>입력: crt_remove.txt

```Input
This file will be deleted.
```

### <a name="sample-output"></a>샘플 출력

```Output
Deleted 'CRT_REMOVE.TXT'
```

## <a name="see-also"></a>참고자료

[파일 처리](../../c-runtime-library/file-handling.md)<br/>
[_unlink, _wunlink](unlink-wunlink.md)<br/>

---
title: _eof | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _eof
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _eof
dev_langs:
- C++
helpviewer_keywords:
- eof function
- end of file, testing for
- _eof function
- files [C++], end of
- testing, for end-of-file
- end of file
ms.assetid: 265703f4-d07e-4005-abf3-b1d0cdd9e0b0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: da7ccad98491762d30db2741f8c3d9fe0d784dc6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32395126"
---
# <a name="eof"></a>_eof

파일의 끝(EOF)을 테스트합니다.

## <a name="syntax"></a>구문

```C
int _eof(
   int fd
);
```

### <a name="parameters"></a>매개 변수

*fd*<br/>
열려 있는 파일을 참조하는 파일 설명자입니다.

## <a name="return-value"></a>반환 값

**_eof** 현재 위치가 파일의 끝에 또는 0 되지 않았으면 1을 반환 합니다. 반환 값이-1은 오류;를 나타냅니다. 이 경우에 잘못 된 매개 변수 처리기가 호출에 설명 된 대로 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)합니다. 실행을 계속 하도록 허용 된 경우 **errno** 로 설정 된 **EBADF**, 잘못 된 파일 설명자를 나타내는입니다.

## <a name="remarks"></a>설명

**_eof** 함수는 파일의 끝에 연결 된 있는지 여부를 결정 *fd* 에 도달 했습니다.

## <a name="requirements"></a>요구 사항

|함수|필수 헤더|선택적 헤더|
|--------------|---------------------|---------------------|
|**_eof**|\<io.h>|\<errno.h>|

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_eof.c
// This program reads data from a file
// ten bytes at a time until the end of the
// file is reached or an error is encountered.
//
#include <io.h>
#include <fcntl.h>
#include <stdio.h>
#include <stdlib.h>
#include <share.h>

int main( void )
{
   int  fh, count, total = 0;
   char buf[10];
   if( _sopen_s( &fh, "crt_eof.txt", _O_RDONLY, _SH_DENYNO, 0 ) )
   {
        perror( "Open failed");
        exit( 1 );
   }
   // Cycle until end of file reached:
   while( !_eof( fh ) )
   {
      // Attempt to read in 10 bytes:
      if( (count = _read( fh, buf, 10 )) == -1 )
      {
         perror( "Read error" );
         break;
      }
      // Total actual bytes read
      total += count;
   }
   printf( "Number of bytes read = %d\n", total );
   _close( fh );
}
```

### <a name="input-crteoftxt"></a>입력: crt_eof.txt

```Input
This file contains some text.
```

### <a name="output"></a>출력

```Output
Number of bytes read = 29
```

## <a name="see-also"></a>참고자료

[오류 처리](../../c-runtime-library/error-handling-crt.md)<br/>
[하위 수준 I/O](../../c-runtime-library/low-level-i-o.md)<br/>
[clearerr](clearerr.md)<br/>
[feof](feof.md)<br/>
[ferror](ferror.md)<br/>
[perror, _wperror](perror-wperror.md)<br/>

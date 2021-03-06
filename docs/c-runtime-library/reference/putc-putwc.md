---
title: putc, putwc | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- putwc
- putc
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
- _puttc
- putwc
- putc
dev_langs:
- C++
helpviewer_keywords:
- streams, writing characters to
- characters, writing
- putwc function
- putc function
- _puttc function
- puttc function
ms.assetid: a37b2e82-9d88-4565-8190-ff8d04c0ddb9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 931a1a586f46327dd800ca5e1b2ef9a0b22f469d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32404378"
---
# <a name="putc-putwc"></a>putc, putwc

스트림에 문자를 씁니다.

## <a name="syntax"></a>구문

```C
int putc(
   int c,
   FILE *stream
);
wint_t putwc(
   wchar_t c,
   FILE *stream
);
```

### <a name="parameters"></a>매개 변수

*c*<br/>
쓸 문자입니다.

*스트림*<br/>
**FILE** 구조체에 대한 포인터입니다.

## <a name="return-value"></a>반환 값

쓴 문자를 반환합니다. 오류 또는 파일 끝 조건을 나타내기 위해 **putc** 및 **putchar** 반환 * * EOF`; **putwc` 및 **putwchar** 반환 **WEOF**합니다. 4개 루틴 모두에 대해 [ferror](ferror.md) 또는 [feof](feof.md)를 사용하여 오류 또는 파일 끝을 확인합니다. Null 포인터에 전달 되 면 *스트림*에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)합니다. 실행을 계속 허용 된 경우 이러한 함수가 반환 **EOF** 또는 **WEOF** 설정 **errno** 를 **EINVAL**합니다.

이러한 오류 코드 및 기타 오류 코드에 대한 자세한 내용은 [_doserrno, errno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조하세요.

## <a name="remarks"></a>설명

**putc** 루틴 단일 문자를 씁니다 *c* 출력에 *스트림* 현재 위치에 있습니다. 모든 정수에 전달 될 수 **putc**만 하위 8 비트가 기록 됩니다. **putchar** 루틴은 동일 **putc (** * c ***, stdout)** 합니다. 각 루틴에 대해 읽기 오류가 발생하는 경우 스트림에 대한 오류 표시기가 설정됩니다. **putc** 및 **putchar** 비슷합니다 **fputc** 및 **_fputchar**각각 하지만 함수 및 매크로로 구현 됩니다 (참조 [ 함수와 매크로 중 선택](../../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md)). **putwc** 및 **putwchar** 와이드 문자 버전의 **putc** 및 **putchar**각각. **putwc** 및 **putc** 스트림이 ANSI 모드에서 열리는 경우 동일 하 게 작동 합니다. **putc** 현재 출력 유니코드 스트림을 지원 하지 않습니다.

**_nolock** 접미사가 있는 버전은 다른 스레드에 의한 간섭에서 보호되지 않는 점을 제외하면 동일합니다. 자세한 내용은 **_putc_nolock, _putwc_nolock**을 참조하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_puttc**|**putc**|**putc**|**putwc**|

## <a name="requirements"></a>요구 사항

|루틴|필수 헤더|
|-------------|---------------------|
|**putc**|\<stdio.h>|
|**putwc**|\<stdio.h> 또는 \<wchar.h>|

콘솔 유니버설 Windows 플랫폼 (UWP) 응용 프로그램에서 지원 되지 않습니다. 콘솔을 사용 하는 연결 된 표준 스트림 핸들 **stdin**, **stdout**, 및 **stderr**, C 런타임 함수 UWP 앱에서 사용할 수 있는 전에 리디렉션되어야 . 호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

모든 버전의 [C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)입니다.

## <a name="example"></a>예제

```C
// crt_putc.c
/* This program uses putc to write buffer
* to a stream. If an error occurs, the program
* stops before writing the entire buffer.
*/

#include <stdio.h>

int main( void )
{
   FILE *stream;
   char *p, buffer[] = "This is the line of output\n";
   int  ch;

   ch = 0;
   /* Make standard out the stream and write to it. */
   stream = stdout;
   for( p = buffer; (ch != EOF) && (*p != '\0'); p++ )
      ch = putc( *p, stream );
}
```

### <a name="output"></a>출력

```Output
This is the line of output
```

## <a name="see-also"></a>참고자료

[스트림 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fputc, fputwc](fputc-fputwc.md)<br/>
[getc, getwc](getc-getwc.md)<br/>

---
title: sprintf, _sprintf_l, swprintf, _swprintf_l, __swprintf_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- __swprintf_l
- sprintf
- _sprintf_l
- _swprintf_l
- swprintf
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
- ntdll.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- _stprintf_l
- __swprintf_l
- sprintf_l
- swprintf
- _sprintf_l
- sprintf
- _stprintf
- stprintf_l
dev_langs:
- C++
helpviewer_keywords:
- _swprintf_l function
- _stprintf function
- __swprintf_l function
- stprintf function
- sprintf function
- _sprintf_l function
- _stprintf_l function
- swprintf function
- strings [C++], writing to
- _CRT_NON_CONFORMING_SWPRINTFS
- swprintf_l function
- stprintf_l function
- sprintf_l function
- formatted text [C++]
ms.assetid: f6efe66f-3563-4c74-9455-5411ed939b81
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 02538d8c74de4f48cb4a3d6285e10c3c4e03c322
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32415938"
---
# <a name="sprintf-sprintfl-swprintf-swprintfl-swprintfl"></a>sprintf, _sprintf_l, swprintf, _swprintf_l, __swprintf_l

문자열에 서식이 지정된 데이터를 씁니다. 이러한 함수 중 일부의 더 안전한 버전을 사용할 수 있습니다. [sprintf_s, _sprintf_s_l, swprintf_s, _swprintf_s_l](sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)을 참조하세요. 안전한 버전의 **swprintf** 및 **_swprintf_l** 사용 하지 않는 한 *count* 매개 변수입니다.

## <a name="syntax"></a>구문

```C
int sprintf(
   char *buffer,
   const char *format [,
   argument] ...
);
int _sprintf_l(
   char *buffer,
   const char *format,
   locale_t locale [,
   argument] ...
);
int swprintf(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format [,
   argument]...
);
int _swprintf_l(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format,
   locale_t locale [,
   argument] ...
);
int __swprintf_l(
   wchar_t *buffer,
   const wchar_t *format,
   locale_t locale [,
   argument] ...
);
template <size_t size>
int sprintf(
   char (&buffer)[size],
   const char *format [,
   argument] ...
); // C++ only
template <size_t size>
int _sprintf_l(
   char (&buffer)[size],
   const char *format,
   locale_t locale [,
   argument] ...
); // C++ only

```

### <a name="parameters"></a>매개 변수

*buffer*<br/>
출력을 위한 저장소 위치

*count*<br/>
이 함수의 유니코드 버전에 저장할 최대 문자 수입니다.

*format*<br/>
형식 컨트롤 문자열

*argument*<br/>
선택적 인수

*locale*<br/>
사용할 로캘입니다.

자세한 내용은 [형식 사양](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)을 참조하세요.

## <a name="return-value"></a>반환 값

작성 된 문자 수 또는 오류가 발생 한 경우-1입니다. 경우 *버퍼* 또는 *형식* 가 null 포인터에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)합니다. 실행을 계속 허용 된, 하는 경우 이러한 함수가-1을 반환 하 고 설정 **errno** 를 **EINVAL**합니다.

**sprintf** 에 저장 된 바이트 수를 반환 *버퍼*, 종결 null 문자를 제외 합니다. **swprintf** 에 저장 된 와이드 문자 수를 반환 *버퍼*, 종료 null 와이드 문자를 제외 합니다.

## <a name="remarks"></a>설명

**sprintf** 포맷 하 고 일련의 문자 및 값을 저장 하는 함수 *버퍼*합니다. 각 *인수* (있는 경우)이 변환 되 고 해당 형식 사양에 따라 출력 *형식*합니다. 형식은 일반 문자로 구성 되어 있으며 동일한 형태와 기능을는 *형식* 에 대 한 인수 [printf](printf-printf-l-wprintf-wprintf-l.md)합니다. 기록된 마지막 문자 뒤에 null 문자가 추가됩니다. 중복되는 문자열 간에 복사가 이뤄지면 이 동작은 정의되지 않습니다.

> [!IMPORTANT]
> 사용 하 여 **sprintf**, 작성 된 문자를 사용 하 여 코드을 의미 하는 수를 제한할 방법이 있으면 **sprintf** 는 버퍼 오버런에 취약 합니다. 관련된 함수를 사용 하는 것이 좋습니다 [_snprintf](snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)에 쓰려고 문자의 최대 수를 지정 하는 *버퍼*, 사용 또는 [_scprintf](scprintf-scprintf-l-scwprintf-scwprintf-l.md) 확인 하려면 크기는 버퍼는 필요 합니다. 또한 되도록 *형식* 사용자 정의 문자열이 아닌지 합니다.

**swprintf** 의 와이드 문자 버전이 **sprintf**;에 대 한 포인터 인수 **swprintf** 는 와이드 문자 문자열입니다. 인코딩 오류를 탐지 **swprintf** 에 다를 수 있습니다 **sprintf**합니다. **swprintf** 및 **fwprintf** 점을 제외 하 고 동일 하 게 작동 **swprintf** 유형의 대상 대신 문자열에 출력을 기록 **파일**, 및 **swprintf** 필요는 *count* 매개 변수를 쓸 문자의 최대 수를 지정 합니다. 있는 이러한 함수 버전은 **_l** 은 현재 스레드 로캘 대신 전달 된 로캘 매개 변수를 사용 하는 점을 제외 하 고 접미사는 동일 합니다.

**swprintf** 두 번째 매개 변수를 필요로 하는 ISO C 표준을 따르는 *count*, 형식의 **size_t**합니다. 기존 비표준 동작을 강제로 표시 하려면 정의 **_CRT_NON_CONFORMING_SWPRINTFS**합니다. 이후 버전에서 기존 동작이 제거될 수도 있으므로 새 준수 동작을 사용하도록 코드를 변경해야 합니다.

C++에서 이러한 함수는 보다 최신의 보안 대응 함수를 호출하는 템플릿 오버로드를 갖고 있습니다. 자세한 내용은 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)을 참조하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_stprintf**|**sprintf**|**sprintf**|**_swprintf**|
|**_stprintf_l**|**_sprintf_l**|**_sprintf_l**|**__swprintf_l**|

## <a name="requirements"></a>요구 사항

|루틴|필수 헤더|
|-------------|---------------------|
|**sprintf**, **_sprintf_l**|\<stdio.h>|
|**swprintf**, **_swprintf_l**|\<stdio.h> 또는 \<wchar.h>|

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_sprintf.c
// compile with: /W3
// This program uses sprintf to format various
// data and place them in the string named buffer.

#include <stdio.h>

int main( void )
{
   char  buffer[200], s[] = "computer", c = 'l';
   int   i = 35, j;
   float fp = 1.7320534f;

   // Format and print various data:
   j  = sprintf( buffer,     "   String:    %s\n", s ); // C4996
   j += sprintf( buffer + j, "   Character: %c\n", c ); // C4996
   j += sprintf( buffer + j, "   Integer:   %d\n", i ); // C4996
   j += sprintf( buffer + j, "   Real:      %f\n", fp );// C4996
   // Note: sprintf is deprecated; consider using sprintf_s instead

   printf( "Output:\n%s\ncharacter count = %d\n", buffer, j );
}
```

```Output
Output:
   String:    computer
   Character: l
   Integer:   35
   Real:      1.732053

character count = 79
```

## <a name="example"></a>예제

```C
// crt_swprintf.c
// wide character example
// also demonstrates swprintf returning error code
#include <stdio.h>

int main( void )
{
   wchar_t buf[100];
   int len = swprintf( buf, 100, L"%s", L"Hello world" );
   printf( "wrote %d characters\n", len );
   len = swprintf( buf, 100, L"%s", L"Hello\xffff world" );
   // swprintf fails because string contains WEOF (\xffff)
   printf( "wrote %d characters\n", len );
}
```

```Output
wrote 11 characters
wrote -1 characters
```

## <a name="see-also"></a>참고자료

[스트림 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[vprintf 함수](../../c-runtime-library/vprintf-functions.md)<br/>

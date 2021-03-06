---
title: _mbsbtype, _mbsbtype_l | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _mbsbtype_l
- _mbsbtype
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
- api-ms-win-crt-multibyte-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- mbsbtype
- mbsbtype_l
- _mbsbtype_l
- _mbsbtype
dev_langs:
- C++
helpviewer_keywords:
- _mbsbtype function
- mbsbtype function
- _mbsbtype_l function
- mbsbtype_l function
ms.assetid: 0d5dd91a-d32d-4f98-ac57-98dfc9e98eac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: be098cb1fe53e1345f0c4f40212657f4bfd97f4f
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/22/2018
ms.locfileid: "34451021"
---
# <a name="mbsbtype-mbsbtypel"></a>_mbsbtype, _mbsbtype_l

문자열 내에서 바이트의 형식을 반환합니다.

> [!IMPORTANT]
> 이 API는 Windows 런타임에서 실행되는 응용 프로그램에서 사용할 수 없습니다. 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
int _mbsbtype(
   const unsigned char *mbstr,
   size_t count
);
int _mbsbtype_l(
   const unsigned char *mbstr,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>매개 변수

*mbstr*<br/>
멀티바이트 문자 시퀀스의 주소입니다.

*count*<br/>
문자열의 헤드로부터의 바이트 오프셋입니다.

*locale*<br/>
사용할 로캘입니다.

## <a name="return-value"></a>반환 값

**_mbsbtype** 및 **_mbsbtype_l** 에 지정 된 바이트 테스트의 결과 나타내는 정수 값을 반환 합니다. 다음 표의 매니페스트 상수는 Mbctype.h에 정의됩니다.

|반환 값|바이트 형식|
|------------------|---------------|
|**_MBC_SINGLE** (0)|싱글바이트 문자입니다. 예를 들어 코드 페이지 932에에서 **_mbsbtype** 내에 있으면 지정 된 바이트 범위 0x20-0x7E 또는 0xA1-0xDF 0을 반환 합니다.|
|**_MBC_LEAD** (1)|멀티바이트 문자의 선행 바이트입니다. 예를 들어 코드 페이지 932에에서 **_mbsbtype** 0xFC 0x81-0x9F 또는 0xE0-범위 내에서 지정 된 바이트는 경우 1을 반환 합니다.|
|**_MBC_TRAIL** (2)|멀티바이트 문자의 후행 바이트입니다. 예를 들어 코드 페이지 932에에서 **_mbsbtype** 0xFC 0x40-0x7E 또는 0x80-범위 내에서 지정 된 바이트는 경우 2를 반환 합니다.|
|**_MBC_ILLEGAL** (-1)|**NULL** 문자열, 잘못 된 문자 또는 바이트 오프셋에서 이전에 찾은 null 바이트 *count* 에 *mbstr*합니다.|

## <a name="remarks"></a>설명

**_mbsbtype** 함수는 멀티 바이트 문자열의 바이트 형식을 결정 합니다. 함수 검사 오프셋에서 바이트만 *개수* 에 *mbstr*, 지정 된 바이트 앞에 잘못 된 문자를 무시 합니다.

출력 값은 로캘의 **LC_CTYPE** 범주 설정에 따른 영향을 받습니다. 자세한 내용은 [setlocale](setlocale-wsetlocale.md)을 참조하세요. 없이이 함수의 버전은 **_l** 접미사가 로캘 종속 동작에 대 한 현재 로캘을 사용 하 여 버전으로는 **_l** 제외 하 고 전달 된 로캘 매개 변수를 사용 하 여 접미사는 동일 대신 합니다. 자세한 내용은 [Locale](../../c-runtime-library/locale.md)을 참조하세요.

입력된 문자열의 형식이 **NULL**에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)합니다. 실행을 계속 하도록 허용 된 경우 **errno** 로 설정 된 **EINVAL** 함수가 반환 하 고 **_MBC_ILLEGAL**합니다.

## <a name="requirements"></a>요구 사항

|루틴|필수 헤더|선택적 헤더|
|-------------|---------------------|---------------------|
|**_mbsbtype**|\<mbstring.h>|\<mbctype.h>*|
|**_mbsbtype_l**|\<mbstring.h>|\<mbctype.h>*|

\* 매니페스트 상수에 대해 반환 값으로 사용됩니다.

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고자료

[바이트 분류](../../c-runtime-library/byte-classification.md)<br/>

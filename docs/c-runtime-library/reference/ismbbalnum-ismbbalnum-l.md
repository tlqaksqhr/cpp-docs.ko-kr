---
title: _ismbbalnum, _ismbbalnum_l | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _ismbbalnum
- _ismbbalnum_l
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
- _ismbbalnum
- ismbbalnum
- _ismbbalnum_l
- ismbbalnum_l
dev_langs:
- C++
helpviewer_keywords:
- _ismbbalnum_l function
- ismbbalnum function
- ismbbalnum_l function
- _ismbbalnum function
ms.assetid: 8025de50-a871-49fd-9ae6-f437b47aa987
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3ace530d1190de5df5eaac92d412b86f2b2cc3d4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32398710"
---
# <a name="ismbbalnum-ismbbalnuml"></a>_ismbbalnum, _ismbbalnum_l

지정된 멀티바이트 문자가 영문자인지 숫자인지를 확인합니다.

## <a name="syntax"></a>구문

```C
int _ismbbalnum(
   unsigned int c
);
int _ismbbalnum_l(
   unsigned int c
);
```

### <a name="parameters"></a>매개 변수

*c*<br/>
테스트할 정수입니다.

*locale*<br/>
사용할 로캘입니다.

## <a name="return-value"></a>반환 값

**_ismbbalnum** 경우 0이 아닌 값을 반환 식:

`isalnum(c) || _ismbbkalnum(c)`

에 대 한이 0이 아닌 *c*, 없는 경우 0입니다.

이 함수의 버전은 **_l** 은 로캘 종속 동작에 현재 로캘 대신에 전달 된 로캘을 사용 하 여 접미사는 동일 합니다.

## <a name="requirements"></a>요구 사항

|루틴|필수 헤더|
|-------------|---------------------|
|**_ismbbalnum**|\<mbctype.h>|
|**_ismbbalnum_l**|\<mbctype.h>|

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

모든 버전의 [C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)입니다.

## <a name="see-also"></a>참고자료

[바이트 분류](../../c-runtime-library/byte-classification.md)<br/>
[_ismbb 루틴](../../c-runtime-library/ismbb-routines.md)<br/>

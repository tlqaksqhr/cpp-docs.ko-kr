---
title: _free_locale | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _free_locale
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
- api-ms-win-crt-locale-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- __free_locale
- free_locale
- _free_locale
dev_langs:
- C++
helpviewer_keywords:
- __free_locale function
- free_locale function
- locales, freeing
- _free_locale function
ms.assetid: 1f08d348-ab32-4028-a145-6cbd51b49af9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0b74725ddd7884bcc714e1048b28c53f201ebe4e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32397134"
---
# <a name="freelocale"></a>_free_locale

로캘 개체를 해제합니다.

## <a name="syntax"></a>구문

```C
void _free_locale(
   _locale_t locale
);
```

### <a name="parameters"></a>매개 변수

*로캘* 해제할 로캘 개체입니다.

## <a name="remarks"></a>설명

**_free_locale** 함수에 대 한 호출에서 얻은 로캘 개체를 해제 하는 데 사용 됩니다 **_get_current_locale** 또는 **_create_locale**합니다.

이 함수의 이전 이름인 **__free_locale** (두 개의 선행 밑줄이)으로 사용 되지 않습니다.

## <a name="requirements"></a>요구 사항

|**루틴**|필수 헤더|
|---------------|---------------------|
|**_free_locale**|\<locale.h>|

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고자료

[_get_current_locale](get-current-locale.md)<br/>
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)<br/>

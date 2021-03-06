---
title: _get_pgmptr | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _get_pgmptr
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- get_pgmptr
- _get_pgmptr
dev_langs:
- C++
helpviewer_keywords:
- get_pgmptr function
- _get_pgmptr function
- pgmptr global variable
- _pgmptr global variable
ms.assetid: 29f16a9f-a685-4721-add3-7fad4f67eece
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0488e2a7b8cd907872e835abb63e62f29f259455
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32397781"
---
# <a name="getpgmptr"></a>_get_pgmptr

현재 값을 가져옵니다는 **_pgmptr** 전역 변수입니다.

## <a name="syntax"></a>구문

```C
errno_t _get_pgmptr( 
   char **pValue 
);
```

### <a name="parameters"></a>매개 변수

*pValue*<br/>
현재 값으로 채울 문자열에 대 한 포인터는 **_pgmptr** 변수입니다.

## <a name="return-value"></a>반환 값

성공하는 경우 0을 반환하고, 실패하는 경우 오류 코드를 반환합니다. 경우 *pValue* 은 **NULL**에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)합니다. 이 함수를 설정 하는 경우 실행을 계속 허용 된, **errno** 를 **EINVAL** 반환 **EINVAL**합니다.

## <a name="remarks"></a>설명

호출 **_get_pgmptr** 프로그램 좁은 진입점이 있으면 같은 **main ()** 또는 **WinMain()** 합니다. **_pgmptr** 전역 변수는 프로세스와 관련 된 실행 파일의 전체 경로 포함 합니다. 자세한 내용은 [_pgmptr, _wpgmptr](../../c-runtime-library/pgmptr-wpgmptr.md)를 참조하세요.

## <a name="requirements"></a>요구 사항

|루틴|필수 헤더|
|-------------|---------------------|
|**_get_pgmptr**|\<stdlib.h>|

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고자료

[_get_wpgmptr](get-wpgmptr.md)<br/>

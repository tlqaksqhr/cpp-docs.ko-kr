---
title: _setmbcp | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _setmbcp
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
- _setmbcp
- setmbcp
dev_langs:
- C++
helpviewer_keywords:
- setmbcp function
- _setmbcp function
- multibyte code pages
ms.assetid: cfde53b5-0b73-4684-81b1-a8d3aafc85de
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 91993171def417adfc389420d1376e5a71f8cda0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32408070"
---
# <a name="setmbcp"></a>_setmbcp

새 멀티바이트 코드 페이지를 설정합니다.

## <a name="syntax"></a>구문

```C
int _setmbcp(
   int codepage
);
```

### <a name="parameters"></a>매개 변수

*코드 페이지*<br/>
로캘 독립적인 멀티바이트 루틴에 대한 새 코드 페이지 설정입니다.

## <a name="return-value"></a>반환 값

코드 페이지가 올바르게 설정되면 0을 반환합니다. 잘못 된 코드 페이지 값을 제공 하는 경우 *코드 페이지*를 반환 하 고-1 코드 페이지 설정이 변경 되지 않습니다. 집합 **errno** 를 **EINVAL** 메모리 할당 오류가 발생 합니다.

## <a name="remarks"></a>설명

**_setmbcp** 함수는 새 멀티 바이트 코드 페이지를 지정 합니다. 기본적으로 런타임 시스템은 멀티바이트 코드 페이지를 시스템 기본 ANSI 코드 페이지로 자동 설정합니다. 멀티바이트 코드 페이지 설정은 로캘에 종속되지 않는 모든 멀티바이트 루틴에 적용됩니다. 그러나,에 지시할 수는 **_setmbcp** 은 현재 로캘에 대해 정의 된 코드 페이지를 사용 하도록 (매니페스트 상수 중 다음 목록을 참조 및 관련 동작으로 인해). 멀티바이트 코드 페이지가 아닌 로캘 코드 페이지를 사용하는 멀티바이트 루틴의 목록은 [멀티바이트 문자 시퀀스 해석](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)을 참조하세요.

멀티바이트 코드 페이지는 다음 런타임 라이브러리 루틴의 멀티바이트 문자 처리에도 영향을 줍니다.

||||
|-|-|-|
|[_exec 함수](../../c-runtime-library/exec-wexec-functions.md)|[_mktemp](mktemp-wmktemp.md)|[_stat](stat-functions.md)|
|[_fullpath](fullpath-wfullpath.md)|[_spawn 함수](../../c-runtime-library/spawn-wspawn-functions.md)|[_tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|
|[_makepath](makepath-wmakepath.md)|[_splitpath](splitpath-wsplitpath.md)|[tmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|

또한 멀티 바이트 문자를 수신 하는 모든 런타임 라이브러리 루틴 *argv* 또는 *envp* 매개 변수로 인수를 프로그램 (예:는 **_exec** 및 **_spawn** 제품군) 멀티 바이트 코드 페이지에 따라 이러한 문자열을 처리 합니다. 따라서 이러한 루틴은 영향도 받기에 대 한 호출 **_setmbcp** 멀티 바이트 코드 페이지를 변경 하는 합니다.

*코드 페이지* 인수는 다음 값 중 하나로 설정할 수 있습니다.

- **_MB_CP_ANSI** 프로그램 시작 시 운영 체제에서 사용 하 여 ANSI 코드 페이지를 가져옵니다.

- **_MB_CP_LOCALE** 사용은 현재 로캘 코드 페이지에 대 한 이전 호출에서 가져온 [setlocale](setlocale-wsetlocale.md)합니다.

- **_MB_CP_OEM** 프로그램 시작 시 운영 체제에서 사용 하 여 OEM 코드 페이지를 가져옵니다.

- **_MB_CP_SBCS** 단일 바이트 코드 페이지를 사용 합니다. 코드 페이지로 설정 되 면 **_MB_CP_SBCS**와 같은 일상적인 [_ismbblead](ismbblead-ismbblead-l.md) 항상 false를 반환 합니다.

- 그 외의 모든 유효 코드 페이지 값. 값이 ANSI인지, OEM인지 아니면 운영 체제에서 지원하는 기타 코드 페이지(지원되지 않는 UTF-7/UTF-8은 제외됨)인지는 관계가 없습니다.

## <a name="requirements"></a>요구 사항

|루틴|필수 헤더|
|-------------|---------------------|
|**_setmbcp**|\<mbctype.h>|

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고자료

[_getmbcp](getmbcp.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>

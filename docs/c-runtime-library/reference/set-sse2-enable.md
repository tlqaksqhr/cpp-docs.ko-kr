---
title: _set_SSE2_enable | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _set_SSE2_enable
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
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _set_SSE2_enable
- set_SSE2_enable
dev_langs:
- C++
helpviewer_keywords:
- _set_SSE2_enable function
- Streaming SIMD Extensions 2 instructions
- set_SSE2_enable function
ms.assetid: 55db895d-fc1e-475a-9110-b781a9bb51c5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 45f4ed5333dd8ae6bab6291233391884e4efc7ff
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32407853"
---
# <a name="setsse2enable"></a>_set_SSE2_enable

CRT 수학 루틴에서 SSE2 스트리밍 SIMD 확장명 2 () 명령 사용 하지 않도록 설정 하거나 사용 합니다. SSE2가 기본적으로 사용하도록 설정되어 있으므로 x64 아키텍처에서 이 함수를 사용할 수 없습니다.

## <a name="syntax"></a>구문

```C
int _set_SSE2_enable(
   int flag
);
```

### <a name="parameters"></a>매개 변수

*flag*<br/>
SSE2 구현을 사용하려면 1, SSE2 구현을 사용하지 않으려면 0입니다. 기본적으로 SSE2 구현은 지원하는 프로세서에서 사용할 수 있습니다.

## <a name="return-value"></a>반환 값

SSE2 구현을 사용할 수 있는 경우 0이 아닌 값이고, SSE2 구현을 사용할 수 없는 경우 0입니다.

## <a name="remarks"></a>설명

다음 함수는 사용 하 여 사용할 수 있는 SSE2 구현은 **_set_SSE2_enable**:

- [atan](atan-atanf-atanl-atan2-atan2f-atan2l.md)

- [ceil](ceil-ceilf-ceill.md)

- [exp](exp-expf.md)

- [floor](floor-floorf-floorl.md)

- [log](log-logf-log10-log10f.md)

- [log10](log-logf-log10-log10f.md)

- [modf](modf-modff-modfl.md)

- [pow](pow-powf-powl.md)

SSE2 중간 값은 64비트 부동 소수점 수량이지만 기본 구현 중간 값은 80비트 부동 소수점 수량이기 때문에 이러한 함수의 SSE2 구현은 기본 구현과는 약간 다른 결과를 낼 수 있습니다.

> [!NOTE]
> 사용 하는 경우는 [/Oi (내장 함수 생성)](../../build/reference/oi-generate-intrinsic-functions.md) 컴파일러 옵션을 프로젝트를 컴파일하는 하는 것이 나타날 **_set_SSE2_enable** 영향을 주지 않습니다. **/Oi** 의 효과 재정의 하는이 동작을 컴파일러 옵션 나타내는 컴파일러 내장 함수를 사용 하 여 CRT 호출을 대체 하는 권한을 **_set_SSE2_enable**합니다. 있다는 것을 보장 하려면 **/Oi** 재정의 하지 않습니다 **_set_SSE2_enable**, 사용 하 여 **/Oi-** 프로그램 프로젝트를 컴파일합니다. 내재 된 다른 컴파일러 스위치를 사용 하면 좋습니다 대해서도이 **/Oi**합니다.

SSE2 구현은 모든 예외가 마스크된 경우에만 사용됩니다. 예외를 마스크하려면 [_control87, _controlfp](control87-controlfp-control87-2.md)를 사용하세요.

## <a name="requirements"></a>요구 사항

|루틴|필수 헤더|
|-------------|---------------------|
|**_set_SSE2_enable**|\<math.h>|

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_set_SSE2_enable.c
// processor: x86
#include <math.h>
#include <stdio.h>

int main()
{
   int i = _set_SSE2_enable(1);

   if (i)
      printf("SSE2 enabled.\n");
   else
      printf("SSE2 not enabled; processor does not support SSE2.\n");
}
```

```Output
SSE2 enabled.
```

## <a name="see-also"></a>참고자료

[CRT 라이브러리 기능](../../c-runtime-library/crt-library-features.md)<br/>

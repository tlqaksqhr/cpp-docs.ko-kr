---
title: '&lt;limits&gt; | Microsoft 문서'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- limits/std::<limits>
- <limits>
dev_langs:
- C++
helpviewer_keywords:
- limits header
ms.assetid: e07d6379-5b00-4a3d-a789-40d41538b59e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 66f9401bed0a6c9d0b1ffa09a10f98afa258069d
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38964758"
---
# <a name="ltlimitsgt"></a>&lt;limits&gt;

템플릿 클래스 `numeric_limits`와 부동 소수점 표현 및 반올림과 관련된 두 개의 열거형을 정의합니다.

## <a name="syntax"></a>구문

```cpp
#include <limits>

```

## <a name="remarks"></a>설명

명시적 특수화 된 `numeric_limits` 클래스는 문자, 정수 및 부동 소수점 형식은 포함 하 여 기본 형식의 많은 속성을 설명 하 고 **bool** 구현으로 해결 하는 것이 아니라 정의 된 c + + 언어의 규칙입니다. \<limits>에 설명된 속성에는 정확도, 최소 및 최대 크기 표현, 반올림 및 신호 형식 오류가 포함됩니다.

### <a name="enumerations"></a>열거형

|||
|-|-|
|[float_denorm_style](../standard-library/limits-enums.md#float_denorm_style)|이 열거형은 구현에서 비정규화된 부동 소수점 값(너무 작아서 정규화된 값으로 나타낼 수 없는 값)을 나타내기 위해 선택할 수 있는 다양한 메서드를 설명합니다.|
|[float_round_style](../standard-library/limits-enums.md#float_round_style)|이 열거형은 구현에서 부동 소수점 값을 정수 값으로 반올림하기 위해 선택할 수 있는 다양한 메서드를 설명합니다.|

### <a name="classes"></a>클래스

|클래스|설명|
|-|-|
|[numeric_limits 클래스](../standard-library/numeric-limits-class.md)|이 템플릿 클래스는 기본 제공 숫자 형식의 산술 속성을 설명합니다.|

## <a name="see-also"></a>참고자료

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>

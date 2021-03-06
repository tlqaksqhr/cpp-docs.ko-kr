---
title: 컴파일러 경고 (수준 1) C4305 | Microsoft Docs
ms.custom: ''
ms.date: 1/17/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4305
dev_langs:
- C++
helpviewer_keywords:
- C4305
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7694c511f57b6907227d62f969b61218f836cb14
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33277825"
---
# <a name="compiler-warning-level-1-c4305"></a>컴파일러 경고(수준 1) C4305

> '*컨텍스트*':에서 잘림 '*type1*'to'*type2*'  

## <a name="remarks"></a>설명

이 경고는 정보의 손실 더 작은 형식 생성자 인수 또는 초기화는 값이 변환 될 때 발생 합니다.

## <a name="example"></a>예제

이 샘플에서는 두 가지 방법으로이 경고가 나타날 수 있습니다.

```cpp
// C4305.cpp
// Compile by using: cl /EHsc /W4 C4305.cpp

struct item
{
    item(float) {}
};

int main()
{
    float f = 2.71828;          // C4305 'initializing'
    item i(3.14159);            // C4305 'argument'
    return static_cast<int>(f);
}
```

이 문제를 해결 하려면 올바른 형식의 값을 사용 하 여 초기화 하거나 올바른 형식으로 명시적 캐스트를 사용 합니다. 사용 예를 들어는 **float** 대신 2.71828f 같은 리터럴는 **double** (부동 소수점 리터럴에 대 한 기본 형식)를 초기화 한 **float** 변수를 또는에 전달 하는 사용 하는 생성자는 **float** 인수입니다.

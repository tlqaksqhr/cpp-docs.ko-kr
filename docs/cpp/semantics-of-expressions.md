---
title: 식의 의미 체계 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- grammar, expressions
- expressions [C++], semantics
- expression evaluation
- expression evaluation, about expression evaluation
ms.assetid: 4a792154-533b-48b9-8709-31bfc170f0a7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3675e8bca6f62a1fbc7e30beefc6cbf6efbf197c
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39462744"
---
# <a name="semantics-of-expressions"></a>식의 의미
식은 해당 연산자의 그룹화 및 우선 순위에 따라 계산됩니다. ([연산자 우선순위 및 결합성](../cpp/cpp-built-in-operators-precedence-and-associativity.md) 에 [어휘 규칙](../cpp/lexical-conventions.md), 연산자가 식에 적용 된 c + + 관계를 보여 줍니다.)  
  
## <a name="order-of-evaluation"></a>계산 순서  
 다음 예제를 고려해 보세요.  
  
```cpp  
// Order_of_Evaluation.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
int main()  
{  
    int a = 2, b = 4, c = 9;  
  
    cout << a + b * c << "\n";  
    cout << a + (b * c) << "\n";  
    cout << (a + b) * c << "\n";  
}  
```  
  
```Output  
38  
38  
54  
```  
  
 ![식에서 계산 순서](../cpp/media/vc38zv1.gif "vc38ZV1")  
식 계산 순서  
  
 위의 그림에 표시된 식이 계산되는 순서는 연산자의 우선 순위 및 결합성에 따라 결정됩니다.  
  
1.  이 식에서는 곱셈(*)의 우선 순위가 가장 높습니다. 따라서 하위 식 `b * c`가 먼저 계산됩니다.  
  
2.  다음으로 덧셈(+)의 우선 순위가 높으므로 `a`와 `b`를 곱한 값에 `c`가 더해집니다.  
  
3.  식에서 왼쪽 시프트(<<)의 우선 순위가 가장 낮지만 이 항목은 두 번 발생합니다. 왼쪽 시프트 연산자는 왼쪽에서 오른쪽으로 그룹화하므로 왼쪽 하위 식이 먼저 계산된 다음 오른쪽 하위 식이 계산됩니다.  
  
 괄호를 사용하여 하위 식을 그룹화할 경우 다음 그림에 표시된 것처럼 우선 순위 및 식이 계산되는 순서도 변경됩니다.  
  
 ![괄호가 있는 식의 평가 순서](../cpp/media/vc38zv2.gif "vc38ZV2")  
괄호가 포함된 식 계산 순서  
  
 위의 그림에 있는 것과 같은 식은 전적으로 의도하지 않은 결과를 위해 계산되며, 이 경우에는 표준 출력 장치로 정보를 전송하기 위해 계산됩니다.  
  
## <a name="notation-in-expressions"></a>식에서의 표기법  
 C++ 언어는 피연산자를 지정할 때 특정 호환성을 지정합니다. 다음 표에서 피연산자의 형식이 허용 형식의 피연산자를 필요로 하는 운영자에 게 *형식*합니다.  
  
### <a name="operand-types-acceptable-to-operators"></a>연산자에 사용할 수 있는 피연산자 형식  
  
|필요한 형식|허용되는 형식|  
|-------------------|-------------------|  
|*type*|`const` *type*<br /> `volatile` *type*<br /> *type*&<br /> `const` *type*&<br /> `volatile` *type*&<br /> `volatile const` *type*<br /> `volatile const` *type*&|  
|*type*\*|*type*\*<br /> `const` *type*\*<br /> `volatile` *type*\*<br /> `volatile const` *type*\*|  
|`const` *type*|*type*<br /> `const` *type*<br />`const` *type*&|  
|`volatile` *type*|*type*<br /> `volatile` *type*<br /> `volatile` *type*&|  
  
 항상 이전 규칙을 조합하여 사용할 수 있으므로 포인터가 필요한 지점에 volatile 개체에 대한 const 포인터를 제공할 수 있습니다.  
  
## <a name="ambiguous-expressions"></a>모호한 식  
 특정 식의 의미가 모호합니다. 이러한 식은 개체의 값이 동일한 식에서 두 번 이상 변경될 때 가장 자주 발생합니다. 이러한 식은 언어에서 하나로 정의되지 않는 특정 계산 순서에 의존합니다. 다음 예제를 참조하세요.  
  
```  
int i = 7;  
  
func( i, ++i );  
```  
  
 C++ 언어에서는 함수 호출에 대한 인수가 계산되는 순서를 보장하지 않습니다. 따라서 위의 예제에서 매개 변수의 계산 방향이 왼쪽에서 오른쪽인지, 아니면 오른쪽에서 왼쪽인지에 따라 `func`는 매개 변수의 값으로 7과 8을 받거나 8과 8을 받을 수 있습니다.  
  
## <a name="c-sequence-points-microsoft-specific"></a>C++ 시퀀스 위치(Microsoft 전용)  
 식은 연속적인 "시퀀스 위치" 사이에서 개체의 값을 한 번만 수정할 수 있습니다.  
  
 현재 C++ 언어 정의는 시퀀스 위치를 지정하지 않습니다. Microsoft C++는 C 연산자를 사용하고 오버로드된 연산자는 사용하지 않는 모든 식에 대해 ANSI C와 동일한 시퀀스 위치를 사용합니다. 연산자가 오버로드되면 연산자 시퀀스에서 함수 호출 시퀀스로 의미 체계가 변경됩니다. Microsoft C++는 다음 시퀀스 위치를 사용합니다.  
  
-   논리 AND 연산자(&&)의 왼쪽 피연산자. 계속하기 전에 논리 AND 연산자의 왼쪽 피연산자가 완전히 계산되고 의도하지 않은 모든 결과가 완료됩니다. 논리 AND 연산자의 오른쪽 피연산자가 계산된다는 보장은 없습니다.  
  
-   논리 OR 연산자의 왼쪽 피연산자 (&#124;&#124;). 계속하기 전에 논리 OR 연산자의 왼쪽 피연산자가 완전히 계산되고 의도하지 않은 모든 결과가 완료됩니다. 논리 OR 연산자의 오른쪽 피연산자가 계산된다는 보장은 없습니다.  
  
-   쉼표 연산자의 왼쪽 피연산자. 계속하기 전에 쉼표 연산자의 왼쪽 피연산자가 완전히 계산되고 의도하지 않은 모든 결과가 완료됩니다. 쉼표 연산자의 두 피연산자는 항상 계산됩니다.  
  
-   함수 호출 연산자. 함수에 들어가기 전에 함수 호출 식 및 기본 인수를 포함한 함수의 모든 인수가 계산되고 의도하지 않은 모든 결과가 완료됩니다. 인수 또는 함수 호출 식에 대해 지정된 계산 순서는 없습니다.  
  
-   조건 연산자의 첫째 피연산자. 계속하기 전에 조건 연산자의 첫째 피연산자가 완전히 계산되고 의도하지 않은 모든 결과가 완료됩니다.  
  
-   전체 초기화 식의 끝(예: 선언 문에서 초기화의 끝)  
  
-   식 문의 식. 식 문은 선택적 식과 세미콜론(;)으로 구성됩니다. 식의 의도하지 않은 결과가 완전히 계산됩니다.  
  
-   선택(if 또는 switch) 문의 제어 식. 선택에 종속된 코드가 실행되기 전에 식이 완전히 계산되고 의도하지 않은 모든 결과가 완료됩니다.  
  
-   while 또는 do 문의 제어 식. while 또는 do 루프의 다음 반복에 있는 문이 실행되기 전에 식이 완전히 계산되고 의도하지 않은 모든 결과가 완료됩니다.  
  
-   for 문의 세 가지 식 각각. 다음 식으로 이동하기 전에 각 식이 완전히 계산되고 의도하지 않은 모든 결과가 완료됩니다.  
  
-   return 문의 식. 호출 함수로 제어가 반환되기 전에 식이 완전히 계산되고 의도하지 않은 모든 결과가 완료됩니다.  
  
## <a name="see-also"></a>참고자료  
 [식](../cpp/expressions-cpp.md)
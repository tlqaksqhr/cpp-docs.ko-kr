---
title: 컴파일러 오류 C3556 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3556
dev_langs:
- C++
helpviewer_keywords:
- C3556
ms.assetid: 9b002dcc-494e-414f-9587-20c2a0a39333
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a9579a5d3963d516328ec4febffc212ee497c615
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33255679"
---
# <a name="compiler-error-c3556"></a>컴파일러 오류 C3556
  
> '*식*': 'decltype' 인수가 잘못 되었습니다.  
  
컴파일러가 `decltype(`*expression*`)` 형식 지정자의 인수인 식의 형식을 추론할 수 없습니다.  
  
## <a name="example"></a>예제  
  
다음 코드 예제에서는 `myFunction` 이 오버로드되어 컴파일러가 `myFunction` 인수의 형식을 추론할 수 없습니다. 이 문제를 해결 하려면 사용할 수 있습니다 `static_cast` 오버 로드 된 함수에서 지정 하는 특정에 대 한 포인터의 인스턴스를 만들 수는 `decltype` 식입니다.  
  
```cpp  
// C3556.cpp
// compile with: cl /W4 /EHsc C3556.cpp
#include <iostream>

void myFunction(int);  
void myFunction(float, float); 

void callsMyFunction(decltype(myFunction) fn); // C3556
// One way to fix is to comment out the line above, and
// use static_cast to create specialized function pointer 
// instances:
auto myFunctionInt = static_cast<void(*)(int)>(myFunction);
auto myFunctionFloatFloat = static_cast<void(*)(float,float)>(myFunction);
void callsMyFunction(decltype(myFunctionInt) fn, int n);
void callsMyFunction(decltype(myFunctionFloatFloat) fn, float f, float g);

void myFunction(int i) { 
    std::cout << "called myFunction(" << i << ")" << std::endl; 
} 

void myFunction(float f, float g) { 
    std::cout << "called myFunction(" << f << ", " << g << ")" << std::endl; 
}  

void callsMyFunction(decltype(myFunctionInt) fn, int n) {
    fn(n);
}

void callsMyFunction(decltype(myFunctionFloatFloat) fn, float f, float g) {
    fn(f, g);
}

int main() {
    callsMyFunction(myFunction, 42);
    callsMyFunction(myFunction, 0.1f, 2.3f);
}
```
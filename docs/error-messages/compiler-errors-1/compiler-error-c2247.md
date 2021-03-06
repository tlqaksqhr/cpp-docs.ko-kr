---
title: 컴파일러 오류 C2247 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2247
dev_langs:
- C++
helpviewer_keywords:
- C2247
ms.assetid: 72efa03e-615e-4ef9-aede-0a98654b20fd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ed27398ea1f51ccc2ef0d3339446b422c7a503c0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33172315"
---
# <a name="compiler-error-c2247"></a>컴파일러 오류 C2247
' identifier' 'class'는 'class'에서 상속 하도록 'specifier'를 사용 하기 때문에 액세스할 수 없습니다.  
  
 `identifier` 전용 또는 보호 된 액세스로 선언 된 클래스에서 상속 됩니다.  
  
 다음 샘플에서는 C2247 오류가 생성 됩니다.  
  
```  
// C2247.cpp  
class A {  
public:  
   int i;  
};  
class B : private A {};    // B inherits a private A  
class C : public B {} c;   // so even though C's B is public  
int j = c.i;               // C2247, i not accessible  
```  
  
 이 오류는 Visual Studio.NET 2003에 대해 수행한 컴파일러 규칙 작업의 결과로 생성 될 수 있습니다: 보호 된 멤버가 포함 된 컨트롤에 액세스 합니다. 보호 된 멤버 (n) (A)는 (n) 멤버인 클래스에서 상속 되는 클래스 (B)의 멤버 함수를 통해 액세스할 수만 있습니다.  
  
 Visual Studio.NET 2003 및 Visual c + +의 Visual Studio.NET 버전 모두에 적용 되는 코드에 대 한 종류의 friend가 될 멤버를 선언 합니다. 공용 상속 사용 될 수도 있습니다.  
  
```  
// C2247b.cpp  
// compile with: /c  
// C2247 expected  
class A {  
public:  
   void f();  
   int n;  
};  
  
class B: protected A {  
   // Uncomment the following line to resolve.  
   // friend void A::f();  
};  
  
void A::f() {  
   B b;  
   b.n;  
}  
```  
  
 C2247 Visual Studio.NET 2003에 대해 수행한 컴파일러 규칙 작업의 결과로 생성 될 수 있습니다: 이제 전용 기본 클래스에 액세스할 수 없습니다. 전용 기본 클래스 형식에는 (A) 클래스 b (C)를 기본 클래스로 B를 사용 하는 형식에 액세스할 수 없습니다.  
  
 Visual Studio.NET 2003 및 Visual c + +의 Visual Studio.NET 버전 둘 다에 적용 되는 코드를 범위 연산자를 사용 합니다.  
  
```  
// C2247c.cpp  
// compile with: /c  
struct A {};  
  
struct B: private A {};  
  
struct C : B {  
   void f() {  
      A *p1 = (A*) this;   // C2247  
      // try the following line instead  
      // ::A *p2 = (::A*) this;  
   }  
};  
```
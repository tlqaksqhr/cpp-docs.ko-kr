---
title: 컴파일러 경고 (수준 4) C4481 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4481
dev_langs:
- C++
helpviewer_keywords:
- C4481
ms.assetid: 7bfd4e0c-b452-4e6c-b7c4-ac5cc93fe4ea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aeef5f2121808c5444af942fac0e3b72919f2354
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33293121"
---
# <a name="compiler-warning-level-4-c4481"></a>컴파일러 경고(수준 4) C4481
비표준 확장이 사용 됨: 재정의 지정자는 'keyword'  
  
 키워드는 c + + 표준에 /clr에서 작동 하는 재정의 지정자의 예를 들어 하나에 없는 사용 되었습니다.  자세한 내용은 다음 항목을 참조하세요.  
  
-   [/clr(공용 언어 런타임 컴파일)](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [Override 지정자](../../windows/override-specifiers-cpp-component-extensions.md)  
  
## <a name="example"></a>예제  
 다음 샘플에서는 C4481 오류가 발생 합니다.  
  
```  
// C4481.cpp  
// compile with: /W4 /c  
class B {  
   virtual void f(unsigned);  
};  
  
class C : B {  
   void f(unsigned) override;   // C4481  
   void f2(unsigned);  
};  
```
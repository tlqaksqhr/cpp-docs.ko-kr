---
title: 컴파일러 오류 C3652 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3652
dev_langs:
- C++
helpviewer_keywords:
- C3652
ms.assetid: 15d68737-177e-41f1-80e0-7c3e2afdf0fc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 12505ded20ab2a543355d51c7761a7f3acdf9feb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33263803"
---
# <a name="compiler-error-c3652"></a>컴파일러 오류 C3652
'override': 명시적으로 재정의 하는 함수는 가상 메서드여야 합니다.  
  
 명시적으로 재정의 하는 함수는 virtual 이어야 합니다. 자세한 내용은 참조 [명시적으로 재정의](../../windows/explicit-overrides-cpp-component-extensions.md)합니다.  
  
 다음 샘플에서는 C3652 오류가 생성 됩니다.  
  
```  
// C3652.cpp  
// compile with: /clr /c  
public interface class I {  
   void f();  
};  
  
public ref struct R : I {  
   void f() = I::f {}   // C3652  
   // try the following line instead  
   // virtual void f() = I::f {}  
};  
```
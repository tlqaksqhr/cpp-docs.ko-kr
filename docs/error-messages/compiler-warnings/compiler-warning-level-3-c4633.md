---
title: 컴파일러 경고 (수준 3) C4633 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4633
dev_langs:
- C++
helpviewer_keywords:
- C4633
ms.assetid: 6d76f268-ba8c-448b-8e83-b903a18b583b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5e77580f0aed27b824805e61c64901bf47604fc7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292716"
---
# <a name="compiler-warning-level-3-c4633"></a>컴파일러 경고(수준 3) C4633
XML 문서 주석 target: 오류: 이유  
  
 에 전달 된 이름을 [ \<param >](../../ide/param-visual-cpp.md) 태그 컴파일러에서 찾을 수 없습니다.  
  
 다음 샘플에서는 C4633 오류가 생성 됩니다.  
  
```  
// C4633.cpp  
// compile with: /clr /doc /LD /W3  
  
/// Text for class MyClass.  
public ref class MyClass {  
   // C4633 remove line for Int3  
   /// <param name="Int1">Used to indicate status.</param>  
   /// <param name="Int3">Used to indicate status.</param>  
   void MyMethod(int Int1) {  
      Int1 = 0;  
      Int1++;  
   }  
};  
```
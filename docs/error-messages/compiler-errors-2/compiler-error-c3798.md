---
title: 컴파일러 오류 C3798 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3798
dev_langs:
- C++
helpviewer_keywords:
- C3798
ms.assetid: b2f8b1d8-8812-49b8-a346-28e48f02ba5c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: da4ca81f2110ff1f76fdc9d0377234087a532017
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269056"
---
# <a name="compiler-error-c3798"></a>컴파일러 오류 C3798
'specifier': 속성 선언 (속성 get/set 메서드 대신에 배치 해야) 재정의 지정자를 사용할 수 없습니다  
  
 속성이 잘못 선언되었습니다. 자세한 내용은 다음 항목을 참조하세요.  
  
-   [속성](../../windows/property-cpp-component-extensions.md)  
  
-   [abstract](../../windows/abstract-cpp-component-extensions.md)  
  
-   [sealed](../../windows/sealed-cpp-component-extensions.md)  
  
## <a name="example"></a>예제  
 다음 샘플에서는 C3798  
  
```  
// C3798.cpp  
// compile with: /clr /c  
ref struct A {  
   property int Prop_1 abstract;   // C3798  
   property int Prop_2 sealed;   // C3798  
  
   // OK  
   property int Prop_3 {  
      virtual int get() abstract;  
      virtual void set(int i) abstract;  
   }  
  
   property int Prop_4 {  
      virtual int get() sealed;  
      virtual void set(int i) sealed;  
   }  
};  
```
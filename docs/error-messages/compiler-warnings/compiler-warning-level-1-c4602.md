---
title: 컴파일러 경고 (수준 1) C4602 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4602
dev_langs:
- C++
helpviewer_keywords:
- C4602
ms.assetid: c1f0300f-e2a2-4c9e-a7c3-4c7318d10509
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b2c25fd983f1ac7cebcc568a0b47c06c4d8e23a9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33279529"
---
# <a name="compiler-warning-level-1-c4602"></a>컴파일러 경고(수준 1) C4602
\#pragma pop_macro: '매크로 이름'이 식별자에 대 한 이전 #pragma push_macro가 없습니다  
  
 특정 매크로 대해 [pop_macro](../../preprocessor/pop-macro.md) 를 사용하는 경우 먼저 해당 매크로 이름을 [push_macro](../../preprocessor/push-macro.md)에 전달했어야 합니다. 예를 들어 다음 샘플에서는 C4602를 생성합니다.  
  
```  
// C4602.cpp  
// compile with: /W1  
int main()  
{  
   #pragma pop_macro("x")   // C4602 x is not on the stack  
}  
```
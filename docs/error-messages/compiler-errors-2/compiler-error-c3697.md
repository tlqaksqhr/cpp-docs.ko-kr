---
title: 컴파일러 오류 C3697 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3697
dev_langs:
- C++
helpviewer_keywords:
- C3697
ms.assetid: 2d3f63c4-b7f8-421d-a7a5-2bf17fd054f9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e4689365859ec121c716e5fb060d2985647bba30
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33263816"
---
# <a name="compiler-error-c3697"></a>컴파일러 오류 C3697
'한정자':에이 한정자를 사용할 수 없습니다 ' ^'  
  
 추적 핸들 (^)를 사용할 수 없는 한정자에 적용 되었습니다.  
  
 다음 샘플에서는 C3697 오류가 생성 됩니다.  
  
```  
// C3697.cpp  
// compile with: /clr  
using namespace System;  
int main() {  
   String ^__restrict s;   // C3697  
   String ^ s2;   // OK  
}  
```
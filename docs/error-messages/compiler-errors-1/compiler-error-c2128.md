---
title: 컴파일러 오류 C2128 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- c2128
dev_langs:
- C++
helpviewer_keywords:
- C2128
ms.assetid: 08cbf734-75b3-49f2-9026-9b319947612d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6db4621a39e704c2b9d19b66b388cc1899b8da12
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33168154"
---
# <a name="compiler-error-c2128"></a>컴파일러 오류 C2128
'function': alloc_text/same_seg는 C 링크가 있는 함수에만 적용  
  
 `pragma` `alloc_text` C 링크를 사용 하도록 선언 된 함수 에서만 사용할 수 있습니다.  
  
 다음 샘플에서는 생성 C2128 됩니다.  
  
```  
// C2128.cpp  
// compile with: /c  
  
// Delete the following line to resolve.  
void func();  
// #pragma alloc_text("my segment", func)   // C2128  
  
extern "C" {  
void func();  
}  
  
#pragma alloc_text("my segment", func)  
void func() {}  
```
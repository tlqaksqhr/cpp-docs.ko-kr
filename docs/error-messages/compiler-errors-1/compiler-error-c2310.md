---
title: 컴파일러 오류 C2310 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2310
dev_langs:
- C++
helpviewer_keywords:
- C2310
ms.assetid: 1969c682-b97e-43fb-b9a9-f783e7ff1710
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: baac68409820683182ff3ee592e00772141625cd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33168960"
---
# <a name="compiler-error-c2310"></a>컴파일러 오류 C2310
catch 처리기 유형임을 지정 해야 합니다.  
  
 Catch 처리기 형식이 없는 또는 여러 형식을 지정 합니다.  
  
 다음 샘플에서는 C2310 오류가 생성 됩니다.  
  
```  
// C2310.cpp  
// compile with: /EHsc  
#include <eh.h>  
int main() {  
   try {  
      throw "Out of memory!";  
   }  
   catch( int ,int) {}   // C2310 two types  
   // try the following line instead  
   // catch( int)  {}  
}  
```
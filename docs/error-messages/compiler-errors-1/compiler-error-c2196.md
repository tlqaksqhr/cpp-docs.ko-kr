---
title: 컴파일러 오류 C2196 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2196
dev_langs:
- C++
helpviewer_keywords:
- C2196
ms.assetid: fd2f6a58-48ce-4e58-96f8-e37720feb8e7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 378e8dccb5f5f0735cb941b3c0b3a791ba3c06a3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33167881"
---
# <a name="compiler-error-c2196"></a>컴파일러 오류 C2196
case 값 'value'를 이미 사용했습니다.  
  
 switch 문에서 동일한 case 값을 두 번 이상 사용합니다.  
  
 다음 샘플에서는 C2196을 생성합니다.  
  
```  
// C2196.cpp  
int main() {  
   int i = 0;  
   switch( i ) {  
   case 0:  
      break;  
   case 0:   // C2196  
   // try the following line instead  
   // case 1:  
      break;  
   }  
}  
```
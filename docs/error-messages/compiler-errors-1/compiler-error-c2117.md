---
title: 컴파일러 오류 C2117 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2117
dev_langs:
- C++
helpviewer_keywords:
- C2117
ms.assetid: b947379d-5861-42fc-ac26-170318579cbd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7a51bebc1edf7398d91356adb16f35443820cef2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33166876"
---
# <a name="compiler-error-c2117"></a>컴파일러 오류 C2117
'identifier': 배열 범위 오버플로입니다  
  
 배열에 이니셜라이저가 너무 많습니다.  
  
-   배열 요소와 이니셜라이저의 크기 및 수량이 일치 하지 않습니다.  
  
-   문자열에 null 종결자를 위한 공간이 없습니다.  
  
 다음 샘플에서는 C2117 오류가 생성 됩니다.  
  
```  
// C2117.cpp  
int main() {  
   char abc[4] = "abcd";   // C2117  
   char def[4] = "abd";   // OK  
}  
```
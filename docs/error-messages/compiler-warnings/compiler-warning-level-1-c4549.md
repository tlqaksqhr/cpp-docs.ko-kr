---
title: 컴파일러 경고 (수준 1) C4549 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4549
dev_langs:
- C++
helpviewer_keywords:
- C4549
ms.assetid: 81a07676-625b-4f58-9b0c-3ee22830b04a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a31a2aec4753cf0cd800ca22ea1e997a5929bf3d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33284331"
---
# <a name="compiler-warning-level-1-c4549"></a>컴파일러 경고(수준 1) C4549
'operator': 쉼표 효과가 없습니다; 앞의 연산자 'operator' 사용 하려고 했습니까?  
  
 컴파일러가 쉼표 잘못 된 형식의 식을 발견 했습니다.  
  
 기본적으로 이 경고는 해제되어 있습니다. 자세한 내용은 [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md)을 참조하세요.  
  
 다음 샘플에서는 C4549 오류가 생성 됩니다.  
  
```  
// C4549.cpp  
// compile with: /W1  
#pragma warning (default : 4549)  
  
int main() {  
   int i = 0, k = 0;  
  
   if ( i == 0, k )   // C4549  
   // try the following line instead  
   // if ( i == 0 )  
      i++;  
}  
```
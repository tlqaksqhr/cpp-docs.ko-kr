---
title: 컴파일러 오류 C2361 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2361
dev_langs:
- C++
helpviewer_keywords:
- C2361
ms.assetid: efbdaeb9-891c-4f7d-97da-89088a8413f3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9223916543119c16fc5d8c19bf5cb9ae38e77909
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33222282"
---
# <a name="compiler-error-c2361"></a>컴파일러 오류 C2361
'i'의 초기화 'default' 레이블에 의해 생략 되었습니다.  
  
 초기화 `identifier` 건너 뛸 수 있습니다는 `switch` 문. 선언 블록 포함 하지 않는 한 이니셜라이저와 함께 선언 점프할 수 없습니다. (하지 않은 블록 내에 선언 된 변수는 범위 내에서 끝날 때까지 `switch` 문.)  
  
 다음 샘플에서는 C2361 오류가 생성 됩니다.  
  
```  
// C2361.cpp  
void func( void ) {  
   int x;  
   switch (x) {  
   case 0 :  
      int i = 1;  
      { int j = 1; }  
   default :   // C2361 error  
      int k = 1;  
   }  
}  
```  
  
 해결 방법:  
  
```  
// C2361b.cpp  
// compile with: /c  
void func( void ) {  
   int x = 0;  
   switch (x) {  
   case 0 :  
      { int j = 1; int i = 1;}  
   default :  
      int k = 1;  
   }  
}  
```
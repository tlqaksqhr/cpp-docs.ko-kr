---
title: 컴파일러 오류 C2422 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2422
dev_langs:
- C++
helpviewer_keywords:
- C2422
ms.assetid: ef0ec302-4028-4778-b134-0b8cea4bcad9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 89a808e4b324b11c88be38ae7d8815bee4e232cd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33196349"
---
# <a name="compiler-error-c2422"></a>컴파일러 오류 C2422
'피연산자'에 잘못 된 세그먼트 재정의가 있습니다.  
  
 인라인 어셈블리 코드 올바르게에서 사용 했습니다 세그먼트 재정의 (콜론) 연산자를 피연산자입니다.  이 오류가 발생하는 원인은 다음과 같습니다.  
  
-   연산자 앞에 오는 레지스터가 세그먼트 레지스터가 아닙니다.  
  
-   연산자 앞에 오는 레지스터가 피연산자의 유일한 세그먼트 레지스터가 아닙니다.  
  
-   세그먼트 재정의 연산자 간접 참조 연산자 (괄호) 내에 나타납니다.  
  
-   세그먼트 재정의 연산자 다음에 나오는 식 직접 피연산자 또는 메모리 피연산자 아닙니다.  
  
 다음 샘플에서는 C2422 오류가 생성 됩니다.  
  
```  
// C2422.cpp  
// processor: x86  
int main() {  
   _asm {  
      mov AX, [BX:ES]   // C2422  
      mov AX, ES   // OK  
   }  
}  
```
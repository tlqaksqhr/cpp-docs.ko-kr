---
title: 컴파일러 오류 C2015 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2015
dev_langs:
- C++
helpviewer_keywords:
- C2015
ms.assetid: 8f40af0a-3a5a-4d6a-8ed7-125966e6bfed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 91c682aadeab5a572ec2bb5c2e649a1511af77ef
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33165625"
---
# <a name="compiler-error-c2015"></a>컴파일러 오류 C2015
상수에 문자가 너무 많습니다.  
  
 문자 상수 두 개 이상의 문자를 포함 합니다. 표준 문자 상수에 대 한 하나의 문자 및 긴 문자 상수에 대 한 두 개의 문자도 제한이 됩니다.  
  
 예: \t 이스케이프 시퀀스를 하나의 문자로 변환 됩니다.  
  
## <a name="example"></a>예제  
 다음 샘플에서는 C2015 오류가 생성 됩니다.  
  
```  
// C2015.cpp  
// compile with: /c  
  
char test1 = 'error';   // C2015  
char test2 = 'e';   // OK  
```  
  
## <a name="example"></a>예제  
 C2015는 Microsoft 확장을 정수로 변환할 문자 상수를 사용 하는 경우에 발생할 수 있습니다.  다음 샘플에서는 C2015 오류가 생성 됩니다.  
  
```  
// C2015b.cpp  
#include <stdio.h>  
  
int main()   
{  
    int a = 'abcde';   // C2015  
  
    int b = 'a';   // 'a' = ascii 0x61  
    printf_s("%x\n", b);  
}  
```
---
title: 컴파일러 오류 C2764 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2764
dev_langs:
- C++
helpviewer_keywords:
- C2764
ms.assetid: 3754f5af-e094-4425-be20-d0c9a9b5baec
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bd07a00e701804a56f74c86e8a0aedf67e470320
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33236455"
---
# <a name="compiler-error-c2764"></a>컴파일러 오류 C2764
'param': 템플릿 매개 변수 사용 하거나 부분 특수화 'specialization'에서 추론할 수 없습니다  
  
 부분 특수화에 템플릿 매개 변수가 사용 되지 않습니다. 이 부분 특수화를 사용할 수 없게 되므로 템플릿 매개 변수를 추론할 수 없습니다.  
  
## <a name="example"></a>예제  
 다음 샘플에서는 C2764 오류가 생성 됩니다.  
  
```  
// C2764.cpp  
#include <stdio.h>  
template <class T1, class T2>  
struct S  {  
   int m_i;  
};  
  
template <class T1, class T2>  
struct S<int, T2*> {   // C2764  
// try the following line instead  
// struct S<T1(*)(T2), T2*> {  
   char m_c;  
};  
  
int main() {  
   S<int, char> s1;  
   S<void (*)(short), short *> s2;  
   s2.m_c = 10;  
   s1.m_i = s2.m_c;  
   printf_s("%d\n", s1.m_i);  
}  
```
---
title: 컴파일러 오류 C2427 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2427
dev_langs:
- C++
helpviewer_keywords:
- C2427
ms.assetid: a7d421af-6180-40b4-b7a6-9f3bc7dfaaf9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b98f04dd02b4881f3177afd93b2acf74a304b7fc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33196911"
---
# <a name="compiler-error-c2427"></a>컴파일러 오류 C2427
'class':이 범위에서 클래스를 정의할 수 없습니다  
  
 중첩 된 클래스를 정의 하려고 했습니다 있지만 중첩 된 클래스는 기본 클래스, 하지 가장 포함 하는 클래스의 멤버입니다.  
  
 다음 샘플에서는 C2427 오류가 생성 됩니다.  
  
```  
// C2427.cpp  
// compile with: /c  
template <class T>   
struct S {  
   struct Inner;   
};   
  
struct Y : S<int> {};   
  
struct Y::Inner {};   // C2427  
  
// OK  
template<typename T>  
struct S<T>::Inner {};  
```
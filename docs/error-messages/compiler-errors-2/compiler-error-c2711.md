---
title: 컴파일러 오류 C2711 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2711
dev_langs:
- C++
helpviewer_keywords:
- C2711
ms.assetid: 9df9f808-7419-4e63-abdd-e6538ff0871f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fb2e5c904d7f6d865b94ea4fb4ba65be4c974f8b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33234277"
---
# <a name="compiler-error-c2711"></a>컴파일러 오류 C2711
'function': 두이 일 수 없습니다는 관리 코드로 #pragma 고려  
  
 일부 명령에서 바깥쪽 함수에 대 한 MSIL을 생성할 컴파일러 수 없게 됩니다.  
  
 다음 샘플에서는 C2711 오류가 생성 됩니다.  
  
```  
// C2711.cpp  
// compile with: /clr  
// processor: x86  
using namespace System;  
value struct V {  
   static const t = 10;  
};  
  
void bar() {  
   V::t;  
   __asm int 3   // C2711 inline asm can't be compiled managed  
}  
```
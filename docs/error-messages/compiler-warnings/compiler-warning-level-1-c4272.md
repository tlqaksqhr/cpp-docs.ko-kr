---
title: 컴파일러 경고 (수준 1) C4272 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4272
dev_langs:
- C++
helpviewer_keywords:
- C4272
ms.assetid: 0d6c1de4-2eef-42c4-b861-c221f8b495ef
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b6de736c3226a9d3377769b65604a458c08e25df
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33277201"
---
# <a name="compiler-warning-level-1-c4272"></a>컴파일러 경고(수준 1) C4272
'function': __declspec (dllimport); 표시 함수를 가져올 때에 네이티브 호출 규칙을 지정 해야 합니다.  
  
 으로 표시 된 함수를 내보내려면 오류가 발생 된 [__clrcall](../../cpp/clrcall.md) 표시 된 함수를 가져오려 할 경우이 경고가 발생 호출 규칙 및 컴파일러 `__clrcall`합니다.  
  
 다음 샘플에서는 C4272 오류가 생성 됩니다.  
  
```  
// C4272.cpp  
// compile with: /c /W1 /clr  
__declspec(dllimport) void __clrcall Test();   // C4272  
__declspec(dllimport) void Test2();   // OK  
```
---
title: 컴파일러 오류 C2337 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2337
dev_langs:
- C++
helpviewer_keywords:
- C2337
ms.assetid: eccc9178-a15e-42cd-bbd0-3cea7cf2d55b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: af10023a044e8f4f602ca6a018139d557b99dffe
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33195128"
---
# <a name="compiler-error-c2337"></a>컴파일러 오류 C2337
'attribute name': 특성을 찾을 수 없습니다.  
  
 이 버전의 Visual C++에서 지원되지 않는 특성을 사용했습니다.  
  
 다음 샘플에서는 C2337을 생성합니다.  
  
```  
// C2337.cpp  
// compile with: /c  
[emitidl];  
[module(name="x")];  
[grasshopper]   // C2337, not a supported attribute  
class a{};  
```
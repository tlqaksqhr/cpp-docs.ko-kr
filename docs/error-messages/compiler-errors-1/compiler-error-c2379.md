---
title: 컴파일러 오류 C2379 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2379
dev_langs:
- C++
helpviewer_keywords:
- C2379
ms.assetid: 37dc3015-a4af-4341-bbf3-da6150df7e51
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a1016bedfa9df0e9dfacb56734ee60397108d046
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33198078"
---
# <a name="compiler-error-c2379"></a>컴파일러 오류 C2379
형식 매개 변수 번호의 형식이 다릅니다.  
  
 지정 된 매개 변수 형식의 기본 확장이 긴 하지만 이전 선언에 형식이 호환 되지 않습니다. 이것은 ANSI C에서 오류 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))에서는 경고 이며 Microsoft 확장명 (**/Ze**).  
  
 다음 샘플에서는 C2379 오류가 생성 됩니다.  
  
```  
// C2379.c  
// compile with: /Za  
void func();  
void func(char);   // C2379, char promotes to int  
```
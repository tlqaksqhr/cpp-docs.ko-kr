---
title: 컴파일러 오류 C3455 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3455
dev_langs:
- C++
helpviewer_keywords:
- C3455
ms.assetid: 218e5cfe-5391-4eeb-81c2-85c47e3a6cd2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 61f48f16164327645eb0c1982e9e11e8ea394276
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33253382"
---
# <a name="compiler-error-c3455"></a>컴파일러 오류 C3455
'attribute': 해당 인수와 일치하는 특성 생성자가 없습니다.  
  
 잘못된 값이 특성을 선언하는 데 사용되었습니다.  자세한 내용은 [attribute](../../windows/attribute.md) 를 참조하세요.  
  
## <a name="example"></a>예제  
 다음 샘플에서는 C3455를 생성합니다.  
  
```  
// C3455.cpp  
// compile with: /clr /c  
using namespace System;  
  
[attribute("MyAt")]   // C3455  
// try the following line instead  
// [attribute(All)]  
ref struct MyAttr {  
   MyAttr() {}  
};  
```
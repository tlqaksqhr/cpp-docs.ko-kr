---
title: 컴파일러 오류 C3369 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3369
dev_langs:
- C++
helpviewer_keywords:
- C3369
ms.assetid: c6ceb9cb-3df9-4334-9a5c-d16db351d476
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a15a8e52b7bf311f20883c6ebc5635e86c6a7ffd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33248716"
---
# <a name="compiler-error-c3369"></a>컴파일러 오류 C3369
'module name': idl_module이 이미 정의되었습니다.  
  
 DLL을 정의하는 [idl_module](../../windows/idl-module.md) 사용은 프로그램에서 한 번만 발생할 수 있습니다.  
  
 다음 샘플에서는 C3369를 생성합니다.  
  
```  
// C3369.cpp  
// compile with: /c  
[idl_module(name="name1", dllname="x.dll")]; // C3369  
[idl_module(name="name1", dllname="x.dll")];  
```
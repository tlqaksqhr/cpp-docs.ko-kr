---
title: 컴파일러 경고 C4962 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4962
dev_langs:
- C++
helpviewer_keywords:
- C4962
ms.assetid: 62b156fe-04e5-4a6e-9339-6ab148185f87
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 74878342e153a78c6149ae3b177eff8c49e4a261
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33272102"
---
# <a name="compiler-warning-c4962"></a>컴파일러 경고 C4962
'function': 최적화를 하면 프로필 데이터가 일관성이 없어지므로 프로필 기반 최적화를 사용하지 않습니다.  
  
 함수의 개수(프로필) 데이터를 신뢰할 수 없기 때문에 함수가 /LTCG:PGO로 컴파일되지 않았습니다. 해당 함수에 대한 신뢰할 수 없는 프로필 데이터가 포함된 .pgc 파일을 다시 생성하려면 프로파일링을 다시 실행합니다.  
  
 기본적으로 이 경고는 해제되어 있습니다. 자세한 내용은 [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md)을 참조하세요.
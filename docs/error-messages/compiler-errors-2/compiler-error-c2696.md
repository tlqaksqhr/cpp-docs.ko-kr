---
title: 컴파일러 오류 C2696 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2696
dev_langs:
- C++
helpviewer_keywords:
- C2696
ms.assetid: 6c6eb7df-1230-4346-9a73-abf14c20785d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 65ccdd6d2c8c34c360811b80d5a93abe76f5ef8e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33235041"
---
# <a name="compiler-error-c2696"></a>컴파일러 오류 C2696
관리 되는 형식 'type'의 임시 개체를 만들 수 없습니다.  
  
에 대 한 참조 `const` 관리 되지 않는 프로그램에서 사용 하면 컴파일러가 생성자를 호출 하 고 스택에 임시 개체를 만듭니다. 그러나 관리 되는 클래스를 스택에 되지 만들 수 있습니다.  
  
C2696은 사용 되지 않는 컴파일러 옵션을 사용 하 여 연결할 수만 **/clr:oldSyntax**합니다.  

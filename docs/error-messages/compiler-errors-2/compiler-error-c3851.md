---
title: 컴파일러 오류 C3851 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3851
dev_langs:
- C++
helpviewer_keywords:
- C3851
ms.assetid: da30c21c-33aa-4439-8fb3-2f5021ea4985
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 82104776b2d1153310d0552bd873238333e746f2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33268837"
---
# <a name="compiler-error-c3851"></a>컴파일러 오류 C3851
'char': 유니버설 문자 이름에는 기본 문자 집합의 문자를 지정할 수 없습니다.  
  
 C++로 컴파일된 코드에서는 문자열 또는 문자 리터럴 외부에서 기본 소스 문자 집합의 문자를 나타내는 유니버설 문자 이름을 사용할 수 없습니다. 자세한 내용은 참조 [문자 집합](../../cpp/character-sets.md)합니다. C로 컴파일된 코드에서는 0x24('$'), 0x40('@') 또는 0x60('`')을 제외하고 0x20-0x7f(포함) 범위의 문자에 유니버설 문자 이름을 사용할 수 없습니다.  
  
 다음 샘플에서는 C3851을 생성하고 해결 방법을 보여 줍니다.  
  
```cpp  
// C3851.cpp  
int main()  
{  
   int test1_\u0041 = 0;   // C3851, \u0041 = 'A' in basic character set  
   int test2_A = 0;        // OK  
}  
```
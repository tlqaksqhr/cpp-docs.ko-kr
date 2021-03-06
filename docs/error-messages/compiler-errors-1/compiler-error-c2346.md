---
title: 컴파일러 오류 C2346 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2346
dev_langs:
- C++
helpviewer_keywords:
- C2346
ms.assetid: 246145be-5645-4cd6-867c-e3bc39e33dca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9459d7330738180e92776e93fcba9a07bfd39640
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33222295"
---
# <a name="compiler-error-c2346"></a>컴파일러 오류 C2346
'function' 네이티브로 컴파일할 수 없습니다: 이유  
  
 컴파일러는 함수를 MSIL로 컴파일할 수 없습니다.  
  
 자세한 내용은 참조 [관리, 관리 되지 않는](../../preprocessor/managed-unmanaged.md) 및 [/clr (공용 언어 런타임 컴파일)](../../build/reference/clr-common-language-runtime-compilation.md)합니다.  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
1.  MSIL로 컴파일할 수 없는 함수에서 코드를 제거 합니다.  
  
2.  사용 하 여 모듈을 컴파일하지 않거나 하나 **/clr**, 또는 관리 되지 않는 pragma 관리 되지 않는 함수로 표시 합니다.  
  
## <a name="example"></a>예제  
 다음 샘플에서는 C2346 오류가 발생 합니다.  
  
```  
// C2346.cpp  
// processor: x86  
// compile with: /clr   
// C2346 expected  
struct S  
{  
   S()  
   {  
      { __asm { nop } }  
   }  
   virtual __clrcall ~S() { }  
};  
  
void main()  
{  
   S s;  
}  
```
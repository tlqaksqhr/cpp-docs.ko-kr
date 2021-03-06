---
title: 인라인 어셈블리의 함수를 호출한 C | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- function calls, C functions
- function calls, in inline assembly
- functions [C], calling in inline assembly
- Visual C, functions
- inline assembly, calling functions
- __asm keyword [C++], calling functions
ms.assetid: f8a8d568-d175-4e23-9b24-36ef60a4cab3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c3f6d03ba77c7a4cdb3478a1bfe8729019dea002
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/28/2018
ms.locfileid: "32049520"
---
# <a name="calling-c-functions-in-inline-assembly"></a>인라인 어셈블리에서 C 함수 호출
## <a name="microsoft-specific"></a>Microsoft 전용  
 `__asm` 블록은 C 라이브러리 루틴을 비롯한 C 함수를 호출할 수 있습니다. 다음 예제에서는 `printf` 라이브러리 루틴을 호출합니다.  
  
```  
// InlineAssembler_Calling_C_Functions_in_Inline_Assembly.cpp  
// processor: x86  
#include <stdio.h>  
  
char format[] = "%s %s\n";  
char hello[] = "Hello";  
char world[] = "world";  
int main( void )  
{  
   __asm  
   {  
      mov  eax, offset world  
      push eax  
      mov  eax, offset hello  
      push eax  
      mov  eax, offset format  
      push eax  
      call printf  
      //clean up the stack so that main can exit cleanly  
      //use the unused register ebx to do the cleanup  
      pop  ebx  
      pop  ebx  
      pop  ebx  
   }  
}  
```  
  
 함수 인수가 스택에 전달되기 때문에 함수를 호출하기 전에 필요한 인수(이전 예제에서는 문자열 포인터)를 푸시하기만 하면 됩니다. 인수는 역순으로 푸시되므로 원하는 순서로 스택에서 나옵니다. 다음 C 문을 에뮬레이트하기 위해  
  
```  
printf( format, hello, world );  
```  
  
 예제에서는 `world`, `hello` 및 `format`에 대한 포인터를 이 순서대로 푸시한 다음 `printf`를 호출합니다.  
  
 **Microsoft 전용 종료**  
  
## <a name="see-also"></a>참고 항목  
 [인라인 어셈블러](../../assembler/inline/inline-assembler.md)
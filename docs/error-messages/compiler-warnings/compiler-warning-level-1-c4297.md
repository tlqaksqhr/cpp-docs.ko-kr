---
title: 컴파일러 경고 (수준 1) C4297 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4297
dev_langs:
- C++
helpviewer_keywords:
- C4297
ms.assetid: ba92fcdc-9f70-4f60-abe6-281f9582ca59
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d2c37f82b646902d08c8fc2ce633948969d0755f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33281978"
---
# <a name="compiler-warning-level-1-c4297"></a>컴파일러 경고(수준 1) C4297
'function': 함수는 예외를 throw하지 않도록 지정되었으나 예외를 throw했습니다.  
  
 함수 선언에는 (암시적 일 수 있는) `noexcept` 지정자, 빈 `throw` 예외 지정자 또는 [__declspec (nothrow)](../../cpp/nothrow-cpp.md) 특성과 정의 하나 이상 포함 [throw ](../../cpp/try-throw-and-catch-statements-cpp.md) 문. C4297를 해결하려면 선언된 `__declspec(nothrow)`, `noexcept(true)` 또는 `throw()`인 함수에서 예외를 throw하도록 시도하지 마세요. 또는 `noexcept`, `throw()` 또는 `__declspec(nothrow)` 사양을 제거합니다.  
  
 기본적으로 컴파일러에서는 사용자 정의 소멸자 및 비할당자 함수와 컴파일러에서 생성된 특수 멤버 함수에 대한 암시적 `noexcept(true)` 지정자를 생성합니다. 이는 ISO C++11 표준을 따릅니다. 암시적 noexcept 지정자의 생성을 방지 하 컴파일러 Visual Studio 2013의 비표준 동작으로 되돌리려면, 사용 된 **/zc: implicitnoexcept-** 컴파일러 옵션입니다. 자세한 내용은 참조 [/zc: implicitnoexcept (암시적 예외 지정자)](../../build/reference/zc-implicitnoexcept-implicit-exception-specifiers.md)합니다.  
  
 예외 사양에 대 한 자세한 내용은 참조 하십시오. [예외 사양 (throw)](../../cpp/exception-specifications-throw-cpp.md)합니다. 참고: [/EH (예외 처리 모델)](../../build/reference/eh-exception-handling-model.md) 컴파일 타임에 예외 처리 동작을 수정 하는 방법에 대 한 내용은 합니다.  
  
 __Declspec에도이 경고가 생성 됩니다 ([dllexport](../../cpp/dllexport-dllimport.md)) 함수 c + + 함수의 경우에 extern "C"를 표시 합니다.  
  
 다음 샘플에서는 C4297 오류가 발생하는 경우를 보여 줍니다.  
  
```  
// C4297.cpp  
// compile with: /W1 /LD  
void __declspec(nothrow) f1()   // declared nothrow  
// try the following line instead  
// void f1()  
{  
   throw 1;   // C4297  
}  
```
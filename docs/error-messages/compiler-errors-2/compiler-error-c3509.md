---
title: 컴파일러 오류 C3509 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3509
dev_langs:
- C++
helpviewer_keywords:
- C3509
ms.assetid: cc2db39a-2f98-4e40-b803-496e585494e6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d28504941efcf3eb2138b0926a4f16eae637fe6d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33257417"
---
# <a name="compiler-error-c3509"></a>컴파일러 오류 C3509
'type': 자동화 반환 형식이 잘못 되었습니다. 'void', 'HRESULT' 또는 'SCODE' 해야 경우 매개 변수는 표시 된 'retval', 반환 형식  
  
 COM 인터페이스에서 메서드는 void 또는 HRESULT 반환 해야 합니다.  
  
 다음 샘플에서는 C3509 오류가 생성 됩니다.  
  
```  
// C3509.cpp  
#define _ATL_DEBUG_QI  
  
#define WIN32_LEAN_AND_MEAN   // Exclude rarely-used stuff from Windows headers  
#define STRICT  
#ifndef _WIN32_WINNT  
#define _WIN32_WINNT 0x0400  
#endif  
  
#define _ATL_ATTRIBUTES 1  
#include <atlbase.h>  
extern CComModule _Module;  
#include <atlcom.h>  
#include <atlctl.h>  
#include <atlstr.h>  
  
[module(name=oso)];  
  
[dispinterface, uuid(00000000-0000-0000-0000-000000000001)]  
__interface I {  
   [id(1)] int f([out, retval] int*);   // C3509  
   // try the following line instead  
   // [id(1)] void f([out, retval] int*);  
};  
  
[coclass, uuid(00000000-0000-0000-0000-000000000002)]  
struct C : I {  
   int f(int*) {  
   // try the following line instead, and delete return statement  
   // void f(int*) {  
      return 0;  
   }  
};  
  
int main() {  
}  
```
---
title: 링커 도구 오류 LNK2020 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2020
dev_langs:
- C++
helpviewer_keywords:
- LNK2020
ms.assetid: 4dd017d0-5e83-471b-ac8a-538ac1ed6870
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 33dd1b381d36a90f2e9b144e690e364ac512c081
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33301959"
---
# <a name="linker-tools-error-lnk2020"></a>링커 도구 오류 LNK2020
확인 되지 않은 토큰 '토큰이 있습니다.  
  
 참조 메타 데이터를 통해이 제외 하 고 정의 되지 않은 외부 오류로 유사 합니다. 메타 데이터의 모든 함수 및 데이터를 정의 합니다.  
  
 해결 방법:  
  
-   누락 된 함수 또는 데이터를 정의 하거나  
  
-   개체 파일 또는 누락 된 함수 또는 데이터가 이미 정의 된 라이브러리를 포함 합니다.  
  
## <a name="example"></a>예제  
 다음 샘플에서는 LNK2020 합니다.  
  
```  
// LNK2020.cpp  
// compile with: /clr /LD  
ref struct A {  
   A(int x);   // LNK2020  
   static int f();   // LNK2020  
};  
  
// OK  
ref struct B {  
   B(int x) {}  
   static int f() { return 0; }  
};  
```  
  
## <a name="example"></a>예제  
 LNK2020 관리 되는 서식 파일 형식의 변수를 만들지만 형식을 인스턴스화하지 않습니다 하는 경우에 발생 합니다.  
  
 다음 샘플에서는 LNK2020 합니다.  
  
```  
// LNK2020_b.cpp  
// compile with: /clr   
  
template <typename T>  
ref struct Base {  
   virtual void f1() {};  
};  
  
template <typename T>  
ref struct Base2 {  
   virtual void f1() {};  
};  
  
int main() {  
   Base<int>^ p;   // LNK2020  
   Base2<int>^ p2 = gcnew Base2<int>();   // OK  
};  
```
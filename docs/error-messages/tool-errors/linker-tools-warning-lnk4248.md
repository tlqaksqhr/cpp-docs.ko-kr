---
title: 링커 도구 경고 LNK4248 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4248
dev_langs:
- C++
helpviewer_keywords:
- LNK4248
ms.assetid: e40523ff-e3cb-4ba6-ab79-23f0f339f6cf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e3b67661d1ad260f388f8425420711ae2f708ce3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302635"
---
# <a name="linker-tools-warning-lnk4248"></a>링커 도구 경고 LNK4248
확인 되지 않은 형식 정의 토큰 (토큰) 'type'; 이미지가 실행 되지 않습니다.  
  
 형식에는 MSIL 메타 데이터에는 정의 되어 있지 않습니다.  
  
 LNK4248 MSIL 모듈의 형식에 대 한 정방향 선언에만 있는 경우 발생할 수 있습니다 (사용 하 여 컴파일된 **/clr**), MSIL 모듈에서 형식을 참조 및 MSIL 모듈이에 대 한 정의가 있는 네이티브 모듈에 링크 형식입니다.  
  
 이 경우 링커는 MSIL 메타 데이터에 네이티브 형식 정의 제공 합니다 하 고 올바른 동작에 대 한를 제공할 수 있습니다.  
  
 그러나 전달 형식 선언을 CLR 형식인 경우 다음 링커의 네이티브 형식 정의가 올바르지 않을 수 있습니다.  
  
 자세한 내용은 [/clr(공용 언어 런타임 컴파일)](../../build/reference/clr-common-language-runtime-compilation.md)을 참조하세요.  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
1.  MSIL 모듈의 형식 정의 제공 합니다.  
  
## <a name="example"></a>예제  
 다음 샘플에서는 LNK4248 합니다. 해결 하려면 구조체 A를 정의 합니다.  
  
```  
// LNK4248.cpp  
// compile with: /clr /W1  
// LNK4248 expected  
struct A;  
void Test(A*){}  
  
int main() {  
   Test(0);  
}  
```  
  
## <a name="example"></a>예제  
 다음 샘플에서는 형식의 앞으로 정의 합니다.  
  
```  
// LNK4248_2.cpp  
// compile with: /clr /c  
class A;   // provide a definition for A here to resolve  
A * newA();  
int valueA(A * a);  
  
int main() {  
   A * a = newA();  
   return valueA(a);  
}  
```  
  
## <a name="example"></a>예제  
 다음 샘플에서는 LNK4248 합니다.  
  
```  
// LNK4248_3.cpp  
// compile with: /c  
// post-build command: link LNK4248_2.obj LNK4248_3.obj  
class A {  
public:   
   int b;  
};  
  
A* newA() {  
   return new A;  
}  
  
int valueA(A * a) {  
   return (int)a;  
}  
```
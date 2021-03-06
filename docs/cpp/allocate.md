---
title: 할당 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- allocate_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], allocate
- allocate __declspec keyword
ms.assetid: 67828b31-de60-4c0e-b0a6-ef3aab22641d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 82ce0af801b77a9566bd6395a9f03b05f41676d7
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/01/2018
ms.locfileid: "39408768"
---
# <a name="allocate"></a>할당
**Microsoft 전용**  
  
 합니다 **할당할** 선언 지정자는 데이터 항목이 할당 될 데이터 세그먼트 이름을 지정 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
   __declspec(allocate("segname")) declarator  
```  
  
## <a name="remarks"></a>설명  
 이름을 *segname* 다음 pragma 중 하나를 사용 하 여 선언 해야 합니다.  
  
-   [code_seg](../preprocessor/code-seg.md)  
  
-   [const_seg](../preprocessor/const-seg.md)  
  
-   [data_seg](../preprocessor/data-seg.md)  
  
-   [init_seg](../preprocessor/init-seg.md)  
  
-   [section](../preprocessor/section.md)  
  
## <a name="example"></a>예  
  
```cpp 
// allocate.cpp  
#pragma section("mycode", read)  
__declspec(allocate("mycode"))  int i = 0;  
  
int main() {  
}  
```  
  
 **Microsoft 전용 종료**  
  
## <a name="see-also"></a>참고자료  
 [__declspec](../cpp/declspec.md)   
 [키워드](../cpp/keywords-cpp.md)
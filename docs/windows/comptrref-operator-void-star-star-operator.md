---
title: 'Comptrref:: Operator void * * 연산자 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef::operator void**
dev_langs:
- C++
helpviewer_keywords:
- operator void** operator
ms.assetid: f020045c-9de4-4392-8783-73f0fc0761c6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 16fa7964af8f56ec54f6870b8866e69266bdc414
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39648791"
---
# <a name="comptrrefoperator-void-operator"></a>Comptrref:: Operator void\* \* 연산자
WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
operator void**() const;  
```  
  
## <a name="remarks"></a>설명  
 현재 삭제 **ComPtrRef** 개체에서 나타내는 인터페이스에 대 한 포인터 캐스팅, 합니다 **ComPtrRef** 개체에 대 한 포인터--포인터-을 변수로 **void**, 차례로 캐스트 포인터를 반환합니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** client.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>참고 항목  
 [ComPtrRef 클래스](../windows/comptrref-class.md)   
 [Microsoft::WRL::Details 네임스페이스](../windows/microsoft-wrl-details-namespace.md)
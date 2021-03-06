---
title: 'Weakreference:: Decrementstrongreference 메서드 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference::DecrementStrongReference
dev_langs:
- C++
helpviewer_keywords:
- DecrementStrongReference method
ms.assetid: 97d70d9f-41b8-4f8d-a6fa-4137cc4f9029
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 19dcb3e90faef86fd291381a7082e8b5bfa89069
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40013459"
---
# <a name="weakreferencedecrementstrongreference-method"></a>WeakReference::DecrementStrongReference 메서드
WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
ULONG DecrementStrongReference();  
```  
  
## <a name="remarks"></a>설명  
 현재는 강력한 참조 횟수를 감소 시킵니다 **WeakReference** 개체입니다.  
  
 강력한 참조 횟수가 0이 되 면 강력한 참조로 설정 됩니다 **nullptr**합니다.  
  
## <a name="return-value"></a>반환 값  
 감소 된 강력한 참조 수입니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** implements.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>참고 항목  
 [WeakReference 클래스](../windows/weakreference-class1.md)  
 [Microsoft::WRL::Details 네임스페이스](../windows/microsoft-wrl-details-namespace.md)
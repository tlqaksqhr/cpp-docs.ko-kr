---
title: 'Eventtargetarray:: Addtail 메서드 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::EventTargetArray::AddTail
dev_langs:
- C++
helpviewer_keywords:
- AddTail method
ms.assetid: d0fafab9-049c-40e0-a40c-d126c9ee63e6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3e80bf6d4313be5c90b4b4486cb31f3705252f33
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39651267"
---
# <a name="eventtargetarrayaddtail-method"></a>EventTargetArray::AddTail 메서드
WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
void AddTail(  
   _In_ IUnknown* element  
);  
```  
  
### <a name="parameters"></a>매개 변수  
 *요소*  
 추가할 이벤트 처리기에 대 한 포인터입니다.  
  
## <a name="remarks"></a>설명  
 이벤트 처리기의 내부 배열의 끝에 지정된 된 이벤트 처리기를 추가합니다.  
  
 **AddTail()** 만 내부적으로 사용할 수는 `EventSource` 클래스입니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** event.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>참고 항목  
 [EventTargetArray 클래스](../windows/eventtargetarray-class.md)   
 [Microsoft::WRL::Details 네임스페이스](../windows/microsoft-wrl-details-namespace.md)
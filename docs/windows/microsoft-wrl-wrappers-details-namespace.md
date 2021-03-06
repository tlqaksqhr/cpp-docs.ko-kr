---
title: Microsoft::WRL::Wrappers::Details Namespace | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details
- internal/Microsoft::WRL::Details
- async/Microsoft::WRL::Details
- corewrappers/Microsoft::WRL::Wrappers::Details
- client/Microsoft::WRL::Details
- module/Microsoft::WRL::Details
- event/Microsoft::WRL::Details
dev_langs:
- C++
helpviewer_keywords:
- Details namespace
ms.assetid: 6d3f04ac-9b53-4a82-a188-a85309ec34a4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3f74f8fe3e5b637869af7b03bb2eaf5e13df9550
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40020165"
---
# <a name="microsoftwrlwrappersdetails-namespace"></a>Microsoft::WRL::Wrappers::Details 네임스페이스
WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
namespace Microsoft::WRL::Wrappers::Details;  
```  
  
## <a name="members"></a>멤버  
  
### <a name="classes"></a>클래스  
  
|이름|설명|  
|----------|-----------------|  
|[SyncLockT 클래스](../windows/synclockt-class.md)|단독으로 사용할 수 있는 형식을 나타내는 또는 리소스의 소유권을 공유 합니다.|  
|[SyncLockWithStatusT 클래스](../windows/synclockwithstatust-class.md)|단독으로 사용할 수 있는 형식을 나타내는 또는 리소스의 소유권을 공유 합니다.|  
  
### <a name="methods"></a>메서드  
  
|이름|설명|  
|----------|-----------------|  
|[CompareStringOrdinal 메서드](../windows/comparestringordinal-method.md)|지정 된 두 `HSTRING` 개체 및 정렬 순서에서 상대 위치를 나타내는 정수를 반환 합니다.|  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>참고 항목  
 [Microsoft::WRL::Wrappers 네임스페이스](../windows/microsoft-wrl-wrappers-namespace.md)
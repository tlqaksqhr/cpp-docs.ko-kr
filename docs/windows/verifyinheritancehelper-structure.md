---
title: VerifyInheritanceHelper 구조체 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::VerifyInheritanceHelper
dev_langs:
- C++
helpviewer_keywords:
- VerifyInheritanceHelper structure
ms.assetid: 8a48a702-0f71-4807-935b-8311f0a7a8b6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7ed375a30ddadf72b7eee8a2cc852dec6620a992
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40011119"
---
# <a name="verifyinheritancehelper-structure"></a>VerifyInheritanceHelper 구조체
WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
template <  
   typename I,  
   typename Base  
>  
struct VerifyInheritanceHelper;  
template <  
   typename I  
>  
struct VerifyInheritanceHelper<I, Nil>;  
```  
  
### <a name="parameters"></a>매개 변수  
 *I*  
 형식입니다.  
  
 *자료*  
 다른 형식입니다.  
  
## <a name="remarks"></a>설명  
 하나의 인터페이스는 다른 인터페이스에서 파생 됩니다 있는지 테스트 합니다.  
  
## <a name="members"></a>멤버  
  
### <a name="public-methods"></a>Public 메서드  
  
|이름|설명|  
|----------|-----------------|  
|[VerifyInheritanceHelper::Verify 메서드](../windows/verifyinheritancehelper-verify-method.md)|현재 템플릿 매개 변수로 지정 된 두 가지 인터페이스를 테스트 하 고 하나의 인터페이스는 다른 파생 되었는지 여부를 결정 합니다.|  
  
## <a name="inheritance-hierarchy"></a>상속 계층  
 `VerifyInheritanceHelper`  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** implements.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>참고 항목  
 [Microsoft::WRL::Details 네임스페이스](../windows/microsoft-wrl-details-namespace.md)
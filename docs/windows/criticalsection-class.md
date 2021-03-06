---
title: CriticalSection 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection
dev_langs:
- C++
helpviewer_keywords:
- CriticalSection class
ms.assetid: f2e0a024-71a3-4f6b-99ea-d93a4a608ac4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b65ded3ae56eb1d57bad771a8875cce4948d2953
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642095"
---
# <a name="criticalsection-class"></a>CriticalSection 클래스
임계 영역 개체를 나타냅니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
class CriticalSection;  
```  
  
## <a name="members"></a>멤버  
  
### <a name="constructor"></a>생성자  
  
|name|설명|  
|----------|-----------------|  
|[CriticalSection::CriticalSection 생성자](../windows/criticalsection-criticalsection-constructor.md)|뮤텍스 개체와 유사하지만 단일 프로세스의 스레드에만 사용할 수 있는 동기화 개체를 초기화합니다.|  
|[CriticalSection::~CriticalSection 소멸자](../windows/criticalsection-tilde-criticalsection-destructor.md)|초기화를 취소 하 고 현재 소멸 **CriticalSection** 개체입니다.|  
  
### <a name="public-methods"></a>Public 메서드  
  
|이름|설명|  
|----------|-----------------|  
|[CriticalSection::TryLock 메서드](../windows/criticalsection-trylock-method.md)|임계 영역을 차단 하지 않고 입력 하려고 합니다. 호출이 성공 하면 호출 스레드가 중요 섹션의 소유권을 갖습니다.|  
|[CriticalSection::Lock 메서드](../windows/criticalsection-lock-method.md)|지정된 임계 영역 개체의 소유권을 기다립니다. 함수가 호출 스레드가 소유권을 부여받는 시기를 반환합니다.|  
|[CriticalSection::IsValid 메서드](../windows/criticalsection-isvalid-method.md)|현재 임계 영역이 유효한지 여부를 나타냅니다.|  
  
### <a name="protected-data-members"></a>보호된 데이터 멤버  
  
|name|설명|  
|----------|-----------------|  
|[CriticalSection::cs_ 데이터 멤버](../windows/criticalsection-cs-data-member.md)|임계 영역 데이터 멤버를 선언합니다.|  
  
## <a name="inheritance-hierarchy"></a>상속 계층  
 `CriticalSection`  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>참고 항목  
 [Microsoft::WRL::Wrappers 네임스페이스](../windows/microsoft-wrl-wrappers-namespace.md)
---
title: 'Verifyinheritancehelper:: Verify 메서드 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::VerifyInheritanceHelper::Verify
dev_langs:
- C++
helpviewer_keywords:
- Verify method
ms.assetid: 3360082b-81ad-4191-9ec3-b4372f7207d7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 04bf01b5fad5a9fec579e347497a28b5e8abb861
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40018818"
---
# <a name="verifyinheritancehelperverify-method"></a>VerifyInheritanceHelper::Verify 메서드
WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
static void Verify();  
```  
  
## <a name="remarks"></a>설명  
 현재 템플릿 매개 변수로 지정 된 두 가지 인터페이스를 테스트 하 고 하나의 인터페이스는 다른 파생 되었는지 여부를 결정 합니다.  
  
 오류는 하나의 인터페이스는 다른에서 파생 되지 않은 경우에 내보내집니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** implements.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>참고 항목  
 [VerifyInheritanceHelper 구조체](../windows/verifyinheritancehelper-structure.md)   
 [Microsoft::WRL::Details 네임스페이스](../windows/microsoft-wrl-details-namespace.md)
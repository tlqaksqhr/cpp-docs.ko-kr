---
title: SafeAdd | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeAdd
dev_langs:
- C++
helpviewer_keywords:
- SafeAdd function
ms.assetid: 3f82b91d-59fe-4ee1-873b-d056182fa8be
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9ff51780cc05a4c133975d95dc89455a90e717d1
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40014614"
---
# <a name="safeadd"></a>SafeAdd
오버플로 방지 하는 방식으로 두 숫자를 추가 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
template<typename T, typename U>  
inline bool SafeAdd (  
   T t,  
   U u,  
   T& result  
) throw ();  
```  
  
### <a name="parameters"></a>매개 변수  
 [in] *t*  
 추가할 첫 번째 숫자입니다. T 형식이어야 합니다.  
  
 [in] *u*  
 추가할 두 번째 숫자입니다. U 형식이어야 합니다.  
  
 [out] *결과*  
 매개 변수가 있는 **SafeAdd** 결과 저장 합니다.  
  
## <a name="return-value"></a>반환 값  
 **true** 오류가 발생 하지 않으면; **false** 오류가 발생 합니다.  
  
## <a name="remarks"></a>설명  
 이 메서드는 부분 [SafeInt 라이브러리](../windows/safeint-library.md) 의 인스턴스를 만들지 않고 단일 추가 작업을 위해 설계 되는 [SafeInt 클래스](../windows/safeint-class.md)합니다.  
  
> [!NOTE]
>  이 메서드는 단일 수학 연산을 보호해야 하는 경우에만 사용해야 합니다. 작업이 여러 개 있으면 개별 독립 실행형 함수를 호출하는 대신 `SafeInt` 클래스를 사용해야 합니다.  
  
 템플릿 형식 T 및 U에 대 한 자세한 내용은 참조 하세요. [SafeInt 함수](../windows/safeint-functions.md)합니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** safeint.h  
  
 **Namespace:** microsoft:: utilities  
  
## <a name="see-also"></a>참고 항목  
 [SafeInt 함수](../windows/safeint-functions.md)   
 [SafeInt 라이브러리](../windows/safeint-library.md)   
 [SafeInt 클래스](../windows/safeint-class.md)   
 [SafeSubtract](../windows/safesubtract.md)
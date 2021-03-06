---
title: pointer_default | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.pointer_default
dev_langs:
- C++
helpviewer_keywords:
- pointer_default attribute
ms.assetid: 2d0c7bbc-a1e8-4337-9e54-e304523e2735
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 98e3b9e78f46b14dfeca18a8e69538111d3ba219
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40010317"
---
# <a name="pointerdefault"></a>pointer_default
매개 변수 목록에 표시 되는 최상위 포인터를 제외 하 고 모든 포인터에 대 한 기본 포인터 특성을 지정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
[ pointer_default(  
   value  
) ]  
```  
  
### <a name="parameters"></a>매개 변수  
 *값*  
 포인터 형식을 설명 하는 값: **ptr**하십시오 **ref**, 또는 **고유**.  
  
## <a name="remarks"></a>설명  
 합니다 **pointer_default** c + + 특성에 동일한 기능을 합니다 [pointer_default](http://msdn.microsoft.com/library/windows/desktop/aa367141) MIDL 특성입니다.  
  
## <a name="example"></a>예  
 예를 참조 하세요 [defaultvalue](../windows/defaultvalue.md) 의 샘플 사용에 대 한 **pointer_default**합니다.  
  
## <a name="requirements"></a>요구 사항  
  
### <a name="attribute-context"></a>특성 컨텍스트  
  
|||  
|-|-|  
|**적용 대상**|**interface**|  
|**반복 가능**|아니요|  
|**필수 특성**|없음|  
|**잘못된 특성**|없음|  
  
 특성 컨텍스트에 대한 자세한 내용은 [특성 컨텍스트](../windows/attribute-contexts.md)를 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [IDL 특성](../windows/idl-attributes.md)   
 [인터페이스 특성](../windows/interface-attributes.md)   
---
title: defaultvalue | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.defaultvalue
dev_langs:
- C++
helpviewer_keywords:
- defaultvalue attribute
ms.assetid: efa5d050-b2cc-4d9e-9b8e-79954f218d3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: deda09913f2774a2b3b246a285df0c8b6f1c62eb
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39652827"
---
# <a name="defaultvalue"></a>defaultvalue
형식화 된 선택적 매개 변수 기본값을 지정할 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
[ defaultvalue= value ]  
```  
  
### <a name="parameters"></a>매개 변수  
 *값*  
 매개 변수의 기본 값입니다.  
  
## <a name="remarks"></a>설명  
 합니다 **defaultvalue** c + + 특성에 동일한 기능을 합니다 [defaultvalue](http://msdn.microsoft.com/library/windows/desktop/aa366793) MIDL 특성입니다.  
  
## <a name="example"></a>예  
 다음 코드를 사용 하 여 인터페이스 메서드를 표시 합니다 **defaultvalue** 특성:  
  
```cpp  
// cpp_attr_ref_defaultvalue.cpp  
// compile with: /LD  
#include <windows.h>  
  
[export] typedef long HRESULT;  
[export, ptr, string] typedef unsigned char * MY_STRING_TYPE;  
  
[  uuid("479B29EE-9A2C-11D0-B696-00A0C903487A"),  
   dual, oleautomation,  
   helpstring("IFireTabCtrl Interface"),  
   helpcontext(122), pointer_default(unique) ]  
  
__interface IFireTabCtrl : IDispatch {  
   [bindable, propget] HRESULT get_Size([out, retval, defaultvalue("33")] long *nSize);  
   [bindable, propput] HRESULT put_Size([in] int nSize);  
};  
  
[ module(name="ATLFIRELib", uuid="479B29E1-9A2C-11D0-B696-00A0C903487A",  
      version="1.0", helpstring="ATLFire 1.0 Type Library") ];  
```  
  
## <a name="requirements"></a>요구 사항  
  
### <a name="attribute-context"></a>특성 컨텍스트  
  
|||  
|-|-|  
|**적용 대상**|인터페이스 매개 변수|  
|**반복 가능**|아니요|  
|**필수 특성**|없음|  
|**잘못된 특성**|없음|  
  
 자세한 내용은 [특성 컨텍스트](../windows/attribute-contexts.md)를 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [IDL 특성](../windows/idl-attributes.md)   
 [매개 변수 특성](../windows/parameter-attributes.md)   
 [out](../windows/out-cpp.md)   
 [retval](../windows/retval.md)   
 [in](../windows/in-cpp.md)   
 [pointer_default](../windows/pointer-default.md)   
 [unique](../windows/unique-cpp.md)   
---
title: 연산자 Type ^ | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: b24ffc83-0780-4f9a-8ee0-f5725db339d1
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3c0900da889e5bf9e8629349593ffce7740a1cf0
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34256287"
---
# <a name="operator-type"></a>연산자 Type^
[Windows::UI::Xaml::Interop::TypeName](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx) 을 `Platform::Type`으로 변환할 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
Operator Type^(Windows::UI::Xaml::Interop::TypeName typeName)  
```  
  
### <a name="return-value"></a>반환 값  
 `Platform::Type` Windows::UI::Xaml::Interop::TypeName [이 제공되면](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx)을 반환합니다.  
  
### <a name="remarks"></a>설명  
 `TypeName` 은 형식 정보를 나타내기 위한 언어 중립 Windows 런타임 구조체입니다. [Platform::Type](../cppcx/platform-type-class.md) 은 C++에서만 사용되며 ABI(응용 프로그램 이진 인터페이스) 전반에서 전달될 수 없습니다. 다음은 `TypeName`Navigate [함수에서](http://msdn.microsoft.com/library/windows/apps/hh702394.aspx) 을 사용하는 한 가지 방법입니다.  
  
```  
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);  
```  
  
### <a name="example"></a>예제  
 다음 예제에서는 `TypeName` 과 `Type`간을 변환하는 방법을 보여 줍니다.  
  
```  
  
// Convert from Type to TypeName  
TypeName tn = TypeName(MainPage::typeid);  
  
// Convert back from TypeName to Type  
Type^ tx2 = (Type^)(tn);  
  
```  
  
## <a name="net-framework-equivalent"></a>.NET Framework의 해당 값  
 .NET Framework는 `TypeName` 프로젝트를 [System.Type](assetId:///System.Type?qualifyHint=False&autoUpgrade=True)으로 변환할 수 있습니다.  
  
### <a name="requirements"></a>요구 사항  
  
## <a name="see-also"></a>참고 항목  
 [Windows::UI::Xaml::Interop::TypeName 연산자](../cppcx/operator-windows-ui-xaml-interop-typename.md)   
 [Platform::Type 클래스](../cppcx/platform-type-class.md)
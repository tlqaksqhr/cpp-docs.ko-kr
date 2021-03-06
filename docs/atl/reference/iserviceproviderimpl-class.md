---
title: IServiceProviderImpl 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IServiceProviderImpl
- ATLCOM/ATL::IServiceProviderImpl
- ATLCOM/ATL::IServiceProviderImpl::QueryService
dev_langs:
- C++
helpviewer_keywords:
- IServiceProviderImpl class
- IServiceProvider interface, ATL implementation
ms.assetid: 251254d3-c4ce-40d7-aee0-3d676d1d72f2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2e298f8398041b7b83a581b95f95c4ff9521cd4b
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37883608"
---
# <a name="iserviceproviderimpl-class"></a>IServiceProviderImpl 클래스
이 클래스의 기본 구현을 제공 합니다 `IServiceProvider` 인터페이스입니다.  
  
## <a name="syntax"></a>구문  
  
```
template <class T>  
class ATL_NO_VTABLE IServiceProviderImpl : public IServiceProvider
```  
  
#### <a name="parameters"></a>매개 변수  
 *T*  
 클래스에서 파생 된 `IServiceProviderImpl`합니다.  
  
## <a name="members"></a>멤버  
  
### <a name="public-methods"></a>Public 메서드  
  
|이름|설명|  
|----------|-----------------|  
|[IServiceProviderImpl::QueryService](#queryservice)|만듭니다 또는 지정된 된 서비스에 액세스 하 고 지정된 된 인터페이스는 서비스에 대 한 인터페이스 포인터를 반환 합니다.|  
  
## <a name="remarks"></a>설명  
 `IServiceProvider` 인터페이스 해당 GUID로 지정 된 서비스를 찾고 서비스에서 요청된 된 인터페이스에 대 한 인터페이스 포인터를 반환 합니다. 클래스 `IServiceProviderImpl` 이 인터페이스의 기본 구현을 제공 합니다.  
  
 `IServiceProviderImpl` 하나의 메서드를 지정 합니다. [QueryService](#queryservice), 생성 되 나 지정된 된 서비스에 액세스 하 고 서비스에 대해 지정된 된 인터페이스에 인터페이스 포인터를 반환 합니다.  
  
 `IServiceProviderImpl` 부터, 서비스 맵을 사용 하 여 [BEGIN_SERVICE_MAP](service-map-macros.md#begin_service_map) 끝나는 [END_SERVICE_MAP](service-map-macros.md#end_service_map)합니다.  
  
 두 항목을 포함 하는 서비스 맵: [SERVICE_ENTRY](service-map-macros.md#service_entry), 개체에 의해 지원 되는 지정 된 서비스 id (SID)를 나타내는 및 [SERVICE_ENTRY_CHAIN](service-map-macros.md#service_entry_chain)를 호출 하는 `QueryService` 다른 연결 개체입니다.  
  
## <a name="inheritance-hierarchy"></a>상속 계층  
 `IServiceProvider`  
  
 `IServiceProviderImpl`  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** atlcom.h  
  
##  <a name="queryservice"></a>  IServiceProviderImpl::QueryService  
 만듭니다 또는 지정된 된 서비스에 액세스 하 고 지정된 된 인터페이스는 서비스에 대 한 인터페이스 포인터를 반환 합니다.  
  
```
STDMETHOD(QueryService)(
    REFGUID guidService,
    REFIID riid,
    void** ppvObject);
```  
  
### <a name="parameters"></a>매개 변수  
 [IN] *guidService*  
 서비스 식별자 (SID)에 대 한 포인터입니다.  
  
 [IN] *riid*  
 호출자가 액세스할 인터페이스의 식별자입니다.  
  
 [OUT] *ppvObj*  
 요청된 된 인터페이스에 대 한 간접 포인터입니다.  
  
### <a name="return-value"></a>반환 값  
 반환 된 HRESULT 값을 다음 중 하나입니다.  
  
|반환 값|의미|  
|------------------|-------------|  
|S_OK|성공적으로 서비스를 만들거나 검색 됩니다.|  
|E_INVALIDARG|하나 이상의 인수가 잘못된 경우|  
|E_OUTOFMEMORY|서비스를 만들 충분 한 메모리가 없습니다.|  
|E_UNEXPECTED|알 수 없는 오류가 발생했습니다.|  
|E_NOINTERFACE|요청된 된 인터페이스가이 서비스의 일부가 아니거나 서비스 알 수 없는 합니다.|  
  
### <a name="remarks"></a>설명  
 `QueryService` 지정된 된 서비스에서 요청된 된 인터페이스에 대 한 간접 포인터를 반환합니다. 호출자에 게는 더 이상 필요한 경우이 포인터를 해제 하는 일을 담당 합니다.  
  
 호출 하는 경우 `QueryService`을 두는 서비스 id를 전달 하면 (*guidService*) 및 인터페이스 식별자 (*riid*). *guidService* 액세스 하려는 서비스를 지정 하며 *riid* 서비스의 일부인 인터페이스를 식별 합니다. 반환 시 인터페이스에 대 한 간접 포인터를 받게 됩니다.  
  
 인터페이스를 구현 하는 개체는 다른 서비스의 일부인 인터페이스를 구현할 수도 있습니다. 다음을 살펴보세요.  
  
-   이러한 인터페이스의 일부 선택 사항이 될 수 있습니다. 서비스 설명에 정의 된 모든 인터페이스 반환 된 모든 개체 또는 서비스의 모든 구현에서 반드시 변수가 있습니다.  
  
-   에 대 한 호출 달리 `QueryInterface`, 다양 한 서비스 식별자를 전달 해도 반드시 다른 구성 요소 개체 모델 (COM) 개체를 반환 됩니다.  
  
-   반환된 된 개체에는 서비스 정의의 일부분이 아닌 추가 인터페이스 있을 수 있습니다.  
  
 SID_SMyService SID_SYourService, 등 두 개의 서비스에 둘 다 지정할 수 동일한 인터페이스를 사용 하지만 인터페이스 구현의 두 서비스 간에 공통 전혀 없을 수 있습니다. 이 작동 하기 때문에 대 한 호출 `QueryService` (SID_SMyService, IID_IDispatch)는 다른 개체를 반환할 수 있습니다 `QueryService` (SID_SYourService, IID_IDispatch). 개체 id는 다양 한 서비스 식별자를 지정 하는 경우에 간주 되지 않습니다.  
  
## <a name="see-also"></a>참고 항목  
 [클래스 개요](../../atl/atl-class-overview.md)

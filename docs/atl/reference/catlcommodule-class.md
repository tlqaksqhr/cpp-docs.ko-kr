---
title: CAtlComModule 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAtlComModule
- ATLBASE/ATL::CAtlComModule
- ATLBASE/ATL::CAtlComModule::CAtlComModule
- ATLBASE/ATL::CAtlComModule::RegisterServer
- ATLBASE/ATL::CAtlComModule::RegisterTypeLib
- ATLBASE/ATL::CAtlComModule::UnregisterServer
- ATLBASE/ATL::CAtlComModule::UnRegisterTypeLib
dev_langs:
- C++
helpviewer_keywords:
- CAtlComModule class
ms.assetid: af5dd71a-a0d1-4a2e-9a24-154a03381c75
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b553a6b99afd2de34c11aa0ad8a979580177d042
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37885064"
---
# <a name="catlcommodule-class"></a>CAtlComModule 클래스
이 클래스는 COM 서버 모듈을 구현합니다.  
  
## <a name="syntax"></a>구문  
  
```
class CAtlComModule : public _ATL_COM_MODULE
```  
  
## <a name="members"></a>멤버  
  
### <a name="public-constructors"></a>Public 생성자  
  
|이름|설명|  
|----------|-----------------|  
|[CAtlComModule::CAtlComModule](#catlcommodule)|생성자입니다.|  
|[CAtlComModule:: ~ CAtlComModule](#dtor)|소멸자입니다.|  
  
### <a name="public-methods"></a>Public 메서드  
  
|이름|설명|  
|----------|-----------------|  
|[CAtlComModule::RegisterServer](#registerserver)|개체 맵의 각 개체에 대 한 시스템 레지스트리를 업데이트 하려면이 메서드를 호출 합니다.|  
|[CAtlComModule::RegisterTypeLib](#registertypelib)|형식 라이브러리를 등록 하려면이 메서드를 호출 합니다.|  
|[CAtlComModule::UnregisterServer](#unregisterserver)|개체 맵의 각 개체의 등록을 취소 하려면이 메서드를 호출 합니다.|  
|[CAtlComModule::UnRegisterTypeLib](#unregistertypelib)|형식 라이브러리의 등록을 취소 하려면이 메서드를 호출 합니다.|  
  
## <a name="remarks"></a>설명  
 `CAtlComModule` COM 서버 모듈의 경우 모듈의 구성 요소에 액세스 하는 클라이언트를 구현 합니다.  
  
 이 클래스는 사용 되지 않는 대체 [CComModule](../../atl/reference/ccommodule-class.md) ATL.의 이전 버전에서 사용 되는 클래스 참조 [ATL 모듈 클래스](../../atl/atl-module-classes.md) 대 한 자세한 내용은 합니다.  
  
## <a name="inheritance-hierarchy"></a>상속 계층  
 [_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)  
  
 `CAtlComModule`  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** atlbase.h  
  
##  <a name="catlcommodule"></a>  CAtlComModule::CAtlComModule  
 생성자입니다.  
  
```
CAtlComModule() throw();
```  
  
### <a name="remarks"></a>설명  
 모듈을 초기화 합니다.  
  
##  <a name="dtor"></a>  CAtlComModule:: ~ CAtlComModule  
 소멸자입니다.  
  
```
~CAtlComModule();
```  
  
### <a name="remarks"></a>설명  
 모든 클래스 팩터리를 해제합니다.  
  
##  <a name="registerserver"></a>  CAtlComModule::RegisterServer  
 개체 맵의 각 개체에 대 한 시스템 레지스트리를 업데이트 하려면이 메서드를 호출 합니다.  
  
```
HRESULT RegisterServer(BOOL bRegTypeLib = FALSE, const CLSID* pCLSID = NULL);
```  
  
### <a name="parameters"></a>매개 변수  
 *bRegTypeLib*  
 TRUE 이면 형식 라이브러리 등록 됩니다. 기본값은 FALSE입니다.  
  
 *하면*  
 등록할 개체의 CLSID 가리킵니다. NULL (기본값), 개체 맵의 모든 개체를 등록할 경우.  
  
### <a name="return-value"></a>반환 값  
 성공 하면 s_ok이 고, 또는 실패 시 오류 HRESULT 반환합니다.  
  
### <a name="remarks"></a>설명  
 전역 함수를 호출 [AtlComModuleRegisterServer](server-registration-global-functions.md#atlcommoduleregisterserver)합니다.  
  
##  <a name="registertypelib"></a>  CAtlComModule::RegisterTypeLib  
 형식 라이브러리를 등록 하려면이 메서드를 호출 합니다.  
  
```
HRESULT RegisterTypeLib(LPCTSTR lpszIndex);
HRESULT RegisterTypeLib();
```  
  
### <a name="parameters"></a>매개 변수  
 *lpszIndex*  
 형식에서 문자열 "\\\N", 여기서 N은 TYPELIB 리소스의 정수 인덱스입니다.  
  
### <a name="return-value"></a>반환 값  
 성공 하면 s_ok이 고, 또는 실패 시 오류 HRESULT 반환합니다.  
  
### <a name="remarks"></a>설명  
 시스템 레지스트리를 형식 라이브러리에 대 한 정보를 추가합니다. 모듈 인스턴스 형식 라이브러리가 여러 개 있으면는 형식 라이브러리를 사용할지 지정 하려면이 메서드의 첫 번째 버전을 사용 합니다.  
  
##  <a name="unregisterserver"></a>  CAtlComModule::UnregisterServer  
 개체 맵의 각 개체의 등록을 취소 하려면이 메서드를 호출 합니다.  
  
```
HRESULT UnregisterServer(
  BOOL bRegTypeLib = FALSE,  
  const CLSID* pCLSID = NULL);
```  
  
### <a name="parameters"></a>매개 변수  
 *bRegTypeLib*  
 형식 라이브러리 등록을 취소할 이면 TRUE입니다. 기본값은 FALSE입니다.  
  
 *하면*  
 등록을 취소할 개체의 CLSID 가리킵니다. 경우 NULL (기본값), 개체 맵의 모든 개체를 등록 취소 됩니다.  
  
### <a name="return-value"></a>반환 값  
 성공 하면 s_ok이 고, 또는 실패 시 오류 HRESULT 반환합니다.  
  
### <a name="remarks"></a>설명  
 전역 함수를 호출 [AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver)합니다.  
  
##  <a name="unregistertypelib"></a>  CAtlComModule::UnRegisterTypeLib  
 형식 라이브러리의 등록을 취소 하려면이 메서드를 호출 합니다.  
  
```
HRESULT UnRegisterTypeLib(LPCTSTR lpszIndex);
HRESULT UnRegisterTypeLib();
```  
  
### <a name="parameters"></a>매개 변수  
 *lpszIndex*  
 형식에서 문자열 "\\\N", 여기서 N은 TYPELIB 리소스의 정수 인덱스입니다.  
  
### <a name="remarks"></a>설명  
 시스템 레지스트리에서 형식 라이브러리에 대 한 정보를 제거합니다. 모듈 인스턴스 형식 라이브러리가 여러 개 있으면는 형식 라이브러리를 사용할지 지정 하려면이 메서드의 첫 번째 버전을 사용 합니다.  
  
### <a name="return-value"></a>반환 값  
 성공 하면 s_ok이 고, 또는 실패 시 오류 HRESULT 반환합니다.  
  
## <a name="see-also"></a>참고 항목  
 [_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)   
 [클래스 개요](../../atl/atl-class-overview.md)

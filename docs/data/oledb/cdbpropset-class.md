---
title: CDBPropSet 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDBPropSet
- ATL.CDBPropSet
- ATL::CDBPropSet
- CDBPropSet::AddProperty
- CDBPropSet.AddProperty
- AddProperty
- ATL::CDBPropSet::AddProperty
- ATL.CDBPropSet.AddProperty
- CDBPropSet.CDBPropSet
- CDBPropSet::CDBPropSet
- ATL::CDBPropSet::CDBPropSet
- ATL.CDBPropSet.CDBPropSet
- CDBPropSet.operator=
- ATL::CDBPropSet::operator=
- ATL.CDBPropSet.operator=
- CDBPropSet::operator=
- ATL.CDBPropSet.SetGUID
- CDBPropSet.SetGUID
- ATL::CDBPropSet::SetGUID
- SetGUID
- CDBPropSet::SetGUID
dev_langs:
- C++
helpviewer_keywords:
- CDBPropSet class
- AddProperty method
- CDBPropSet class, constructor
- operator =, property sets
- = operator, with OLE DB templates
- operator=, property sets
- SetGUID method
- AddProperty method
ms.assetid: 54190149-c277-4679-b81a-ef484d4d1c00
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 15a1506980519880652abc637549ec2c7bf17e1d
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/30/2018
ms.locfileid: "39337599"
---
# <a name="cdbpropset-class"></a>CDBPropSet 클래스
상속 되는 `DBPROPSET` 구조체 및 키 필드를 초기화 하는 생성자를 추가 `AddProperty` 메서드에 액세스 합니다.  
  
## <a name="syntax"></a>구문

```cpp
class CDBPropSet : public tagDBPROPSET  
```  

## <a name="requirements"></a>요구 사항  
 **헤더:** atldbcli.h  

## <a name="members"></a>멤버  
  
### <a name="methods"></a>메서드  
  
|||  
|-|-|  
|[AddProperty](#addproperty)|속성 집합에는 속성을 추가합니다.|  
|[CDBPropSet](#cdbpropset)|생성자입니다.|  
|[SetGUID](#setguid)|집합의 `guidPropertySet` 필드는 `DBPROPSET` 구조입니다.|  
  
### <a name="operators"></a>연산자  
  
|||  
|-|-|  
|[operator =](#op_equal)|하나의 속성이 다른 설정의 콘텐츠를 할당 합니다.|  
  
## <a name="remarks"></a>설명  
 OLE DB 공급자와 소비자가 사용 하 여 `DBPROPSET` 배열을 전달 하는 구조 `DBPROP` 구조입니다. 각 `DBPROP` 구조 설정할 수 있는 단일 속성을 나타냅니다.  

## <a name="addproperty"></a> Cdbpropset:: Addproperty
속성 집합에는 속성을 추가합니다.  
  
### <a name="syntax"></a>구문  
  
```cpp
bool AddProperty(DWORD dwPropertyID,   
   constVARIANT& var,   
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,  
   LPCSTR szValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,  
   LPCWSTR szValue,DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,  
   bool bValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,  
   BYTE bValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED);bool AddProperty(DWORD dwPropertyID,  
   short nValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED);bool AddProperty(DWORD dwPropertyID,  
   long nValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED);bool AddProperty(DWORD dwPropertyID,  
   float fltValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED);bool AddProperty(DWORD dwPropertyID,  
   double dblValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,  
   CY cyValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();  
```  
  
#### <a name="parameters"></a>매개 변수  
 *dwPropertyID*  
 [in] 추가할 속성의 ID입니다. 초기화 하는 데 사용 합니다 `dwPropertyID` 의 `DBPROP` 구조 속성 집합에 추가 합니다.  
  
 *var*  
 [in] 에 대 한 속성 값을 초기화 하는 데 사용 하는 variant를 `DBPROP` 구조 속성 집합에 추가 합니다.  
  
 *szValue*  
 [in] 에 대 한 속성 값을 초기화 하는 데 사용 하는 문자열을 `DBPROP` 구조 속성 집합에 추가 합니다.  
  
 *bValue*  
 [in] A `BYTE` 또는 부울 값에 대 한 속성 값을 초기화 하는 데는 `DBPROP` 구조 속성 집합에 추가 합니다.  
  
 *n 값*  
 [in] 에 대 한 속성 값을 초기화 하는 데 사용 하는 정수 값을 `DBPROP` 구조 속성 집합에 추가 합니다.  
  
 *fltValue*  
 [in] 부동 소수점 값에 대 한 속성 값을 초기화 하는 데는 `DBPROP` 구조 속성 집합에 추가 합니다.  
  
 *dblValue*  
 [in] 에 대 한 속성 값을 초기화 하는 데 사용 하는 배정밀도 부동 소수점 값을 `DBPROP` 구조 속성 집합에 추가 합니다.  
  
 *cyValue*  
 [in] CY 통화 값에 대 한 속성 값을 초기화 하는 데는 `DBPROP` 구조 속성 집합에 추가 합니다.  
  
### <a name="return-value"></a>반환 값  
 **true** 경우 속성이 추가 되었습니다. 그렇지 않으면 **false**합니다. 

## <a name="cdbpropset"></a> Cdbpropset:: Cdbpropset
생성자입니다. 초기화 합니다 `rgProperties`, `cProperties`, 및 `guidPropertySet` 의 필드를 [DBPROPSET](https://msdn.microsoft.com/library/ms714367.aspx) 구조입니다.  
  
### <a name="syntax"></a>구문  
  
```cpp
CDBPropSet(const GUID& guid);  

CDBPropSet(const CDBPropSet& propset);  

CDBPropSet();  
```  
  
#### <a name="parameters"></a>매개 변수  
 *guid*  
 [in] GUID를 초기화 하는 데는 `guidPropertySet` 필드입니다.  
  
 *propset*  
 [in] 복사 생성을 위한 다른 `CDBPropSet` 개체입니다.  

## <a name="setguid"></a> Cdbpropset:: Setguid
집합의 `guidPropertySet` 필드에 `DBPROPSET` 구조입니다.  
  
### <a name="syntax"></a>구문  
  
```cpp
void SetGUID(const GUID& guid) throw();  
```  
  
#### <a name="parameters"></a>매개 변수  
 *guid*  
 [in] 설정 하는 데 GUID를 `guidPropertySet` 필드를 [DBPROPSET](https://msdn.microsoft.com/library/ms714367.aspx) 구조입니다.  
  
### <a name="remarks"></a>설명  
 이 필드에서 설정할 수는 [생성자](../../data/oledb/cdbpropset-cdbpropset.md) 도 합니다.  

## <a name="op_equal"></a> Cdbpropset:: Operator =
콘텐츠를 다른 속성 집합에 두 속성을 할당 합니다.  
  
### <a name="syntax"></a>구문  
  
```cpp
CDBPropSet& operator =(CDBPropSet& propset) throw();  
```  
  
## <a name="see-also"></a>참고 항목  
 [OLE DB 소비자 템플릿](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 소비자 템플릿 참조](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CDBPropIDSet 클래스](../../data/oledb/cdbpropidset-class.md)   
 [DBPROPSET 구조](https://msdn.microsoft.com/library/ms714367.aspx)   
 [DBPROP 구조](https://msdn.microsoft.com/library/ms717970.aspx)
---
title: CDefaultCharTraits 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CDefaultCharTraits
- ATLCOLL/ATL::CDefaultCharTraits
- ATLCOLL/ATL::CDefaultCharTraits::CharToLower
- ATLCOLL/ATL::CDefaultCharTraits::CharToUpper
dev_langs:
- C++
helpviewer_keywords:
- CDefaultCharTraits class
ms.assetid: f94a3934-597f-401d-8513-ed6924ae069a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e591bc8c77e2130548e65c6197f9e550efc480fb
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37881856"
---
# <a name="cdefaultchartraits-class"></a>CDefaultCharTraits 클래스
이 클래스는 대 문자와 소문자 사이 문자를 변환 하기 위한 두 개의 정적 함수를 제공 합니다.  
  
## <a name="syntax"></a>구문  
  
```
template <typename T>  
class CDefaultCharTraits
```  
  
#### <a name="parameters"></a>매개 변수  
 *T*  
 컬렉션에 저장할 데이터의 형식입니다.  
  
## <a name="members"></a>멤버  
  
### <a name="public-methods"></a>Public 메서드  
  
|이름|설명|  
|----------|-----------------|  
|[CDefaultCharTraits::CharToLower](#chartolower)|(정적) 문자를 대문자로 변환 하려면이 함수를 호출 합니다.|  
|[CDefaultCharTraits::CharToUpper](#chartoupper)|(정적) 문자를 소문자로 변환 하려면이 함수를 호출 합니다.|  
  
## <a name="remarks"></a>설명  
 이 클래스는 클래스에 의해 사용 되는 함수를 제공 [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)합니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** atlcoll.h  
  
##  <a name="chartolower"></a>  CDefaultCharTraits::CharToLower  
 문자를 소문자로 변환 하려면이 함수를 호출 합니다.  
  
```
static wchar_t CharToLower(wchar_t x);  
static char CharToLower(char x);
```  
  
### <a name="parameters"></a>매개 변수  
 *x*  
 소문자로 변환할 문자입니다.  
  
### <a name="example"></a>예  
 [!code-cpp[NVC_ATL_Utilities#132](../../atl/codesnippet/cpp/cdefaultchartraits-class_1.cpp)]  
  
##  <a name="chartoupper"></a>  CDefaultCharTraits::CharToUpper  
 문자를 대문자로 변환 하려면이 함수를 호출 합니다.  
  
```
static wchar_t CharToUpper(wchar_t x);  
static char CharToUpper(char x);
```  
  
### <a name="parameters"></a>매개 변수  
 *x*  
 대문자로 변환할 문자입니다.  
  
## <a name="see-also"></a>참고 항목  
 [클래스 개요](../../atl/atl-class-overview.md)

---
title: CUIntArray 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CUIntArray
- AFXCOLL/CUIntArray
- AFXCOLL/CObArray::CObArray
- AFXCOLL/CObArray::Add
- AFXCOLL/CObArray::Append
- AFXCOLL/CObArray::Copy
- AFXCOLL/CObArray::ElementAt
- AFXCOLL/CObArray::FreeExtra
- AFXCOLL/CObArray::GetAt
- AFXCOLL/CObArray::GetCount
- AFXCOLL/CObArray::GetData
- AFXCOLL/CObArray::GetSize
- AFXCOLL/CObArray::GetUpperBound
- AFXCOLL/CObArray::InsertAt
- AFXCOLL/CObArray::IsEmpty
- AFXCOLL/CObArray::RemoveAll
- AFXCOLL/CObArray::RemoveAt
- AFXCOLL/CObArray::SetAt
- AFXCOLL/CObArray::SetAtGrow
- AFXCOLL/CObArray::SetSize
dev_langs:
- C++
helpviewer_keywords:
- CObArray [MFC], CObArray
- CObArray [MFC], Add
- CObArray [MFC], Append
- CObArray [MFC], Copy
- CObArray [MFC], ElementAt
- CObArray [MFC], FreeExtra
- CObArray [MFC], GetAt
- CObArray [MFC], GetCount
- CObArray [MFC], GetData
- CObArray [MFC], GetSize
- CObArray [MFC], GetUpperBound
- CObArray [MFC], InsertAt
- CObArray [MFC], IsEmpty
- CObArray [MFC], RemoveAll
- CObArray [MFC], RemoveAt
- CObArray [MFC], SetAt
- CObArray [MFC], SetAtGrow
- CObArray [MFC], SetSize
ms.assetid: d71f3d8f-ef9f-4e48-9b69-7782c0e2ddf7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b2f5f0a72c08aeabcd764cf4c7763c9506769585
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37121626"
---
# <a name="cuintarray-class"></a>CUIntArray 클래스
부호 없는 정수의 배열을 지원합니다.  
  
## <a name="syntax"></a>구문  
  
```  
class CUIntArray : public CObject  
```  
  
## <a name="members"></a>멤버  
 멤버 함수 `CUIntArray` 클래스의 멤버 함수와 비슷한 [CObArray](../../mfc/reference/cobarray-class.md)합니다. 이처럼 두 함수가 비슷하므로 `CObArray` 참조 설명서에서 멤버 함수 관련 사항을 확인할 수 있습니다. 볼 때마다는 `CObject` UINT으로 포인터를 함수 매개 변수 또는 반환 값으로 대체 합니다.  
  
 `CObject* CObArray::GetAt( int <nIndex> ) const;`  
  
 예를 들어 위의 코드는  
  
 `UINT CUIntArray::GetAt( int <nIndex> ) const;`  
  
### <a name="public-constructors"></a>Public 생성자  
  
|이름|설명|  
|----------|-----------------|  
|[CObArray::CObArray](../../mfc/reference/cobarray-class.md#cobarray)|빈 배열을 생성합니다.|  
  
### <a name="public-methods"></a>Public 메서드  
  
|이름|설명|  
|----------|-----------------|  
|[CObArray::Add](../../mfc/reference/cobarray-class.md#add)|배열 끝에 요소를 추가하고 필요하면 배열을 확장합니다.|  
|[CObArray::Append](../../mfc/reference/cobarray-class.md#append)|배열에 다른 배열을 추가하고 필요하면 배열을 확장합니다.|  
|[CObArray::Copy](../../mfc/reference/cobarray-class.md#copy)|배열에 다른 배열을 복사하고 필요하면 배열을 확장합니다.|  
|[CObArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat)|배열 내의 요소 포인터에 대한 임시 참조를 반환합니다.|  
|[CObArray::FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|현재 상한을 초과하며 사용되지 않는 모든 메모리를 해제합니다.|  
|[CObArray::GetAt](../../mfc/reference/cobarray-class.md#getat)|지정된 인덱스의 값을 반환합니다.|  
|[CObArray::GetCount](../../mfc/reference/cobarray-class.md#getcount)|이 배열에 있는 요소의 수를 가져옵니다.|  
|[CObArray::GetData](../../mfc/reference/cobarray-class.md#getdata)|배열의 요소에 대한 액세스를 허용합니다. NULL이 될 수 있습니다.|  
|[CObArray::GetSize](../../mfc/reference/cobarray-class.md#getsize)|이 배열에 있는 요소의 수를 가져옵니다.|  
|[CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)|유효한 최대 인덱스를 반환합니다.|  
|[CObArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat)|지정한 인덱스에 요소 하나 또는 다른 배열의 모든 요소를 삽입합니다.|  
|[CObArray::IsEmpty](../../mfc/reference/cobarray-class.md#isempty)|배열이 비어 있는지를 확인합니다.|  
|[CObArray::RemoveAll](../../mfc/reference/cobarray-class.md#removeall)|이 배열의 모든 요소를 반환합니다.|  
|[CObArray::RemoveAt](../../mfc/reference/cobarray-class.md#removeat)|특정 인덱스의 요소를 제거합니다.|  
|[CObArray::SetAt](../../mfc/reference/cobarray-class.md#setat)|지정된 인덱스의 값을 설정합니다. 배열은 확장할 수 없습니다.|  
|[CObArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)|지정된 인덱스의 값을 설정합니다. 필요한 경우 배열을 확장합니다.|  
|[CObArray::SetSize](../../mfc/reference/cobarray-class.md#setsize)|이 배열에 포함된 요소의 수를 설정합니다.|  
  
### <a name="public-operators"></a>Public 연산자  
  
|이름|설명|  
|----------|-----------------|  
|[CObArray::operator]](../../mfc/reference/cobarray-class.md#operator_at)|지정한 인덱스에 있는 요소를 설정하거나 가져옵니다.|  
  
## <a name="remarks"></a>설명  
 부호 없는 정수 또는 UINT, 단어 및 2 배 워드 점에서 다릅니다 UINT의 실제 크기는 대상 운영 환경에 따라 변경할 수 있습니다. UINT는 워드 단위 크기가 같은 합니다.  
  
 `CUIntArray` 통합 된 [IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic) 런타임 형식 액세스 및 덤프를 지원 하기 위해 매크로 [CDumpContext](../../mfc/reference/cdumpcontext-class.md) 개체입니다. 부호 없는 정수 개별 요소의 덤프가 필요한 경우 덤프 컨텍스트 깊이 1 이상으로 설정 해야 합니다. 부호 없는 정수 배열은 직렬화 할 수 없습니다.  
  
> [!NOTE]
>  배열을 사용하기 전에 `SetSize`를 사용하여 배열 크기를 설정하고 배열에 대해 메모리를 할당합니다. `SetSize`를 사용하지 않는 경우 배열에 요소를 추가하면 배열이 자주 다시 할당되고 복사됩니다. 이처럼 다시 할당 및 복사가 자주 수행되면 효율성이 떨어지며 메모리가 조각화될 수 있습니다.  
  
 사용 하 여 대 한 자세한 내용은 `CUIntArray`, 문서를 참조 [컬렉션](../../mfc/collections.md)합니다.  
  
## <a name="inheritance-hierarchy"></a>상속 계층  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CUIntArray`  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** afxcoll.h  
  
## <a name="see-also"></a>참고 항목  
 [CObject 클래스](../../mfc/reference/cobject-class.md)   
 [계층 구조 차트](../../mfc/hierarchy-chart.md)




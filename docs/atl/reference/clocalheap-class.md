---
title: CLocalHeap 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CLocalHeap
- ATLMEM/ATL::CLocalHeap
- ATLMEM/ATL::CLocalHeap::Allocate
- ATLMEM/ATL::CLocalHeap::Free
- ATLMEM/ATL::CLocalHeap::GetSize
- ATLMEM/ATL::CLocalHeap::Reallocate
dev_langs:
- C++
helpviewer_keywords:
- CLocalHeap class
ms.assetid: 1ffa87a5-5fc8-4f8d-8809-58e87e963bd2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8e0489d46ada0e68456f6ae16e7cd702c892a7b9
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37880117"
---
# <a name="clocalheap-class"></a>CLocalHeap 클래스
이 클래스는 구현 [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) Win32 로컬 힙 함수를 사용 합니다.  
  
> [!IMPORTANT]
>  이 클래스 및 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.  
  
## <a name="syntax"></a>구문  
  
```
class CLocalHeap : public IAtlMemMgr
```  
  
## <a name="members"></a>멤버  
  
### <a name="public-methods"></a>Public 메서드  
  
|이름|설명|  
|----------|-----------------|  
|[Clocalheap:: Allocate](#allocate)|메모리 블록을 할당하려면 이 메서드를 호출합니다.|  
|[Clocalheap::](#free)|이 메모리 관리자에 의해 할당 된 메모리 블록을 해제 하려면이 메서드를 호출 합니다.|  
|[CLocalHeap::GetSize](#getsize)|이 메모리 관리자에 의해 할당 된 메모리 블록의 할당 된 크기를 가져오려면이 메서드를 호출 합니다.|  
|[Clocalheap:: Reallocate](#reallocate)|이 메모리 관리자에 의해 할당된 메모리를 다시 할당하려면 이 메서드를 호출합니다.|  
  
## <a name="remarks"></a>설명  
 `CLocalHeap` Win32 로컬 힙 함수를 사용 하 여 메모리 할당 함수를 구현 합니다.  
  
> [!NOTE]
>  로컬 힙 함수를 다른 메모리 관리 함수와 보다 느린 및 많은 기능을 제공 하지 않습니다. 따라서 새 응용 프로그램을 사용 해야 합니다 [힙 함수](http://msdn.microsoft.com/library/windows/desktop/aa366711)합니다. 사용할 수 있는 이러한 합니다 [CWin32Heap](../../atl/reference/cwin32heap-class.md) 클래스입니다.  
  
## <a name="example"></a>예  
 예를 참조 하세요 [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)합니다.  
  
## <a name="inheritance-hierarchy"></a>상속 계층  
 `IAtlMemMgr`  
  
 `CLocalHeap`  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** atlmem.h  
  
##  <a name="allocate"></a>  Clocalheap:: Allocate  
 메모리 블록을 할당하려면 이 메서드를 호출합니다.  
  
```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```  
  
### <a name="parameters"></a>매개 변수  
 *nBytes*  
 새 메모리 블록의 요청된 바이트 수입니다.  
  
### <a name="return-value"></a>반환 값  
 새로 할당된 메모리 블록의 시작 부분에 대한 포인터를 반환합니다.  
  
### <a name="remarks"></a>설명  
 호출 [clocalheap:: Free](#free) 하거나 [clocalheap:: Reallocate](#reallocate) 이 메서드에 의해 할당 된 메모리를 해제 합니다.  
  
 사용 하 여 구현 [LocalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366723) LMEM_FIXED 플래그 매개 변수를 사용 하 여 합니다.  
  
##  <a name="free"></a>  Clocalheap::  
 이 메모리 관리자에 의해 할당 된 메모리 블록을 해제 하려면이 메서드를 호출 합니다.  
  
```
virtual void Free(void* p) throw();
```  
  
### <a name="parameters"></a>매개 변수  
 *p*  
 이 메모리 관리자에 의해 이전에 할당된 메모리에 대한 포인터입니다. NULL 유효한 값 이며 아무 작업도 수행 합니다.  
  
### <a name="remarks"></a>설명  
 사용 하 여 구현 [LocalFree](http://msdn.microsoft.com/library/windows/desktop/aa366730)합니다.  
  
##  <a name="getsize"></a>  CLocalHeap::GetSize  
 이 메모리 관리자에 의해 할당 된 메모리 블록의 할당 된 크기를 가져오려면이 메서드를 호출 합니다.  
  
```
virtual size_t GetSize(void* p) throw();
```  
  
### <a name="parameters"></a>매개 변수  
 *p*  
 이 메모리 관리자에 의해 이전에 할당된 메모리에 대한 포인터입니다.  
  
### <a name="return-value"></a>반환 값  
 할당된 된 메모리 블록의 크기 (바이트)를 반환합니다.  
  
### <a name="remarks"></a>설명  
 사용 하 여 구현 [LocalSize](http://msdn.microsoft.com/library/windows/desktop/aa366745)합니다.  
  
##  <a name="reallocate"></a>  Clocalheap:: Reallocate  
 이 메모리 관리자에 의해 할당된 메모리를 다시 할당하려면 이 메서드를 호출합니다.  
  
```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```  
  
### <a name="parameters"></a>매개 변수  
 *p*  
 이 메모리 관리자에 의해 이전에 할당된 메모리에 대한 포인터입니다.  
  
 *nBytes*  
 새 메모리 블록의 요청된 바이트 수입니다.  
  
### <a name="return-value"></a>반환 값  
 새로 할당된 메모리 블록의 시작 부분에 대한 포인터를 반환합니다.  
  
### <a name="remarks"></a>설명  
 호출 [clocalheap::](#free) 이 메서드에 의해 할당 된 메모리를 해제 합니다.  
  
 사용 하 여 구현 [LocalReAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366742)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [클래스 개요](../../atl/atl-class-overview.md)   
 [CComHeap 클래스](../../atl/reference/ccomheap-class.md)   
 [CWin32Heap 클래스](../../atl/reference/cwin32heap-class.md)   
 [CGlobalHeap 클래스](../../atl/reference/cglobalheap-class.md)   
 [CCRTHeap 클래스](../../atl/reference/ccrtheap-class.md)   
 [IAtlMemMgr 클래스](../../atl/reference/iatlmemmgr-class.md)

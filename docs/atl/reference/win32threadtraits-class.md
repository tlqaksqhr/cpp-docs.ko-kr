---
title: Win32ThreadTraits 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- Win32ThreadTraits
- ATLBASE/ATL::Win32ThreadTraits
- ATLBASE/ATL::Win32ThreadTraits::CreateThread
dev_langs:
- C++
helpviewer_keywords:
- threading [ATL], Windows threads
- threading [ATL], creation functions
- Win32ThreadTraits class
ms.assetid: 50279c38-eae1-4301-9ea6-97ccea580f3e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c61ba91fe29610f4b313cf31c65f514ef8e46f96
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37883676"
---
# <a name="win32threadtraits-class"></a>Win32ThreadTraits 클래스
이 클래스는 Windows 스레드 생성 함수를 제공합니다. 스레드 CRT 함수를 사용 하지 않는 경우이 클래스를 사용 합니다.  
  
> [!IMPORTANT]
>  이 클래스 및 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.  
  
## <a name="syntax"></a>구문  
  
```
class Win32ThreadTraits
```  
  
## <a name="members"></a>멤버  
  
### <a name="public-methods"></a>Public 메서드  
  
|이름|설명|  
|----------|-----------------|  
|[Win32ThreadTraits::CreateThread](#createthread)|(정적) CRT 함수를 사용 해야 하는 스레드를 만드는 데이 함수를 호출 합니다.|  
  
## <a name="remarks"></a>설명  
 스레드 특성은 스레드의 특정 형식에 대 한 생성 함수를 제공 하는 클래스입니다. 생성 함수 동일한 서명 및 의미 체계는 Windows 갖습니다 [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453) 함수입니다.  
  
 스레드 특성은 다음 클래스로 사용 됩니다.  
  
- [CThreadPool](../../atl/reference/cthreadpool-class.md)  
  
- [CWorkerThread](../../atl/reference/cworkerthread-class.md)  
  
 스레드는 CRT 함수를 사용 하는 경우 사용 하 여 [CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md) 대신 합니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** atlbase.h  
  
##  <a name="createthread"></a>  Win32ThreadTraits::CreateThread  
 CRT 함수를 사용 해야 하는 스레드를 만드는 데이 함수를 호출 합니다.  
  
```
static HANDLE CreateThread(
    LPSECURITY_ATTRIBUTES lpsa,
    DWORD dwStackSize,
    LPTHREAD_START_ROUTINE pfnThreadProc,
    void* pvParam,
    DWORD dwCreationFlags,
    DWORD* pdwThreadId) throw();
```  
  
### <a name="parameters"></a>매개 변수  
 *lpsa*  
 새 스레드의 보안 특성입니다.  
  
 *dwStackSize*  
 새 스레드의 스택 크기입니다.  
  
 *pfnThreadProc*  
 새 스레드의 스레드 프로시저입니다.  
  
 *pvParam*  
 스레드 프로시저에 전달할 매개 변수입니다.  
  
 *dwCreationFlags*  
 만들기 (0 또는 CREATE_SUSPENDED) 플래그를 지정 합니다.  
  
 *pdwThreadId*  
 [out] 성공 하면 새로 만든 스레드의 스레드 ID를 수신 하는 DWORD 변수의 주소입니다.  
  
### <a name="return-value"></a>반환 값  
 새로 만든된 스레드에 또는 NULL로 실패 시 핸들을 반환합니다. 호출 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) 확장 오류 정보를 가져오려면.  
  
### <a name="remarks"></a>설명  
 참조 [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453) 이 함수에 매개 변수에 대 한 자세한 내용은 합니다.  
  
 이 함수 호출 `CreateThread` 스레드를 만들려고 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [클래스 개요](../../atl/atl-class-overview.md)

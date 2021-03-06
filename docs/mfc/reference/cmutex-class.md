---
title: CMutex 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMutex
- AFXMT/CMutex
- AFXMT/CMutex::CMutex
dev_langs:
- C++
helpviewer_keywords:
- CMutex [MFC], CMutex
ms.assetid: 6330c050-4f01-4195-a099-2029b92f8cf1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f3bde85e64fe8593ec2637e767e8c3c70d3b8200
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37038079"
---
# <a name="cmutex-class"></a>CMutex 클래스
"뮤텍스" 나타냅니다-한 스레드가 리소스에 상호 배타적 액세스 허용 하는 동기화 개체입니다.  
  
## <a name="syntax"></a>구문  
  
```  
class CMutex : public CSyncObject  
```  
  
## <a name="members"></a>멤버  
  
### <a name="public-constructors"></a>Public 생성자  
  
|이름|설명|  
|----------|-----------------|  
|[CMutex::CMutex](#cmutex)|`CMutex` 개체를 생성합니다.|  
  
## <a name="remarks"></a>설명  
 뮤텍스는 데이터 또는 다른 제어 된 리소스가 수정으로 한 번에 하나의 스레드를 이동할 수 있는 경우에 유용 합니다. 예를 들어, 한 번에 한 스레드에서 허용 해야 하는 프로세스는 연결 된 목록의 노드를 추가 합니다. 사용 하 여 한 `CMutex` 만 한 번에 한 스레드만 목록에 액세스할 수 있는 연결된 리스트를 제어 하는 개체입니다.  
  
 사용 하는 `CMutex` 개체를 생성 하는 `CMutex` 필요할 때 개체입니다. 때까지 기다렸다가 뮤텍스의 이름을 지정 하 고 응용 프로그램에서 소유한 처음 해야 합니다. 생성자는 반환 될 때 뮤텍스에 액세스할 수 있습니다. 호출 [CSyncObject::Unlock](../../mfc/reference/csyncobject-class.md#unlock) 완료 되 면 제어 된 리소스에 액세스 합니다.  
  
 다른 방법을 사용 하 여 `CMutex` 개체 형식의 변수를 추가 하는 것 `CMutex` 제어 하려는 클래스를 데이터 멤버로 합니다. 제어 되는 개체의 생성 되는 동안 호출의 생성자는 `CMutex` 뮤텍스 처음 소유 하 고, 뮤텍스 (프로세스 경계를 넘어 사용될지) 하는 경우의 이름 및 보안 특성을 원하는 경우를 지정 하는 데이터 멤버입니다.  
  
 리소스에 액세스 하 여 제어 `CMutex` 이 방법으로 개체는 두 가지 형식의 변수를 만들고 먼저 [경우 CSingleLock](../../mfc/reference/csinglelock-class.md) 또는 형식 [CMultiLock](../../mfc/reference/cmultilock-class.md) 리소스의 액세스 멤버 함수에 있습니다. 그런 다음 잠금 개체의 호출 `Lock` 멤버 함수 (예를 들어 [CSingleLock::Lock](../../mfc/reference/csinglelock-class.md#lock)). 이 시점에서 스레드는 중 하나는 리소스에 액세스, 리소스를 해제 하 고 액세스를 하거나 출시 될 리소스 및 리소스에 액세스 실패 하는 시간이 초과 될 때까지 기다리는 합니다. 어떤 경우 든, 스레드로부터 안전한 방식으로 리소스에 액세스 합니다. 리소스를 해제 하려면 잠금 개체를 사용 하 여 `Unlock` 멤버 함수 (예를 들어 [CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock)), 또는 범위에 속하지 않을 수 있는 잠금 개체를 허용 합니다.  
  
 사용 하 여 대 한 자세한 내용은 `CMutex` 개체, 문서를 참조 하십시오. [다중 스레딩: 동기화 클래스 사용 방법](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)합니다.  
  
## <a name="inheritance-hierarchy"></a>상속 계층  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSyncObject](../../mfc/reference/csyncobject-class.md)  
  
 `CMutex`  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** afxmt.h  
  
##  <a name="cmutex"></a>  CMutex::CMutex  
 명명 되거나 명명 되지 않은 `CMutex` 개체입니다.  
  
```  
CMutex(
    BOOL bInitiallyOwn = FALSE,  
    LPCTSTR lpszName = NULL,  
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```  
  
### <a name="parameters"></a>매개 변수  
 *bInitiallyOwn*  
 지정 하는 경우 스레드 만들기는 `CMutex` 개체 뮤텍스에 의해 제어 되는 리소스에 대 한 액세스를 처음에 있습니다.  
  
 *lpszName*  
 `CMutex` 개체의 이름입니다. 이름이 같은 다른 뮤텍스 있으면 *lpszName* 프로세스 경계를 넘어 개체를 사용할 경우 제공 해야 합니다. 경우 **NULL**, 뮤텍스 명명 됩니다. 생성자는 새 빌드 이름에서 일치 하는 기존 뮤텍스 경우 `CMutex` 해당 이름의 뮤텍스를 참조 하는 개체입니다. 이름에서 일치 하는 뮤텍스 되지 않은 기존 동기화 개체 생성이 실패 합니다.  
  
 *lpsaAttribute*  
 뮤텍스 개체에 대 한 보안 특성입니다. 에 대 한 전체 설명은이 구조를 참조 하세요. [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) Windows sdk에서입니다.  
  
### <a name="remarks"></a>설명  
 에 액세스 하거나 해제 하려면는 `CMutex` 개체를 만들기는 [CMultiLock](../../mfc/reference/cmultilock-class.md) 또는 [경우 CSingleLock](../../mfc/reference/csinglelock-class.md) 개체와 호출 해당 [잠금](../../mfc/reference/csinglelock-class.md#lock) 및 [잠금 해제](../../mfc/reference/csinglelock-class.md#unlock) 멤버 함수입니다. 경우는 `CMutex` 개체를 사용한 독립 실행형, 호출 해당 `Unlock` 멤버 함수를 해제 합니다.  
  
> [!IMPORTANT]
>  만든 후의 `CMutex` 개체를 가져오려면 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) 뮤텍스가 이미 존재 하지 않으면 되도록 합니다. 뮤텍스 예기치 않게 존재 않는 rogue 프로세스가 무단 점유 되 고 뮤텍스를 악의적으로 사용 하도록 의도 수를 나타낼 수 있습니다. 이 경우 보안을 중요시 위한 권장된 절차는 핸들을 종료 하 고 것 처럼 계속 개체 만들기에 오류가 발생 한 것입니다.  
  
## <a name="see-also"></a>참고 항목  
 [CSyncObject 클래스](../../mfc/reference/csyncobject-class.md)   
 [계층 구조 차트](../../mfc/hierarchy-chart.md)




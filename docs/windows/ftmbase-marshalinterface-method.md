---
title: 'Ftmbase:: Marshalinterface 메서드 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase::MarshalInterface
dev_langs:
- C++
helpviewer_keywords:
- MarshalInterface method
ms.assetid: fc8421b4-06e4-4925-b908-c285fe4790d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 23779cbe0b27680122c6aa3a8f8748c39f28078e
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39647409"
---
# <a name="ftmbasemarshalinterface-method"></a>FtmBase::MarshalInterface 메서드
일부 클라이언트 프로세스에서 프록시 개체를 초기화 하는 데 필요한 데이터를 스트림으로 씁니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
STDMETHODIMP MarshalInterface(  
   __in IStream *pStm,  
   __in REFIID riid,  
   __in_opt void *pv,  
   __in DWORD dwDestContext,  
   __reserved void *pvDestContext,  
   __in DWORD mshlflags  
) override;  
```  
  
### <a name="parameters"></a>매개 변수  
 *pStm*  
 마샬링 중 사용할 스트림에 대 한 포인터입니다.  
  
 *riid*  
 마샬링될 인터페이스의 식별자에 대 한 참조입니다. 이 인터페이스에서 파생 되어야 합니다는 `IUnknown` 인터페이스입니다.  
  
 *pv*  
 마샬링될; 인터페이스 포인터에 대 한 포인터 호출자가 원하는 인터페이스에 대 한 포인터 없는 경우 NULL 일 수 있습니다.  
  
 *dwDestContext*  
 대상 위치 지정된 된 인터페이스를 컨텍스트 마샬링해야 합니다.  
  
 하나 이상의 MSHCTX 열거형 값을 지정 합니다.  
  
 역마샬링 현재 프로세스 (MSHCTX_LOCAL)와 동일한 컴퓨터에서 다른 프로세스 또는 현재 프로세스 (MSHCTX_INPROC)의 다른 아파트에서 발생할 수 있습니다.  
  
 *pvDestContext*  
 나중에 사용하도록 예약되어 있습니다. 0이어야 합니다.  
  
 *mshlflags*  
 클라이언트 프로세스에 다시 전송할 데이터를 마샬링할 수 인지 여부를 지정-일반적인 사례-여러 클라이언트에서 검색할 수 있는 전역 테이블에 기록 합니다.  
  
## <a name="return-value"></a>반환 값  
 S_OK  
 인터페이스 포인터를 성공적으로 마샬링됩니다.  
  
 E_NOINTERFACE  
 지정된 된 인터페이스는 지원 되지 않습니다.  
  
 STG_E_MEDIUMFULL  
 스트림을 꽉 찼습니다.  
  
 E_FAIL  
 작업을 수행하지 못했습니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** ftm.h  
  
 **네임스페이스:** Microsoft::WRL  
  
## <a name="see-also"></a>참고 항목  
 [FtmBase 클래스](../windows/ftmbase-class.md)
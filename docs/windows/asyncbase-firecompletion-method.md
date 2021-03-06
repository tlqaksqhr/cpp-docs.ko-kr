---
title: 'Asyncbase:: Firecompletion 메서드 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::FireCompletion
dev_langs:
- C++
helpviewer_keywords:
- FireCompletion method
ms.assetid: b5e29d6d-52e7-4148-a7f3-a313b1359819
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 199d84afe198c4fc41808144105ea704822aa00a
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39646609"
---
# <a name="asyncbasefirecompletion-method"></a>AsyncBase::FireCompletion 메서드
완료 이벤트 처리기를 호출 하거나 내부 진행률 대리자를 다시 설정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
void FireCompletion(  
   void  
) override;  
  
virtual void FireCompletion();  
```  
  
## <a name="remarks"></a>설명  
 첫 번째 버전 **FireCompletion()** 내부 진행률 대리자 변수를 다시 설정 합니다. 비동기 작업이 완료 될 경우 완료 이벤트 처리기를 호출 하는 두 번째 버전입니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** async.h  
  
 **네임스페이스:** Microsoft::WRL  
  
## <a name="see-also"></a>참고 항목  
 [AsyncBase 클래스](../windows/asyncbase-class.md)
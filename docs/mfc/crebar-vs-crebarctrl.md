---
title: CReBar vs입니다. CReBarCtrl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CReBar
- CReBarCtrl
dev_langs:
- C++
helpviewer_keywords:
- CReBar class [MFC], vs. CReBarCtrl
- rebar controls [MFC], CReBarCtrl class [MFC]
- GetReBarCtrl class [MFC]
ms.assetid: 7f9c1d7e-5d5f-4956-843c-69ed3df688d0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c98b2fd9baf97d351c812f2c442d408ff6221d82
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36932262"
---
# <a name="crebar-vs-crebarctrl"></a>CReBar vs입니다. CReBarCtrl
MFC는 두 개의 클래스를 만드는 rebars: [CReBar](../mfc/reference/crebar-class.md) 및 [CReBarCtrl](../mfc/reference/crebarctrl-class.md) (Windows 공용 컨트롤 API 래핑합니다 입니다). `CReBar` 모든 rebar 공용 컨트롤의 기능을 제공 하며 대부분의 필수 공용 컨트롤 설정 및 구조를 처리 합니다.  
  
 `CReBarCtrl` Win32 rebar 컨트롤에 대 한 래퍼 클래스 이며 따라서 보다 쉽게 rebar MFC 아키텍처에 통합 하려는 경우 구현할 수 있습니다. 사용 하려는 경우 `CReBarCtrl` rebar MFC 아키텍처에 통합 하 고, rebar 컨트롤 조작 MFC에 통신 하기 위해 추가 주의 해야 합니다. 이 통신이 어렵습니다. 그러나 사용할 때 필요 하지 않은 추가 작업은 `CReBar`합니다.  
  
 Visual c + +는 rebar 공용 컨트롤을 활용 하는 두 가지를 제공 합니다.  
  
-   사용 하 여 rebar 만들 `CReBar`, 한 다음 호출 [CReBar::GetReBarCtrl](../mfc/reference/crebar-class.md#getrebarctrl) 에 액세스 하는 `CReBarCtrl` 멤버 함수입니다.  
  
    > [!NOTE]
    >  `CReBar::GetReBarCtrl` 캐스팅 하는 인라인 멤버 함수는 **이** rebar 개체의 포인터입니다. 즉, 실행 시 함수 호출에 오버 헤드가 없습니다.  
  
-   사용 하 여 rebar 만들 [CReBarCtrl](../mfc/reference/crebarctrl-class.md)의 생성자입니다.  
  
 두 방법 중 하나는 rebar 컨트롤의 멤버 함수에 액세스할 수 있습니다. 호출 하는 경우 `CReBar::GetReBarCtrl`, 반환에 대 한 참조는 `CReBarCtrl` 개체 멤버 함수의 집합 중 하나를 사용할 수 있도록 합니다. 참조 [CReBar](../mfc/reference/crebar-class.md) 생성 하 고 사용 하 여 rebar 만들기에 대 한 내용은 `CReBar`합니다.  
  
## <a name="see-also"></a>참고 항목  
 [CReBarCtrl 사용](../mfc/using-crebarctrl.md)   
 [컨트롤](../mfc/controls-mfc.md)


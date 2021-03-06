---
title: 컨트롤 그리기 최적화 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], optimizing
ms.assetid: 29ff985d-9bf5-4678-b62d-aad12def75fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8103e1e342756f9b715c1a0959ed256403e130bf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33351296"
---
# <a name="optimizing-control-drawing"></a>컨트롤 그리기 최적화
컨테이너 공급 장치 컨텍스트에 컨트롤을 그리게 되는 경우 일반적으로 장치 컨텍스트에 GDI 개체(예: 펜, 브러시, 글꼴 등)를 선택하고 해당 그리기 작업을 수행하고, 이전의 GDI 개체를 복원합니다. 컨테이너에 동일한 장치 컨텍스트로 그려지는 여러 컨트롤이 있고 각 컨트롤이 필요한 GDI 개체를 선택하는 경우 컨트롤이 이전에 선택한 개체를 개별적으로 복원하지 않으면 시간을 절약할 수 있습니다. 모든 컨트롤이 그려진 후 컨테이너에서는 원래 개체를 자동으로 복원할 수 있습니다.  
  
 컨테이너가이 기술을 지원 여부를 검색 하려면 컨트롤을 호출할 수는 [colecontrol:: Isoptimizeddraw](../mfc/reference/colecontrol-class.md#isoptimizeddraw) 멤버 함수입니다. 이 함수에서 반환 하는 경우 **TRUE**, 컨트롤에서 이전에 선택한 개체를 복원 하는 일반적인 단계를 건너뛸 수 있습니다.  
  
 다음 `OnDraw` 함수(최적화되지 않음)가 있는 컨트롤을 가정합니다.  
  
 [!code-cpp[NVC_MFC_AxOpt#15](../mfc/codesnippet/cpp/optimizing-control-drawing_1.cpp)]  
  
 예제에서 펜과 브러시는 지역 변수입니다. 이는 소멸자가 범위를 벗어날 경우(`OnDraw` 함수가 종료할 때) 호출된다는 의미입니다. 소멸자는 해당 GDI 개체를 삭제하려고 합니다. 그러나 `OnDraw`에서 반환 시 선택한 해당 개체를 장치 컨텍스트에 남기려는 경우 삭제하지 않아야 합니다.  
  
 방지 하기 위해는 [CPen](../mfc/reference/cpen-class.md) 및 [CBrush](../mfc/reference/cbrush-class.md) 때 제거 되 고 개체 `OnDraw` 완료 되 면가 지역 변수 대신 멤버 변수를 저장 합니다. 컨트롤의 클래스 선언에서 두 개의 새 멤버 변수에 대한 선언을 추가합니다.  
  
 [!code-cpp[NVC_MFC_AxOpt#16](../mfc/codesnippet/cpp/optimizing-control-drawing_2.h)]  
[!code-cpp[NVC_MFC_AxOpt#17](../mfc/codesnippet/cpp/optimizing-control-drawing_3.h)]  
  
 다음과 같이 `OnDraw` 함수를 다시 쓸 수 있습니다.  
  
 [!code-cpp[NVC_MFC_AxOpt#18](../mfc/codesnippet/cpp/optimizing-control-drawing_4.cpp)]  
  
 이 방법을 사용하면 `OnDraw`를 호출할 때마다 펜 및 브러시를 만들지 않습니다. 추가 인스턴스 데이터를 관리하는 대신 속도가 향상됩니다.  
  
 ForeColor 또는 BackColor 속성이 변경되는 경우 펜 또는 브러시를 다시 만들어야 합니다. 이 작업을 수행 하려면 재정의 [OnForeColorChanged](../mfc/reference/colecontrol-class.md#onforecolorchanged) 및 [OnBackColorChanged](../mfc/reference/colecontrol-class.md#onbackcolorchanged) 멤버 함수:  
  
 [!code-cpp[NVC_MFC_AxOpt#19](../mfc/codesnippet/cpp/optimizing-control-drawing_5.cpp)]  
  
 마지막으로 불필요한 `SelectObject` 호출을 제거하려면 `OnDraw`를 다음과 같이 수정합니다.  
  
 [!code-cpp[NVC_MFC_AxOpt#20](../mfc/codesnippet/cpp/optimizing-control-drawing_6.cpp)]  
  
## <a name="see-also"></a>참고 항목  
 [MFC ActiveX 컨트롤: 최적화](../mfc/mfc-activex-controls-optimization.md)   
 [COleControl 클래스](../mfc/reference/colecontrol-class.md)   
 [MFC ActiveX 컨트롤](../mfc/mfc-activex-controls.md)   
 [MFC ActiveX 컨트롤](../mfc/mfc-activex-controls.md)   
 [MFC ActiveX 컨트롤 마법사](../mfc/reference/mfc-activex-control-wizard.md)   
 [MFC ActiveX 컨트롤: ActiveX 컨트롤 그리기](../mfc/mfc-activex-controls-painting-an-activex-control.md)


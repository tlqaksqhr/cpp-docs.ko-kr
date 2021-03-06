---
title: 데이터 교환 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- property sheets [MFC], data exchange
- exchanging data with property sheets [MFC]
- DDX (dialog data exchange) [MFC], property sheets
ms.assetid: 689f02d0-51a9-455b-8ffb-5b44f0aefa28
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e503bd9268423fbe63ec76de4bcb5443a7d52696
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33345822"
---
# <a name="exchanging-data"></a>데이터 교환
대부분의 대화 상자와 마찬가지로 속성 시트 및 응용 프로그램 간의 데이터 교환을 속성 시트의 가장 중요 한 기능 중 하나입니다. 이 문서에서는이 작업을 수행 하는 방법을 설명 합니다.  
  
 속성 시트와 데이터 교환는 것은 실제로 속성 시트의 개별 속성 페이지를 사용 하 여 데이터를 교환 합니다. 속성 페이지를 사용 하 여 데이터를 교환 하기 위한 절차는 이후 대화 상자를 사용 하 여 데이터를 교환 하는 경우와 동일는 [CPropertyPage](../mfc/reference/cpropertypage-class.md) 만 특수 개체는 [CDialog](../mfc/reference/cdialog-class.md) 개체입니다. 프로시저는 프레임 워크의 대화 상자 데이터 교환 (DDX) 기능을 컨트롤과 대화 상자 개체의 대화 상자와 멤버 변수 간에 데이터를 교환 합니다.  
  
 속성 시트와 일반 대화 상자 데이터 교환에 대 한 중요 한 차이점은 속성 시트의 속성 시트의 모든 페이지를 사용 하 여 데이터를 교환 해야 하므로 여러 페이지에는 합니다. DDX에 대 한 자세한 내용은 참조 하십시오. [대화 상자 데이터 교환 및 유효성 검사](../mfc/dialog-data-exchange-and-validation.md)합니다.  
  
 다음 예제는 뷰와 속성 시트의 두 페이지 사이 교환할 데이터입니다.  
  
 [!code-cpp[NVC_MFCDocView#4](../mfc/codesnippet/cpp/exchanging-data_1.cpp)]  
  
## <a name="see-also"></a>참고 항목  
 [속성 시트](../mfc/property-sheets-mfc.md)


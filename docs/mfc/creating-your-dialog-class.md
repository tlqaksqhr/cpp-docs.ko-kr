---
title: 대화 상자 클래스 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- files [MFC], creating
- dialog classes [MFC], Add Class Wizard
- dialog classes [MFC], creating
ms.assetid: d5321741-da41-47a8-bb1c-6a0e8b28c4c1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d70f27639344fd00a2e99ad79bf2db166f3270a8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33341912"
---
# <a name="creating-your-dialog-class"></a>대화 상자 클래스 만들기
프로그램의 각 대화 상자에 대 한 대화 상자 리소스를 사용 하는 새 대화 상자 클래스를 만듭니다.  
  
 [클래스 추가](../ide/adding-a-class-visual-cpp.md) 새 대화 상자 클래스를 만드는 방법을 설명 합니다. 클래스 추가 마법사와 대화 상자 클래스를 만들 때 기록 다음 항목의 합니다. H 및 합니다. 지정 하는 CPP 파일:  
  
 안에. H 파일:  
  
-   대화 상자 클래스에 대 한 클래스 선언입니다. 클래스에서 파생 된 [CDialog](../mfc/reference/cdialog-class.md)합니다.  
  
 안에. CPP 파일:  
  
-   클래스에 대 한 메시지 맵입니다.  
  
-   대화 상자에 대 한 표준 생성자입니다.  
  
-   재정의 [DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange) 멤버 함수입니다. 이 함수를 편집 합니다. 나중에 설명 된 대로 대화 상자 데이터 교환 및 유효성 검사 기능에 사용 되 [대화 상자 데이터 교환 및 유효성 검사](../mfc/dialog-data-exchange-and-validation.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [코드 마법사로 대화 상자 클래스 만들기](../mfc/creating-a-dialog-class-with-code-wizards.md)   
 [대화 상자의 수명 주기](../mfc/life-cycle-of-a-dialog-box.md)


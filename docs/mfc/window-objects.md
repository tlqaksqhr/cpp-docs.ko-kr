---
title: "창 개체 소멸 시키기 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- objects [MFC], window
- Windows window [MFC]
- MFC, windows
- frame windows [MFC], C++ window objects
- window objects [MFC]
- windows [MFC], C++ window objects
- window messages [MFC]
- HWND
- messages [MFC], Windows
- Visual C++, window objects [MFC]
- HWND, window objects [MFC]
ms.assetid: 28b33ce2-af05-4617-9d03-1cb9a02be687
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 15f53db2d0ec6a57261e22c58abd3e5e8423b716
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="window-objects"></a>창 개체
MFC 클래스를 제공 [CWnd](../mfc/reference/cwnd-class.md) 캡슐화 하는 `HWND` 는 창의 핸들입니다. `CWnd` 개체는 Windows 창을 나타내는 `HWND`와 다른 C++ 창 개체이지만 이를 포함합니다. `CWnd`를 사용하여 고유한 자식 창 클래스를 파생시키거나 `CWnd`에서 파생된 여러 MFC 클래스 중 하나를 사용합니다. `CWnd` 클래스는 프레임 창, 대화 상자, 자식 창, 컨트롤 및 컨트롤 막대(예: 도구 모음)를 포함하는 모든 창에 대한 기본 클래스입니다. 에 대해 잘 알고 [c + + 창 개체와 HWND 간 관계](../mfc/relationship-between-a-cpp-window-object-and-an-hwnd.md) MFC 통한 효율적인 프로그래밍에 대 한 매우 중요 합니다.  
  
 MFC에서는 몇 가지 기본 기능 및 창 관리를 제공하지만 `CWnd`에서 고유한 클래스를 파생시킬 수 있고 해당 멤버 함수를 사용하여 제공된 기능을 사용자 지정할 수 있습니다. 자식 창을 만들거나 구성 하 여 한 `CWnd` 개체와 호출 해당 [만들기](../mfc/reference/cwnd-class.md#create) 멤버 함수를 사용 하 여 자식 창을 사용자 지정 후 `CWnd` 멤버 함수입니다. 파생 된 개체를 포함할 수 있습니다 [CView](../mfc/reference/cview-class.md), 예: 폼 뷰 또는 프레임 창에서 트리 보기입니다. 클래스에서 제공 하는 분할자 창을 통해 문서의 여러 뷰를 지원할 수 및 [CSplitterWnd](../mfc/reference/csplitterwnd-class.md)합니다.  
  
 `CWnd` 클래스에서 파생된 각 개체에는 Windows 메시지 또는 명령 ID를 고유한 처리기에 매핑할 수 있는 메시지 맵이 포함됩니다.  
  
 Windows 프로그래밍에 대한 일반 문서는 `CWnd` API를 캡슐화하는 `HWND` 멤버 함수를 사용하는 방법을 학습하기 위한 좋은 리소스입니다.  
  
## <a name="functions-for-operating-on-a-cwnd"></a>CWnd에서 작동하는 함수  
 `CWnd`및 해당 [파생 된 창 클래스](../mfc/derived-window-classes.md) 생성자, 소멸자 및 개체를 초기화 하는 멤버 함수 내부 Windows 구조를 만들고 캡슐화 된 액세스를 제공 `HWND`합니다. `CWnd`는 메시지 전송, 창 상태에 액세스, 좌표 변환, 업데이트, 스크롤, 클립보드에 액세스 및 기타 여러 작업을 위해 Windows API를 캡슐화하는 멤버 함수도 제공합니다. `HWND` 인수를 사용하는 대부분의 Windows 창 관리 API는 `CWnd` 멤버 함수로 캡슐화됩니다. 함수와 매개 변수 이름은 `CWnd` 멤버 함수에서 유지됩니다. Windows Api에 의해 캡슐화에 대 한 자세한 내용은 `CWnd`, 클래스 참조 [CWnd](../mfc/reference/cwnd-class.md)합니다.  
  
## <a name="cwnd-and-windows-messages"></a>CWnd 및 Windows 메시지  
 `CWnd`의 주요 목적 중 하나는 `WM_PAINT` 또는 `WM_MOUSEMOVE` 같은 Windows 메시지를 처리하기 위한 인터페이스를 제공하는 것입니다. 멤버 함수 중 많은 `CWnd` 표준 메시지에 대 한 처리기가-식별자로 시작 하는 것 **afx_msg** 와 접두사 "On"와 같은 `OnPaint` 및 **OnMouseMove**합니다. [메시지 처리 및 매핑](../mfc/message-handling-and-mapping.md) 메시지 및 메시지 처리에서 자세히 다룹니다. 프레임워크의 창과 특수 목적을 위해 사용자가 직접 만든 창에 정보가 동일하게 적용됩니다.  
  
### <a name="what-do-you-want-to-know-more-about"></a>에 대 한 자세한 내용을 하 시겠습니까  
  
-   [C + + 창 개체와 HWND 간 관계](../mfc/relationship-between-a-cpp-window-object-and-an-hwnd.md)  
  
-   [파생 된 창 클래스](../mfc/derived-window-classes.md)  
  
-   [창 만들기](../mfc/creating-windows.md)  
  
-   [창 개체 소멸 시키기](../mfc/destroying-window-objects.md)  
  
-   [CWnd를 해당 HWND에서 분리](../mfc/detaching-a-cwnd-from-its-hwnd.md)  
  
-   [창 개체 작업](../mfc/working-with-window-objects.md)  
  
-   [장치 컨텍스트](../mfc/device-contexts.md): Windows 그리기 장치 독립화 개체  
  
-   [그래픽 개체](../mfc/graphic-objects.md): 펜, 브러시, 글꼴, 비트맵, 색상표, 영역  
  
## <a name="see-also"></a>참고 항목  
 [Windows](../mfc/windows.md)

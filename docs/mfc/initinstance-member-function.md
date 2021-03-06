---
title: InitInstance 멤버 함수 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- InitInstance
dev_langs:
- C++
helpviewer_keywords:
- InitInstance method [MFC]
- applications [MFC], initializing
- MFC, initializing
- initializing MFC applications
ms.assetid: 4ef09267-ff7f-4c39-91a0-57454a264f83
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a9379fef6a1d676d6a3bc757ee51d5d27acd5f6f
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930178"
---
# <a name="initinstance-member-function"></a>InitInstance 멤버 함수
Windows 운영 체제를 사용 하면 둘 이상의 복사본, 즉 "," 동일한 응용 프로그램 인스턴스를 실행할 수 있습니다. `WinMain` 호출 [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) 될 때마다 응용 프로그램의 새 인스턴스를 시작 합니다.  
  
 표준 `InitInstance` 구현 MFC 응용 프로그램 마법사로 만든 다음 작업을 수행 합니다.  
  
-   주요 작업으로 차례로 문서, 뷰 및 프레임 창 만드는 문서 서식 파일을 만듭니다. 이 프로세스에 대 한 참조 [문서 서식 파일 만들기](../mfc/document-template-creation.md)합니다.  
  
-   가장 최근에 사용한 파일의 이름을 포함 한 Windows 레지스트리 또는.ini 파일에서 표준 파일 옵션을 로드 합니다.  
  
-   하나 이상의 문서 템플릿이 등록합니다.  
  
-   MDI 응용 프로그램에 대 한 주 프레임 창을 만듭니다.  
  
-   명령줄을 명령줄에 지정 된 문서 또는 새로 만든 빈 문서를 처리 합니다.  
  
 직접 초기화 코드를 추가 하거나 마법사에서 작성 된 코드를 수정할 수 있습니다.  
  
> [!NOTE]
>  MFC 응용 프로그램은 단일 스레드 아파트 (STA)으로 초기화 되어야 합니다. 호출 하는 경우 [CoInitializeEx](http://msdn.microsoft.com/library/windows/desktop/ms695279) 에 프로그램 `InitInstance` 재정의 COINIT_APARTMENTTHREADED (COINIT_MULTITHREADED 아님)를 지정 합니다. 자세한 내용은 참조 PRB: MFC 응용 프로그램이 다른 이름으로 다중 스레드 아파트 (828643)에서 응용 프로그램을 초기화 하는 경우 응답 하지 [ http://support.microsoft.com/default.aspxscid=kb; en-us; 828643](http://support.microsoft.com/default.aspxscid=kb;en-us;828643)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [CWinApp: 응용 프로그램 클래스](../mfc/cwinapp-the-application-class.md)

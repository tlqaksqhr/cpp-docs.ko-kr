---
title: 'TN021: 명령 및 메시지 라우팅 | Microsoft Docs'
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.routing
dev_langs:
- C++
helpviewer_keywords:
- TN021
- command routing [MFC], technical note TN021
- Windows messages [MFC], routing
ms.assetid: b5952c8b-123e-406c-a36d-a6ac7c6df307
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e31a35878564fc09fa6c045566811a3ff9e4b0ef
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37122019"
---
# <a name="tn021-command-and-message-routing"></a>TN021: 명령 및 메시지 라우팅

> [!NOTE]
>  다음 기술 노트는 온라인 설명서에 먼저 포함되어 있었으므로 업데이트되지 않았습니다. 따라서 일부 절차 및 항목은 만료되거나 올바르지 않을 수 있습니다. 최신 정보를 보려면 온라인 설명서 색인에서 관심 있는 항목을 검색하는 것이 좋습니다.

이 노트는 일반적인 창 메시지 라우팅에 고급 항목 뿐만 아니라 명령 라우팅 및 디스패치 아키텍처를 설명합니다.

참조 하십시오 Visual c + +에 대 한 일반적인 내용은 여기에서 설명 하는 아키텍처 특히 구별 Windows 메시지, 컨트롤 알림 및 명령. 이 노트에는 인쇄 된 문서에 설명 된 문제에 잘 알고 있고만 매우 고급 항목을 다룹니다 가정 합니다.

## <a name="command-routing-and-dispatch-mfc-10-functionality-evolves-to-mfc-20-architecture"></a>명령 라우팅 및 디스패치 MFC 1.0 기능 진화 함에 따라 MFC 2.0에 아키텍처

Windows 메뉴 명령과 액셀러레이터 키 대화 상자 컨트롤 알림에 대 한 알림을 제공 하도록 오버 로드는 WM_COMMAND 메시지를 있습니다.

MFC 1.0 기반으로 하는 약간 명령 처리기 (예: "OnFileNew")를 허용 하 여는 `CWnd` 특정 WM_COMMAND에 대 한 응답에서 호출 하는 클래스를 파생 합니다. 이 메시지 맵 이라는 데이터 구조를 함께 연결점 하 고 매우 공간 효율적 명령 메커니즘에 있습니다.

MFC 1.0 명령 메시지에서 컨트롤 알림 분리에 대 한 추가 기능을 제공 합니다. 명령 id입니다. 명령 라고도 하는 16 비트 ID 별로 표시 됩니다. 명령에서 정상적으로 시작 한 `CFrameWnd` (즉, 메뉴 선택 또는 번역 된 액셀러레이터 키) 및 다양 한 다른 창으로 라우팅됩니다.

MFC 1.0의 인터페이스 MDI (다중 문서) 구현에 대 한 제한 된 의미에서 지정 된 명령 라우팅을 사용 합니다. (MDI 프레임 창은 대리자 활성 MDI 자식 창에 명령 합니다.)

이 기능은 범용으로 설정 되었으며 MFC 2.0 보다 넓은 범위의 개체 (뿐 아니라: 창 개체)에서 처리 명령을 허용 하도록 확장 합니다. 더 많은 정식 제공 하 고 라우팅을 위한 확장 가능한 아키텍처 메시지 및 명령 처리 뿐만 아니라 뿐만 아니라 명령의 현재 가용성을 반영 하도록 UI 개체 (예: 메뉴 항목 및 도구 모음 단추)를 업데이트 하기 위한 명령 대상 라우팅 다시 사용 .

## <a name="command-ids"></a>명령 ID

명령 라우팅 및 바인딩 프로세스의 설명은 Visual c + +를 참조 하십시오. [Technical Note 20](../mfc/tn020-id-naming-and-numbering-conventions.md) ID 명명에 대 한 정보를 포함 합니다.

명령 Id에 대 한 제네릭 접두사 "ID_"를 사용 했습니다. 명령 Id는 > = 0x8000입니다. 메시지 줄 또는 상태 표시줄이 표시 됩니다. 명령 설명 문자열 경우 명령 id입니다.와 동일한 Id 사용 하 여 STRINGTABLE 리소스

응용 프로그램의 리소스 ID 수 명령 여러 위치에 나타납니다.

-   리소스 한 개에서 STRINGTABLE 메시지 줄 프롬프트와 동일한 ID를 포함 합니다.

-   수 많은 메뉴 리소스에서 동일한 명령을 호출 하는 메뉴 항목에 연결 되어 있는 합니다.

-   GOSUB 명령에 대 한 대화 상자 단추에 (고급).

응용 프로그램의 소스 코드에 ID 수 명령 여러 위치에 나타납니다.

-   리소스입니다. H (또는 다른 주 기호 헤더 파일) 응용 프로그램별 명령 Id를 정의할 수 있습니다.

-   에 도구 모음을 만드는 데 ID 배열입니다.

-   ON_COMMAND 매크로입니다.

-   아마도에 ON_UPDATE_COMMAND_UI 매크로입니다.

명령 Id를 필요로 하는 MFC의만 구현 될 현재, > = 0x8000GOSUB 대화 상자/명령의 구현입니다.

## <a name="gosub-commands-using-command-architecture-in-dialogs"></a>대화 상자에 명령을 아키텍처를 사용 하 여 GOSUB 명령

라우팅 및 명령을 사용 하는 명령 아키텍처의 프레임 창, 메뉴 항목, 도구 모음 단추, 대화 상자 막대 단추, 다른 컨트롤 막대 및 기타 사용자 인터페이스 요소를 요청 및 경로 명령에 업데이트 하거나 컨트롤을 기본 Id 설계와 잘 작동 명령 대상 (일반적으로 주 프레임 창)입니다. 주 명령 대상으로 하는 적절 하 게 다른 명령 대상 개체에 명령 또는 컨트롤 알림 라우팅할 수 있습니다.

적절 한 명령 id와 같습니다. 대화 상자 컨트롤의 컨트롤 ID를 할당 하는 경우 대화 상자 (모달 또는 모덜리스) 명령 아키텍처의 기능 중 일부에서 얻을 수합니다 있습니다. 대화 상자에 대 한 지원을 자동으로 하지 않으므로 몇 가지 추가 코드를 작성할 수 있습니다.

제대로 작동 하려면 이러한 모든 기능에 대 한 명령 Id 여야 합니다 > = 0x8000입니다. 많은 대화 상자에 같은 프레임 라우트되지 수, 이므로 공유 명령 수 > 특정 대화 상자에서 공유 되지 않는 IDCs 해야 하는 동안 0x8000, = < = 0x7FFF 합니다.

적절 한 명령 ID로 설정 하는 단추의 IDC와 일반 모달 대화 상자에 표준 단추를 배치할 수 있습니다. 사용자가 단추를 선택 대화 상자 (일반적으로 주 프레임 창)의 소유자는 다른 명령와 마찬가지로 명령을 가져옵니다. 일반적으로 다른 대화 상자 (첫 번째 대화의 GOSUB)를 표시 사용 되기 때문이 GOSUB 명령을 호출 됩니다.

함수를 호출할 수도 있습니다 `CWnd::UpdateDialogControls` 프로그램 대화 상자에 주 프레임 창의 주소를 전달 합니다. 이 함수를 사용 하도록 설정 되거나 프레임에 명령 처리기 권한이 있는지 여부에 따라 프로그램 대화 상자 컨트롤을 사용 하지 않도록 설정 됩니다. 이 함수는 호출 자동으로 사용자에 대 한 응용 프로그램의 유휴 상태 루프에서 컨트롤 막대에 대 한 되지만이 기능이 하고자 하는 일반 대화 상자에 대 한 직접 호출 해야 합니다.

## <a name="when-onupdatecommandui-is-called"></a>ON_UPDATE_COMMAND_UI 호출 될 때

항상 프로그램의 모든 메뉴 항목의 활성화/확인 상태를 유지 계산이 문제가 될 수 있습니다. 일반적인 기술 사용/검사 메뉴 항목 사용자가 팝업을 선택 하는 경우에와 야 합니다. MFC 2.0 구현 `CFrameWnd` WM_INITMENUPOPUP 메시지를 처리 하 고 명령 라우팅 아키텍처를 사용 하 여 ON_UPDATE_COMMAND_UI 처리기를 통해 메뉴의 상태를 결정 합니다.

`CFrameWnd` 또한 현재 메뉴 상태 표시줄 (메시지 줄 라고도 함)에 선택한 항목을 설명 하기 위해 WM_ENTERIDLE 메시지를 처리 합니다.

Visual c + +가 편집 되는 응용 프로그램의 메뉴 구조 WM_INITMENUPOPUP 시 사용할 수 있는 잠재적인 명령을 나타내는 데 사용 됩니다. ON_UPDATE_COMMAND_UI 처리기 상태 또는 메뉴의 텍스트를 수정 하거나 (예: 파일 MRU 목록 또는 OLE 동사 팝업 메뉴) 고급 용도로 실제로 구조를 수정할 메뉴의 메뉴를 그리기 전에 수 있습니다.

도구 모음 (및 다른 컨트롤 막대) 같은 종류의 ON_UPDATE_COMMAND_UI 처리는 수행 응용 프로그램의 유휴 상태 루프를 시작 하는 경우. 참조는 *클래스 라이브러리 참조* 및 [Technical Note 31](../mfc/tn031-control-bars.md) 컨트롤 막대에 대 한 자세한 내용은 합니다.

## <a name="nested-pop-up-menus"></a>중첩 된 팝업 메뉴

중첩 된 메뉴 구조를 사용 하는 경우 팝업 메뉴의 첫 번째 메뉴 항목에 대 한 ON_UPDATE_COMMAND_UI 처리기 두 가지 서로 다른 경우에 호출 되도록 확인할 수 있습니다.

첫째, 팝업 메뉴 자체에 대 한 호출 됩니다. 팝업 메뉴 Id가 없는 및 전체 팝업 메뉴를 참조 하는 팝업 메뉴의 첫 번째 메뉴 항목의 ID 사용 되므로이 작업이 필요 합니다. 이 경우에 *m_pSubMenu* 의 멤버 변수는 `CCmdUI` 개체가 NULL이 아닌 되 고 팝업 메뉴를 가리킵니다.

둘째, 팝업 메뉴에 메뉴 항목이 그릴 수 있도록 하기 바로 전에 호출 됩니다. 이 경우 ID 항목을 참조만 첫 번째 메뉴와 *m_pSubMenu* 의 멤버 변수는 `CCmdUI` 개체가 NULL이 됩니다.

이렇게 하면 팝업 메뉴가 해당 메뉴 항목을 구분 수 있지만 일부 메뉴 인식 코드를 작성 해야 합니다. 예를 들어 다음과 같은 구조의 중첩된 메뉴:

```Output
File>
    New>
    Sheet (ID_NEW_SHEET)
    Chart (ID_NEW_CHART)
```

ID_NEW_SHEET 명령과 ID_NEW_CHART를 독립적으로 설정 하거나 해제할 수 있습니다. **새로** 두 사용 되는 경우 팝업 메뉴를 활성화 해야 합니다.

ID_NEW_SHEET (팝업에서 첫 번째 명령은)에 대 한 명령 처리기는 다음과 같이 표시 됩니다.

```cpp
void CMyApp::OnUpdateNewSheet(CCmdUI* pCmdUI)
{
    if (pCmdUI->m_pSubMenu != NULL)
    {
        // enable entire pop-up for "New" sheet and chart
        BOOL bEnable = m_bCanCreateSheet || m_bCanCreateChart;
        // CCmdUI::Enable is a no-op for this case, so we
        // must do what it would have done.
        pCmdUI->m_pMenu->EnableMenuItem(pCmdUI->m_nIndex,
            MF_BYPOSITION | 
            (bEnable  MF_ENABLED : (MF_DISABLED | MF_GRAYED)));

        return;
    }
    // otherwise just the New Sheet command
    pCmdUI->Enable(m_bCanCreateSheet);
}
```

명령 처리기 ID_NEW_CHART에 대 한 일반 업데이트 명령 처리기와 같은 내용을 확인 합니다.

```cpp
void CMyApp::OnUpdateNewChart(CCmdUI* pCmdUI)
{
    pCmdUI->Enable(m_bCanCreateChart);
}
```

## <a name="oncommand-and-onbnclicked"></a>ON_COMMAND 및 ON_BN_CLICKED

에 대 한 메시지 맵 매크로 **ON_COMMAND** 및 **ON_BN_CLICKED** 동일 합니다. MFC 명령 및 제어 알림 라우팅 메커니즘만를 사용 하 여 명령 ID로 라우팅하는 위치를 결정 합니다. 0 컨트롤 알림 코드를 사용 하 여 알림을 제어 (**BN_CLICKED**)이 명령으로 해석 됩니다.

> [!NOTE]
> 모든 컨트롤 알림 메시지는 실제로 명령 처리기 체인을 통해 이동합니다. 예를 들어 것은 기술적으로 가능 하 여에 대 한 컨트롤 알림 처리기를 작성할 수 **EN_CHANGE** 문서 클래스에 있습니다. 이이 기능의 유용한 팁은 몇 가지, 기능 클래스 마법사에서 지원 되지 않습니다 및 기능의 취약 한 코드에서 발생할 수 있습니다 있으므로 일반적으로 권장 하지 않습니다.

## <a name="disabling-the-automatic-disabling-of-button-controls"></a>단추 컨트롤의 자동 해제를 사용 하지 않도록 설정

대화 상자 모음에 단추 컨트롤을 추가 하거나 호출 위치를 사용 하 여 대화 상자에서 **CWnd::UpdateDialogControls** 사용자 고유의에 없으면 해당 단추 알게 될 **ON_COMMAND** 또는 **ON_UPDATE_COMMAND_UI** 프레임 워크에 의해 있습니다에 처리기를 자동으로 사용 되지 것입니다. 일부 경우에는 처리기 하지 않아도 됩니다 있지만 단추를 사용 하도록 유지 해야 합니다. 이 작업을 수행할 수는 가장 쉬운 방법은 (쉽게 클래스 마법사를 사용 하 여 수행할 수)는 더미 명령 처리기를 추가 하는 것에 아무 작업도 수행 합니다.

## <a name="window-message-routing"></a>창 메시지 라우팅

다음은 MFC 클래스 및 Windows 메시지 라우팅 및 기타 항목이 미치는 영향에 일부 추가적인 고급 항목을 설명 합니다. 만 정보 간략하게 설명 합니다. 참조는 *클래스 라이브러리 참조* 공용 Api에 대 한 세부 정보에 대 한 합니다. 구현 세부 사항에 대 한 자세한 내용은 MFC 라이브러리 소스 코드를 참조 하십시오.

참조 하십시오 [기술 참고 17](../mfc/tn017-destroying-window-objects.md) 창 정리에 대 한 세부 정보, 모든에 대 한 매우 중요 한 항목에 대 한 **CWnd**-파생 된 클래스입니다.

## <a name="cwnd-issues"></a>CWnd 문제

구현 멤버 함수 **cwnd:: Onchildnotify** 후크 하거나 그렇지 않은 경우에 대해 숙지 메시지, 명령 및 컨트롤을 자식 창 (제어)에 대 한 강력 하 고 확장 가능한 아키텍처를 제공 해당 부모 (또는 "소유자")로 이동 하는 알림입니다. 경우 자식 창 (/ 제어)는 c + +는 **CWnd** 개체 자체 가상 함수 **OnChildNotify** 원본 메시지에서 매개 변수를 가진 먼저 호출 되어 (즉, 한 **MSG**구조). 자식 창 메시지를 그대로,에서는 하거나 (드물게) 부모에 대 한 메시지를 수정할 수 있습니다.

기본 **CWnd** 구현을 다음 메시지를 처리 하 고 사용 하 여는 **OnChildNotify** 후크 자식 windows (제어)는 메시지에서 첫 번째 액세스 하도록 허용 하려면:

- **WM_MEASUREITEM** 및 **WM_DRAWITEM** (에 대 한 자체 그리기)

- **WM_COMPAREITEM** 및 **WM_DELETEITEM** (에 대 한 자체 그리기)

- **WM_HSCROLL** 및 **WM_VSCROLL**

- **WM_CTLCOLOR**

- **창에 WM_PARENTNOTIFY**

알 수는 **OnChildNotify** 후크 자체 그리기 메시지로 소유자 그리기 메시지를 변경 하는 데 사용 됩니다.

외에 **OnChildNotify** 후크, 스크롤 메시지 추가 동작을 라우팅 있어야 합니다. 스크롤 막대와 소스에 대 한 자세한 내용은 아래를 참조 하십시오 **WM_HSCROLL** 및 **WM_VSCROLL** 메시지입니다.

## <a name="cframewnd-issues"></a>CFrameWnd 문제

**CFrameWnd** 대부분의 명령 라우팅 및 사용자 인터페이스를 제공 하는 클래스 구현을 업데이트 합니다. 응용 프로그램의 주 프레임 창에 주로 사용 됩니다 (**M_pmainwnd**) 이지만 모든 프레임 창에 적용 됩니다.

주 프레임 창 메뉴 모음으로 창이 고 상태 표시줄의 부모인 또는 줄 메시지입니다. 명령 라우팅에 대 한 위의 설명과 참조 하십시오 및 **WM_INITMENUPOPUP 합니다.**

**CFrameWnd** 클래스 현재 보기의 관리 기능을 제공 합니다. 다음과 같은 메시지가 활성 뷰를 통해 라우팅됩니다.

- 모든 명령 메시지 (현재 보기에 대 한 첫 번째 액세스를 get).

- **WM_HSCROLL** 및 **WM_VSCROLL** 메시지에서 형제 스크롤 막대 (아래 참조).

- **WM_ACTIVATE** (및 **WM_MDIACTIVATE** MDI에) 가상 함수에 대 한 호출으로 설정 되어 가져오기 **CView::OnActivateView**합니다.

## <a name="cmdiframewndcmdichildwnd-issues"></a>CMDIFrameWnd/CMDIChildWnd 문제

두 MDI 프레임 창 클래스에서 파생 **CFrameWnd** 하 고 따라서 둘 다 사용 하도록 설정 된 동일한 종류의 명령 라우팅에 제공 된 사용자 인터페이스 업데이트 및 **CFrameWnd**합니다. 일반적인 MDI 응용 프로그램에서 주 프레임 창 (즉,는 **CMDIFrameWnd** 개체) 메뉴 모음 및 상태 표시줄을 보유 하 고 따라서 명령 라우팅 구현의 기본 소스를 있습니다.

일반적인 라우팅 구성표는 활성 MDI 자식 창에 명령에 대 한 첫 번째 액세스 가져옴을입니다. 기본 **PreTranslateMessage** 함수 (첫 번째) 두 MDI 자식 창에 대 한 액셀러레이터 키 테이블을 처리 하는 MDI 프레임 (두 번째)에 의해 처리 일반적으로 표준 MDI 시스템 명령 액셀러레이터 뿐만 아니라  **TranslateMDISysAccel** (마지막).

## <a name="scroll-bar-issues"></a>스크롤 막대 문제

스크롤 메시지를 처리 하는 경우 (**WM_HSCROLL**/**OnHScroll** 및/또는 **WM_VSCROLL**/**OnVScroll**), 스크롤 막대 메시지에서 제공 하는 위치에 의존 하지 않는 처리기 코드를 작성 하려고 노력 해야 합니다. 이것이 일반적인 Windows 문제만 스크롤 메시지 true 스크롤 막대 컨트롤 또는에서 비롯 될 수 있으므로 **WS_HSCROLL**/**WS_VSCROLL** 스크롤 막대 없는 스크롤 막대 컨트롤입니다.

MFC 확장을 자식 또는 형제는 스크롤되는 창의 스크롤 막대 컨트롤에 대 한 허용 하는 (실제로 스크롤되는 창과 스크롤 막대의 부모/자식 관계 가능 아무 것도). 분할 창 함께 공유 스크롤 막대에 대 한 경우 특히 유용합니다. 참조 하십시오 [기술 참고 29](../mfc/tn029-splitter-windows.md) 의 구현에 대 한 내용은 **CSplitterWnd** 스크롤 막대 문제 공유에 자세한 정보를 포함 합니다.

보조 노트에는 두 개의 **CWnd** 파생된 클래스에서 지정 된 스크롤 막대 스타일 생성 시간 트래핑 아니며 Windows로 전달 되지 않습니다. 작성 루틴에 전달 될 때 **WS_HSCROLL** 및 **WS_VSCROLL** 독립적으로 설정할 수 없습니다, 후에 만들기를 변경할 수 없습니다. 물론, 직접 테스트 하거나 해야는 자신이 만든 창 WS_SCROLL 스타일 비트가 설정 합니다.

에 대 한 **CMDIFrameWnd** 스크롤 막대 스타일에 전달할 있습니다 **만들기** 또는 **LoadFrame** 는 MDICLIENT를 만드는 데 사용 됩니다. 스크롤 막대의 스타일으로 설정 해야 스크롤 가능한 MDICLIENT 영역 (같은 Windows 프로그램 관리자)을 두려는 경우 둘 다 (**WS_HSCROLL** &#124; **WS_VSCROLL**)는 를만드는데스타일에대한**CMDIFrameWnd**합니다.

에 대 한 **CSplitterWnd** 분할 영역에 대 한 특별 한 공유 스크롤 막대에 스크롤 막대 스타일 적용. 정적 분할 창에 대 한 아닌 일반적인 두 가지 스크롤 막대 스타일을 설정 합니다. 동적 분할 창에 대 한 있습니다은 일반적으로 스크롤 막대 스타일 집합 즉, 분할 하는 방향에 대 한 **WS_HSCROLL** 행을 분할할 수 하는 경우 **WS_VSCROLL** 경우 열을 분할할 수 있습니다.

## <a name="see-also"></a>참고 항목

[번호별 기술 참고 사항](../mfc/technical-notes-by-number.md)  
[범주별 기술 참고 사항](../mfc/technical-notes-by-category.md)  

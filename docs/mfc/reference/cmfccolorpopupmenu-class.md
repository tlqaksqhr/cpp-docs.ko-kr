---
title: CMFCColorPopupMenu 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCColorPopupMenu
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::CMFCColorPopupMenu
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::CreateTearOffBar
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::GetMenuBar
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::SetPropList
dev_langs:
- C++
helpviewer_keywords:
- CMFCColorPopupMenu [MFC], CMFCColorPopupMenu
- CMFCColorPopupMenu [MFC], CreateTearOffBar
- CMFCColorPopupMenu [MFC], GetMenuBar
- CMFCColorPopupMenu [MFC], SetPropList
ms.assetid: 0bf9efe8-aed5-4ab7-b23b-eb284b4668be
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b32317f4fd67a627a272ea8eefcc949d1b0e63c8
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/05/2018
ms.locfileid: "37852996"
---
# <a name="cmfccolorpopupmenu-class"></a>CMFCColorPopupMenu 클래스
사용자가 문서 또는 응용 프로그램에서 색을 선택 하는 데 사용할 팝업 메뉴를 나타냅니다.  
  
## <a name="syntax"></a>구문  
  
```  
class CMFCColorPopupMenu : public CMFCPopupMenu  
```  
  
## <a name="members"></a>멤버  
  
### <a name="public-constructors"></a>Public 생성자  
  
|||  
|-|-|  
|이름|설명|  
|[CMFCColorPopupMenu::CMFCColorPopupMenu](#cmfccolorpopupmenu)|`CMFCColorPopupMenu` 개체를 생성합니다.|  
|`CMFCColorPopupMenu::~CMFCColorPopupMenu`|소멸자|  
  
### <a name="public-methods"></a>Public 메서드  
  
|||  
|-|-|  
|이름|설명|  
|[CMFCColorPopupMenu::CreateTearOffBar](#createtearoffbar)|도킹 가능한 분리 색 막대를 만듭니다. (재정의 [CMFCPopupMenu::CreateTearOffBar](../../mfc/reference/cmfcpopupmenu-class.md#createtearoffbar).)|  
|[CMFCColorPopupMenu::GetMenuBar](#getmenubar)|반환 된 [CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md) 팝업 메뉴 내에 포함 되어 있는 합니다. (재정의 [CMFCPopupMenu::GetMenuBar](../../mfc/reference/cmfcpopupmenu-class.md#getmenubar).)|  
|`CMFCColorPopupMenu::GetThisClass`|에 대 한 포인터를 가져오는 데 프레임 워크에 의해 합니다 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 이 클래스 형식과 연결 된 개체입니다.|  
|[CMFCColorPopupMenu::SetPropList](#setproplist)|포함 된 속성 표 컨트롤 개체를 설정 `CMFCColorBar` 개체입니다.|  
  
### <a name="data-members"></a>데이터 멤버  
  
|||  
|-|-|  
|name|설명|  
|`m_bEnabledInCustomizeMode`|색 막대를 표시할지 여부를 결정 하는 부울 값입니다.|  
|`m_wndColorBar`|`CMFCColorBar` 색 선택 영역을 제공 하는 개체입니다.|  
  
### <a name="remarks"></a>설명  
 이 클래스의 팝업 메뉴 기능을 상속 합니다 `CMFCPopupMenu` 클래스 및 관리는 `CMFCColorBar` 색 선택 영역을 제공 하는 개체입니다. 사용자 지정 모드에서 도구 모음 프레임 워크의 경우 및 `m_bEnabledInCustomizeMode` 멤버가 FALSE로 설정, 색 막대 개체 표시 되지 않습니다. 사용자 지정 모드에 대 한 자세한 내용은 참조 하세요. [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)  
  
 에 대 한 자세한 내용은 `CMFCColorBar`를 참조 하세요 [CMFCColorBar 클래스](../../mfc/reference/cmfccolorbar-class.md)합니다.  
  
## <a name="inheritance-hierarchy"></a>상속 계층  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)  
  
 [CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)  
  
 [CMFCColorPopupMenu](../../mfc/reference/cmfccolorpopupmenu-class.md)  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** afxcolorpopupmenu.h  
  
##  <a name="cmfccolorpopupmenu"></a>  CMFCColorPopupMenu::CMFCColorPopupMenu  
 `CMFCColorPopupMenu` 개체를 생성합니다.  
  
```  
CMFCColorPopupMenu(
    const CArray<COLORREF, COLORREF>& colors,  
    COLORREF color,  
    LPCTSTR lpszAutoColor,  
    LPCTSTR lpszOtherColor,  
    LPCTSTR lpszDocColors, CList<COLORREF, COLORREF>& lstDocColors,  
    int nColumns,  
    int nHorzDockRows,  
    int nVertDockColumns,  
    COLORREF colorAutomatic,  
    UINT uiCommandID,  
    BOOL bStdColorDlg = FALSE);

 
CMFCColorPopupMenu(
    CMFCColorButton* pParentBtn,  
    const CArray<COLORREF, COLORREF>& colors,  
    COLORREF color,  
    LPCTSTR lpszAutoColor,  
    LPCTSTR lpszOtherColor,  
    LPCTSTR lpszDocColors, CList<COLORREF, COLORREF>& lstDocColors,  
    int nColumns,  
    COLORREF colorAutomatic);

 
CMFCColorPopupMenu(
    CMFCRibbonColorButton* pParentBtn,  
    const CArray<COLORREF, COLORREF>& colors,  
    COLORREF color,  
    LPCTSTR lpszAutoColor,  
    LPCTSTR lpszOtherColor,  
    LPCTSTR lpszDocColors, CList<COLORREF, COLORREF>& lstDocColors,  
    int nColumns,  
    COLORREF colorAutomatic,  
    UINT nID);
```  
  
### <a name="parameters"></a>매개 변수  
 [in] *색*  
 배열 프레임 워크 팝업 메뉴에 표시 되는 색입니다.  
  
 [in] *색*  
 기본 색을 선택 합니다.  
  
 [in] *lpszAutoColor*  
 텍스트 레이블을 합니다 *자동* 색 단추 (기본값) 또는 NULL입니다.  
  
 자동 단추에 대 한 표준 레이블이 **자동**합니다.  
  
 [in] *lpszOtherColor*  
 텍스트 레이블을 합니다 *다른* 단추를 표시 하는 색 중에서 더 또는 NULL입니다.  
  
 기타 단추에 대 한 표준 레이블이 **다른 색...** .  
  
 [in] *lpszDocColors*  
 문서 색 단추 텍스트 레이블입니다. 문서 색 색상표를 문서에서 현재 사용 하는 모든 색을 나열 합니다.  
  
 [in] *lstDocColors*  
 현재 문서에 사용 된 색 목록을 합니다.  
  
 [in] *nColumns*  
 색 배열에 있는 열의 수입니다.  
  
 [in] *nHorzDockRows*  
 가로로 도킹 될 때 색 막대에는 행의 수입니다.  
  
 [in] *nVertDockColumns*  
 세로로 도킹 될 때 색 막대에 있는 열의 수입니다.  
  
 [in] *colorAutomatic*  
 프레임 워크에는 자동 단추를 클릭할 때 적용 되는 기본 색입니다.  
  
 [in] *uiCommandID*  
 색 막대 컨트롤 명령 id입니다.  
  
 [in] *bStdColorDlg*  
 표준 시스템 색 대화 상자를 표시할지 여부를 나타내는 부울 값 또는 [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) 대화 상자.  
  
 [in] *pParentBtn*  
 부모 단추에 대 한 포인터입니다.  
  
 [in] *nID*  
 명령 ID입니다.  
  
### <a name="remarks"></a>설명  
 생성자 오버 로드 된 각는 `m_bEnabledInCustomizeMode` 멤버 FALSE입니다.  
  
### <a name="example"></a>예  
 다음 예제에서는 생성 하는 방법에 설명 된 `CMFCColorPopupMenu` 개체입니다.  
  
 [!code-cpp[NVC_MFC_RibbonApp#34](../../mfc/reference/codesnippet/cpp/cmfccolorpopupmenu-class_1.cpp)]  
  
##  <a name="createtearoffbar"></a>  CMFCColorPopupMenu::CreateTearOffBar  
 도킹 가능한 분리 색 막대를 만듭니다.  
  
```  
virtual CPane* CreateTearOffBar(
    CFrameWnd* pWndMain,  
    UINT uiID,  
    LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>매개 변수  
  
|||  
|-|-|  
|매개 변수|설명|  
|[in] *pWndMain*|분리 막대가 막대의 부모 창에 대 한 포인터입니다.|  
|[in] *uiID*|분리 막대가 막대의 명령 ID입니다.|  
|[in] *lpszName*|창 텍스트 분리 모음입니다.|  
  
### <a name="return-value"></a>반환 값  
 새 분리 컨트롤 막대 개체에 대 한 포인터입니다.  
  
### <a name="remarks"></a>설명  
 이 메서드를 만듭니다는 [CMFCColorBar 클래스](../../mfc/reference/cmfccolorbar-class.md) 개체를 캐스팅 하는 [CPane 클래스](../../mfc/reference/cpane-class.md) 포인터입니다. 이 값으로 캐스팅할 수 있습니다 다시를 [CMFCColorBar 클래스](../../mfc/reference/cmfccolorbar-class.md) 에 설명 된 캐스팅 매크로 중 하나를 사용 하 여 포인터 [MFC 클래스 개체의 형식 캐스팅의](../../mfc/reference/type-casting-of-mfc-class-objects.md)합니다.  
  
##  <a name="getmenubar"></a>  CMFCColorPopupMenu::GetMenuBar  
 반환 된 [CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md) 팝업 메뉴 내에 포함 되어 있는 합니다.  
  
```  
virtual CMFCPopupMenuBar* GetMenuBar();
```  
  
### <a name="return-value"></a>반환 값  
 포함에 대 한 포인터 `CMFCPopupMenuBar`합니다.  
  
### <a name="remarks"></a>설명  
 색 팝업 메뉴에 포함 된 [CMFCPopupMenuBar 클래스](../../mfc/reference/cmfcpopupmenubar-class.md) 개체입니다. 응용 프로그램에 포함 된 유형을 사용 하는 경우 파생된 클래스에서이 메서드를 재정의 합니다.  
  
##  <a name="setproplist"></a>  CMFCColorPopupMenu::SetPropList  
 포함 된 속성 표 컨트롤 개체를 설정 `CMFCColorBar` 개체입니다.  
  
```  
void SetPropList(CMFCPropertyGridCtrl* pWndList);
```  
  
### <a name="parameters"></a>매개 변수  
 [in] *pWndList*  
 속성 표 컨트롤 개체에 대 한 포인터입니다.  
  
## <a name="see-also"></a>참고 항목  
 [계층 구조 차트](../../mfc/hierarchy-chart.md)   
 [클래스](../../mfc/reference/mfc-classes.md)

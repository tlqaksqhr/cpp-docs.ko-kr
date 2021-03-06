---
title: DDX_DHtml 도우미 매크로 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- AFXDHTML/DDX_DHtml_ElementValue
- AFXDHTML/DDX_DHtml_ElementInnerText
- AFXDHTML/DDX_DHtml_ElementInnerHtml
- AFXDHTML/DDX_DHtml_Anchor_Href
- AFXDHTML/DDX_DHtml_Anchor_Target
- AFXDHTML/DDX_DHtml_Img_Src
- AFXDHTML/DDX_DHtml_Frame_Src
- AFXDHTML/DDX_DHtml_IFrame_Src
dev_langs:
- C++
helpviewer_keywords:
- macros [MFC], exchanging data with HMTL pages
- DDX macros [MFC]
- HTML pages [MFC], helper macros
- DDX (dialog data exchange), DHtml helper macros
- macros [MFC], DDX_DHtml helpers
ms.assetid: c46302d2-ea43-4fea-bfc2-6f590d99f267
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6de53324eac663df7c12ee0cb2c0f4f02558157d
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37121704"
---
# <a name="ddxdhtml-helper-macros"></a>DDX_DHtml 도우미 매크로
DDX_DHtml 도우미 매크로 사용 하는 HTML 페이지에 있는 컨트롤의 자주 사용 되는 속성에 쉽게 액세스할 수 있습니다.  
  
### <a name="data-exchange-macros"></a>데이터 교환 매크로  
  
|||  
|-|-|  
|[DDX_DHtml_ElementValue](#ddx_dhtml_elementvalue)|설정 하거나 선택된 된 컨트롤에서 속성 값을 검색 합니다.|  
|[DDX_DHtml_ElementInnerText](#ddx_dhtml_elementinnertext)|설정 하거나 현재 요소의 시작 및 끝 태그 사이 오는 텍스트를 검색 합니다.|  
|[DDX_DHtml_ElementInnerHtml](#ddx_dhtml_elementinnerhtml)|설정 하거나 현재 요소의 시작 및 끝 태그 사이의 HTML을 검색 합니다.|  
|[DDX_DHtml_Anchor_Href](#ddx_dhtml_anchor_href)|설정 하거나 대상 URL 또는 앵커 지점을 검색 합니다.|  
|[DDX_DHtml_Anchor_Target](#ddx_dhtml_anchor_target)|설정 하거나 대상 창이 나 프레임을 검색 합니다.|  
|[DDX_DHtml_Img_Src](#ddx_dhtml_img_src)|설정 하거나 이미지 또는 문서에서 비디오 클립의 이름을 검색 합니다.|  
|[DDX_DHtml_Frame_Src](#ddx_dhtml_frame_src)|설정 하거나 연결된 된 프레임의 URL을 검색 합니다.|  
|[DDX_DHtml_IFrame_Src](#ddx_dhtml_iframe_src)|설정 하거나 연결된 된 프레임의 URL을 검색 합니다.|  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** afxdhtml.h  

## <a name="ddx_dhtml_anchor_href"></a> DDX_DHtml_Anchor_Href
설정 하거나 대상 URL 또는 앵커 지점을 검색 합니다.  
  
  
  
```  
DDX_DHtml_Anchor_Href(
    CDataExchange* dx,  
    LPCTSTR name,  
    CString& var)  
```  
  
#### <a name="parameters"></a>매개 변수  
 *dx*  
 에 대 한 포인터는 [CDataExchange](../../mfc/reference/cdataexchange-class.md) 개체입니다.  
  
 *name*  
 HTML 컨트롤의 ID 매개 변수에 지정한 값입니다.  
  
 *var*  
 교환 되는 값입니다.  
  
## <a name="remarks"></a>설명  
 이 매크로 호출의 [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) 함수는 DISPID_IHTMLANCHORELEMENT_HREF를 사용 하 여 디스패치 id입니다.

## <a name="ddx_dhtml_anchor_target"></a>  DDX_DHtml_Anchor_Target
 설정 하거나 대상 창이 나 프레임을 검색 합니다.  
    
```  
DDX_DHtml_Anchor_Target(
    CDataExchange* dx,  
    LPCTSTR name,  
    CString& var)  
```  
  
#### <a name="parameters"></a>매개 변수  
 *dx*  
 에 대 한 포인터는 [CDataExchange](../../mfc/reference/cdataexchange-class.md) 개체입니다.  
  
 *name*  
 HTML 컨트롤의 ID 매개 변수에 지정한 값입니다.  
  
 *var*  
 교환 되는 값입니다.  
  
## <a name="remarks"></a>설명  
 이 매크로 호출의 [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) 함수는 DISPID_IHTMLANCHORELEMENT_TARGET를 사용 하 여 디스패치 id입니다.  

## <a name="ddx_dhtml_elementinnerhtml"></a>  DDX_DHtml_ElementInnerHtml
 설정 하거나 현재 요소의 시작 및 끝 태그 사이의 HTML을 검색 합니다.  
  
  
  
```  
DDX_DHtml_ElementInnerHtml(
    CDataExchange* dx,  
    LPCTSTR name,  
    CString& var)  
```  
  
#### <a name="parameters"></a>매개 변수  
 *dx*  
 에 대 한 포인터는 [CDataExchange](../../mfc/reference/cdataexchange-class.md) 개체입니다.  
  
 *name*  
 HTML 컨트롤의 ID 매개 변수에 지정한 값입니다.  
  
 *var*  
 교환 되는 값입니다.  
  
## <a name="remarks"></a>설명  
 이 매크로 호출의 [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) 함수는 DISPID_IHTMLELEMENT_INNERHTML를 사용 하 여 디스패치 id입니다.  
  

## <a name="ddx_dhtml_elementinnertext"></a>  DDX_DHtml_ElementInnerText
설정 하거나 현재 요소의 시작 및 끝 태그 사이 오는 텍스트를 검색 합니다.  
  
  
  
```  
DDX_DHtml_ElementInnerText(
    CDataExchange* dx,  
    LPCTSTR name,  
    CString& var)  
```  
  
#### <a name="parameters"></a>매개 변수  
 *dx*  
 에 대 한 포인터는 [CDataExchange](../../mfc/reference/cdataexchange-class.md) 개체입니다.  
  
 *name*  
 HTML 컨트롤의 ID 매개 변수에 지정한 값입니다.  
  
 *var*  
 교환 되는 값입니다.  
  
## <a name="remarks"></a>설명  
 이 매크로 호출의 [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) 함수는 DISPID_IHTMLELEMENT_INNERTEXT를 사용 하 여 디스패치 id입니다. 

## <a name="ddx_dhtml_elementvalue"></a> DDX_DHtml_ElementValue  
설정 하거나 선택된 된 컨트롤에서 속성 값을 검색 합니다.  
 
```  
DDX_DHtml_ElementValue(
    CDataExchange* dx,  
    LPCTSTR name,
    var)  
```  
  
#### <a name="parameters"></a>매개 변수  
 *dx*  
 에 대 한 포인터는 [CDataExchange](../../mfc/reference/cdataexchange-class.md) 개체입니다.  
  
 *name*  
 HTML 컨트롤의 ID 매개 변수에 지정한 값입니다.  
  
 *var*  
 교환 되는 값입니다. 참조 *값* 에 [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext)합니다.  
  
## <a name="remarks"></a>설명  
 이 매크로 Value 속성에 있는 컨트롤에서 실행 하는 경우에 성공할 수 있습니다. Value 속성에 있는 컨트롤에는 편집 상자, 목록 상자 및 콤보 상자 포함 됩니다.  
  
 이 매크로 호출의 [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) 함수는 DISPID_A_VALUE를 사용 하 여 디스패치 id입니다.  

## <a name="ddx_dhtml_frame_src"></a> DDX_DHtml_Frame_Src
설정 하거나 연결된 된 프레임의 URL을 검색 합니다.  
  
```  
DDX_DHtml_Frame_Src(
    CDataExchange* dx,  
    LPCTSTR name,  
    CString& var)  
```  
  
#### <a name="parameters"></a>매개 변수  
 *dx*  
 에 대 한 포인터는 [CDataExchange](../../mfc/reference/cdataexchange-class.md) 개체입니다.  
  
 *name*  
 HTML 컨트롤의 ID 매개 변수에 지정한 값입니다.  
  
 *var*  
 교환 되는 값입니다.  
  
## <a name="remarks"></a>설명  
 이 매크로 호출의 [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) 함수는 DISPID_IHTMLFRAMEBASE_SRC를 사용 하 여 디스패치 id입니다.  

## <a name="ddx_dhtml_iframe_src"></a> DDX_DHtml_IFrame_Src
설정 하거나 연결된 된 프레임의 URL을 검색 합니다.  
  
  
  
```  
DDX_DHtml_IFrame_Src(
    CDataExchange* dx,  
    LPCTSTR name,  
    CString& var)  
```  
  
#### <a name="parameters"></a>매개 변수  
 *dx*  
 에 대 한 포인터는 [CDataExchange](../../mfc/reference/cdataexchange-class.md) 개체입니다.  
  
 *name*  
 HTML 컨트롤의 ID 매개 변수에 지정한 값입니다.  
  
 *var*  
 교환 되는 값입니다.  
  
## <a name="remarks"></a>설명  
 이 매크로 호출의 [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) 함수는 DISPID_IHTMLFRAMEBASE_SRC를 사용 하 여 디스패치 id입니다. 

## <a name="ddx_dhtml_img_src"></a>DDX_DHtml_Img_Src
이미지 또는 문서에서 비디오 클립의 이름을 검색 하거나 가져옵니다.  
  
```  
DDX_DHtml_Img_Src(
    CDataExchange* dx,  
    LPCTSTR name,  
    CString& var)  
```  
  
#### <a name="parameters"></a>매개 변수  
 *dx*  
 에 대 한 포인터는 [CDataExchange](../../mfc/reference/cdataexchange-class.md) 개체입니다.  
  
 *name*  
 HTML 컨트롤의 ID 매개 변수에 지정한 값입니다.  
  
 *var*  
 교환 되는 값입니다.  
  
## <a name="remarks"></a>설명  
 DDX_DHtml_Img_Src 매크로 사용 하 여 이미지 요소에 대 한 src 속성을 검색, Internet Explorer image 개체는 이미지 원본에 대 한 완전 하 게 이스케이프 된 URL을 반환 합니다. 예를 들어 "몇 가지 흥미로운 그림" 문자열에 이미지 요소의 src 속성을 설정 하려면 DDX_DHtml_Img_Src 매크로 사용 하는 경우 Internet Explorer 해당 속성을 검색할 때 반환 합니다 "res://d:\myapplication\myapp.exe/some% 문자열 20interesting %20picture입니다. "  
  
 이 매크로 호출의 [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) 함수는 DISPID_IHTMLIMGELEMENT_SRC를 사용 하 여 디스패치 id입니다.  

  
## <a name="see-also"></a>참고 항목  
 [CDHtmlDialog 클래스](../../mfc/reference/cdhtmldialog-class.md)

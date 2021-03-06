---
title: 'TN065: OLE 자동화 서버에 대 한 이중 인터페이스 지원 | Microsoft Docs'
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.ole
dev_langs:
- C++
helpviewer_keywords:
- dual interfaces [MFC], OLE Automation
- TN065 [MFC]
- ACDUAL sample [MFC]
- Automation servers [MFC], dual-interface support
ms.assetid: b5c8ed09-2f7f-483c-80fc-2a47ad896063
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e30be46aeab92f63f1b4cba593cda52bf9aeef9a
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37122185"
---
# <a name="tn065-dual-interface-support-for-ole-automation-servers"></a>TN065: OLE 자동화 서버에 대한 이중 인터페이스 지원

> [!NOTE]
> 다음 기술 노트는 온라인 설명서에 먼저 포함되어 있었으므로 업데이트되지 않았습니다. 따라서 일부 절차 및 항목은 만료되거나 올바르지 않을 수 있습니다. 최신 정보를 보려면 온라인 설명서 색인에서 관심 있는 항목을 검색하는 것이 좋습니다.

이 노트에서는 MFC 기반 OLE 자동화 서버 응용 프로그램에 이중 인터페이스를 추가 하는 방법을 설명 합니다. [ACDUAL](../visual-cpp-samples.md) 예제에서는 이중 인터페이스 지원 및 ACDUAL에서이 정보에 예제 코드를 가져옵니다. 예: DECLARE_DUAL_ERRORINFO, DUAL_ERRORINFO_PART, 및 IMPLEMENT_DUAL_ERRORINFO,이 정보에 설명 된 매크로 ACDUAL 샘플의 일부 이며 MFCDUAL에서 확인할 수 있습니다. 8.

## <a name="dual-interfaces"></a>이중 인터페이스

OLE 자동화를 사용 하면 구현할 수 있지만 `IDispatch` 인터페이스, VTBL 인터페이스 또는 이중 인터페이스 (포괄 하는 둘 다), 표시 된 모든 OLE 자동화 개체에 대 한 이중 인터페이스를 구현 하는 적극 권장 합니다. 이중 인터페이스를 통해 중요 한 이점이 `IDispatch`-유일한 또는 VTBL 전용 인터페이스:

- 바인딩 VTBL 인터페이스를 통해 컴파일 시 또는 런타임에 통해 수행 될 수 `IDispatch`합니다.

- VTBL 인터페이스를 사용할 수 있는 OLE 자동화 컨트롤러에서 향상 된 성능 이점을 얻을 수 있습니다.

- 사용 하는 기존 OLE 자동화 컨트롤러는 `IDispatch` 인터페이스는 계속 작동 합니다.

- VTBL 인터페이스는 c + +에서 호출할 수 있습니다.

- 이중 인터페이스는 Visual Basic 개체 지원 기능에 대 한 호환성을 위해 필요 합니다.

## <a name="adding-dual-interface-support-to-a-ccmdtarget-based-class"></a>CCmdTarget 기반 클래스에 이중 인터페이스 지원 추가

이중 인터페이스에서 파생 된 사용자 지정 인터페이스 실제로 `IDispatch`합니다. 이중 인터페이스 지원에서 구현 하는 가장 간단한 방법은 `CCmdTarget`-정상적인 디스패치 MFC 및 클래스 마법사를 사용 하 여 클래스에 인터페이스 다음 나중에 사용자 지정 인터페이스를 추가 하는 첫 번째 구현에 따라 클래스는 합니다. 대부분의 경우 사용자 지정 인터페이스 구현에서 MFC에 다시 위임 단순히 `IDispatch` 구현 합니다.

첫째, 개체에 대 한 이중 인터페이스를 정의 하 여 서버에 대 한 ODL 파일을 수정 합니다. 대신에 인터페이스 문을 사용 해야 하는 이중 인터페이스를 정의 하려면는 `DISPINTERFACE` Visual c + + 마법사에서 생성 하는 문입니다. 기존 제거 하는 대신 `DISPINTERFACE` 문, 새 인터페이스 문을 추가 합니다. 유지 하 여는 `DISPINTERFACE` 폼 클래스 마법사를 사용 하 여 사용자 개체에 메서드와 속성을 추가 하려면를 계속할 수 있지만 인터페이스 문에 해당 하는 속성 및 메서드를 추가 해야 합니다.

이중 인터페이스에 대 한 인터페이스 문이 있어야는 *OLEAUTOMATION* 및 *이중* 특성과 인터페이스에서 파생 되어야 합니다 `IDispatch`합니다. 사용할 수는 [GUIDGEN](../visual-cpp-samples.md) 를 만들기 위한 샘플은 **IID** 이중 인터페이스에 대 한 합니다.

```IDL
[ uuid(0BDD0E81-0DD7-11cf-BBA8-444553540000), // IID_IDualAClick
    oleautomation,
    dual
]
interface IDualAClick : IDispatch
    {
    };
```

인터페이스 문을 위치에 있으면 메서드 및 속성에 대 한 항목을 추가 하기 시작 합니다. 이중 인터페이스에 대 한 메서드 및 이중 인터페이스의 속성 접근자 함수를 반환 하는 매개 변수 목록을 다시 정렬 해야는 **HRESULT** 특성을가진매개변수로반환값을전달`[retval,out]`. 속성에는 필요 합니다 모두 읽기를 추가 하려면 (`propget`) 및 쓰기 (`propput`) 동일한 id 가진 함수에 액세스 합니다. 예를 들어:

```IDL
[propput, id(1)] HRESULT text([in] BSTR newText);
[propget, id(1)] HRESULT text([out, retval] BSTR* retval);
```

메서드 및 속성을 정의한 후 coclass 문에서 인터페이스에 대 한 참조를 추가 해야 합니다. 예를 들어:

```IDL
[ uuid(4B115281-32F0-11cf-AC85-444553540000) ]
coclass Document
{
    dispinterface IAClick;
    [default] interface IDualAClick;
};
```

ODL 파일을 업데이트 후 MFC의 인터페이스 맵 메커니즘을 사용 하 여 개체 클래스에 이중 인터페이스에 대 한 구현 클래스를 정의 하 고 mfc의 해당 항목을 확인 하려면 `QueryInterface` 메커니즘입니다. 에 있는 하나의 항목 필요는 `INTERFACE_PART` ODL의 인터페이스 문에서 각 항목 및 디스패치 인터페이스에 대 한 항목에 대 한 블록입니다. 각 ODL 항목으로는 *propput* 특성 라는 함수가 필요 `put_propertyname`합니다. 각 항목은 *propget* 특성 라는 함수가 필요 `get_propertyname`합니다.

이중 인터페이스에 대 한 구현 클래스를 정의 하려면 추가 `DUAL_INTERFACE_PART` 개체 클래스 정의에 블록입니다. 예를 들어:

```cpp
BEGIN_DUAL_INTERFACE_PART(DualAClick, IDualAClick)
    STDMETHOD(put_text)(THIS_ BSTR newText);
    STDMETHOD(get_text)(THIS_ BSTR FAR* retval);
    STDMETHOD(put_x)(THIS_ short newX);
    STDMETHOD(get_x)(THIS_ short FAR* retval);
    STDMETHOD(put_y)(THIS_ short newY);
    STDMETHOD(get_y)(THIS_ short FAR* retval);
    STDMETHOD(put_Position)(THIS_ IDualAutoClickPoint FAR* newPosition);
    STDMETHOD(get_Position)(THIS_ IDualAutoClickPoint FAR* FAR* retval);
    STDMETHOD(RefreshWindow)(THIS);
    STDMETHOD(SetAllProps)(THIS_ short x, short y, BSTR text);
    STDMETHOD(ShowWindow)(THIS);
END_DUAL_INTERFACE_PART(DualAClick)
```

MFC의 이중 인터페이스를 연결할 [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms687230) 메커니즘을 추가 `INTERFACE_PART` 인터페이스 맵에 항목:

```cpp
BEGIN_INTERFACE_MAP(CAutoClickDoc, CDocument)
    INTERFACE_PART(CAutoClickDoc, DIID_IAClick, Dispatch)
    INTERFACE_PART(CAutoClickDoc, IID_IDualAClick, DualAClick)
END_INTERFACE_MAP()
```

다음으로, 인터페이스의 구현을 입력 해야 합니다. 대부분의 경우 기존 MFC에 위임할 수는 `IDispatch` 구현 합니다. 예를 들어:

```cpp
STDMETHODIMP_(ULONG) CAutoClickDoc::XDualAClick::AddRef()
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    return pThis->ExternalAddRef();
}

STDMETHODIMP_(ULONG) CAutoClickDoc::XDualAClick::Release()
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    return pThis->ExternalRelease();
}

STDMETHODIMP CAutoClickDoc::XDualAClick::QueryInterface(
    REFIID iid,
    LPVOID* ppvObj)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    return pThis->ExternalQueryInterface(&iid, ppvObj);
}

STDMETHODIMP CAutoClickDoc::XDualAClick::GetTypeInfoCount(
    UINT FAR* pctinfo)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);
    ASSERT(lpDispatch != NULL);
    return lpDispatch->GetTypeInfoCount(pctinfo);
}

STDMETHODIMP CAutoClickDoc::XDualAClick::GetTypeInfo(
    UINT itinfo,
    LCID lcid,
    ITypeInfo FAR* FAR* pptinfo)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);
    ASSERT(lpDispatch != NULL);

    return lpDispatch->GetTypeInfo(itinfo, lcid, pptinfo);
}

STDMETHODIMP CAutoClickDoc::XDualAClick::GetIDsOfNames(
    REFIID riid,
    OLECHAR FAR* FAR* rgszNames,
    UINT cNames,
    LCID lcid,
    DISPID FAR* rgdispid)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);
    ASSERT(lpDispatch != NULL);

    return lpDispatch->GetIDsOfNames(riid, rgszNames, cNames, lcid, rgdispid);
}

STDMETHODIMP CAutoClickDoc::XDualAClick::Invoke(
    DISPID dispidMember,
    REFIID riid,
    LCID lcid,
    WORD wFlags,
    DISPPARAMS FAR* pdispparams,
    VARIANT FAR* pvarResult,
    EXCEPINFO FAR* pexcepinfo,
    UINT FAR* puArgErr)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);
    ASSERT(lpDispatch != NULL);

    return lpDispatch->Invoke(dispidMember, riid, lcid,
        wFlags, pdispparams, pvarResult, pexcepinfo, puArgErr);
}
```

개체의 메서드 및 속성 접근자 함수를 구현을 입력 해야 합니다. 메서드 및 속성 함수는 클래스 마법사를 사용 하 여 생성 하는 방법에 다시 일반적으로 위임할 수 있습니다. 그러나 변수를 직접 액세스 속성을 설정 하는 경우 코드 값을 변수에 get/put를 작성 해야 합니다. 예를 들어:

```cpp
STDMETHODIMP CAutoClickDoc::XDualAClick::put_text(BSTR newText)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    // MFC automatically converts from Unicode BSTR to
    // Ansi CString, if necessary...
    pThis->m_str = newText;
    return NOERROR;
}

STDMETHODIMP CAutoClickDoc::XDualAClick::get_text(BSTR* retval)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    // MFC automatically converts from Ansi CString to
    // Unicode BSTR, if necessary...
    pThis->m_str.SetSysString(retval);
    return NOERROR;
}
```

## <a name="passing-dual-interface-pointers"></a>이중 인터페이스 포인터를 전달합니다.

이중 인터페이스 포인터에 전달 되지를 호출 해야 하는 경우에 특히 간단 `CCmdTarget::FromIDispatch`합니다. `FromIDispatch` MFC의에 대해서만 작동 `IDispatch` 포인터입니다. 이 해결 하는 한 가지 방법은 원본에 대 한 쿼리를 `IDispatch` 포인터 MFC에 의해 집합과 해당 포인터를 필요로 하는 함수에 전달 합니다. 예를 들어:

```
STDMETHODIMP CAutoClickDoc::XDualAClick::put_Position(
    IDualAutoClickPoint FAR* newPosition)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDisp = NULL;
    newPosition->QueryInterface(IID_IDispatch, (LPVOID*)&lpDisp);
    pThis->SetPosition(lpDisp);
    lpDisp->Release();
    return NOERROR;
}
```

이중 인터페이스 메서드를 통해 다시 포인터를 전달 하기 전에 MFC에서 변환 해야 할 수 있습니다 `IDispatch` 이중 인터페이스 포인터에 대 한 포인터입니다. 예:

```
STDMETHODIMP CAutoClickDoc::XDualAClick::get_Position(
    IDualAutoClickPoint FAR* FAR* retval)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDisp;
    lpDisp = pThis->GetPosition();
    lpDisp->QueryInterface(IID_IDualAutoClickPoint, (LPVOID*)retval);
    return NOERROR;
}
```

## <a name="registering-the-applications-type-library"></a>응용 프로그램의 형식 라이브러리를 등록 하는 중

응용 프로그램 마법사는 시스템에는 OLE 자동화 서버 응용 프로그램의 형식 라이브러리를 등록 하는 코드를 생성 하지 않습니다. 형식 라이브러리를 등록 하는 다른 방법의 있을 때는 응용 프로그램을 업데이트 OLE 형식 정보, 즉, 응용 프로그램은 독립 실행형 실행 될 때마다 때 형식 라이브러리를 등록 하는 것입니다.

등록 하는 응용 프로그램이 실행 될 때마다 응용 프로그램의 형식 라이브러리 독립 실행형:

- AFXCTL 포함 됩니다. 표준 프로그램에 H STDAFX 헤더 파일에 포함 되어 있습니다. H의 정의 액세스 하는 `AfxOleRegisterTypeLib` 함수입니다.

- 응용 프로그램에서 `InitInstance` 함수를 호출을 찾습니다 `COleObjectFactory::UpdateRegistryAll`합니다. 이 호출 다음에 대 한 호출을 추가 `AfxOleRegisterTypeLib`을 지정 하는 **LIBID** 에 형식 라이브러리로 형식 라이브러리의 이름과 함께 해당:

    ```cpp
    // When a server application is launched stand-alone, it is a good idea
    // to update the system registry in case it has been damaged.
    m_server.UpdateRegistry(OAT_DISPATCH_OBJECT);

    COleObjectFactory::UpdateRegistryAll();

    // DUAL_SUPPORT_START
        // Make sure the type library is registered or dual interface won't work.
        AfxOleRegisterTypeLib(AfxGetInstanceHandle(),
            LIBID_ACDual,
            _T("AutoClik.TLB"));
    // DUAL_SUPPORT_END
    ```

## <a name="modifying-project-build-settings-to-accommodate-type-library-changes"></a>형식 라이브러리 변경 내용에 맞게 프로젝트 빌드 설정 수정

프로젝트의 빌드 설정을 수정 하려면 있도록 포함 된 헤더 파일 **UUID** 형식 라이브러리 다시 빌드될 때마다 정의 MkTypLib 하 여 생성 됩니다.

1. 에 **빌드** 메뉴를 클릭 **설정을**, 한 다음 각 구성에 대 한 파일 목록에서 ODL 파일을 선택 합니다.

2. 클릭는 **OLE 형식** 탭에 파일 이름을 지정 하 고는 **출력 헤더** 파일 이름 필드입니다. MkTypLib에 있던 기존 파일을 덮어쓰므로 프로젝트를 이미 사용 되지 않는 파일 이름을 사용 합니다. 클릭 **확인** 를 닫으려면는 **빌드 설정** 대화 상자.

추가 하는 **UUID** MkTypLib에서 생성 된 헤더 파일에서 정의 프로젝트에:

1. 포함 하 여 생성 된 헤더 파일에서 표준 헤더 파일, STDAFX를 포함 합니다. 8.

2. INITIIDS 새 파일을 만듭니다. CPP, 프로젝트에 추가 합니다. 이 파일에서 OLE2 포함 한 후 MkTypLib에서 생성 된 헤더 파일을 포함 합니다. H와 INITGUID 합니다. H:

    ```cpp
    // initIIDs.c: defines IIDs for dual interfaces
    // This must not be built with precompiled header.
    #include <ole2.h>
    #include <initguid.h>
    #include "acdual.h"
    ```

3. 에 **빌드** 메뉴에서 클릭 **설정을**, 한 다음 INITIIDS를 선택 합니다. 각 구성에 대 한 파일 목록에서 CPP 합니다.

4. 클릭는 **c + +** 탭에서 범주를 클릭 **미리 컴파일된 헤더**, 선택는 **미리 컴파일된 헤더를 사용 하지 않는** 라디오 단추입니다. 확인을 눌러 닫습니다는 **빌드 설정** 대화 상자.

## <a name="specifying-the-correct-object-class-name-in-the-type-library"></a>형식 라이브러리의 올바른 개체 클래스 이름 지정

와 함께 제공 되지 Visual c + + 올바르게 마법사 구현 클래스 이름을 사용 하 여 OLE 생성 가능한 클래스에 대 한 서버의 ODL 파일에서 coclass를 지정할 수 있습니다. 이 작동 하는 동안 구현 클래스 이름이 사용자가 사용 하 여 개체의 클래스 이름이 되지 않았을 수입니다. 올바른 이름을 지정 하려면 각 coclass 문에 ODL 파일을 열고 찾은 구현 클래스 이름이 올바른 외부 이름으로 대체 합니다.

Coclass 문을 변경 되 면 변수 이름을 유의 **CLSID**의MkTypLib에서 생성 된 헤더 파일에 따라 변경 됩니다. 새 변수 이름을 사용 하도록 코드를 업데이트 해야 합니다.

## <a name="handling-exceptions-and-the-automation-error-interfaces"></a>예외 처리 및 자동화 오류 인터페이스

자동화 개체의 메서드 및 속성 접근자 함수에 예외를 throw 될 수 있습니다. 이중 인터페이스 구현에서 처리 하 고 OLE 자동화 오류 처리 인터페이스를 통해 컨트롤러에 다시 예외에 대 한 정보를 전달 해야, `IErrorInfo`합니다. 이 인터페이스를 모두 처리 한 상황에 맞는 자세한 오류 정보에 대 한 제공 `IDispatch` 및 VTBL 인터페이스입니다. 오류 처리기를 사용할 수, 구현 해야 하는 `ISupportErrorInfo` 인터페이스입니다.

오류 처리 메커니즘을 설명 하기 위해 표준 디스패치 지원을 구현 하기 위해 사용 되는 클래스 마법사에서 생성 된 함수가 예외를 throw를 가정 합니다. MFC 구현을 `IDispatch::Invoke` 일반적으로 이러한 예외를 catch 하 고를 통해 반환 되는 EXCEPTINFO 구조도 변환 하는 `Invoke` 호출 합니다. 그러나, VTBL 인터페이스를 사용 하는 경우는 예외를 직접 검색 하는 일을 담당 됩니다. 이중 인터페이스 메서드를 보호 하는 예를 들어 다음

```cpp
STDMETHODIMP CAutoClickDoc::XDualAClick::put_text(BSTR newText)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    TRY_DUAL(IID_IDualAClick)
    {
        // MFC automatically converts from Unicode BSTR to
        // Ansi CString, if necessary...
        pThis->m_str = newText;
        return NOERROR;
    }
    CATCH_ALL_DUAL
}
```

`CATCH_ALL_DUAL` 처리 예외가 발생할 경우 정확한 오류 코드를 반환 합니다. `CATCH_ALL_DUAL` MFC 예외를 사용 하 여 OLE 자동화 오류 처리 정보로 변환 된 `ICreateErrorInfo` 인터페이스입니다. (예 `CATCH_ALL_DUAL` 매크로 MFCDUAL 파일입니다. 에 H는 [ACDUAL](../visual-cpp-samples.md) 샘플. 예외를 처리 하려면 호출 함수 `DualHandleException`, MFCDUAL 파일에 있습니다. CPP입니다.) `CATCH_ALL_DUAL` 형식 발생 한 예외에 따라 반환할 오류 코드를 결정 합니다.

- [COleDispatchException](../mfc/reference/coledispatchexception-class.md) 이 경우 `HRESULT` 다음 코드를 사용 하 여 생성 됩니다.

    ```cpp
    hr = MAKE_HRESULT(SEVERITY_ERROR, FACILITY_ITF, (e->m_wCode + 0x200));
    ```

     그렇기 때문에 프로그램 `HRESULT` 예외를 발생 하는 인터페이스에 특정 합니다. 오류 코드는 시스템에서 정의 된 모든 충돌을 피하기 위해 0x200 오프셋 `HRESULT`표준 OLE 인터페이스에 대 한 합니다.

- [CMemoryException](../mfc/reference/cmemoryexception-class.md) 이 경우 `E_OUTOFMEMORY` 반환 됩니다.

- 이 경우 다른 예외- `E_UNEXPECTED` 반환 됩니다.

OLE 자동화 오류 처리기를 사용, 구현 해야 하는 `ISupportErrorInfo` 인터페이스입니다.

먼저 코드 표시를 지원 하도록 자동화 클래스 정의를 추가 `ISupportErrorInfo`합니다.

둘째, 연결할 자동화 클래스의 인터페이스 맵을에 코드를 추가 `ISupportErrorInfo` mfc의 구현 클래스 `QueryInterface` 메커니즘입니다. `INTERFACE_PART` 문이 대해 정의 된 클래스와 일치 `ISupportErrorInfo`합니다.

마지막으로 지원 하기 위해 정의 된 클래스를 구현 `ISupportErrorInfo`합니다.

(의 [ACDUAL](../visual-cpp-samples.md) 샘플에 다음 세 가지 단계를 수행 하려면 세 가지 매크로 `DECLARE_DUAL_ERRORINFO`, `DUAL_ERRORINFO_PART`, 및 `IMPLEMENT_DUAL_ERRORINFO`MFCDUAL에 포함 된 모든 합니다. 8.)

다음 예제에서는 지원 하기 위해 정의 하는 클래스를 구현 `ISupportErrorInfo`합니다. `CAutoClickDoc` 자동화 클래스의 이름 및 `IID_IDualAClick` 는 **IID** OLE 자동화 오류 개체를 통해 보고 된 오류 소스 인터페이스에 대 한:

```cpp
STDMETHODIMP_(ULONG) CAutoClickDoc::XSupportErrorInfo::AddRef()
{
    METHOD_PROLOGUE(CAutoClickDoc, SupportErrorInfo)
    return pThis->ExternalAddRef();
}

STDMETHODIMP_(ULONG) CAutoClickDoc::XSupportErrorInfo::Release()
{
    METHOD_PROLOGUE(CAutoClickDoc, SupportErrorInfo)
    return pThis->ExternalRelease();
}

STDMETHODIMP CAutoClickDoc::XSupportErrorInfo::QueryInterface(
    REFIID iid,
    LPVOID* ppvObj)
{
    METHOD_PROLOGUE(CAutoClickDoc, SupportErrorInfo)
    return pThis->ExternalQueryInterface(&iid, ppvObj);
}

STDMETHODIMP CAutoClickDoc::XSupportErrorInfo::InterfaceSupportsErrorInfo(
    REFIID iid)
{
    METHOD_PROLOGUE(CAutoClickDoc, SupportErrorInfo)
    return (iid == IID_IDualAClick) S_OK : S_FALSE;
}
```

## <a name="see-also"></a>참고자료

[번호별 기술 참고 사항](../mfc/technical-notes-by-number.md)  
[범주별 기술 참고 사항](../mfc/technical-notes-by-category.md)  

---
title: 속성 추가 마법사, 이름 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.prop.overview
dev_langs:
- C++
ms.assetid: 0453b7ea-89cb-41a1-80a2-d45f61589c0a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 17c3fd5cfc86f76fcdc1c301bd92bb1fdfac3b9c
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2018
ms.locfileid: "33339568"
---
# <a name="names-add-property-wizard"></a>속성 추가 마법사, 이름
이 마법사를 사용하여 인터페이스에 속성을 추가합니다.  
  
 **속성 형식**  
 추가할 속성의 형식을 설정합니다. MFC dispinterface의 경우, 형식을 직접 제공하거나 미리 정의된 목록에서 선택합니다. 속성의 스톡 구현을 제공하는 경우 **속성 형식**이 스톡 형식으로 설정되고 변경할 수 없습니다.  
  
 **속성 이름**  
 속성 이름을 설정합니다. ActiveX 컨트롤과 연결된 MFC dispinterface의 경우, 사용자 고유의 이름을 제공하거나 미리 정의된 목록에서 스톡 속성 이름을 선택할 수 있습니다. 고유한 속성 이름을 제공하는 경우 **스톡** 구현 형식을 사용할 수 없습니다. 목록의 속성에 대한 설명은 [스톡 속성](../ide/stock-properties.md)을 참조하세요.  
  
|인터페이스 유형|설명|  
|--------------------|-----------------|  
|ATL 이중 인터페이스, 사용자 지정 인터페이스 및 로컬 사용자 지정 인터페이스|속성 이름을 제공합니다.|  
|MFC dispinterface, MFC ActiveX 컨트롤 dispinterface|속성 이름을 입력하거나 목록에서 스톡 속성을 선택합니다. 목록에서 속성을 선택하면 **속성 형식** 상자에 적절한 값이 표시됩니다. **구현 형식**에서 선택한 항목에 따라 이 형식을 변경할 수 있습니다.|  
  
 **반환 형식**  
 ATL 인터페이스 전용. 속성의 반환 형식을 설정합니다. 이중 인터페이스의 경우, `HRESULT`는 항상 반환 형식이며 이 상자는 사용할 수 없습니다. 사용자 지정 인터페이스의 경우, 목록에서 반환 형식을 선택할 수 있습니다. `HRESULT`은 오류를 반환하는 표준 방식을 제공하기 때문에 여전히 권장됩니다.  
  
 **변수 이름**  
 MFC dispinterface 전용. **구현 형식**에서 **멤버 변수**를 지정한 경우에만 사용할 수 있습니다. 속성이 연결된 멤버 변수의 이름을 설정합니다. 기본적으로 변수 이름은 m_*PropertyName*으로 설정됩니다. 이 이름을 편집할 수 있습니다.  
  
 **알림 함수**  
 MFC dispinterface 전용. **구현 형식**에서 **멤버 변수**를 지정한 경우에만 사용할 수 있습니다. 속성이 변경될 경우 호출되는 알림 함수의 이름을 설정합니다. 기본적으로 알림 함수의 이름은 On*PropertyName*Changed로 설정됩니다. 이 이름을 편집할 수 있습니다.  
  
 **Get 함수**  
 MFC dispinterface용. **구현 형식**에서 **Get/Set 메서드**를 지정한 경우에만 사용할 수 있습니다. 속성을 가져올 함수의 이름을 설정합니다. 기본적으로 Get 함수의 이름은 Get*PropertyName*으로 설정됩니다. 이 이름을 편집할 수 있습니다. 이 이름을 삭제하면 [GetNotSupported](../mfc/reference/colecontrol-class.md#getnotsupported) 함수가 인터페이스 디스패치 맵에 삽입됩니다. Get*PropertyName* 함수는 속성을 읽을 수 있는 것으로 지정합니다.  
  
 **Set 함수**  
 MFC dispinterface 전용. **구현 형식**에서 **Get/Set 메서드**를 지정한 경우에만 사용할 수 있습니다. 속성을 설정할 함수의 이름을 설정합니다. 기본적으로 Set 함수의 이름은 Set*PropertyName*으로 설정됩니다. 이 이름을 편집할 수 있습니다. 이 이름을 삭제하면 [SetNotSupported](../mfc/reference/colecontrol-class.md#setnotsupported) 함수가 인터페이스 디스패치 맵에 삽입됩니다. Set*PropertyName* 함수는 속성이 쓰기 가능하도록 지정합니다.  
  
 **구현 형식**  
 MFC dispinterface 전용. 추가하는 속성을 구현하는 방법을 지정합니다.  
  
|구현 형식|설명|  
|-------------------------|-----------------|  
|**스톡**|**속성 이름**에서 선택한 속성의 스톡 구현을 지정합니다. 기본값입니다. 자세한 내용은 [스톡 속성](../ide/stock-properties.md)을 참조하세요.<br /><br /> **스톡**을 지정한 후에는 **속성 형식**, **매개 변수 형식** 및 **매개 변수 이름**이 흐리게 표시됩니다.|  
|**멤버 변수**|속성이 멤버 변수로 추가되도록 지정합니다. 사용자 지정 속성 또는 대부분의 스톡 속성을 멤버 변수로 추가할 수 있습니다. **캡션**, **hWnd** 및 **텍스트** 속성에는 **멤버 변수**를 지정할 수 없습니다.<br /><br /> **변수 이름** 및 **알림 함수**에 기본 이름을 제공합니다. 이 이름을 편집할 수 있습니다.|  
|**Get/Set 메서드**|기본적으로 속성은 Get*PropertyName* 및 Set*PropertyName* 함수로 추가되도록 지정합니다. 이러한 이름은 **Get 함수** 및 **Set 함수** 아래에 나타납니다.<br /><br /> Get 함수의 값을 전달하는 기본 **속성 형식**을 변경할 수 있습니다. **Get** 및 `Set` 함수에 대한 매개 변수를 지정할 수 있습니다.|  
  
 **Get 함수**  
 ATL 인터페이스용. 속성을 읽을 수 있도록 설정합니다. 즉, 개체에서 이 속성을 검색하기 위해 **Get** 메서드를 만듭니다. **Get**, `Put` 또는 둘 모두를 선택해야 합니다.  
  
 **Put 함수**  
 ATL 인터페이스 전용. 속성을 쓰기 가능으로 설정합니다. 즉, 개체의 이 속성을 설정하거나 "배치"하기 위해 `Put` 메서드를 만듭니다. **Get**, `Put` 또는 둘 모두를 선택해야 합니다. 이 옵션을 선택하면 다음 두 가지 메서드 구현 방법 중에서 선택할 수 있습니다.  
  
|옵션|설명|  
|------------|-----------------|  
|**PropPut**|[PropPut](../windows/propput.md) 함수는 개체의 복사본을 반환합니다. 속성을 쓰기 가능하도록 만드는 기본적이고 가장 일반적인 방법입니다.|  
|**PropPutRef**|[PropPutRef](../windows/propputref.md) 함수는 개체 자체의 복사본을 반환하지 않고 개체에 대한 참조를 반환합니다. 큰 구조체 또는 배열과 같은 초기화 오버헤드가 있을 수 있는 개체에는 이 옵션을 사용하는 것이 좋습니다.|  
  
 **매개 변수 특성**  
 ATL 인터페이스 전용. **매개 변수 이름**으로 지정한 매개 변수가 **in**, **out**, 둘 모두 또는 없음인지 여부를 설정합니다.  
  
|옵션|설명|  
|------------|-----------------|  
|**in**|호출하는 프로시저에서 호출된 프로시저로 매개 변수가 전달됩니다.|  
|**out**|포인터 매개 변수는 호출된 프로시저에서 호출하는 프로시저로(서버에서 클라이언트로) 반환됩니다.|  
  
 **매개 변수 형식**  
 매개 변수의 데이터 형식을 설정합니다. 목록에서 형식을 선택합니다.  
  
 **매개 변수 이름**  
 속성에 매개 변수가 있는 경우, 속성에 추가할 매개 변수의 이름을 설정합니다. **추가**를 클릭하면 매개 변수 이름이 **매개 변수 목록**에 나타납니다.  
  
 **매개 변수 목록**  
 속성에 추가할 특성 목록을 표시합니다. 목록의 각 항목은 매개 변수 이름, 매개 변수 형식 및 특성으로 구성됩니다. **추가** 및 **제거**를 사용하여 목록을 업데이트합니다.  
  
 **추가**  
 **매개 변수 이름** 및 **매개 변수 형식**에서 지정한 매개 변수를 **매개 변수 목록**에 추가합니다. 매개 변수를 목록에 추가하려면 **추가**를 클릭해야 합니다.  
  
 **제거**  
 **매개 변수 목록**에서 선택한 매개 변수를 제거합니다.  
  
 **기본 속성**  
 MFC dispinterface 전용. 이 속성을 인터페이스의 기본값으로 설정합니다. 기본 속성을 지정하면 인터페이스에는 하나의 기본 속성만 있을 수 있으며, 인터페이스에 추가하는 다른 모든 속성에 이 상자를 사용할 수 없습니다.  
  
## <a name="see-also"></a>참고 항목  
 [속성 추가](../ide/adding-a-property-visual-cpp.md)   
 [IDL 특성, 속성 추가 마법사](../ide/idl-attributes-add-property-wizard.md)   
 [인터페이스 구현](../ide/implementing-an-interface-visual-cpp.md)
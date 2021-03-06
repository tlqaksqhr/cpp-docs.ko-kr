---
title: 속성 (C + + /cli CX) | Microsoft Docs
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 64c7bc56-3191-4cd5-bdf4-476d07d285d5
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6393b5e5849ab2198fa8d084c2c1d15838c69bdd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33089561"
---
# <a name="properties-ccx"></a>속성(C++/CX)
공용 데이터를 속성으로 노출 하는 Windows 런타임 형식입니다. 클라이언트 코드는 공용 데이터 멤버처럼 속성에 액세스합니다. 내부적으로 속성은 get 접근자 메서드, set 접근자 메서드 또는 둘 다 포함된 블록으로 구현됩니다. 접근자 메서드를 사용하면 값을 검색하기 전이나 후에 추가 작업을 수행할 수 있습니다. 예를 들어 이벤트를 발생시키거나 유효성 검사를 수행할 수 있습니다.  
  
### <a name="remarks"></a>설명  
 속성 값은 속성과 형식이 동일한 *백업 저장소*라고 하는 전용 변수에 포함됩니다. 속성에는 백업 저장소에 값을 할당하는 set 접근자와 백업 저장소의 값을 검색하는 get 접근자가 모두 포함될 수 있습니다. 속성은 get 접근자만 제공하는 경우 읽기 전용이고, set 접근자만 제공하는 경우 쓰기 전용이며 두 접근자를 모두 제공하는 경우 읽기/쓰기(수정 가능) 속성입니다.  
  
 *trivial* 속성은 컴파일러가 접근자 및 백업 저장소를 자동으로 구현하는 읽기/쓰기 속성입니다. 컴파일러의 구현에 액세스할 필요가 없습니다. 그러나 사용자 지정 속성을 선언하고 접근자 및 백업 저장소를 명시적으로 선언할 수 있습니다. 접근자 내에서 set 접근자에 대한 입력 유효성 검사, 속성 값 계산, 데이터베이스 액세스 또는 속성이 변경될 때 이벤트 발생과 같이 필요한 모든 논리를 수행할 수 있습니다.  
  
 C++/CX ref 클래스가 인스턴스화되면 생성자가 호출되기 전에 메모리가 0으로 초기화되므로 선언 시점에서 모든 속성에 기본값 0 또는 nullptr이 할당됩니다.  
  
### <a name="examples"></a>예제  
 다음 코드 예제에서는 속성을 선언하고 액세스하는 방법을 보여 줍니다. 첫 번째 속성 `Name`은 *trivial* 속성이라고도 합니다. 컴파일러가 자동으로 `set` accessor, `get` 접근자와 백업 저장소를 생성하기 때문입니다.  
  
 두 번째 속성 `Doctor`는 *접근자만 명시적으로 선언하는* 속성 블록 `get` 을 지정하므로 읽기 전용 속성입니다. 속성 블록이 선언되었으므로 백업 저장소, 즉 전용 String^ 변수 `doctor_`를 명시적으로 선언해야 합니다. 일반적으로 읽기 전용 속성은 백업 저장소의 값만 반환합니다. 클래스 자체만 백업 저장소의 값을 대개 생성자에 설정할 수 있습니다.  
  
 세 번째 속성 `Quantity`는 `set` 접근자와 `get` 접근자를 모두 선언하는 속성 블록을 선언하므로 읽기-쓰기 속성입니다.  
  
 `set` 접근자는 할당된 값에 대해 사용자 정의 유효성 테스트를 수행합니다. C#과 달리 여기서 *value* 라는 이름은 키워드가 아니라 `set` 접근자의 매개 변수에 대한 식별자입니다. *value* 가 0보다 크지 않으면 Platform::InvalidArgumentException이 throw됩니다. 그렇지 않으면 백업 저장소 `quantity_`가 할당된 값으로 업데이트됩니다.  
  
 멤버 목록에서는 속성을 초기화할 수 없습니다. 물론 멤버 목록에서 백업 저장소 변수를 초기화할 수 있습니다.  
  
 [!code-cpp[cx_properties#01](../cppcx/codesnippet/CPP/cx_properties/class1.h#01)]  
  
## <a name="see-also"></a>참고 항목  
 [형식 시스템](../cppcx/type-system-c-cx.md)   
 [Visual c + + 언어 참조](../cppcx/visual-c-language-reference-c-cx.md)   
 [네임 스페이스 참조](../cppcx/namespaces-reference-c-cx.md)
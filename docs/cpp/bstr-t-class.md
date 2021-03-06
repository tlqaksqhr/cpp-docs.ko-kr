---
title: _bstr_t 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t
dev_langs:
- C++
helpviewer_keywords:
- BSTR object
- _bstr_t class
- BSTR object [C++], COM encapsulation
ms.assetid: 58841fef-fe21-4a84-aab9-780262b5201f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f7cb3d05997cfe3d803f522962ed9e7382269bd3
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404927"
---
# <a name="bstrt-class"></a>_bstr_t 클래스
**Microsoft 전용**  
  
 A `_bstr_t` 개체를 캡슐화 합니다 [BSTR 데이터 형식](http://msdn.microsoft.com/1b2d7d2c-47af-4389-a6b6-b01b7e915228)합니다. 클래스가 관리 리소스 할당 및 할당 해제 함수 호출을 통해 `SysAllocString` 하 고 `SysFreeString` 및 기타 `BSTR` 적절 한 경우 Api. 합니다 **_bstr_t** 클래스는 과도 한 오버 헤드를 방지 하기 위해 참조 가산을 사용 합니다.  
  
### <a name="construction"></a>생성  
  
|||  
|-|-|  
|[_bstr_t](../cpp/bstr-t-bstr-t.md)|`_bstr_t` 개체를 생성합니다.|  
  
### <a name="operations"></a>작업  
  
|||  
|-|-|  
|[할당](../cpp/bstr-t-assign.md)|`BSTR`을 `BSTR`로 래핑된 `_bstr_t`로 복사합니다.|  
|[Attach](../cpp/bstr-t-attach.md)|`_bstr_t` 래퍼를 `BSTR`에 연결합니다.|  
|[copy](../cpp/bstr-t-copy.md)|캡슐화된 `BSTR`의 복사본을 구성합니다.|  
|[Detach](../cpp/bstr-t-detach.md)|`BSTR`로 래핑된 `_bstr_t`을 반환하고 `BSTR`을 `_bstr_t`에서 분리합니다.|  
|[GetAddress](../cpp/bstr-t-getaddress.md)|`BSTR`로 래핑된 `_bstr_t`을 가리킵니다.|  
|[GetBSTR](../cpp/bstr-t-getbstr.md)|`BSTR`에 의해 래핑되는 `_bstr_t`의 시작 부분을 가리킵니다.|  
|[length](../cpp/bstr-t-length.md)|`_bstr_t`에 있는 문자의 수를 반환합니다.|  
  
### <a name="operators"></a>연산자  
  
|||  
|-|-|  
|[operator =](../cpp/bstr-t-operator-equal.md)|기존 `_bstr_t` 개체에 새 값을 할당합니다.|  
|[operator + =](../cpp/bstr-t-operator-add-equal-plus.md)|`_bstr_t` 개체의 끝 부분에 문자를 추가합니다.|  
|[연산자 +](../cpp/bstr-t-operator-add-equal-plus.md)|두 문자열을 연결합니다.|  
|[연산자 !](../cpp/bstr-t-operator-logical-not.md)|확인 캡슐화 된 `BSTR` NULL 문자열입니다.|  
|[operator ==, !=, \<, >, \<=, >=](../cpp/bstr-t-relational-operators.md)|두 `_bstr_t` 개체를 비교합니다.|  
|[연산자 wchar_t * &#124; char\*](../cpp/bstr-t-wchar-t-star-bstr-t-char-star.md)|캡슐화된 유니코드 또는 멀티바이트 `BSTR` 개체에 대한 포인터를 추출합니다.|  
  
**Microsoft 전용 종료**  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** \<comutil.h >  
  
 **Lib:** comsuppw.lib 또는 comsuppwd.lib (참조 [/zc: wchar_t (wchar_t는 네이티브 형식임)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) 자세한)  
  
## <a name="see-also"></a>참고자료  
 [컴파일러 COM 지원 클래스](../cpp/compiler-com-support-classes.md)
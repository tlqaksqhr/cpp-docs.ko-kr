---
title: is_member_object_pointer 클래스 | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_member_object_pointer
dev_langs:
- C++
helpviewer_keywords:
- is_member_object_pointer class
- is_member_object_pointer
ms.assetid: 64f9cdf3-4621-4310-a076-a7bc986926b9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7a045abd8bb6a41e96febf972d21bae80b9b4f7a
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38955418"
---
# <a name="ismemberobjectpointer-class"></a>is_member_object_pointer 클래스

형식이 멤버 개체에 대한 포인터인지 여부를 테스트합니다.

## <a name="syntax"></a>구문

```cpp
template <class Ty>
struct is_member_object_pointer;
```

### <a name="parameters"></a>매개 변수

*Ty* 쿼리할 형식입니다.

## <a name="remarks"></a>설명

형식 조건자의 인스턴스 형태인 경우 true 형식을 *Ty* 멤버 개체에 대 한 포인터 또는 `cv-qualified` 멤버 개체 이거나 그렇지 않으면 false에 대 한 포인터입니다. 사실은 `is_member_object_pointer` 이면 false를 보유 *Ty* 멤버 함수에 대 한 포인터입니다.

## <a name="example"></a>예

```cpp
// std__type_traits__is_member_object_pointer.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

struct functional
    {
    int f();
    };

int main()
    {
    std::cout << "is_member_object_pointer<trivial *> == "
        << std::boolalpha
        << std::is_member_object_pointer<trivial *>::value
        << std::endl;
    std::cout << "is_member_object_pointer<int trivial::*> == "
        << std::boolalpha
        << std::is_member_object_pointer<int trivial::*>::value
        << std::endl;
    std::cout << "is_member_object_pointer<int (functional::*)()> == "
        << std::boolalpha
        << std::is_member_object_pointer<int (functional::*)()>::value
        << std::endl;

    return (0);
    }

```

```Output
is_member_object_pointer<trivial *> == false
is_member_object_pointer<int trivial::*> == true
is_member_object_pointer<int (functional::*)()> == false
```

## <a name="requirements"></a>요구 사항

**헤더:** \<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고자료

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_member_pointer 클래스](../standard-library/is-member-pointer-class.md)<br/>

---
title: integral_constant 클래스, bool_constant 클래스 | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::integral_constant
- XTR1COMMON/std::integral_constant
- type_traits/std::bool_constant
- XTR1COMMON/std::bool_constant
dev_langs:
- C++
helpviewer_keywords:
- std::integral_constant [C++]
- std::bool_constant [C++]
ms.assetid: 11c002c6-4d31-4042-9341-f2543f43e108
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8bff57549307eeaa9245c0bb4083b206471fe726
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38962535"
---
# <a name="integralconstant-class-boolconstant-class"></a>integral_constant 클래스, bool_constant 클래스

형식 및 값에서 정수 계열 상수를 만듭니다.

## <a name="syntax"></a>구문

```cpp
template<class T, T v>
struct integral_constant {
   static constexpr T value = v;
   typedef T value_type;
   typedef integral_constant<T, v> type;
   constexpr operator value_type() const noexcept;
   constexpr value_type operator()() const noexcept;
   };
```

### <a name="parameters"></a>매개 변수

*T* 상수의 형식입니다.

*v* 상수의 값입니다.

## <a name="remarks"></a>설명

정수 계열 형식 *T* 및 해당 형식의 *v* 값으로 특수화된 경우 `integral_constant` 템플릿 클래스는 지정된 값이 있는 해당 정수 계열 형식의 상수를 포함하는 개체를 나타냅니다. `type`이라는 멤버는 생성된 템플릿 특수화 형식에 대한 별칭이고, `value` 멤버는 특수화를 만드는 데 사용되는 *v* 값을 포함합니다.

합니다 `bool_constant` 템플릿 클래스의 명시적 부분 특수화는 `integral_constant` 사용 하는 **bool** 으로 *T* 인수입니다.

## <a name="example"></a>예

```cpp
// std__type_traits__integral_constant.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

int main()
    {
    std::cout << "integral_constant<int, 5> == "
        << std::integral_constant<int, 5>::value << std::endl;
    std::cout << "integral_constant<bool, false> == " << std::boolalpha
        << std::integral_constant<bool, false>::value << std::endl;

    return (0);
    }

```

```Output
integral_constant<int, 5> == 5
integral_constant<bool, false> == false
```

## <a name="requirements"></a>요구 사항

**헤더:** \<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고자료

[<type_traits>](../standard-library/type-traits.md)<br/>
[false_type](../standard-library/type-traits-typedefs.md#false_type)<br/>
[true_type](../standard-library/type-traits-typedefs.md#true_type)<br/>

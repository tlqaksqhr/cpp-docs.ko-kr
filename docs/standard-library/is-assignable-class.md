---
title: is_assignable 클래스 | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_assignable
ms.assetid: 53444287-c8be-4ad2-9487-a85c066a4f84
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d5666aca2d6a855b64af26d38a1ae834fecec5d6
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38958467"
---
# <a name="isassignable-class"></a>is_assignable 클래스

`From` 형식의 값을 `To` 형식에 할당할 수 있는지 여부를 테스트합니다.

## <a name="syntax"></a>구문

```cpp
template <class To, class From>
struct is_assignable;
```

### <a name="parameters"></a>매개 변수

할당을 받는 개체의 형식입니다.

값을 제공 하는 개체의 형식입니다.

## <a name="remarks"></a>설명

평가되지 않은 `declval<To>() = declval<From>()` 식은 올바른 형식이어야 합니다. 둘 다 `From` 하 고 `To` 완전 한 형식 이어야 합니다 **void**, 또는 범위를 알 수 없는 배열입니다.

## <a name="requirements"></a>요구 사항

**헤더:** \<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고자료

[<type_traits>](../standard-library/type-traits.md)<br/>

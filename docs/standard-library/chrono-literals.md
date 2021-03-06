---
title: chrono 리터럴 | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
ms.assetid: 1a9e23b1-256f-4570-8226-5fa7364fb032
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 059974efa00d384f669c88a3e2dafbc3a7bc5746
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38953693"
---
# <a name="chrono-literals"></a>chrono 리터럴

(C++14) \<chrono> 헤더는 12가지 [사용자 정의 리터럴](../cpp/user-defined-literals-cpp.md)을 정의하여 시, 분, 초, 밀리초, 마이크로초 및 나노초를 나타내는 리터럴의 사용을 한층 쉽게 만듭니다. 각 사용자 정의 리터럴에는 정수 계열 및 부동 소수점 오버로드가 있습니다. 리터럴은 std::chrono가 범위에 있을 때 자동으로 범위로 가져오는 literals::chrono_literals 인라인 네임스페이스에서 정의됩니다.

## <a name="syntax"></a>구문

```cpp
inline namespace literals {
    inline namespace chrono_literals {
 // return integral hours
    constexpr chrono::hours operator"" h(unsigned long long Val);

// return floating-point hours
    constexpr chrono::duration<double, ratio<3600>> operator"" h(long double Val);

// return integral minutes
    constexpr chrono::minutes(operator"" min)(unsigned long long Val);

// return floating-point minutes
    constexpr chrono::duration<double, ratio<60>>(operator"" min)(long double Val);

// return integral seconds
    constexpr chrono::seconds operator"" s(unsigned long long Val);

// return floating-point seconds
    constexpr chrono::duration<double> operator"" s(long double Val);

// return integral milliseconds
    constexpr chrono::milliseconds operator"" ms(unsigned long long Val);

// return floating-point milliseconds
    constexpr chrono::duration<double, milli> operator"" ms(long double Val);

// return integral microseconds
    constexpr chrono::microseconds operator"" us(unsigned long long Val);

// return floating-point microseconds
    inline constexpr chrono::duration<double, micro> operator"" us(long double Val);

// return integral nanoseconds
    inline constexpr chrono::nanoseconds operator"" ns(unsigned long long Val);

// return floating-point nanoseconds
    constexpr chrono::duration<double, nano> operator"" ns(long double Val);

}// inline namespace chrono_literals
}// inline namespace literals
```

## <a name="return-value"></a>반환 값

사용 하는 리터럴은 **long long** 인수 값 또는 해당 형식을 반환 합니다. 부동 소수점 인수를 사용하는 리터럴은 [duration](../standard-library/duration-class.md)을 반환합니다.

## <a name="example"></a>예

다음 예에서는 chrono 리터럴을 사용하는 방법을 보여 줍니다.

```cpp
constexpr auto day = 24h;
constexpr auto week = 24h* 7;
constexpr auto my_duration_unit = 108ms;
```

## <a name="requirements"></a>요구 사항

**헤더**: \<chrono>

**네임스페이스**: std::literals::chrono_literals

## <a name="see-also"></a>참고자료

[\<chrono>](../standard-library/chrono.md)<br/>

---
title: mersenne_twister_engine 클래스 | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- random/std::mersenne_twister_engine
dev_langs:
- C++
helpviewer_keywords:
- mersenne_twister_engine class
ms.assetid: 7ee968fa-a1cc-450f-890f-7305de062685
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bb03b35ed792bda7c506fd06d6102dda83c768e6
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38959273"
---
# <a name="mersennetwisterengine-class"></a>mersenne_twister_engine 클래스

메르센 트위스터 알고리즘을 기반으로 정수의 고품질 임의 시퀀스를 생성합니다.

## <a name="syntax"></a>구문

```cpp
template <class UIntType,
    size_t W, size_t N, size_t M, size_t R,
    UIntType A, size_t U, UIntType D, size_t S,
    UIntType B, size_t T, UIntType C, size_t L, UIntType F>
class mersenne_twister_engine;
```

### <a name="parameters"></a>매개 변수

*UIntType* 부호 없는 정수 결과 형식입니다. 가능한 형식은 [\<random>](../standard-library/random.md)를 참조하세요.

*W* **단어 크기**합니다. 상태 시퀀스의 각 단어 크기입니다(비트). **사전 조건**: `2u < W ≤ numeric_limits<UIntType>::digits`

*N* **상태 크기**합니다. 상태 시퀀스의 요소(값) 수입니다.

*M* **시프트 크기**합니다. 각 트위스트 중 건너 뛸 요소의 수입니다. **사전 조건**: `0 < M ≤ N`

*R* **마스크 비트**합니다. **사전 조건**: `R ≤ W`

*A* **XOR 마스크**합니다. **사전 조건**: `A ≤ (1u<<W) - 1u`

*U*, *S*합니다 *T*를 *L* **Tempering shift 매개 변수**합니다. 암호화(조작)할 때 시프트 값으로 사용됩니다. 사전 조건: `U,S,T,L ≤ W`

*D*하십시오 *B*를 *C* **Tempering 비트 마스크 매개 변수**합니다. 암호화(조작)할 때 비트 마스크 값으로 사용됩니다. 사전 조건: `D,B,C ≤ (1u<<W) - 1u`

*F* **초기화 승수**합니다. 시퀀스 초기화를 지원하는 데 사용됩니다. 사전 조건: `F ≤ (1u<<W) - 1u`

## <a name="members"></a>멤버

||||
|-|-|-|
|`mersenne_twister_engine::mersenne_twister_engine`|`mersenne_twister_engine::min`|`mersenne_twister_engine::discard`|
|`mersenne_twister_engine::operator()`|`mersenne_twister_engine::max`|`mersenne_twister_engine::seed`|

`default_seed`는 `5489u`로 정의된 멤버 상수로, `mersenne_twister_engine::seed` 및 단일 값 생성자의 기본 매개 변수 값으로 사용됩니다.

엔진 구성원에 대한 자세한 내용은 [\<random>](../standard-library/random.md)을 참조하세요.

## <a name="remarks"></a>설명

이 템플릿 클래스는 닫힌 간격 [ `0`, `2`<sup>W</sup> - `1`]에 대한 값을 반환하는 난수 엔진을 설명합니다. 여기에는 `W * (N - 1) + R`비트의 큰 정수 값이 들어 있습니다. 추출 *W* 모든 비트를 사용 하는 경우 및이 큰 값에서 한 번에 비트 비틉니다 large value 시프트 후 새에서 추출 하는 비트 집합을 갖도록 비트를 혼합 하 여 합니다. 엔진의 상태는 마지막 `N` `W`-경우에 사용 되는 값을 비트 `operator()` 이상 호출한 *N* 번이 고, 그렇지는 `M` `W`-사용 된 값과 마지막 `N - M` 시드 값입니다.

시프트 값으로 정의 고 일반화 된 피드백 시프트 레지스터를 사용 하 여 보유 하는 큰 값을 트위스트 *N* 하 고 *M*, 트위스트 값 *R*, 및 조건부 XOR 마스크 *는*합니다. 또한 원시 시프트 레지스터의 비트를 암호화 (조작) 값으로 정의 하는 비트 암호화 매트릭스에 따라 *U*를 *D*하십시오 *S*, *B* , *T*합니다 *C*, 및 *L*합니다.

템플릿 인수 `UIntType`은 최대 `2`<sup>W</sup> - `1`까지 값을 보유할 수 있도록 충분히 커야 합니다. 다른 템플릿 인수의 값은 다음 요구 사항을 충족해야 합니다. `2u < W, 0 < M, M ≤ N, R ≤ W, U ≤ W, S ≤ W, T ≤ W, L ≤ W, W ≤ numeric_limits<UIntType>::digits, A ≤ (1u<<W) - 1u, B ≤ (1u<<W) - 1u, C ≤ (1u<<W) - 1u, D ≤ (1u<<W) - 1u, and F ≤ (1u<<W) - 1u`.

이 엔진에서 직접 생성기를 생성할 수 있더라도 다음의 미리 정의된 형식 정의 중 하나를 사용하는 것이 좋습니다.

`mt19937`: 32비트 메르센 트위스터 엔진입니다(Matsumoto 및 Nishimura, 1998).

```cpp
typedef mersenne_twister_engine<unsigned int, 32, 624, 397,
    31, 0x9908b0df,
    11, 0xffffffff,
    7, 0x9d2c5680,
    15, 0xefc60000,
    18, 1812433253> mt19937;
```

`mt19937_64`: 64비트 메르센 트위스터 엔진입니다(Matsumoto 및 Nishimura, 2000).

```cpp
typedef mersenne_twister_engine<unsigned long long, 64, 312, 156,
    31, 0xb5026f5aa96619e9ULL,
    29, 0x5555555555555555ULL,
    17, 0x71d67fffeda60000ULL,
    37, 0xfff7eee000000000ULL,
    43, 6364136223846793005ULL> mt19937_64;
```

메르센 트위스터 알고리즘에 대한 자세한 내용은 Wikipedia 문서 [Mersenne twister](http://go.microsoft.com/fwlink/p/?linkid=402356)(메르센 트위스터)를 참조하세요.

## <a name="example"></a>예

코드 예제는 [\<random>](../standard-library/random.md)을 참조하세요.

## <a name="requirements"></a>요구 사항

**헤더:** \<random>

**네임스페이스:** std

## <a name="see-also"></a>참고자료

[\<random>](../standard-library/random.md)<br/>

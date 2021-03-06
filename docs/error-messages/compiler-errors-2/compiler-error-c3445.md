---
title: 컴파일러 오류 C3445 | Microsoft Docs
ms.custom: ''
ms.date: 04/10/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3445
dev_langs:
- C++
helpviewer_keywords:
- C3445
ms.assetid: 0d272bfc-136b-4025-a9ba-5e4eea5f8215
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c37f04b907183b883772fd144ae0179683f088f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33256768"
---
# <a name="compiler-error-c3445"></a>컴파일러 오류 C3445

> 초기화-복사-목록 '*형식*' 명시적 생성자를 사용할 수 없습니다

ISO C + + 17 표준에 따라 컴파일러는 오버 로드 확인에 복사-목록-초기화에 대 한 명시적 생성자를 고려해 야 하는 데 필요한 하지만 오버 로드 하는 실제로 선택 하는 경우 오류가 발생 합니다.

Visual Studio 2017 년부터 컴파일러는 Visual Studio 2015에서 찾을 수 없는 이니셜라이저 목록을 사용 하 여 개체 만들기와 관련 된 오류를 찾습니다. 이러한 오류 중단을 일으키거나 런타임에 정의 되지 않은 동작이 발생할 수 있습니다.

## <a name="example"></a>예제

다음 샘플에서는 C3445 합니다.

```cpp
// C3445.cpp
struct A
{
    explicit A(int) {}
    A(double) {}
};

int main()
{
    A a1 = { 1 };     // error C3445: copy-list-initialization of
                      //     'A' cannot use an explicit constructor
}
```

오류를 해결 하려면 직접 초기화를 대신 사용:

```cpp
// C3445b.cpp
struct A
{
    explicit A(int) {}
    A(double) {}
};

int main()
{
    A a1{ 1 };
}
```

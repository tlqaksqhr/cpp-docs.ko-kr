---
title: '&lt;filesystem&gt; 연산자 | Microsoft 문서'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- FILESYSTEM/std::experimental::filesystem::operator==
- FILESYSTEM/std::experimental::filesystem::operator!=
- FILESYSTEM/std::experimental::filesystem::operator<
- FILESYSTEM/std::experimental::filesystem::operator<=
- FILESYSTEM/std::experimental::filesystem::operator>
- FILESYSTEM/std::experimental::filesystem::operator>=
- FILESYSTEM/std::experimental::filesystem::operator/
- FILESYSTEM/std::experimental::filesystem::operator<<
- FILESYSTEM/std::experimental::filesystem::operator>>
dev_langs:
- C++
ms.assetid: 102c4833-aa3b-41a8-8998-f5003c546bfd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6e93cbd4298a0f2094c2c5950220610a17642512
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38965580"
---
# <a name="ltfilesystemgt-operators"></a>&lt;filesystem&gt; 연산자

연산자는 문자열로 두 경로의 어휘 비교를 수행합니다. 사용 된 `equivalent` 동일한 파일 또는 디스크의 디렉터리에 두 경로 (예: 상대 경로 및 절대 경로)를 참조 하는지 여부를 결정 하는 함수입니다.

자세한 내용은 [파일 시스템 탐색(C++)](../standard-library/file-system-navigation.md)을 참조하세요.

## <a name="operator"></a>operator==

```cpp
bool operator==(const path& left, const path& right) noexcept;
```

함수는 left.native() == right.native()를 반환합니다.

## <a name="operator"></a>operator!=

```cpp
bool operator!=(const path& left, const path& right) noexcept;
```

함수는 !(left == right)를 반환합니다.

## <a name="operator"></a>operator<

```cpp
bool operator<(const path& left, const path& right) noexcept;
```

함수는 left.native() < right.native()를 반환합니다.

## <a name="operator"></a>operator<=

```cpp
bool operator<=(const path& left, const path& right) noexcept;
```

함수는 !(right \< left)를 반환합니다.

## <a name="operator"></a>operator>

```cpp
bool operator>(const path& left, const path& right) noexcept;
```

함수는 right \< left를 반환합니다.

## <a name="operator"></a>operator>=

```cpp
bool operator>=(const path& left, const path& right) noexcept;
```

함수는 !(left < right)를 반환합니다.

## <a name="operator"></a>operator/

```cpp
path operator/(const path& left, const path& right);
```

함수는 다음을 실행합니다.

```cpp
basic_string<Elem, Traits> str;
path ans = left;
return (ans /= right);
```

## <a name="operator"></a>operator<<

```cpp
template <class Elem, class Traits>
basic_ostream<Elem, Traits>& operator<<(basic_ostream<Elem, Traits>& os, const path& pval);
```

함수는 os << pval.string\<Elem, Traits>()를 반환합니다.

## <a name="operator"></a>operator>>

```cpp
template <class Elem, class Traits>
basic_istream<Elem, Traits>& operator<<(basic_istream<Elem, Traits>& is, const path& pval);
```

함수는 다음을 실행합니다.

```cpp
basic_string<Elem, Traits> str;
is>> str;
pval = str;
return (is);
```

## <a name="see-also"></a>참고자료

[path 클래스 (c + + 표준 라이브러리)](../standard-library/path-class.md)<br/>
[파일 시스템 탐색(C++)](../standard-library/file-system-navigation.md)<br/>
[\<filesystem>](../standard-library/filesystem.md)<br/>

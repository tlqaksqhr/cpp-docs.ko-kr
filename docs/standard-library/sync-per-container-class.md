---
title: sync_per_container 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- allocators/stdext::sync_per_container
- allocators/stdext::sync_per_container::equals
dev_langs:
- C++
helpviewer_keywords:
- sync_per_container class
ms.assetid: 0b4b2904-b668-4d94-a422-d4f919cbffab
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2d511eb29c081cfbb85770b35e31aab927b2480b
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38957123"
---
# <a name="syncpercontainer-class"></a>sync_per_container 클래스

각 할당자 개체에 대해 별도의 캐시 개체를 제공하는 [동기화 필터](../standard-library/allocators-header.md)를 설명합니다.

## <a name="syntax"></a>구문

```cpp
template <class Cache>
class sync_per_container
 : public Cache
```

### <a name="parameters"></a>매개 변수

|매개 변수|설명|
|---------------|-----------------|
|*캐시*|동기화 필터와 연결된 캐시 형식입니다. [cache_chunklist](../standard-library/cache-chunklist-class.md), [cache_freelist](../standard-library/cache-freelist-class.md) 또는 [cache_suballoc](../standard-library/cache-suballoc-class.md)일 수 있습니다.|

### <a name="member-functions"></a>멤버 함수

|멤버 함수|설명|
|-|-|
|[equals](#equals)|두 캐시가 같은지 비교합니다.|

## <a name="requirements"></a>요구 사항

**헤더:** \<allocators>

**네임스페이스:** stdext

## <a name="equals"></a>  sync_per_container::equals

두 캐시가 같은지 비교합니다.

```cpp
bool equals(const sync_per_container<Cache>& Other) const;
```

### <a name="parameters"></a>매개 변수

|매개 변수|설명|
|---------------|-----------------|
|*캐시*|동기화 필터의 캐시 개체입니다.|
|*기타*|같은지 비교할 캐시 개체입니다.|

### <a name="return-value"></a>반환 값

멤버 함수는 항상 반환 **false**합니다.

### <a name="remarks"></a>설명

## <a name="see-also"></a>참고자료

[\<allocators>](../standard-library/allocators-header.md)<br/>

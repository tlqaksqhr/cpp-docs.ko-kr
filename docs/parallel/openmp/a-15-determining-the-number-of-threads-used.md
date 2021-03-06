---
title: 사용 되는 스레드 수를 결정 하는 A.15 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 026bb59a-f668-40db-a7cb-69a1bae83d2d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b50858a3384fa5f8d867f13a699e1fc271c101ef
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686388"
---
# <a name="a15---determining-the-number-of-threads-used"></a>A.15   사용된 스레드 수 확인
예를 들어 다음과 같은 잘못 된 (에 대 한 [단원 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) 페이지 37):  
  
```  
np = omp_get_num_threads(); // misplaced   
#pragma omp parallel for schedule(static)  
    for (i=0; i<np; i++)  
        work(i);  
```  
  
 `omp_get_num_threads()` 호출이 반환 1 직렬 코드의 섹션에 있으므로 *np* 앞의 예제에서 1과 같지 항상 됩니다. 병렬 영역에 배포할 수 있는 스레드 수를 확인 하려면 호출 병렬 영역 안에 있어야 합니다.  
  
 다음 예제에는 스레드 수에 대 한 쿼리를 포함 하지 않고이 프로그램을 다시 작성 하는 방법을 보여 줍니다.  
  
```  
#pragma omp parallel private(i)  
{  
    i = omp_get_thread_num();  
    work(i);  
}  
```
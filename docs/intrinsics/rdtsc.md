---
title: __rdtsc | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __rdtsc
dev_langs:
- C++
helpviewer_keywords:
- __rdtsc intrinsic
- rdtsc instruction
- Read Time Stamp Counter instruction
ms.assetid: e31d0e51-c9bb-42ca-bbe9-a81ffe662387
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 81b47a76b3045465d8c3c5c21a87020ee1e74a69
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33337082"
---
# <a name="rdtsc"></a>__rdtsc
**Microsoft 전용**  
  
 생성 된 `rdtsc` 프로세서 타임 스탬프를 반환 하는 명령입니다. 프로세서 타임 스탬프는 마지막 다시 설정 이후 클록 주기 수를 기록합니다.  
  
## <a name="syntax"></a>구문  
  
```  
unsigned __int64 __rdtsc();  
```  
  
## <a name="return-value"></a>반환 값  
 틱 수를 나타내는 64 비트 부호 없는 정수입니다.  
  
## <a name="requirements"></a>요구 사항  
  
|내장 함수|아키텍처|  
|---------------|------------------|  
|`__rdtsc`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **헤더 파일** \<. h >  
  
## <a name="remarks"></a>설명  
 이 루틴은 내장 함수로 사용할 수 있습니다.  
  
 이전 버전의이 세대의 하드웨어에 TSC 값의 해석 다른 [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]합니다. 자세한 내용은 하드웨어 설명서를 참조 하십시오.  
  
## <a name="example"></a>예제  
  
```  
// rdtsc.cpp  
// processor: x86, x64  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(__rdtsc)  
  
int main()  
{  
    unsigned __int64 i;  
    i = __rdtsc();  
    printf_s("%I64d ticks\n", i);  
}  
```  
  
```Output  
3363423610155519 ticks  
```  
  
**Microsoft 전용 종료**  
  
## <a name="see-also"></a>참고 항목  
 [컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
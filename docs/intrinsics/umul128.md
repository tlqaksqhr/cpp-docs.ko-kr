---
title: _umul128 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __umul128
dev_langs:
- C++
helpviewer_keywords:
- __umul128 intrinsic
ms.assetid: 13684df3-3ac7-467c-b258-a0e93bc490b5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a6998b51be8fd11092c4266fa7eee7434be8e5b1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33331534"
---
# <a name="umul128"></a>_umul128
**Microsoft 전용**  
  
 처음 두 인수로 전달된 64비트 부호 없는 정수 두 개를 곱한 다음 곱의 상위 64비트를 `HighProduct`가 가리키는 64비트 부호 없는 정수에 배치하고 곱의 하위 64비트를 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```  
unsigned __int64 _umul128(   
   unsigned __int64 Multiplier,   
   unsigned __int64 Multiplicand,   
   unsigned __int64 *HighProduct   
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 [in] `Multiplier`  
 곱할 첫 번째 64비트 정수입니다.  
  
 [in] `Multiplicand`  
 곱할 두 번째 64비트 정수입니다.  
  
 [out] `HighProduct`  
 곱의 상위 64비트입니다.  
  
## <a name="return-value"></a>반환 값  
 곱의 하위 64비트입니다.  
  
## <a name="requirements"></a>요구 사항  
  
|내장 함수|아키텍처|Header|  
|---------------|------------------|------------|  
|`_umul128`|ARM, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h>|  
  
## <a name="example"></a>예제  
  
```  
// umul128.c  
// processor: IPF, x64  
  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(_umul128)  
  
int main()  
{  
    unsigned __int64 a = 0x0fffffffffffffffI64;  
    unsigned __int64 b = 0xf0000000I64;  
    unsigned __int64 c, d;  
  
    d = _umul128(a, b, &c);  
  
    printf_s("%#I64x * %#I64x = %#I64x%I64x\n", a, b, c, d);  
}  
```  
  
```Output  
0xfffffffffffffff * 0xf0000000 = 0xeffffffffffffff10000000  
```  
  
**Microsoft 전용 종료**  
  
## <a name="see-also"></a>참고 항목  
 [컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
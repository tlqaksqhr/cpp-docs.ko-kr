---
title: _BitScanForward, _BitScanForward64 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _BitScanForward
- _BitScanForward_cpp
- _BitScanForward64_cpp
- _BitScanForward64
dev_langs:
- C++
helpviewer_keywords:
- _BitScanForward intrinsic
- bsf instruction
- BitScanForward intrinsic
ms.assetid: 405e60fb-0815-42a7-9b02-6fc035122203
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ad785bb7789156a2f5105e89a493877fb30c2f3e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33331899"
---
# <a name="bitscanforward-bitscanforward64"></a>_BitScanForward, _BitScanForward64
**Microsoft 전용**  
  
 LSB(최하위 비트)에서 MSB(최상위 비트)로의 마스크 데이터에서 설정 비트(1)를 검색합니다.  
  
## <a name="syntax"></a>구문  
  
```  
unsigned char _BitScanForward(  
   unsigned long * Index,  
   unsigned long Mask  
);  
unsigned char _BitScanForward64(  
   unsigned long * Index,  
   unsigned __int64 Mask  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 [out] `Index`  
 발견된 첫 번째 설정 비트(1)의 비트 위치를 사용하여 로드됩니다.  
  
 [in] `Mask`  
 검색할 32비트 또는 64비트 값입니다.  
  
## <a name="return-value"></a>반환 값  
 마스크가 0이면 0이고 그렇지 않으면 0이 아닙니다.  
  
## <a name="remarks"></a>설명  
 설정 비트가 발견되면 첫 번째로 발견된 설정 비트의 비트 위치가 첫 번째 매개 변수에서 반환됩니다. 설정 비트가 발견되지 않으면 0이 반환되고 그렇지 않으면 1이 반환됩니다.  
  
## <a name="requirements"></a>요구 사항  
  
|내장 함수|아키텍처|  
|---------------|------------------|  
|`_BitScanForward`|x86, ARM, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`_BitScanForward64`|ARM, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **헤더 파일** \<. h >  
  
## <a name="example"></a>예제  
  
```  
// BitScanForward.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
#pragma intrinsic(_BitScanForward)  
  
int main()  
{  
   unsigned long mask = 0x1000;  
   unsigned long index;  
   unsigned char isNonzero;  
  
   cout << "Enter a positive integer as the mask: " << flush;  
   cin >> mask;  
   isNonzero = _BitScanForward(&index, mask);  
   if (isNonzero)  
   {  
      cout << "Mask: " << mask << " Index: " << index << endl;  
   }  
   else  
   {  
      cout << "No set bits found.  Mask is zero." << endl;  
   }  
}  
```  
  
## <a name="input"></a>입력  
  
```  
12  
```  
  
## <a name="sample-output"></a>샘플 출력  
  
```  
Enter a positive integer as the mask:   
Mask: 12 Index: 2  
```  
  
**Microsoft 전용 종료**  
  
## <a name="see-also"></a>참고 항목  
 [컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
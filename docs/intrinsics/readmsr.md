---
title: __readmsr | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __readmsr
dev_langs:
- C++
helpviewer_keywords:
- Read Model Specific Register
- rdmsr instruction
- __readmsr intrinsic
ms.assetid: 7ab1f8e8-72cb-4ce4-817d-3e728a3c9716
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4e8196b25b1507c92542faa6dd8ca59b4632d8f0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33335915"
---
# <a name="readmsr"></a>__readmsr
**Microsoft 전용**  
  
 에서는 오류가 발생 하는 `rdmsr` 로 지정 된 모델 특정 레지스터를 읽는 명령 `register` 해당 값을 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
__int64 __readmsr(   
   int register   
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 [in] `register`  
 읽을 모델 특정 레지스터입니다.  
  
## <a name="return-value"></a>반환 값  
 지정된 된 레지스터의 값입니다.  
  
## <a name="requirements"></a>요구 사항  
  
|내장 함수|아키텍처|  
|---------------|------------------|  
|`__readmsr`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **헤더 파일** \<. h >  
  
## <a name="remarks"></a>설명  
 이 함수는 커널 모드에서 사용할 수만 및 루틴은 내장 함수로 사용할 수만 있습니다.  
  
 자세한 내용은 AMD 설명서를 참조 합니다.  
  
**Microsoft 전용 종료**  
  
## <a name="see-also"></a>참고 항목  
 [컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
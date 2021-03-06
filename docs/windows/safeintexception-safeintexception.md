---
title: 'Safeintexception:: Safeintexception | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeIntException
- SafeIntException.SafeIntException
- SafeIntException::SafeIntException
dev_langs:
- C++
helpviewer_keywords:
- SafeIntException, constructor
ms.assetid: 8e5a0c24-a56b-4c80-9ee8-876604b1e7dc
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 393c424feb2a84fff85ba0efb5de7cbcaf54737c
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40016761"
---
# <a name="safeintexceptionsafeintexception"></a>SafeIntException::SafeIntException
만듭니다는 **SafeIntException** 개체입니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
SafeIntException();  
  
SafeIntException(  
   SafeIntError code  
);  
```  
  
### <a name="parameters"></a>매개 변수  
 [in] *코드*  
 발생 한 오류를 설명 하는 열거형된 데이터 값입니다.  
  
## <a name="remarks"></a>설명  
 가능한 값에 대 한 *코드* Safeint.h 파일에 정의 됩니다. 편의 위해 가능한 값도 여기에 나와 있습니다.  
  
-   `SafeIntNoError`  
  
-   `SafeIntArithmeticOverflow`  
  
-   `SafeIntDivideByZero`  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** safeint.h  
  
 **Namespace:** msl:: utilities  
  
## <a name="see-also"></a>참고 항목  
 [SafeInt 라이브러리](../windows/safeint-library.md)   
 [SafeIntException 클래스](../windows/safeintexception-class.md)   
 [SafeInt 클래스](../windows/safeint-class.md)
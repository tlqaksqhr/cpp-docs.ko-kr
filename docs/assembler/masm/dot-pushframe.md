---
title: . PUSHFRAME | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .PUSHFRAME
dev_langs:
- C++
helpviewer_keywords:
- .PUSHFRAME directive
ms.assetid: 17b123d0-4c6d-4fd2-85eb-798e8ad0a73c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 66531207d21bb7e9e0c165db135f5a0c0d77e478
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/28/2018
ms.locfileid: "32053206"
---
# <a name="pushframe"></a>.PUSHFRAME
생성 된 `UWOP_PUSH_MACHFRAME` 코드 항목을 해제 합니다. 경우 선택적 `code` 지정을 해제 코드 항목 1의 한정자를 제공 됩니다. 그렇지 않으면 한정자는 0입니다.  
  
## <a name="syntax"></a>구문  
  
```  
.PUSHFRAME [code]  
```  
  
## <a name="remarks"></a>설명  
 . PUSHFRAME ml64.exe 사용자가 프레임 함수 해제 하는 방법을 지정할 수 있으며에서 확장 되는 프롤로그만 사용할 수는 [PROC](../../assembler/masm/proc.md) 프레임 선언을 [합니다. 프롤로그 끝](../../assembler/masm/dot-endprolog.md) 지시문입니다. 이러한 지시문 코드를 생성 하지 않습니다. 만 생성할 `.xdata` 및 `.pdata`합니다. . PUSHFRAME 실제로 해제 해제 되도록 작업을 구현 하는 지침 뒤에 야 합니다. 해제 지시문와 실제 매크로에서 해제 하는 코드를 래핑하는 것이 좋습니다.  
  
 자세한 내용은 참조 [MASM (ml64.exe) x64](../../assembler/masm/masm-for-x64-ml64-exe.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [지시문 참조](../../assembler/masm/directives-reference.md)
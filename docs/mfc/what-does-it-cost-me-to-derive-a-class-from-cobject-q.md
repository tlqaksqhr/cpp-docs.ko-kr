---
title: CObject에서 클래스를 파생시키는 비용 | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CObject
dev_langs:
- C++
helpviewer_keywords:
- CObject class [MFC], overhead of derived classes [MFC]
ms.assetid: 9b92c98b-b3dd-48a7-9d24-c3b8554edf90
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3ffff35cdef6cf2f730687334bbb56bc078371a7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33381679"
---
# <a name="what-does-it-cost-me-to-derive-a-class-from-cobject"></a>CObject에서 클래스를 파생시키는 비용
클래스에서 파생 된에 오버 헤드가 [CObject](../mfc/reference/cobject-class.md) 최소화 됩니다. 파생된 클래스 상속 4 개의 가상 함수 및 하나의 [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) 개체입니다.  
  
## <a name="see-also"></a>참고 항목  
 [CObject 클래스: 질문과 대답](../mfc/cobject-class-frequently-asked-questions.md)

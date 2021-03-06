---
title: 메시지 처리기 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- message handlers [MFC]
- command handling [MFC], message handlers
- handlers [MFC]
- message handling [MFC], message handler functions
- handlers [MFC], command
- handlers [MFC], message
ms.assetid: 51bc4e76-dbe3-4cc2-b026-3199d56b2fa9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: be4ccf9ec33e5ddf497193c1942e9f300f8cae57
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33347632"
---
# <a name="message-handlers"></a>메시지 처리기
Mfc에서 전용 *처리기* 함수는 각 메시지를 처리 합니다. 메시지 처리기 함수는 클래스의 멤버 함수입니다. 이 설명서에서는 용어 *메시지 처리기 멤버 함수*, *메시지-처리기 함수의*, *메시지 처리기*, 및 *처리기*같은 의미로 합니다. 일부 종류의 메시지 처리기에는 "명령 처리기입니다." 라고도 합니다.  
  
 프레임 워크 응용 프로그램을 작성 작업의 상당한 부분에 대 한 메시지 처리기 계정을 작성 합니다. 이 문서에서는 메시지 처리 메커니즘의 작동 방식을 설명 합니다.  
  
 이 작업을 수행할 메시지에 대 한 처리기가 해당 메시지에 대 한 응답에서 원하는 작업이 무엇이 든 않습니다. 클래스의 속성 창을 사용 하 여 처리기를 만들 수 있으며 소스 코드 편집기를 사용 하 여 처리기의 코드를 채웁니다.  
  
 에 처리기를 작성 하의 모든 Microsoft Visual c + + 및 MFC의 기능을 사용할 수 있습니다. 목록이 모든 클래스에 대 한 참조 [클래스 라이브러리 개요](../mfc/class-library-overview.md) 에 *MFC 참조*합니다.  
  
## <a name="see-also"></a>참고 항목  
 [프레임워크의 메시지 및 명령](../mfc/messages-and-commands-in-the-framework.md)


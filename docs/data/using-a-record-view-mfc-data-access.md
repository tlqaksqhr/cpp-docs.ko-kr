---
title: 레코드 뷰 (데이터 액세스)를 사용 하 여 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- record views, customizing default code
ms.assetid: 91f2828f-0666-4273-ae28-e4703fd98521
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 23dd3335f6c77a3efec26f13e78824806f05821a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33104645"
---
# <a name="using-a-record-view--mfc-data-access"></a>레코드 뷰 사용  (MFC Data Access)
이 항목에서는 마법사가 자동으로 작성하는 레코드 뷰의 기본 코드를 사용자 지정하는 일반적인 방법을 설명합니다. 와 레코드 선택을 제한 하려면 일반적으로 [필터](../data/odbc/recordset-filtering-records-odbc.md) 또는 [매개 변수](../data/odbc/recordset-parameterizing-a-recordset-odbc.md), 아마도 [정렬](../data/odbc/recordset-sorting-records-odbc.md) , 레코드에는 SQL 문을 사용자 지정 합니다.  
  
 사용 하 여 `CRecordView` 은 사용 하 여 상당히 같습니다 [CFormView](../mfc/reference/cformview-class.md)합니다. 기본적인 방식은 레코드 뷰를 사용하여 단일 레코드 집합의 레코드를 표시하고 필요에 따라 업데이트하는 것입니다. 도에서 설명한 대로 다른 레코드 집합을 사용할 수 있습니다, 그 외에도 [레코드 뷰: 두 번째 레코드 집합에서 목록 상자 채우기](../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [레코드 뷰 (데이터 액세스)](../data/record-views-mfc-data-access.md)   
 [ODBC 드라이버 목록](../data/odbc/odbc-driver-list.md)
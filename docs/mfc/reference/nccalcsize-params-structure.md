---
title: NCCALCSIZE_PARAMS 구조체 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- NCCALCSIZE_PARAMS
dev_langs:
- C++
helpviewer_keywords:
- NCCALCSIZE_PARAMS structure [MFC]
ms.assetid: 3424cd9f-806a-4089-82fb-414187589edf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 095b66af9dab08e3d8fad040c43e2eaf8d2beb81
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37335645"
---
# <a name="nccalcsizeparams-structure"></a>NCCALCSIZE_PARAMS 구조체
`NCCALCSIZE_PARAMS` 구조 크기, 위치 및 유효한 내용의 창의 클라이언트 영역을 계산 하 여 WM_NCCALCSIZE 메시지를 처리 하는 동안 응용 프로그램을 사용할 수 있는 정보를 포함 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
typedef struct tagNCCALCSIZE_PARAMS {  
    RECT rgrc[3];  
    PWINDOWPOS lppos;  
} NCCALCSIZE_PARAMS;  
```  
  
#### <a name="parameters"></a>매개 변수  
 *rgrc*  
 사각형의 배열을 지정합니다. 첫 번째 이동 되거나 크기를 조정 된 창의 새 좌표를 포함 합니다. 두 번째를 이동 하거나 크기를 조정 하기 전에 창의 좌표를 포함 합니다. 세 번째를 이동 하거나 크기를 조정 하기 전에 창의 클라이언트 영역의 좌표를 포함 합니다. 창의 자식 창 이면 부모 창의 클라이언트 영역을 기준으로 좌표 있습니다. 창의 최상위 창 이면 좌표가 화면을 기준으로 합니다.  
  
 *lppos*  
 가리키는 [WINDOWPOS](../../mfc/reference/windowpos-structure1.md) 이동 하거나 크기를 조정할 창 발생 시킨 작업에 지정 된 크기와 위치 값을 포함 하는 구조입니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** winuser.h  
  
## <a name="see-also"></a>참고 항목  
 [구조체, 스타일, 콜백 및 메시지 맵](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)


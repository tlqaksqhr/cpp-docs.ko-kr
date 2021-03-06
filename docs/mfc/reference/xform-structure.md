---
title: XFORM 구조체 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- XFORM
dev_langs:
- C++
helpviewer_keywords:
- XFORM structure [MFC]
ms.assetid: 4fb4ef5b-05d2-4884-82d1-1cb8f7be6302
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6084882bed6690269fbb926f394159491d22978a
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37885886"
---
# <a name="xform-structure"></a>XFORM 구조체
`XFORM` 구조는 다음과 같은 형식을 갖습니다.  
  
## <a name="syntax"></a>구문  
  
```  
typedef struct  tagXFORM {  /* xfrm */  
    FLOAT eM11;  
    FLOAT eM12;  
    FLOAT eM21;  
    FLOAT eM22;  
    FLOAT eDx;  
    FLOAT eDy;  
} XFORM;  
```  
  
## <a name="remarks"></a>설명  
 `XFORM` 구조 페이지 공백 변환 세계 좌표 공간을 지정 합니다. 합니다 `eDx` 및 `eDy` 멤버 가로 및 세로 변환 구성 요소를 각각 지정 합니다. 다음 표에서 작업에 따라 다른 멤버 사용 하는 방법을 보여 줍니다.  
  
|작업|eM11|eM12|eM21|eM22|  
|---------------|----------|----------|----------|----------|  
|`Rotation`|회전 각도의 코사인 값|회전 각도의 사인|회전 각도의 사인 음수 값|회전 각도의 코사인 값|  
|`Scaling`|가로 크기 조정 구성 요소|Nothing|Nothing|세로 크기 조정 구성 요소|  
|`Shear`|Nothing|가로 너비 대 높이 비율 상수|세로 너비 대 높이 비율 상수|Nothing|  
|`Reflection`|가로 리플렉션 구성 요소|Nothing|Nothing|세로 리플렉션 구성 요소|  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** wingdi.h  
  
## <a name="see-also"></a>참고 항목  
 [구조체, 스타일, 콜백 및 메시지 맵](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CRgn::CreateFromData](../../mfc/reference/crgn-class.md#createfromdata)


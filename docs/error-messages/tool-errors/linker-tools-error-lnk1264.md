---
title: 링커 도구 오류 LNK1264 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1264
dev_langs:
- C++
helpviewer_keywords:
- LNK1264
ms.assetid: 23b1aad7-d382-42c1-bae8-db68575c57a8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7ed21327028fc9849f6e0694bb82ae34c6084842
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33301465"
---
# <a name="linker-tools-error-lnk1264"></a>링커 도구 오류 LNK1264
/Ltcg: pginstrument 지정 되었지만 코드를 생성 하지 않아도 됩니다. 계측 하지 못했습니다.  
  
 **/Ltcg: pginstrument** 지정으로 컴파일된.obj 파일을 찾을 수 없음 되었지만 [/GL](../../build/reference/gl-whole-program-optimization.md)합니다. 계측 링크 하지 못했습니다을 발생 시킬 수 없습니다. 명령줄에서로 컴파일한 하나 이상.obj 파일이 있어야 **/GL** 계측 발생할 수 있도록 합니다.  
  
 프로필 기반 최적화 (PGO)는 64 비트 컴파일러에서 사용할 수만 있습니다.
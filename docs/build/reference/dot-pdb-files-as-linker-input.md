---
title: . 링커 입력 파일로 Pdb 파일 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- .pdb files, as linker input
- PDB files, as linker input
ms.assetid: c1071478-2369-4b03-9df8-71761cf82f3b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f6707be955b5c4a332d1162f53b1cb854391a2ce
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32370178"
---
# <a name="pdb-files-as-linker-input"></a>링커 입력 파일로 사용하는 .Pdb 파일
개체 (.obj) 파일 /Zi 옵션을 사용 하 여 컴파일된 프로그램 데이터베이스 (PDB)의 이름이 들어 있습니다. 링커에; 개체의 PDB 파일 이름을 지정 하지 않으면 필요한 경우 PDB를 찾을 수 포함된 된 이름을 사용 하는 링크 합니다. 이 적용 됩니다.을 라이브러리에 포함 된 디버깅할 수 있는 개체 디버깅 가능한 라이브러리에 대 한 PDB 링커 라이브러리와 함께 사용할 수 있어야 합니다.  
  
 또한 링크.exe 파일이 나.dll 파일에 대 한 디버깅 정보를 보관 하는 PDB를 사용 합니다. 링크 된 프로그램을 다시 때 PDB를 업데이트 하기 때문에 프로그램의 PDB는는 출력 파일과 입력된 파일입니다.  
  
## <a name="see-also"></a>참고 항목  
 [LINK 입력된 파일](../../build/reference/link-input-files.md)   
 [링커 옵션](../../build/reference/linker-options.md)
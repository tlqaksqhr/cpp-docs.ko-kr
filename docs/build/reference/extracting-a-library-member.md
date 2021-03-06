---
title: 라이브러리 멤버 추출 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- Lib
dev_langs:
- C++
helpviewer_keywords:
- LIB [C++], extracting library members
- EXTRACT library manager option
- libraries, extracting members
- -EXTRACT library manager option
- extracting library members
- /EXTRACT library manager option
ms.assetid: a2c5c2a1-9b7e-489a-a9a4-1dec694e1fc5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0dc0dc67a6d9e4a3ff61aa3b82ac10b9eabcb94b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32371244"
---
# <a name="extracting-a-library-member"></a>라이브러리 멤버 추출
LIB를 사용 하 여 기존 라이브러리의 멤버의 복사본이 포함 된 개체 (.obj) 파일을 만들 수 있습니다. 멤버의 복사본을 추출 하려면 다음 구문을 사용 합니다.  
  
```  
LIB library /EXTRACT:member /OUT:objectfile  
```  
  
 이 명령은 라는.obj 파일로 만듭니다 *objectfile* 의 복사본을 포함 하는 `member` 의 *라이브러리*합니다. `member` 이름은 대/소문자 구분입니다. 단일 명령으로 한 멤버를 추출할 수 있습니다. /OUT 옵션을 지정 해야 합니다. 기본 출력 이름이 없습니다. 파일을 호출 하는 경우 *objectfile* 지정된 된 디렉터리에 이미 있습니다 (또는 지정 된 디렉터리가 없는 경우 현재 디렉터리 *objectfile*), 추출 된 *objectfile*기존 파일을 대체 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [LIB 참조](../../build/reference/lib-reference.md)
---
title: DLL 가져오기 및 내보내기 함수 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- DLLs [C++], importing
- dllimport attribute [C++], storage-class attribute
- DLL exports [C++]
- declaring functions, with dllexport and dllimport
- extended storage-class attributes
- dllexport attribute [C++], storage-class attribute
ms.assetid: 08d164b9-770a-4e14-afeb-c6f21d9e33e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: da456b7caca59fb874f4da87a342162b53c09319
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32384956"
---
# <a name="dll-import-and-export-functions"></a>DLL 가져오기 및 내보내기 함수
**Microsoft 전용**  
  
 이 내용에 대한 가장 완벽한 최신 정보는 [dllexport, dllimport](../cpp/dllexport-dllimport.md)에서 확인할 수 있습니다.  
  
 **dllimport** 및 `dllexport` 저장소 클래스 한정자는 Microsoft 전용 C 언어 확장입니다. 이러한 한정자는 해당 클라이언트에 대한 DLL 인터페이스(실행 파일 또는 다른 DLL)를 명시적으로 정의합니다. 함수를 `dllexport`로 선언하면 모듈 정의(.DEF) 파일을 사용할 필요가 없습니다. 또한 **dllimport** 및 `dllexport` 한정자는 데이터 및 개체와 함께 사용할 수 있습니다.  
  
 다음 예제와 같이 **dllimport** 및 `dllexport` 저장소 클래스 한정자는 확장된 특성 구문 키워드인 `__declspec`와 함께 사용해야 합니다.  
  
```  
#define DllImport   __declspec( dllimport )  
#define DllExport   __declspec( dllexport )  
  
DllExport void func();  
DllExport int i = 10;  
DllExport int j;  
DllExport int n;  
```  
  
 확장된 저장소 클래스 한정자에 사용되는 구문에 대한 자세한 내용은 [확장된 저장소 클래스 특성](../c-language/c-extended-storage-class-attributes.md)을 참조하세요.  
  
 **Microsoft 전용 종료**  
  
## <a name="see-also"></a>참고 항목  
 [C 함수 정의](../c-language/c-function-definitions.md)
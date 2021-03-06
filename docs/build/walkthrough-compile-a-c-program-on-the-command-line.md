---
title: '연습: 명령줄에서 C 프로그램 컴파일 | Microsoft Docs'
ms.custom: conceptual
ms.date: 06/21/2018
ms.technology:
- cpp-tools
ms.topic: conceptual
helpviewer_keywords:
- command-line applications [C++], C programs
- Visual C, compiling
- compiling programs [C++]
- C program compiling [C++]
ms.assetid: 7e74cc2d-54b1-49de-b7ad-d3ae6b39ab8d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f3578fbc5a85757fedda3e9078e54934016607eb
ms.sourcegitcommit: e013acba70aa29fed60ae7945162adee23e19c3b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/22/2018
ms.locfileid: "36322237"
---
# <a name="walkthrough-compile-a-c-program-on-the-command-line"></a>연습: 명령줄에서 C 프로그램 컴파일

Visual c + +에는 모든를 기본적인 콘솔 프로그램에서 전체 Windows 데스크톱 응용 프로그램, 모바일 응용 프로그램 등을 만드는 데 사용할 수 있는 C 컴파일러가 포함 되어 있습니다.

이 연습에서는 기본 "Hello, World"를 만드는 방법을 보여 줍니다.-편집기에서 텍스트를 사용 하 여 C 프로그램을 스타일 하 고 다음 명령줄에서 컴파일합니다. 대신 명령줄에서 c + +에서 작동 합니다, 참조 [연습: 명령줄에서 네이티브 c + + 프로그램 컴파일](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)합니다. 명령줄을 사용 하는 대신 Visual Studio IDE를 시도 하세요. 참조 하려는 경우 [연습: 프로젝트 및 솔루션 (c + +) 작업](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) 또는 [c + + 데스크톱 개발을 위한 Visual Studio IDE를 사용 하 여](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)합니다.

## <a name="prerequisites"></a>전제 조건

이 연습을 완료 하려면 설치 해야 Visual Studio 및 선택적 Visual c + + 구성 요소 또는 Build Tools for Visual Studio입니다.

Visual Studio는 다양 한 언어 및 플랫폼에 대 한 완전 한 기능의 편집기, 리소스 관리자, 디버거, 및 컴파일러를 지 강력한 통합된 개발 환경입니다. 이러한 기능 및 다운로드 하 고 무료 Visual Studio Community 버전을 비롯해 Visual Studio를 설치 하는 방법에 대 한 내용은 [Visual Studio 설치](/visualstudio/install/install-visual-studio)합니다.

Visual Studio 버전의 Visual Studio 용 빌드 도구만 명령줄 도구 집합과는 컴파일러, 도구 및 C 및 c + + 프로그램을 빌드하는 데 필요한 라이브러리를 설치 합니다. 빌드 랩에 대 한 완벽 한는 또는 강의실을 실행 하 고 상대적으로 신속 하 게 설치 합니다. 명령줄 도구 집합을 설치 하려면 다운로드 [Tools for Visual Studio 빌드](https://go.microsoft.com/fwlink/p/?linkid=875721) 설치 관리자를 실행 하 고 있습니다.

명령줄에서 C 또는 c + + 프로그램을 작성할 수 있습니다, 전에 명령줄에서 액세스할 수 있습니다 및는 도구가 설치 되어 있는지를 확인 해야 합니다. Visual c + + 도구, 헤더 및 라이브러리를 사용 하 여을 찾기 위해 명령줄 환경에 대 한 요구 사항이 복잡 한에 있습니다. **일반 명령 프롬프트 창에서 Visual c + +를 사용할 수 없습니다** 없이 몇 가지 준비 합니다. 필요한는 *개발자 명령 프롬프트* 창은 일반적인 명령 프롬프트 창에 설정 하는 모든 필수 환경 변수입니다. 다행히도 Visual c + + 명령줄 빌드에 대 한 설정 환경을 사용 하는 개발자 명령 프롬프트를 시작할 수 있는 바로 가기 키를 설치 합니다. 그러나 개발자 명령 프롬프트 바로 가기 이름과 위치는 거의 모든 버전의 Visual c + + 및 서로 다른 버전의 Windows에서 서로 다릅니다. 첫 번째 연습 작업의 오른쪽 바로 가기를 사용 하 여 찾는 것입니다.

> [!NOTE]
> 개발자 명령 프롬프트 바로 가기를 컴파일러 및 도구에 대 한 모든 필수 헤더 및 라이브러리의 올바른 경로 자동으로 설정합니다. 이러한 값 중 일부는 각 빌드 구성 마다 다릅니다. 값을 설정 해야 이러한 환경 직접 바로 가기 중 하나를 사용 하지 않는 경우. 자세한 내용은 참조 [명령줄 빌드에 맞는 경로 및 환경 변수 설정](../build/setting-the-path-and-environment-variables-for-command-line-builds.md)합니다. 빌드 환경에서는 복잡 한 이기 때문에 직접 작성 하는 대신 개발자 명령 프롬프트 바로 가기의 사용 하는 것이 좋습니다.

## <a name="open-a-developer-command-prompt"></a>개발자 명령 프롬프트를 열으십시오

1. Windows 10에서 Visual Studio 2017을 설치한 경우 시작 메뉴를 열고 하 고 다음 아래로 스크롤하여 열고는 **Visual Studio 2017** 폴더 (Visual Studio 2017 app 제외). 선택 **VS 2017 용 개발자 명령 프롬프트** 명령 프롬프트 창을 엽니다.

   Windows 10에서 Microsoft Visual c + + 빌드 도구 2015를 설치한 경우 엽니다는 **시작** 메뉴에서 다음 아래로 스크롤하여 및 열기는 **Visual c + + 빌드 도구** 폴더입니다. 선택 **Visual c + + 2015 x86 네이티브 도구 명령 프롬프트** 명령 프롬프트 창을 엽니다.

   다른 버전의 Visual Studio를 사용 하는 다른 버전의 Windows 실행 중인 경우 시작 메뉴에서 확인 하거나 개발자 명령 프롬프트 바로 가기를 포함 하는 Visual Studio tools 폴더에 대 한 페이지를 시작 합니다. 또한 "개발자 명령 프롬프트"를 찾아 선택 하는 설치 된 버전의 Visual Studio가 일치 하는 Windows 검색 기능을 사용할 수 있습니다. 바로 가기를 사용 하 여 명령 프롬프트 창을 엽니다.

2. 다음으로, Visual c + + 개발자 명령 프롬프트 올바르게 설정 되어 있는지 확인 합니다. 명령 프롬프트 창에서 입력 `cl` 출력은 다음과 같이 있는지 확인 합니다.

   ```Output
   C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
   Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
   Copyright (C) Microsoft Corporation.  All rights reserved.

   usage: cl [ option... ] filename... [ /link linkoption... ]

   C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>
   ```

   현재 디렉터리 또는 Visual c + + 및 설치 된 업데이트의 버전에 따라 버전 번호에 차이가 있을 수 있습니다. 표시 되는 것과 비슷합니다, 다음 모르는 경우 명령줄에서 C 또는 c + + 프로그램 빌드 준비입니다.

   > [!NOTE]
   > "'Cl'는 내부 또는 외부 명령, 실행할 수 있는 프로그램 또는 배치 파일으로는 인식 되지 않습니다"와 같은 오류가 발생 하는 경우 오류 C1034 또는 오류 LNK1104 실행 하는 경우는 **cl** 하거나 개발자 명령 프롬프트를 사용 하지 않는 한 다음 명령 또는 Visual c + +의 설치에 문제가 있습니다. 계속 하기 전에이 문제를 해결 해야 합니다.

   개발자 명령 프롬프트 바로 가기를 찾을 수 없으면 또는 입력 하면 오류 메시지가 나타날 경우 `cl`, 다음 Visual c + + 설치에 문제가 있을 수 있습니다. Visual Studio 2017을 사용 하는 경우 다시 설치는 **c + + 데스크톱 개발** Visual Studio 설치 관리자에서 작업 합니다. 자세한 내용은 참조 [Visual Studio에서 c + + 설치 지원](../build/vscpp-step-0-installation.md)합니다. 또는 다시 설치는 [Tools for Visual Studio 빌드](https://go.microsoft.com/fwlink/p/?linkid=875721)합니다. 이 기능은 작동 될 때까지에 다음 섹션 넘어갑니다 하지 마십시오. 설치 및 Visual Studio 문제를 해결 하는 방법에 대 한 자세한 내용은 참조 [Visual Studio 설치](/visualstudio/install/install-visual-studio)합니다.

   > [!NOTE]
   > 컴퓨터와 시스템 보안 구성에서의 Windows 버전에 따라 개발자 명령 프롬프트 바로 가기에 대 한 바로 가기 메뉴를 열고를 마우스 오른쪽 단추로 클릭 해야 할 수 있습니다 **관리자 권한으로 실행** 를 작성 하 고이 연습을 수행 하 여 만든 프로그램을 실행 했습니다.

## <a name="create-a-c-source-file-and-compile-it-on-the-command-line"></a>C 소스 파일을 만들고 명령줄에서 컴파일하십시오.

1. 개발자 명령 프롬프트 창에서 입력 **cd c:\\**  c: 드라이브의 루트에는 현재 작업 디렉터리를 변경할 수 있습니다. 다음으로, 입력 **md c:\simple** 를 디렉터리를 만들려면 다음 입력 **cd c:\simple** 해당 디렉터리로 변경 합니다. 이 소스 파일 및 컴파일된 프로그램을 포함할 디렉터리입니다.

2. 입력 **메모장 simple.c** 개발자 명령 프롬프트입니다. 메모장 경고 대화 상자가 나타나면 선택 **예** 작업 디렉터리에 새 simple.c 파일을 만들려고 합니다.

3. 메모장에서 코드의 다음 줄을 입력 합니다.

    ```C
    #include <stdio.h>

    int main()
    {
        printf("Hello, World! This is a native C program compiled on the command line.\n");
        return 0;
    } 
    ```

4. 메모장의 메뉴 모음에서 선택 **파일**, **저장** simple.c 작업 디렉터리에 저장 합니다.

5. 개발자 명령 프롬프트 창으로 다시 전환 합니다. 입력 **dir** c:\simple 디렉터리의 내용을 나열 하려면 명령 프롬프트입니다. 소스 파일 simple.c 다음과 같은 디렉터리 목록에 나타나야 합니다.

    ```Output
    C:\simple>dir
     Volume in drive C has no label.
     Volume Serial Number is CC62-6545

     Directory of C:\simple

    10/02/2017  03:46 PM    <DIR>          .
    10/02/2017  03:46 PM    <DIR>          ..
    10/02/2017  03:36 PM               143 simple.c
                   1 File(s)            143 bytes
                   2 Dir(s)  514,900,566,016 bytes free

    ```

   컴퓨터에는 날짜 및 기타 세부 정보가 달라 집니다. 소스 코드 파일이 보이지 않으면 simple.c, 만든 c:\simple 디렉터리로 변경 했는지 확인 하 고 메모장에서이 디렉터리에 있는 소스 파일을 저장 했는지 확인 합니다. 또한.c 파일 이름 확장명을.txt 확장명이 아닌으로 소스 코드를 저장 해야 합니다.

6. 프로그램을 컴파일하려면 입력 **cl simple.c** 개발자 명령 프롬프트입니다.

   컴파일러에서 표시 하는 출력 정보 줄에 simple.exe 실행 프로그램 이름을 확인할 수 있습니다.

    ```Output
    c:\simple>cl simple.c
    Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
    Copyright (C) Microsoft Corporation.  All rights reserved.

    simple.c
    Microsoft (R) Incremental Linker Version 14.10.25017.0
    Copyright (C) Microsoft Corporation.  All rights reserved.

    /out:simple.exe
    simple.obj
    ```

   > [!NOTE]
   > "'Cl'는 내부 또는 외부 명령, 실행할 수 있는 프로그램 또는 배치 파일으로는 인식 되지 않습니다"와 같은 오류가 발생 하는 경우 오류 C1034 또는 오류 LNK1104, 개발자 명령 프롬프트가 올바르게 설정 되지 않습니다. 이 문제를 해결 하는 방법에 대 한 내용은 돌아가서는 **개발자 명령 프롬프트를 열고** 섹션.

   > [!NOTE]
   > 다른 컴파일러 또는 링커 오류 또는 경고가 발생 하면 오류를 해결 한 다음 저장 하는 컴파일러를 다시 실행 하도록 소스 코드를 검토 합니다. 특정 오류에 대 한 정보에 대 한 오류 번호를 확인 하려면이 페이지 맨 위에 있는 검색 상자를 사용 합니다.

7. 프로그램을 실행 하려면 입력 **간단한** 명령 프롬프트입니다.

   프로그램이 다음 텍스트를 표시하고 종료됩니다.

    ```Output
    Hello, World! This is a native C program compiled on the command line.
    ```

   축 하 합니다, 방금 컴파일 및 명령줄을 사용 하 여 C 프로그램을 실행 합니다.

## <a name="next-steps"></a>다음 단계

이 "Hello, World" 예제는 약 하기만 C 프로그램을 가져올 수 있습니다. 현실 세계 프로그램 헤더 파일 및 더 많은 소스 파일, 라이브러리에 연결 하 고 유용한 작업을 수행 했습니다.

표시 된 예제 코드를 입력 하는 대신 사용자 고유의 C 코드를 빌드하려면이 연습 단계를 사용할 수 있습니다. 또한 다른 곳에서 검색 하는 많은 C 코드 샘플 프로그램을 빌드할 수 있습니다. 여러 소스 코드 파일을 포함 하는 프로그램을 컴파일하려면 모두 다음과 같은 명령줄에 입력 합니다.

`cl file1.c file2.c file3.c`

컴파일러 라는 file1.exe 프로그램을 출력 합니다. 이름을 program1.exe을 변경 하려면 추가 [/out](../build/reference/out-output-file-name.md) 링커 옵션:

`cl file1.c file2.c file3.c /link /out:program1.exe`

하나를 사용 하 여 컴파일하는 좋습니다 더 많은 프로그래밍 실수를 자동으로 catch 하는 [/W3](../build/reference/compiler-option-warning-level.md) 또는 [/W4](../build/reference/compiler-option-warning-level.md) 경고 수준 옵션:

`cl /W4 file1.c file2.c file3.c /link /out:program1.exe`

컴파일러, cl.exe에 더 많은 옵션을 빌드, 최적화, 디버그, 적용 하 고 코드를 분석할 수 있습니다. 빠른 목록에 대 한 입력 **cl /?** 개발자 명령 프롬프트입니다. 또한 컴파일 및 별도로 연결 및 수 더 복잡 한 빌드 시나리오에서 링커 옵션을 적용 합니다. 컴파일러 및 링커 옵션 및 사용에 대 한 자세한 내용은 참조 하십시오. [C/c + + 빌드 참조](../build/reference/c-cpp-building-reference.md)합니다.

구성 하 고 명령줄에서 보다 복잡 한 프로젝트를 빌드할 NMAKE 및 메이크파일에 또는 MSBuild 및 프로젝트 파일을 사용할 수 있습니다. 이러한 도구를 사용 하 여에 대 한 자세한 내용은 참조 하십시오. [NMAKE 참조](../build/nmake-reference.md) 및 [MSBuild](../build/msbuild-visual-cpp.md)합니다.

C 및 c + + 언어는 유사 하지만 동일 하지는 않습니다. Visual c + + 컴파일러는 코드를 컴파일할 때 사용할 언어를 결정 하는 간단한 규칙을 사용 합니다. 기본적으로 Visual C++ 컴파일러는 .c로 끝나는 파일은 모두 C 소스 코드로, .cpp로 끝나는 파일은 모두 C++ 소스 코드로 취급합니다. 컴파일러가 파일 이름 확장명에 관계 없이 모든 파일을 C로 취급 하도록 하려면을 사용 하 여는 [/Tc](../build/reference/tc-tp-tc-tp-specify-source-file-type.md) 컴파일러 옵션입니다.

Visual c + + C 컴파일러는 ISO C99 표준에 일반적으로 호환 하지만 엄격 하 게 호환 되지 않습니다. 대부분의 경우 이식 가능한 C 코드를 컴파일하고 예상 대로 실행 합니다. Visual c + + ISO C11에서 대부분의 내용 지원 하지 않습니다. 특정 라이브러리 함수 및 POSIX 함수 이름이 Visual c + + 컴파일러에 의해 사용 되지 않습니다. 함수를 지원 하지만 기본 이름이 변경 되었습니다. 자세한 내용은 참조 [CRT의 보안 기능](../c-runtime-library/security-features-in-the-crt.md) 및 [컴파일러 경고 (수준 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)합니다.

## <a name="see-also"></a>참고자료

[연습: 표준 C++ 프로그램 만들기(C++)](../windows/walkthrough-creating-a-standard-cpp-program-cpp.md)  
[C# 언어 참조](../c-language/c-language-reference.md)  
[C/C++ 프로그램 빌드](../build/building-c-cpp-programs.md)  
[호환성](../c-runtime-library/compatibility.md)  

---
title: Visual Studio에서 Linux CMake 프로젝트 구성 | Microsoft Docs
description: Visual Studio에서 Linux CMake 프로젝트를 구성하는 방법
ms.custom: ''
ms.date: 07/20/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-linux
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: f8707b32-f90d-494d-ae0b-1d44425fdc25
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: 743f15cdb9fe8b0233f5b59ca399c0f47704d441
ms.sourcegitcommit: b0d6777cf4b580d093eaf6104d80a888706e7578
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/26/2018
ms.locfileid: "39269542"
---
# <a name="configure-a-linux-cmake-project"></a>Linux CMake 프로젝트 구성

**Visual Studio 2017 버전 15.4 이상**  
Visual Studio에 대한 Linux C++ 워크로드를 설치하면 Linux용 CMake 지원이 기본적으로 선택됩니다. 이제 CMake를 Visual Studio 프로젝트로 변환할 필요 없이 CMake를 사용하는 기존 코드 베이스에서 작업할 수 있습니다. 코드 베이스가 플랫폼 간 기반인 경우 Visual Studio 내에서 Windows와 Linux를 모두 대상으로 할 수 있습니다.

이 항목에서는 Visual Studio의 CMake 지원에 대한 기본 지식이 있다고 가정합니다. 자세한 내용은 [Visual C++용 CMake 도구](../ide/cmake-tools-for-visual-cpp.md)를 참조하세요. CMake 자체에 대한 자세한 내용은 [CMake를 사용하여 소프트웨어 빌드, 테스트 및 패키지](https://cmake.org/)를 참조하세요.

> [!NOTE]  
> Visual Studio에서 CMake가 지원되려면 CMake 3.8에 도입된 서버 모드 지원이 필요합니다. 패키지 관리자가 이전 버전의 CMake를 제공하는 경우 [소스로 CMake를 빌드](#build-a-supported-cmake release-from-source)하거나 공식 [CMake 다운로드 페이지](https://cmake.org/download/)에서 다운로드하여 해결할 수 있습니다. Visual Studio의 [CMake 대상 보기](https://blogs.msdn.microsoft.com/vcblog/2018/04/09/cmake-support-in-visual-studio-targets-view-single-file-compilation-and-cache-generation-settings/) 창에서 지원하는 Microsoft 제공 CMake 변형은 [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases)에서 미리 작성된 최신 이진 파일을 다운로드합니다.

## <a name="open-a-folder"></a>폴더 열기

시작하려면 주 메뉴에서 **파일** > **열기** > **폴더**를 선택하거나 명령줄에서 `devenv.exe <foldername>`을 입력합니다. 열린 폴더에는 소스 코드와 함께 CMakeLists.txt 파일이 있어야 합니다.
다음 예제에서는 간단한 CMakeLists.txt 파일과 .cpp 파일을 보여 줍니다.

```cpp
// hello.cpp

#include <iostream>

int main(int argc, char* argv[])
{
    std::cout << "Hello from Linux CMake" << std::endl;
}
```

CMakeLists.txt:

```cmd
project (hello-cmake)
add_executable(hello-cmake hello.cpp)
```

## <a name="choose-a-linux-target"></a>Linux 대상 선택

폴더를 여는 즉시 Visual Studio에서 CMakeLists.txt 파일을 구문 분석하고 **x86-Debug**의 Windows 대상을 지정합니다. Linux를 대상으로 지정하려면 프로젝트 설정을 **Linux-Debug** 또는 **Linux-Release**로 변경합니다.

기본적으로 Visual Studio는 **도구** > **옵션** > **플랫폼 간** > **연결 관리자** 아래에 있는 목록에서 첫 번째 원격 시스템을 선택합니다. 원격 연결이 발견되지 않으면 만들라는 메시지가 표시됩니다.

Linux 대상을 지정하면 Linux 컴퓨터에 소스가 복사됩니다. 그런 다음 Linux 컴퓨터에서 CMake가 실행되어 프로젝트에 대한 CMake 캐시가 생성됩니다.

![Linux에서 CMake 캐시 생성](media/cmake-linux-1.png "Linux에서 CMake 캐시 생성")

**Visual Studio 2017 버전 15.7 이상:**  
원격 헤더에 IntelliSense 지원을 제공하기 위해 Visual Studio는 로컬 Windows 컴퓨터의 디렉터리에 IntelliSense를 자동으로 복사합니다. 자세한 내용은 [원격 헤더를 위한 IntelliSense](configure-a-linux-project.md#remote_intellisense)를 참조하세요.

## <a name="debug-the-project"></a>프로젝트 디버그

원격 시스템에서 코드를 디버그하려면 중단점을 설정하고, 프로젝트 설정 옆의 도구 모음 메뉴에서 CMake 대상을 시작 항목으로 선택하고, 도구 모음에서 **&#x23f5; 시작**을 선택하거나 F5 키를 누릅니다.

프로그램의 명령줄 인수를 사용자 지정하려면 **솔루션 탐색기**에서 실행 파일을 마우스 오른쪽 단추로 클릭하고 **디버그 및 시작 설정**을 선택합니다. 그러면 프로그램에 대한 정보가 들어 있는 launch.vs.json 구성 파일이 열리거나 만들어집니다. 추가 인수를 지정하려면 `args` JSON 배열에 추가합니다. 자세한 내용은 [Visual C++의 폴더 열기 프로젝트](https://docs.microsoft.com/en-us/cpp/ide/non-msbuild-projects)를 참조하세요.

## <a name="configure-cmake-settings-for-linux"></a>Linux용 CMake 설정 구성

기본 CMake 설정을 변경하려면 주 메뉴에서 **CMake | CMake 설정 변경 | CMakeLists.txt**를 선택하거나 **솔루션 탐색기**에서 CMakeSettings.txt를 마우스 오른쪽 단추로 클릭하고 **CMake 설정 변경**을 선택합니다. 그러면 Visual Studio에서 프로젝트 설정 메뉴 항목에 나열된 기본 구성으로 채워진 `CMakeSettings.json`이라는 폴더에 새 파일을 만듭니다. 다음 예제에서는 이전 코드 예제에 기반을 둔 Linux-Debug에 대한 기본 구성을 보여 줍니다.

```json
{
      "name": "Linux-Debug",
      "generator": "Unix Makefiles",
      "remoteMachineName": "${defaultRemoteMachineName}",
      "configurationType": "Debug",
      "remoteCMakeListsRoot": "/var/tmp/src/${workspaceHash}/${name}",
      "cmakeExecutable": "/usr/local/bin/cmake",
      "buildRoot": "${env.LOCALAPPDATA}\\CMakeBuilds\\${workspaceHash}\\build\\${name}",
      "remoteBuildRoot": "/var/tmp/build/${workspaceHash}/build/${name}",
      "remoteCopySources": true,
      "remoteCopySourcesOutputVerbosity": "Normal",
      "remoteCopySourcesConcurrentCopies": "10",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "",
      "ctestCommandArgs": "",
      "inheritEnvironments": [ "linux-x64" ]
}
```

`name` 값은 원하는 값으로 설정할 수 있습니다. `remoteMachineName` 값은 원격 시스템이 여러 개 있을 경우 대상으로 지정할 항목을 지정합니다. 이 필드에는 올바른 시스템을 선택할 수 있도록 IntelliSense가 활성화됩니다. `remoteCMakeListsRoot` 필드는 원격 시스템에서 프로젝트 소스가 복사될 위치를 지정합니다. `remoteBuildRoot` 필드는 원격 시스템에서 빌드 출력이 생성될 위치입니다. 또한 해당 출력은 `buildRoot`로 지정된 위치에 로컬로 복사됩니다.

## <a name="build-a-supported-cmake-release-from-source"></a>소스로 지원되는 CMake 릴리스 빌드

Linux 컴퓨터에 필요한 CMake의 최소 버전은 3.8이며, 서버 모드도 지원해야 합니다. 이를 확인하려면 이 명령을 실행합니다.

```cmd
cmake --version
```

서버 모드가 활성화되었는지 확인하려면 다음을 실행합니다.

```cmd
cmake -E capabilities
```

출력에서 **"serverMode":true**를 찾습니다. 아래에 설명된 대로 소스로 CMake를 컴파일하는 경우에도 완료 후 기능을 확인해야 합니다. Linux 컴퓨터에 서버 모드가 활성화되지 못하게 하는 제한 사항이 있을 수 있습니다.

Linux 시스템용 셸에서 소스로 CMake 빌드를 시작하려면 패키지 관리자가 최신 상태이고 사용 가능한 git 및 cmake가 있는지 확인해야 합니다.

먼저 Visual Studio의 CMake 지원에 대한 포크를 관리하는 [Microsoft CMake 리포지토리](https://github.com/Microsoft/CMake) 에서 CMake 소스를 복제합니다.

```cmd
sudo apt-get update
sudo apt-get install -y git cmake
git clone https://github.com/Microsoft/CMake.git
cd CMake
```

다음으로, CMake의 현재 릴리스를 빌드하고 /usr/local/bin에 설치하려면 다음 명령을 실행합니다.

```cmd
mkdir out
cd out
cmake ../
make
sudo make install
```

그런 다음, 이 명령을 실행하여 버전이 3.8 이상이고 서버 모드가 활성화되어 있는지 확인합니다.

```cmd
/usr/local/bin/cmake –version
cmake -E capabilities
```

## <a name="see-also"></a>참고 항목

[프로젝트 속성 사용](../ide/working-with-project-properties.md)  
[Visual C++용 CMake 도구](../ide/cmake-tools-for-visual-cpp.md)  

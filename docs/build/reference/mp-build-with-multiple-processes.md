---
title: /MP (여러 프로세스로 빌드) | Microsoft Docs
ms.custom: ''
ms.date: 02/22/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.MultiProcessorCompilation
dev_langs:
- C++
helpviewer_keywords:
- -MP compiler option (C++)
- /MP compiler option (C++)
- MP compiler option (C++)
- cl.exe compiler, multi-process build
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 29f7fd00a9d24b1941830690633befc75c39eb32
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379122"
---
# <a name="mp-build-with-multiple-processes"></a>/MP(여러 프로세스로 빌드)

**/MP** 옵션은 명령줄에서 소스 파일을 컴파일하는 데 걸리는 총 시간을 줄일 수 있습니다. **/MP** 옵션을 사용하면 컴파일러는 별도의 프로세스에서 각각 하나 이상의 자체 복사본을 만듭니다. 그런 다음 이러한 복사본이 소스 파일을 동시에 컴파일합니다. 따라서 소스 파일을 빌드하는 총 시간을 크게 줄일 수 있습니다.

## <a name="syntax"></a>구문

> **/MP**[*processMax*]

## <a name="arguments"></a>인수

*processMax*<br/>
(선택 사항) 컴파일러에서 만들 수 있는 프로세스의 최대 수입니다.

*processMax* 인수는 1에서 65536 사이 사이 여야 합니다. 그렇지 않으면 컴파일러는 경고 메시지 **D9014**, 무시는 *processMax* 인수를 최대 프로세스 수는 1을 가정 합니다.

생략 하면는 *processMax* 컴파일러의 수를 검색 인수를 [유효 프로세서](#effective_processors) 운영 체제에서 컴퓨터에 각 프로세서에 대 한 프로세스를 만듭니다.

## <a name="remarks"></a>설명

**/MP** 컴파일러 옵션은 많은 파일을 컴파일할 때 빌드 시간을 상당히 줄일 수 있습니다. 빌드 시간을 향상 시키려면 컴파일러 최대 만듭니다 *processMax* 자체의 복사한 다음 해당 복사본을 사용 하 여 동시에 소스 파일을 컴파일할 수 있습니다. **/MP** 옵션은 링크 또는 링크 시간 코드 생성이 아니라 컴파일에 적용됩니다. 기본적으로 **/MP** 옵션은 해제되어 있습니다.

빌드 시간의 향상 정도는 컴퓨터에 있는 프로세서의 수, 컴파일할 파일의 수, 시스템 리소스(예: I/O 용량)의 가용성에 따라 달라집니다. 특정 프로젝트 빌드를 위한 최적의 설정을 알아보려면 **/MP** 옵션으로 실험해 보세요. 결정을 내리는 데 도움이 필요하면 [지침](#guidelines)을 참조하세요.

## <a name="incompatible-options-and-language-features"></a>호환되지 않는 옵션 및 언어 기능

**/MP** 옵션은 일부 컴파일러 옵션 및 언어 기능과 호환되지 않습니다. 사용 하는 호환 되지 않는 컴파일러 옵션을 사용 하는 경우는 **/MP** 옵션을 컴파일러 경고가 발생 **D9030** 무시는 **/MP** 옵션입니다. 호환 되지 않는 언어 기능을 사용 하는 경우 컴파일러가 오류 [c 2813](../../error-messages/compiler-errors-2/compiler-error-c2813.md) 종료 하거나 현재 컴파일러 경고 수준 옵션에 따라 계속 합니다.

> [!NOTE]
> 대부분의 옵션은 호환되지 않습니다. 이러한 옵션이 허용되는 경우 동시 실행 컴파일러는 콘솔 또는 특정 파일에 동시에 출력을 작성해야 하기 때문입니다. 그 결과 출력이 뒤섞이거나 알 수 없는 상태가 됩니다. 경우에 따라, 옵션을 조합하는 경우 성능이 저하될 수 있습니다.

다음 표에서는 **/MP** 옵션과 호환되지 않는 컴파일러 옵션 및 언어 기능을 보여 줍니다.

|옵션 또는 언어 기능|설명|
|--------------------------------|-----------------|
|[#import](../../preprocessor/hash-import-directive-cpp.md) 전처리기 지시문|형식 라이브러리의 형식을 C++ 클래스로 변환한 다음 헤더 파일에 이러한 클래스를 기록합니다.|
|[/E](../../build/reference/e-preprocess-to-stdout.md), [/EP](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)|전처리기 출력을 표준 출력에 복사합니다(**stdout**).|
|[/Gm](../../build/reference/gm-enable-minimal-rebuild.md)|증분 다시 빌드를 사용합니다.|
|[/showIncludes](../../build/reference/showincludes-list-include-files.md)|포함 파일의 목록을 표준 오류에 기록합니다(**stderr**).|
|[/Yc](../../build/reference/yc-create-precompiled-header-file.md)|미리 컴파일된 헤더 파일을 만듭니다.|

## <a name="diagnostic-messages"></a>진단 메시지

**/MP** 옵션과 호환되지 않는 옵션 또는 언어 기능을 지정하면 진단 메시지가 표시됩니다. 다음 표에서는 컴파일러의 메시지 및 동작을 보여 줍니다.

|진단 메시지|설명|컴파일러 동작|
|------------------------|-----------------|-----------------------|
|**C2813**|**#import** 지시문은 **/MP** 옵션과 호환되지 않습니다.|[컴파일러 경고 수준](../../build/reference/compiler-option-warning-level.md) 옵션에서 달리 지정하지 않는 한 컴파일이 종료됩니다.|
|**D9014**|에 잘못 된 값이 지정 된 *processMax* 인수입니다.|컴파일러는 잘못된 값을 무시하고 값을 1이라고 가정합니다.|
|**D9030**|지정한 옵션이 **/MP**와 호환되지 않습니다.|컴파일러는 **/MP** 옵션을 무시합니다.|

## <a name="guidelines"></a> 지침

### <a name="measure-performance"></a>성능 측정

총 빌드 시간을 사용하여 성능을 측정합니다. 실제 시계로 빌드 시간을 측정할 수도 있고, 빌드의 시작과 중지 간 차이를 계산하는 소프트웨어를 사용할 수도 있습니다. 컴퓨터에 여러 프로세서가 있는 경우 실제 시계가 소프트웨어 시간 측정보다 더 정확한 결과를 보여줄 수 있습니다.

### <a name="effective_processors"></a> Effective Processors

하나 이상의 가상 프로세서를 라 하 고 있을 수 *유효 프로세서*, 각 해당 실제 프로세서에 대 한 합니다. 각각의 실제 프로세서에는 하나 이상의 코어가 있을 수 있으며, 운영 체제가 코어에 대한 하이퍼스레딩을 사용하도록 설정한 경우 각 코어는 두 개의 가상 프로세서로 나타납니다.

예를 들어 컴퓨터에 1개의 코어를 포함하는 실제 프로세서가 하나 있고 하이퍼스레딩이 사용되지 않으면 유효 프로세서는 하나입니다. 반면, 컴퓨터에 각각 2개의 코어를 포함하는 실제 프로세서가 2개 있고 모든 코어에서 하이퍼스레딩이 사용되면 유효 프로세서는 8개입니다. 즉, (유효 프로세서가 8) (실제 프로세서) = (실제 프로세서당 코어 2 개) x x (유효 프로세서에 따라 하이퍼스레딩).

생략 하면는 *processMax* 인수에는 **/MP** 옵션을 컴파일러 유효 프로세서 수에서 운영 체제를 가져오고 다음 유효 프로세서당 개의 프로세스를 만듭니다. 그러나 컴파일러는 어떤 프로세스가 특정 프로세서에서 실행될지는 보장할 수 없습니다. 이 결정은 운영 체제가 내립니다.

### <a name="number-of-processes"></a>프로세스 수

컴파일러는 소스 파일을 컴파일할 때 사용 할 프로세스의 수를 계산합니다. 이 값은 명령줄에서 지정한 소스 파일의 수와 **/MP** 옵션을 이용해 명시적 또는 암시적으로 지정한 프로세스의 수 중에서 더 작은 수입니다. 제공 하는 경우 프로세스의 최대 수를 명시적으로 설정할 수는 *processMax* 의 인수는 **/MP** 옵션입니다. 또는 것과 같은 유효 프로세서의 수는 컴퓨터에서 생략 하면 기본값을 사용 하는 *processMax* 인수입니다.

예를 들어, 다음 명령줄을 지정한다고 가정해 보겠습니다.

`cl /MP7 a.cpp b.cpp c.cpp d.cpp e.cpp`

이 경우 컴파일러는 5개의 프로세스를 사용합니다. 5개의 소스 파일과 최대 7개의 프로세스 중 더 적은 수가 5이기 때문입니다. 또는 컴퓨터에 유효 프로세서가 2개 있으며 다음 명령줄을 지정한다고 가정해 보겠습니다.

`cl /MP a.cpp b.cpp c.cpp`

이 경우 운영 체제는 프로세서가 2개라고 보고합니다. 따라서 컴파일러는 계산에서 2개의 프로세서를 사용합니다. 결과적으로 컴파일러는 2개의 프로세서로 빌드를 실행합니다. 2개의 프로세스와 3개의 소스 파일 중 더 적은 수가 2이기 때문입니다.

### <a name="source-files-and-build-order"></a>소스 파일 및 빌드 순서

명령줄에 표시된 것과 동일한 순서로 소스 파일이 컴파일되지 않을 수 있습니다. 컴파일러는 컴파일러의 복사본을 포함하는 프로세스의 집합을 만들지만, 운영 체제는 각 프로세스의 실행 시기를 예약합니다. 따라서 소스 파일이 특정 순서로 컴파일될 것임을 보장할 수 없습니다.

프로세스를 컴파일에 사용할 수 있을 때 소스 파일이 컴파일됩니다. 프로세스보다 파일이 더 많은 경우 첫 번째 파일 집합이 사용 가능한 프로세스에 의해 컴파일됩니다. 프로세스가 이전 파일의 처리를 완료하고 나머지 파일 중 하나에 대해 작업할 준비가 될 때 나머지 파일이 처리됩니다.

명령줄에서 같은 소스 파일을 여러 번 지정하지 마세요. 예를 들어, 특정 도구가 프로젝트의 종속성 정보를 기반으로 하는 [makefile](../../build/contents-of-a-makefile.md) 을 자동으로 만들 경우 이러한 일이 발생할 수 있습니다. **/MP** 옵션을 지정하지 않는 경우, 컴파일러는 파일 목록을 순차적으로 처리하고 나타나는 각 파일을 다시 컴파일합니다. 그러나 **/MP** 옵션을 지정하는 경우, 서로 다른 컴파일러가 동시에 같은 파일을 컴파일할 수 있습니다. 따라서 서로 다른 컴파일러가 동시에 동일한 출력 파일에 쓰려고 시도합니다. 하나의 컴파일러가 출력 파일에 대한 배타적인 쓰기 권한을 획득하고 성공하면, 나머지 컴파일러는 파일 액세스 오류와 함께 실패하게 됩니다.

### <a name="using-type-libraries-import"></a>형식 라이브러리 사용(#import)

컴파일러는 [#import](../../preprocessor/hash-import-directive-cpp.md) 지시문을 **/MP** 스위치와 사용하는 것을 지원하지 않습니다. 이 문제를 해결하려면 가능한 경우 다음 단계를 수행하세요.

- 여러 소스 파일에 있는 모든 `#import` 지시문을 하나 이상의 파일로 이동한 다음, **/MP** 옵션 없이 해당 파일을 컴파일합니다. 그 결과 헤더 파일의 집합이 생성됩니다.

- 생성된 헤더를 지정하는 [#include](../../preprocessor/hash-include-directive-c-cpp.md) 지시문을 나머지 소스 파일에 삽입하고, **/MP** 옵션을 사용하여 나머지 소스 파일을 컴파일합니다.

### <a name="visual-studio-project-settings"></a>Visual Studio 프로젝트 설정

#### <a name="the-msbuildexe-tool"></a>MSBUILD.exe 도구

[!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] 는 [MSBuild.exe](/visualstudio/msbuild/msbuild-reference) 도구를 사용하여 솔루션 및 프로젝트를 빌드합니다. **/maxcpucount:**_번호_ (또는 **/m:**_번호_) MSBuild.exe 도구의 명령줄 옵션에서 여러 프로젝트를 빌드할 수는 같은 시간입니다. **/MP** 컴파일러 옵션은 여러 컴파일 단위를 동시에 빌드할 수 있습니다. 응용 프로그램에 대해 적절한 경우 **/MP** 와 **/maxcpucount**중 하나 또는 둘 모두를 사용하여 솔루션의 빌드 시간을 개선할 수 있습니다.

솔루션의 빌드 시간은 부분적으로 빌드를 수행 하는 프로세스의 수에 따라 다릅니다. *번호* 의 인수는 [/maxcpucount](/visualstudio/msbuild/msbuild-command-line-reference) MSBuild 옵션에 동시에 빌드할 프로젝트의 최대 수를 지정 합니다. 마찬가지로,는 *processMax* 의 인수는 **/MP** 컴파일러 옵션 컴파일 단위 동시에 빌드할 수의 최대 수를 지정 합니다. 경우는 **/maxcpucount** 옵션 지정 *P* 프로젝트 및 **/MP** 옵션 지정 *C* 프로세스, 최대 *P*  x *C* 프로세스를 동시에 실행 합니다.

 MSBuild를 사용할 것인지 결정 하기 위한 지침은 또는 **/MP** 기술은 다음과 같습니다.

- 각 프로젝트의 몇 가지 파일은 여러 프로젝트에 있는 경우 MSBuild 도구를 사용 합니다.

- 프로젝트 수는 적고 각 프로젝트의 파일 수는 많은 경우 **/MP** 옵션을 사용합니다.

- 두 MSBuild를 사용 하 여 프로젝트와 프로젝트 당 파일 수는 균형을 하는 경우 및 **/MP**합니다. 처음에는 **/maxcpucount** 옵션을 빌드할 프로젝트의 수로 설정하고, **/MP** 옵션을 컴퓨터의 프로세서 수로 설정합니다. 성능을 측정하고 최상의 결과를 얻을 수 있도록 설정을 조정합니다. 총 빌드 시간에 만족할 때까지 위 과정을 반복합니다.

#### <a name="the-gm-compiler-option"></a>/Gm 컴파일러 옵션

기본적으로 프로젝트 빌드는 디버그 빌드에 대해서는 **/Gm** 컴파일러 옵션(증분 빌드)을 사용하고 릴리스 빌드에 대해서는 사용하지 않습니다. 따라서 **/MP** 컴파일러 옵션은 기본 **/Gm** 컴파일러 옵션과 충돌하기 때문에 디버그 빌드에서 자동으로 사용되지 않습니다.

## <a name="see-also"></a>참고자료

[#import 지시문](../../preprocessor/hash-import-directive-cpp.md)<br/>
[명령줄 참조](/visualstudio/msbuild/msbuild-command-line-reference)<br/>
[/Zf(더 빠른 PDB 생성)](zf.md)<br/>

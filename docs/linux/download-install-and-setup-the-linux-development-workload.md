---
title: Visual Studio에서 C++ Linux 워크로드 설치 | Microsoft Docs
description: Visual Studio에서 C++에 대한 Linux 워크로드를 다운로드하고, 설치하고, 설정하는 방법을 설명합니다.
ms.custom: ''
ms.date: 07/20/2018
ms.technology:
- cpp-linux
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: e11b40b2-f3a4-4f06-b788-73334d58dfd9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: e33b9ac72ca7691ccbb80a9a30349d3a1e31e194
ms.sourcegitcommit: 7eadb968405bcb92ffa505e3ad8ac73483e59685
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2018
ms.locfileid: "39207561"
---
# <a name="download-install-and-setup-the-linux-workload"></a>Linux 작업 다운로드, 설치, 설정

Visual Studio IDE를 사용하여 Linux에서 C++ 프로젝트를 만들고 디버깅하려면 **C++를 사용한 Linux 개발** 워크로드를 설치해야 합니다.

## <a name="visual-studio-setup"></a>Visual Studio 설치
1. Visual Studio 설치 관리자를 시작하고 **C++를 사용한 Linux 개발** 작업을 선택합니다.

   ![Linux 개발용 Visual C++ 확장](media/linuxworkload.png)

2. **설치**를 클릭하여 설치를 계속합니다.

## <a name="linux-setup"></a>Linux 설치
대상 Linux 컴퓨터에 **openssh-server**, **g++**, **gdb** 및 **gdbserver**가 설치되어 있고 ssh 데몬이 실행되고 있어야 합니다.  이러한 항목이 없다면 다음과 같이 설치할 수 있습니다.
 
1. Linux 컴퓨터의 셸 프롬프트에서 다음을 실행합니다.

   `sudo apt-get install openssh-server g++ gdb gdbserver`

   sudo 명령 때문에 루트 암호를 입력하라는 메시지가 표시될 수 있습니다.  메시지가 표시되면 루트 암호를 입력하고 계속합니다.  완료되면 이러한 서비스와 도구가 설치됩니다.

1. 다음을 실행하여 ssh 서비스가 Linux 컴퓨터에서 실행되고 있는지 확인합니다.

   `sudo service ssh start`
   
   그러면 서비스가 시작되고 백그라운드에서 실행되므로 연결을 허용할 준비가 됩니다.

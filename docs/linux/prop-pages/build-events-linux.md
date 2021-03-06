---
title: 원격 빌드 이벤트(Linux C++) | Microsoft Docs
ms.custom: ''
ms.date: 9/26/2017
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: 165d3690-5bd8-4b0b-bc66-8b699d85a61b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: 38c036bf747115823b853d0d66077f4402a7f7ea
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33338408"
---
# <a name="build-event-properties-linux-c"></a>빌드 이벤트 속성(Linux C++) 

## <a name="pre-build-event"></a>빌드 전 이벤트

속성 | 설명
--- | ---
명령줄 | 빌드 전 이벤트 도구가 실행할 명령줄을 지정합니다.
설명 | 빌드 전 이벤트 도구가 표시할 설명을 지정합니다.
빌드에 사용 | 이 빌드 이벤트가 현재 구성의 빌드에서 제외되는지 여부를 지정합니다.
복사할 추가 파일 | 원격 시스템에 복사할 추가 파일을 지정합니다. 필요에 따라 구문(예: fulllocalpath1:=fullremotepath1;fulllocalpath2:=fullremotepath2)을 사용하여 로컬-원격 매핑 쌍으로 목록을 제공할 수 있습니다. 이 경우 로컬 파일이 원격 시스템의 지정된 원격 위치에 복사될 수 있습니다.

## <a name="pre-link-event"></a>링크 전 이벤트

속성 | 설명
--- | ---
명령줄 | 링크 전 이벤트 도구가 실행하는 명령줄을 지정합니다.
설명 | 링크 전 이벤트 도구가 표시할 설명을 지정합니다.
빌드에 사용 | 이 빌드 이벤트가 현재 구성의 빌드에서 제외되는지 여부를 지정합니다.
복사할 추가 파일 | 원격 시스템에 복사할 추가 파일을 지정합니다. 필요에 따라 구문(예: fulllocalpath1:=fullremotepath1;fulllocalpath2:=fullremotepath2)을 사용하여 로컬-원격 매핑 쌍으로 목록을 제공할 수 있습니다. 이 경우 로컬 파일이 원격 시스템의 지정된 원격 위치에 복사될 수 있습니다.

## <a name="post-build-event"></a>빌드 후 이벤트

속성 | 설명
--- | ---
명령줄 | 빌드 후 이벤트 도구가 실행하는 명령줄을 지정합니다.
설명 | 빌드 후 이벤트 도구가 표시할 설명을 지정합니다.
빌드에 사용 | 이 빌드 이벤트가 현재 구성의 빌드에서 제외되는지 여부를 지정합니다.
복사할 추가 파일 | 원격 시스템에 복사할 추가 파일을 지정합니다. 필요에 따라 구문(예: fulllocalpath1:=fullremotepath1;fulllocalpath2:=fullremotepath2)을 사용하여 로컬-원격 매핑 쌍으로 목록을 제공할 수 있습니다. 이 경우 로컬 파일이 원격 시스템의 지정된 원격 위치에 복사될 수 있습니다.

## <a name="remote-pre-build-event"></a>원격 빌드 전 이벤트

속성 | 설명
--- | ---
명령줄 | 빌드 전 이벤트 도구가 원격 시스템에서 실행할 명령줄을 지정합니다.
설명 | 빌드 전 이벤트 도구가 표시할 설명을 지정합니다.
빌드에 사용 | 이 빌드 이벤트가 현재 구성의 빌드에서 제외되는지 여부를 지정합니다.
복사할 추가 파일 | 원격 시스템에서 복사할 추가 파일을 지정합니다. 필요에 따라 구문(예: fullremotepath1:=fulllocalpath1;fullremotepath2:=fulllocalpath2)을 사용하여 원격-로컬 매핑 쌍으로 목록을 제공할 수 있습니다. 이 경우 원격 파일이 로컬 컴퓨터의 지정된 위치에 복사될 수 있습니다.

## <a name="remote-pre-link-event"></a>원격 링크 전 이벤트

속성 | 설명
--- | ---
명령줄 | 링크 전 이벤트 도구가 원격 시스템에서 실행할 명령줄을 지정합니다.
설명 | 링크 전 이벤트 도구가 표시할 설명을 지정합니다.
빌드에 사용 | 이 빌드 이벤트가 현재 구성의 빌드에서 제외되는지 여부를 지정합니다.
복사할 추가 파일 | 원격 시스템에서 복사할 추가 파일을 지정합니다. 필요에 따라 구문(예: fullremotepath1:=fulllocalpath1;fullremotepath2:=fulllocalpath2)을 사용하여 원격-로컬 매핑 쌍으로 목록을 제공할 수 있습니다. 이 경우 원격 파일이 로컬 컴퓨터의 지정된 위치에 복사될 수 있습니다.

## <a name="remote-post-build-event"></a>원격 빌드 후 이벤트

속성 | 설명
--- | ---
명령줄 | 빌드 후 이벤트 도구가 원격 시스템에서 실행할 명령줄을 지정합니다.
설명 | 빌드 후 이벤트 도구가 표시할 설명을 지정합니다.
빌드에 사용 | 이 빌드 이벤트가 현재 구성의 빌드에서 제외되는지 여부를 지정합니다.
복사할 추가 파일 | 원격 시스템에서 복사할 추가 파일을 지정합니다. 필요에 따라 구문(예: fullremotepath1:=fulllocalpath1;fullremotepath2:=fulllocalpath2)을 사용하여 원격-로컬 매핑 쌍으로 목록을 제공할 수 있습니다. 이 경우 원격 파일이 로컬 컴퓨터의 지정된 위치에 복사될 수 있습니다.

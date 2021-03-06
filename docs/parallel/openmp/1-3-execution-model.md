---
title: 1.3 실행 모델 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 85ae8bc4-5bf0-45e0-a45f-02de9adaf716
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0acdd7a5d9f2dcb58850254281b5c18fd0d1123c
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33687896"
---
# <a name="13-execution-model"></a>1.3 실행 모델
OpenMP 병렬 실행 분기-조인 모델을 사용합니다. 이 분기-조인 모델 하는 다양 한 문제를 해결 하는 데 유용 하지만 다소 큰 배열 기반 응용 프로그램에 대 한 맞는 합니다. OpenMP 지원 프로그램을 실행 됩니다 올바르게 둘 다 병렬 프로그램 (다중 스레드 실행 및 전체 OpenMP 지원 라이브러리) 하 고 순차적 프로그램 (무시 지시문 및 간단한 OpenMP 스텁 라이브러리)로 것뿐입니다. 그러나 불가능 하 고 순차적으로 실행 하는 경우 올바르게 동작 하지 않는 하는 프로그램을 개발 허용 합니다. 또한 서로 다른 수준의 병렬 처리 수준 수치 연산의 연결의 변경으로 인해 다른 숫자 결과 발생할 수 있습니다. 예를 들어 직렬 더하기 감소 병렬 감소 보다 추가 연결의 다른 패턴을 있을 수 있습니다. 이러한 서로 다른 연결 부동 소수점 더하기의 결과 변경할 수 있습니다.  
  
 OpenMP C/c + + API로 작성 된 프로그램 호출 실행의 단일 스레드로 실행이 시작 되는 *스레드 마스터*합니다. 첫 번째는 병렬 구문 발견 될 때까지 직렬 지역에서 마스터 스레드가 실행 합니다. OpenMP C/c + + API에는 **병렬** 병렬 구문을 구성 하는 지시문입니다. 병렬 구문에 오류가 발생 하면 마스터 스레드에 스레드 팀 만들고 있는 마스터는 팀의 마스터 됩니다. 팀에서 각 스레드에 작업 공유 생성자를 제외 하 고 병렬 영역의 동적 범위에서 문을 실행 합니다. 작업 공유 구문 동일한 순서로 팀의 모든 스레드에서 발생 해야 하 고 스레드 중 하나 이상의 관련된 구조화 된 블록 내에서 문이 실행 되도록 합니다. 없이 작업 공유 생성자의 끝에 암시적 장벽은 `nowait` 절이 팀의 모든 스레드에서 실행 됩니다.  
  
 스레드가 공유 개체를 수정할 경우 실행 환경 뿐만 아니라 프로그램에 다른 스레드에서 적용 됩니다. 수정 될 수는 개체를 선언 하는 경우에 완료 되는 다음 시퀀스 위치에서 다른 스레드 중 하나의 관점에서 (기본 언어에 정의 됨) 처럼 되도록 보장 합니다. 그렇지 않으면 수정을 먼저 스레드는 수정 후 완료 되도록 보장 하 고 다음 (또는 동시) 다른 스레드에서 발생는 **플러시** (암시적 또는 명시적) 개체를 지정 하는 지시문. 경우는 **플러시** 다른 OpenMP 지시문에 의해 암시 된 지시문 부작용의 원하는 순서를 보장 하지 않는 것은 프로그래머의 책임을 추가 하 고 명시적인 제공,  **플러시** 지시문입니다.  
  
 병렬 구문으로 완료 되 면 팀의 스레드는 암시적 장벽에 동기화 하 고 마스터 스레드에서만 실행을 계속 합니다. 임의 개수의 병렬 구문 한 프로그램에서 지정할 수 있습니다. 결과적으로,는 프로그램 분기 및 실행 하는 동안 여러 번 가입 될 수 있습니다.  
  
 OpenMP C/c + + API 프로그래머가 지시문 병렬 구문 내에서 호출 된 함수에서 사용할 수 있습니다. 병렬 구문 어휘 범위에 표시 되지 않지만 동적 범위 내에 있을 수 있는 지시문 라고 *고아* 지시문입니다. 분리 된 지시문 프로그래머 순차적 프로그램을 최소한의 변경 내용으로 동시에 해당 프로그램의 주요 부분을 실행 하는 기능을 제공 합니다. 이 기능을 통해 사용자는 프로그램 호출 트리의 최상위 수준에서 병렬 구문 코드 및 지시문을 사용 하 여 호출된 되는 함수 중 하나에서 실행을 제어 하 수 있습니다.  
  
 C 및 c + +에 대 한 동기화 되지 않은 호출 출력 같은 파일에 쓰는 함수는 비결 정적 순서로 표시 되는 서로 다른 스레드에 의해 기록 되는 데이터 출력에 발생할 수 있습니다. 마찬가지로, 같은 파일에서 읽는 함수에 입력에 대 한 동기화 되지 않은 호출 비결 정적 순서로 데이터를 읽을 수 있습니다. 동기화 되지 않은 I/O 사용 하 여 다른 파일을 액세스 하는 각 스레드는 I/O 함수의 직렬 실행와 동일한 결과 생성 합니다.
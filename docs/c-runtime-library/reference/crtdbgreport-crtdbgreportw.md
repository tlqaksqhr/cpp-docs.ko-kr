---
title: _CrtDbgReport, _CrtDbgReportW | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _CrtDbgReport
- _CrtDbgReportW
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- CrtDbgReport
- CrtDbgReportW
- _CrtDbgReportW
- _CrtDbgReport
dev_langs:
- C++
helpviewer_keywords:
- debug reporting
- _CrtDbgReport function
- CrtDbgReport function
- CrtDbgReportW function
- _CrtDbgReportW function
ms.assetid: 6e581fb6-f7fb-4716-9432-f0145d639ecc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 57290d2985036ea3df2863e175d742c819a3fe03
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32405063"
---
# <a name="crtdbgreport-crtdbgreportw"></a>_CrtDbgReport, _CrtDbgReportW

디버깅 메시지가 포함된 보고서를 생성하고 이 보고서를 가능한 대상 3개로 보냅니다(디버그 버전에만 해당).

## <a name="syntax"></a>구문

```C
int _CrtDbgReport(
   int reportType,
   const char *filename,
   int linenumber,
   const char *moduleName,
   const char *format [,
   argument] ...
);
int _CrtDbgReportW(
   int reportType,
   const wchar_t *filename,
   int linenumber,
   const wchar_t *moduleName,
   const wchar_t *format [,
   argument] ...
);
```

### <a name="parameters"></a>매개 변수

*reportType*<br/>
보고서 종류: **_CRT_WARN**, **_CRT_ERROR**, 및 **_CRT_ASSERT**합니다.

*filename*<br/>
Assert/report 발생 한 소스 파일의 이름에 대 한 포인터 또는 **NULL**합니다.

*linenumber*<br/>
Assert/report 발생 한 소스 파일의 줄 번호 또는 **NULL**합니다.

*moduleName*<br/>
어설션 또는 보고서가 발생한 모듈(.exe 또는 .dll)의 이름에 대한 포인터입니다.

*format*<br/>
사용자 메시지를 만드는 데 사용되는 형식 컨트롤 문자열에 대한 포인터입니다.

*argument*<br/>
사용 하는 선택적 대체 인수 *형식*합니다.

## <a name="return-value"></a>반환 값

모든 보고서 대상에 대 한 **_CrtDbgReport** 및 **_CrtDbgReportW** 오류가 발생 하는 경우 오류가 발생 한 경우-1과 0을 반환 합니다. 그러나 보고서 대상이 디버그 메시지 창이고 사용자가 **다시 시도** 단추를 클릭하면 이러한 함수는 1을 반환합니다. 사용자가 디버그 메시지 창에서 **중단** 단추를 클릭하면 이러한 함수가 즉시 중단되고 값을 반환하지 않습니다.

[_RPT, _RPTF](rpt-rptf-rptw-rptfw-macros.md) 매크로 호출을 디버그 **_CrtDbgReport** 보고서를 디버그를 생성 하려면. 이러한 매크로의 와이드 문자 버전으로 [_ASSERT, _ASSERTE](assert-asserte-assert-expr-macros.md), [_RPTW](rpt-rptf-rptw-rptfw-macros.md) 및 [_RPTFW](rpt-rptf-rptw-rptfw-macros.md)를 사용 하 여 **_CrtDbgReportW** 를 가 디버그 보고서를 생성 합니다. 때 **_CrtDbgReport** 또는 **_CrtDbgReportW** 1을 반환 타임 (JIT) 디버깅을 사용할 수 있는 경우 이러한 매크로 디버거를 시작 합니다.

## <a name="remarks"></a>설명

**_CrtDbgReport** 및 **_CrtDbgReportW** 3 가지 다른 대상에는 디버그 보고서를 보낼 수 있습니다: 디버그 보고서 파일, 디버그 모니터 (Visual Studio 디버거) 또는 디버그 메시지 창. 두 구성 함수인 [_CrtSetReportMode](crtsetreportmode.md)와 [_CrtSetReportFile](crtsetreportfile.md)은 각 보고서 형식의 대상을 지정하는 데 사용됩니다. 이러한 함수를 사용하면 각 보고서 형식의 보고 대상을 개별적으로 제어할 수 있습니다. 되도록 지정할 수는 예를 들어 한 *reportType* 의 **_CRT_WARN** 수만 디버그 모니터도 전송 하는 동안 한 *reportType* 의 **_CRT_ASSERT** 디버그 메시지 창이 고 사용자 지정 보고서 파일을 전송할 수 있습니다.

**_CrtDbgReportW** 의 와이드 문자 버전이 **_CrtDbgReport**합니다. 이 함수의 모든 출력 및 문자열 매개 변수는 와이드 문자열에 있습니다. 이 점을 제외하면 이 함수는 싱글바이트 문자 버전과 동일합니다.

**_CrtDbgReport** 및 **_CrtDbgReportW** 대체 하 여 디버그 보고서에 대 한 사용자 메시지를 만듭니다는 *인수*[**n**]는 인수*형식* 문자열에 의해 정의 된 동일한 규칙을 사용 하 여 **printf** 또는 **wprintf** 함수입니다. 이러한 함수는 디버그 보고서를 생성 및 현재 보고서 모드에 따라 대상을 결정 하 고 파일에 대해 정의 된 *reportType*합니다. 디버그 메시지 창에 보고서를 보낼 때의 *filename*, **lineNumber**, 및 *moduleName* 창에 표시 되는 정보에 포함 됩니다.

다음 표에서 보고서 모드 및 파일 및의 결과 동작에 대 한 사용 가능한 선택 항목 **_CrtDbgReport** 및 **_CrtDbgReportW**합니다. 이러한 옵션은 \<crtdbg.h>에서 비트 플래그로 정의되어 있습니다.

|보고서 모드|보고서 파일|**_CrtDbgReport**, **_CrtDbgReportW** 동작|
|-----------------|-----------------|------------------------------------------------|
|**_CRTDBG_MODE_DEBUG**|적용할 수 없음|Windows [OutputDebugString](http://msdn.microsoft.com/library/windows/desktop/aa363362.aspx) API를 사용하여 메시지를 작성합니다.|
|**_CRTDBG_MODE_WNDW**|적용할 수 없음|Windows [MessageBox](http://msdn.microsoft.com/library/windows/desktop/ms645505) API를 호출하여 **중단**, **다시 시도** 및 **무시** 단추와 함께 메시지를 표시하는 메시지 상자를 만듭니다. 사용자가 클릭 **중단**, **_CrtDbgReport** 또는 **_CrtDbgReport** 즉시 중단 됩니다. 사용자가 **다시 시도**를 클릭하면 1이 반환됩니다. 사용자가 클릭 **무시**, 실행이 계속 되 고 **_CrtDbgReport** 및 **_CrtDbgReportW** 0을 반환 합니다. 오류 조건이 있을 때 **무시**를 클릭하면 종종 "정의되지 않은 동작"이 발생할 수 있습니다.|
|**_CRTDBG_MODE_FILE**|**__HFILE**|메시지를 사용자가 제공한 씁니다 **처리**, Windows를 사용 하 여 [WriteFile](http://msdn.microsoft.com/library/windows/desktop/aa365747.aspx) API 및 파일 핸들의 유효성을 확인 하지 않으면 응용 프로그램은 보고서 파일을 열어 고 올바른 파일을 전달 하기 위한 핸들입니다.|
|**_CRTDBG_MODE_FILE**|**_CRTDBG_FILE_STDERR**|메시지를 씁니다 **stderr**합니다.|
|**_CRTDBG_MODE_FILE**|**_CRTDBG_FILE_STDOUT**|메시지를 씁니다 **stdout**합니다.|

보고서는 1개, 2개 또는 3개 대상으로 보내거나 아무 대상으로도 보내지 않을 수 있습니다. 보고서 모드 및 보고서 파일을 지정하는 방법에 대한 자세한 내용은 [_CrtSetReportMode](crtsetreportmode.md) 및 [_CrtSetReportFile](crtsetreportfile.md) 함수를 참조하세요. 디버그 매크로 및 보고 함수 사용에 대한 자세한 내용은 [보고서 매크로](/visualstudio/debugger/macros-for-reporting)를 참조하세요.

응용 프로그램에서 제공 된 것 보다 더 뛰어난 유연성이 필요한 경우 **_CrtDbgReport** 및 **_CrtDbgReportW**, 자체 보고 함수를 작성 하 고 C 런타임 라이브러리 보고에 연결할 수 있습니다 사용 하 여 메커니즘은 [_CrtSetReportHook](crtsetreporthook.md) 함수입니다.

## <a name="requirements"></a>요구 사항

|루틴|필수 헤더|
|-------------|---------------------|
|**_CrtDbgReport**|\<crtdbg.h>|
|**_CrtDbgReportW**|\<crtdbg.h>|

**_CrtDbgReport** 및 **_CrtDbgReportW** 는 Microsoft 확장입니다. 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

[C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)의 디버그 버전만 해당됩니다.

## <a name="example"></a>예제

```C
// crt_crtdbgreport.c
#include <crtdbg.h>

int main(int argc, char *argv[]) {
#ifdef _DEBUG
   _CrtDbgReport(_CRT_ASSERT, __FILE__, __LINE__, argv[0], NULL);
#endif
}
```

보고 함수 변경 방법의 예는 [crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2)를 참조하세요.

## <a name="see-also"></a>참고자료

[디버그 루틴](../../c-runtime-library/debug-routines.md)<br/>
[_CrtSetReportMode](crtsetreportmode.md)<br/>
[_CrtSetReportFile](crtsetreportfile.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[_DEBUG](../../c-runtime-library/debug.md)<br/>

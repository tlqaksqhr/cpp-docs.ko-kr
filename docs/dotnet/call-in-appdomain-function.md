---
title: call_in_appdomain 함수 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- call_in_appdomain
dev_langs:
- C++
helpviewer_keywords:
- call_in_appdomain function
ms.assetid: 9a1a5026-b76b-4cae-a3d4-29badeb9db9c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a8689254120416e5b2bf5de617fc3f3ef466abb1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33111288"
---
# <a name="callinappdomain-function"></a>call_in_appdomain 함수
지정 된 응용 프로그램 도메인에서 함수를 실행 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
template <typename ArgType1, ...typename ArgTypeN>  
void call_in_appdomain(  
   DWORD appdomainId,  
   void (*voidFunc)(ArgType1, ...ArgTypeN) [ ,  
   ArgType1 arg1,  
   ...  
   ArgTypeN argN ]  
);  
template <typename RetType, typename ArgType1, ...typename ArgTypeN>  
RetType call_in_appdomain(  
   DWORD appdomainId,  
   RetType (*nonvoidFunc)(ArgType1, ...ArgTypeN) [ ,  
   ArgType1 arg1,  
   ...  
   ArgTypeN argN ]  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `appdomainId`  
 함수를 호출 하는 appdomain 합니다.  
  
 `voidFunc`  
 에 대 한 포인터는 `void` N 매개 변수를 사용 하는 함수 (0 < = N < = 15).  
  
 `nonvoidFunc`  
 이외에 대 한 포인터`void` N 매개 변수를 사용 하는 함수 (0 < = N < = 15).  
  
 `arg1...argN`  
 0 ~ 15 매개 변수를 전달 하도록 `voidFunc` 또는 `nonvoidFunc` 다른 appdomain에서 합니다.  
  
## <a name="return-value"></a>반환 값  
 실행 결과 `voidFunc` 또는 `nonvoidFunc` 지정 된 응용 프로그램 도메인에 있습니다.  
  
## <a name="remarks"></a>설명  
 함수의 인수에 전달 된 `call_in_appdomain` CLR 형식 되지 않아야 합니다.  
  
## <a name="example"></a>예제  
  
```  
// msl_call_in_appdomain.cpp  
// compile with: /clr  
  
// Defines two functions: one takes a parameter and returns nothing,  
// the other takes no parameters and returns an int.  Calls both  
// functions in the default appdomain and in a newly-created  
// application domain using call_in_appdomain.  
  
#include <msclr\appdomain.h>  
  
using namespace System;  
using namespace msclr;  
  
void PrintCurrentDomainName( char* format )  
{  
   String^ s = gcnew String(format);  
   Console::WriteLine( s, AppDomain::CurrentDomain->FriendlyName );  
}  
  
int GetDomainId()  
{  
   return AppDomain::CurrentDomain->Id;  
}  
  
int main()  
{  
   AppDomain^ appDomain1 = AppDomain::CreateDomain( "First Domain" );  
  
   call_in_appdomain( AppDomain::CurrentDomain->Id,  
                   &PrintCurrentDomainName,  
                   (char*)"default appdomain: {0}" );  
   call_in_appdomain( appDomain1->Id,  
                   &PrintCurrentDomainName,  
                   (char*)"in appDomain1: {0}" );  
  
   int id;  
   id = call_in_appdomain( AppDomain::CurrentDomain->Id, &GetDomainId );  
   Console::WriteLine( "default appdomain id = {0}", id );  
   id = call_in_appdomain( appDomain1->Id, &GetDomainId );  
   Console::WriteLine( "appDomain1 id = {0}", id );  
}  
```  
  
## <a name="output"></a>출력  
  
```  
default appdomain: msl_call_in_appdomain.exe  
in appDomain1: First Domain  
default appdomain id = 1  
appDomain1 id = 2  
```  
  
## <a name="requirements"></a>요구 사항  
 **헤더 파일** \<msclr\appdomain.h >  
  
 **Namespace** msclr
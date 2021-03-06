---
title: 개인 (OpenMP) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- private
dev_langs:
- C++
helpviewer_keywords:
- private OpenMP clause
ms.assetid: 772904a2-1345-4562-90e6-eb4dc85aea1a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4af88f450ce6c77a6b0753917516719331199dfd
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33692680"
---
# <a name="private-openmp"></a>private (OpenMP)
각 스레드에 변수의 자체 인스턴스가 있어야 한다는 것을 지정 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
private(var)  
```  
  
## <a name="remarks"></a>설명  
 다음은 각 문자에 대한 설명입니다.  
  
 `var`  
 각 스레드에서 인스턴스를 사용 하는 변수입니다.  
  
## <a name="remarks"></a>설명  
 **개인** 다음과 같은 지시문에 적용 됩니다.  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [섹션](../../../parallel/openmp/reference/sections-openmp.md)  
  
-   [single](../../../parallel/openmp/reference/single.md)  
  
 자세한 내용은 참조 [개인 2.7.2.1](../../../parallel/openmp/2-7-2-1-private.md)합니다.  
  
## <a name="example"></a>예제  
  
```  
// openmp_private.c  
// compile with: /openmp  
#include <windows.h>  
#include <assert.h>  
#include <stdio.h>  
#include <omp.h>  
  
#define NUM_THREADS 4  
#define SLEEP_THREAD 1  
#define NUM_LOOPS 2  
  
enum Types {  
   ThreadPrivate,  
   Private,  
   FirstPrivate,  
   LastPrivate,  
   Shared,  
   MAX_TYPES  
};  
  
int nSave[NUM_THREADS][MAX_TYPES][NUM_LOOPS] = {{0}};  
int nThreadPrivate;  
  
#pragma omp threadprivate(nThreadPrivate)  
#pragma warning(disable:4700)  
  
int main() {  
   int nPrivate = NUM_THREADS;  
   int nFirstPrivate = NUM_THREADS;  
   int nLastPrivate = NUM_THREADS;  
   int nShared = NUM_THREADS;  
   int nRet = 0;  
   int i;  
   int j;  
   int nLoop = 0;  
  
   nThreadPrivate = NUM_THREADS;  
   printf_s("These are the variables before entry "  
           "into the parallel region.\n");  
   printf_s("nThreadPrivate = %d\n", nThreadPrivate);  
   printf_s("      nPrivate = %d\n", nPrivate);  
   printf_s(" nFirstPrivate = %d\n", nFirstPrivate);  
   printf_s("  nLastPrivate = %d\n", nLastPrivate);  
   printf_s("       nShared = %d\n\n", nShared);  
   omp_set_num_threads(NUM_THREADS);  
  
   #pragma omp parallel copyin(nThreadPrivate) private(nPrivate) shared(nShared) firstprivate(nFirstPrivate)  
   {  
      #pragma omp for schedule(static) lastprivate(nLastPrivate)  
      for (i = 0 ; i < NUM_THREADS ; ++i) {  
         for (j = 0 ; j < NUM_LOOPS ; ++j) {  
            int nThread = omp_get_thread_num();  
            assert(nThread < NUM_THREADS);  
  
            if (nThread == SLEEP_THREAD)  
               Sleep(100);  
            nSave[nThread][ThreadPrivate][j] = nThreadPrivate;  
            nSave[nThread][Private][j] = nPrivate;  
            nSave[nThread][Shared][j] = nShared;  
            nSave[nThread][FirstPrivate][j] = nFirstPrivate;  
            nSave[nThread][LastPrivate][j] = nLastPrivate;  
            nThreadPrivate = nThread;  
            nPrivate = nThread;  
            nShared = nThread;  
            nLastPrivate = nThread;  
            --nFirstPrivate;  
         }  
      }  
   }  
  
   for (i = 0 ; i < NUM_LOOPS ; ++i) {  
      for (j = 0 ; j < NUM_THREADS ; ++j) {  
         printf_s("These are the variables at entry of "  
                  "loop %d of thread %d.\n", i + 1, j);  
         printf_s("nThreadPrivate = %d\n",  
                  nSave[j][ThreadPrivate][i]);  
         printf_s("      nPrivate = %d\n",  
                  nSave[j][Private][i]);  
         printf_s(" nFirstPrivate = %d\n",  
                  nSave[j][FirstPrivate][i]);  
         printf_s("  nLastPrivate = %d\n",  
                  nSave[j][LastPrivate][i]);  
         printf_s("       nShared = %d\n\n",  
                  nSave[j][Shared][i]);  
      }  
   }  
  
   printf_s("These are the variables after exit from "  
            "the parallel region.\n");  
   printf_s("nThreadPrivate = %d (The last value in the "  
            "master thread)\n", nThreadPrivate);  
   printf_s("      nPrivate = %d (The value prior to "  
            "entering parallel region)\n", nPrivate);  
   printf_s(" nFirstPrivate = %d (The value prior to "  
            "entering parallel region)\n", nFirstPrivate);  
   printf_s("  nLastPrivate = %d (The value from the "  
            "last iteration of the loop)\n", nLastPrivate);  
   printf_s("       nShared = %d (The value assigned, "  
            "from the delayed thread, %d)\n\n",  
            nShared, SLEEP_THREAD);  
}  
```  
  
```Output  
These are the variables before entry into the parallel region.  
nThreadPrivate = 4  
      nPrivate = 4  
 nFirstPrivate = 4  
  nLastPrivate = 4  
       nShared = 4  
  
These are the variables at entry of loop 1 of thread 0.  
nThreadPrivate = 4  
      nPrivate = 1310720  
 nFirstPrivate = 4  
  nLastPrivate = 1245104  
       nShared = 3  
  
These are the variables at entry of loop 1 of thread 1.  
nThreadPrivate = 4  
      nPrivate = 4488  
 nFirstPrivate = 4  
  nLastPrivate = 19748  
       nShared = 0  
  
These are the variables at entry of loop 1 of thread 2.  
nThreadPrivate = 4  
      nPrivate = -132514848  
 nFirstPrivate = 4  
  nLastPrivate = -513199792  
       nShared = 4  
  
These are the variables at entry of loop 1 of thread 3.  
nThreadPrivate = 4  
      nPrivate = 1206  
 nFirstPrivate = 4  
  nLastPrivate = 1204  
       nShared = 2  
  
These are the variables at entry of loop 2 of thread 0.  
nThreadPrivate = 0  
      nPrivate = 0  
 nFirstPrivate = 3  
  nLastPrivate = 0  
       nShared = 0  
  
These are the variables at entry of loop 2 of thread 1.  
nThreadPrivate = 1  
      nPrivate = 1  
 nFirstPrivate = 3  
  nLastPrivate = 1  
       nShared = 1  
  
These are the variables at entry of loop 2 of thread 2.  
nThreadPrivate = 2  
      nPrivate = 2  
 nFirstPrivate = 3  
  nLastPrivate = 2  
       nShared = 2  
  
These are the variables at entry of loop 2 of thread 3.  
nThreadPrivate = 3  
      nPrivate = 3  
 nFirstPrivate = 3  
  nLastPrivate = 3  
       nShared = 3  
  
These are the variables after exit from the parallel region.  
nThreadPrivate = 0 (The last value in the master thread)  
      nPrivate = 4 (The value prior to entering parallel region)  
 nFirstPrivate = 4 (The value prior to entering parallel region)  
  nLastPrivate = 3 (The value from the last iteration of the loop)  
       nShared = 1 (The value assigned, from the delayed thread, 1)  
```  
  
## <a name="see-also"></a>참고 항목  
 [절](../../../parallel/openmp/reference/openmp-clauses.md)
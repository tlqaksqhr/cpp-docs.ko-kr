---
title: 복사 생성자 및 복사 할당 연산자 (c + +) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- = operator [C++], copying objects
- assignment statements [C++], copying objects
- assignment operators [C++], for copying objects
- objects [C++], copying
- initializing objects, by copying objects
- copying objects
- assigning values to copy objects
ms.assetid: a94fe1f9-0289-4fb9-8633-77c654002c0d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 24f9e4e5b3d157f23c18d46f2857b29e6960e82e
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/01/2018
ms.locfileid: "39405758"
---
# <a name="copy-constructors-and-copy-assignment-operators-c"></a>복사 생성자 및 복사 할당 연산자(C++)
> [!NOTE]
>  C++11부터 언어에서 이라는 두 가지 할당이 지원 됩니다. *복사 할당* 하 고 *이동 할당*합니다. 이 문서에서 별도로 명시하지 않는 한 "할당"은 복사 할당을 의미합니다. 이동 할당에 대 한 정보를 참조 하세요 [이동 생성자 및 이동 할당 연산자 (c + +)](http://msdn.microsoft.com/1442de5f-37a5-42a1-83a6-ec9cfe0414db)합니다.  
>   
>  할당 작업과 초기화 작업은 모두 개체를 복사합니다.  
  
-   **할당**: 한 개체의 값은 다른 개체에 할당할 첫 번째 개체가 두 번째 개체에 복사 됩니다. 따라서  
  
    ```cpp  
    Point a, b;  
    ...  
    a = b;  
    ```  
  
     `b`의 값이 `a`에 복사되도록 합니다.  
  
-   **초기화**: 인수가 값으로 함수에 전달 되 면, 새 개체를 선언 하거나 함수에서 값이 반환 하는 것이 값 초기화가 발생 합니다.  
  
 클래스 형식의 개체에 대해 "복사"의 의미를 정의할 수 있습니다. 예를 들어 다음 코드를 고려합니다.  
  
```cpp  
TextFile a, b;  
a.Open( "FILE1.DAT" );  
b.Open( "FILE2.DAT" );  
b = a;  
```  
  
 앞의 코드는 "FILE1.DAT의 내용을 FILE2.DAT에 복사"를 의미하거나, "FILE2.DAT를 무시하고 `b`를 FILE1.DAT의 두 번째 핸들로 만들기"를 의미할 수도 있습니다. 다음과 같이 각 클래스에 적절한 복사 의미를 연결해야 합니다.  
  
-   대입 연산자를 사용 하 여 **연산자 =** 반환 형식 및 매개 변수에서 전달 되는 클래스 형식에 대 한 참조와 함께 **const** 참조-예를 들어 `ClassName& operator=(const ClassName& x);`합니다.  
  
-   복사 생성자를 사용합니다.   
  
 복사 생성자를 선언하지 않으면 컴파일러는 자동으로 멤버 단위 복사 생성자를 생성합니다.  복사 할당 연산자를 선언하지 않으면 컴파일러는 자동으로 멤버 단위 복사 할당 연산자를 생성합니다. 복사 생성자의 선언은 컴파일러에서 생성된 복사 할당 연산자를 숨기지 않으며 그 반대의 경우에도 마찬가지입니다. 둘 중 하나를 구현하는 경우 다른 하나도 구현하여 코드의 의미를 분명히 하는 것이 좋습니다.  
   
 형식의 인수를 사용 하는 복사 생성자 * 클래스-name ***&** 여기서 *클래스 이름* 생성자가 정의 된 클래스의 이름입니다. 예를 들어:  
  
```cpp  
// spec1_copying_class_objects.cpp  
class Window  
{  
public:  
    Window( const Window& ); // Declare copy constructor.  
    // ...  
};  
  
int main()  
{  
}  
```  
  
> [!NOTE]
>  복사 생성자의 인수 형식을 *const 클래스-이름 * * * &** 가능 합니다. 이는 복사 생성자가 복사 중인 개체를 실수로 변경하는 것을 방지합니다. 복사도 가능 **const** 개체입니다.  
  
## <a name="compiler-generated-copy-constructors"></a>컴파일러에서 생성된 복사 생성자  
 사용자 정의 복사 생성자와 같은 컴파일러 생성 복사 생성자가 형식의 단일 인수 "에 대 한 참조 *클래스 이름*." 모든 기본 클래스와 멤버 클래스 형식의 단일 인수를 선언 하는 복사 생성자가 있는 경우는 예외입니다 **상수** * 클래스-name ***&** 합니다. 이 경우 컴파일러 생성 복사 생성자의 인수는 또한 **const**합니다.  
  
 복사 생성자에 대 한 인수 형식이 없는 경우 **const**를 복사 하 여 초기화를 **const** 개체에 오류가 발생 합니다. 성립 되지: 인수가 **상수**, 하지 않은 개체를 복사 하 여 초기화할 수 있습니다 **const**합니다.  
  
 컴파일러에서 생성 된 할당 연산자 관련해 서 동일한 패턴을 따릅니다 **const입니다.** 형식의 단일 인수 *클래스-이름 * * * &** 형식의 인수를 수행 하는 모든 기본 및 멤버 클래스의 할당 연산자 **const** *클래스 이름 & 합니다.* 이 경우 클래스의 생성 된 할당 연산자는 한 **const** 인수입니다.  
  
> [!NOTE]
>  가상 기본 클래스가 복사 생성자에 의해 초기화되고 컴파일러에서 생성되거나 사용자 정의되는 경우 생성되는 시점에 한 번만 초기화됩니다.  
  
 의미는 복사 생성자의 의미와 비슷합니다. 인수 형식이 없는 경우 **const**에서 할당을 **const** 개체에 오류가 발생 합니다. 성립 되지: 경우는 **상수** 값이 아닌 값으로 할당 **const**, 할당 성공 합니다.  
  
 오버 로드 된 할당 연산자에 대 한 자세한 내용은 참조 하세요. [할당](../cpp/assignment.md)합니다.  
---
title: "컬렉션(C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "01/22/2017"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 914da30b-aac5-4cd7-9da3-a5ac08cdd72c
caps.latest.revision: 35
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 35
---
# 컬렉션(C++/CX)
[!INCLUDE[cppwrt](../cppcx/includes/cppwrt-md.md)]\([!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]\) 프로그램에서는 STL\(표준 템플릿 라이브러리\) 컨테이너 또는 다른 모든 사용자 정의 컬렉션 형식을 자유롭게 사용할 수 있습니다. 그러나 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] ABI\(응용 프로그램 이진 인터페이스\)로 컬렉션을 전달\(예: XAML 컨트롤 또는 JavaScript 클라이언트로 전달\)할 때는 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 컬렉션 형식을 사용해야 합니다.  
  
 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]에서는 컬렉션 및 관련 형식의 인터페이스를 정의하고, [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]에서는 collection.h header 파일의 구체적 C\+\+ 구현을 제공합니다. 다음 그림에서는 컬렉션 형식 간의 관계를 보여 줍니다.  
  
 ![컬렉션 형식의 C&#43;&#43;&#47;CX 상속 트리](../cppcx/media/cppcxcollectionsinheritancetree.png "CPPCXCollectionsInheritanceTree")  
  
-   [Platform::Collections::Vector 클래스](../cppcx/platform-collections-vector-class.md)는 [std::vector 클래스](../Topic/vector%20Class%201.md)와 유사합니다.  
  
-   [Platform::Collections::Map 클래스](../cppcx/platform-collections-map-class.md)는 [std::map 클래스](../standard-library/map-class.md)와 유사합니다.  
  
-   [Platform::Collections::VectorView 클래스](../cppcx/platform-collections-vectorview-class.md) 및 [Platform::Collections::MapView 클래스](../cppcx/platform-collections-mapview-class.md)는 `Vector` 및 `Map`의 읽기 전용 버전입니다.  
  
-   반복기는 [Platform::Collections Namespace](../cppcx/platform-collections-namespace.md)에서 정의됩니다. 이러한 반복기는 STL 반복기에 대한 요구 사항을 충족하며 모든 [Windows::Foundation::Collections](http://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.aspx) 인터페이스 형식 또는 [Platform::Collections](../cppcx/platform-collections-namespace.md) 구체적 형식에 대해 [std::find](http://msdn.microsoft.com/library/021e9ef9-8817-409f-92ee-cd7104867361), [std::count\_if](http://msdn.microsoft.com/library/b785887c-83cd-4099-becc-3284dee05295) 및 기타 STL 알고리즘을 사용할 수 있게 만듭니다. 예를 들어 C\#에서 만들어진 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 구성 요소의 컬렉션을 반복하고 여기에 STL 알고리즘을 적용할 수 있습니다.  
  
    > [!IMPORTANT]
    >  프록시 반복기 `VectorIterator` 및 `VectorViewIterator`는 프록시 개체 `VectoryProxy<T>` 및 `ArrowProxy<T>`를 활용하여 STL 컨테이너에 사용할 수 있게 만듭니다. 자세한 내용은 이 문서 뒷부분의 "VectorProxy 요소"를 참조하세요.  
  
-   [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 컬렉션 형식은 STL 컨테이너에서 지원하는 동일한 스레드 보안 보장을 지원합니다.  
  
-   [Windows::Foundation::Collections::IObservableVector](http://msdn.microsoft.com/library/windows/apps/br226052.aspx) 및 [Windows::Foundation::Collections::IObservableMap](http://msdn.microsoft.com/library/windows/apps/br226050.aspx)은 컬렉션이 다양한 방식으로 변경될 때 발생하는 이벤트를 정의합니다. 이러한 인터페이스를 구현하여 [Platform::Collections::Map](../cppcx/platform-collections-map-class.md) 및 [Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md)는 XAML 컬렉션을 사용한 데이터 바인딩을 지원합니다. 예를 들어, `Vector`에 데이터 바인딩된 `Grid`가 있는 경우 컬렉션에 항목을 추가하면 변경 내용이 Grid UI에 반영됩니다.  
  
## Vector 사용법  
 클래스가 시퀀스 컨테이너를 다른 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 구성 요소에 전달해야 하는 경우 [Windows::Foundation::Collections:: IVector\<T\>](http://msdn.microsoft.com/library/windows/apps/br206631.aspx)를 매개 변수나 반환 형식으로 사용하고 [Platform::Collections::Vector\<T\>](../cppcx/platform-collections-vector-class.md)를 구체적 구현으로 사용합니다. 공용 반환 값 또는 매개 변수에서 `Vector` 형식을 사용하려고 하면 컴파일러 오류 C3986이 발생합니다.`Vector`를 `IVector`로 변경하여 이 오류를 해결할 수 있습니다.  
  
> [!IMPORTANT]
>  자체 프로그램 안에서 시퀀스를 전달하는 경우에는 `Vector`보다 효율적인 `std::vector` 또는 `IVector`를 사용합니다. ABI 너머로 컨테이너를 전달할 때만 `IVector`를 사용합니다.  
>   
>  Windows 런타임 형식 시스템에서는 가변 배열의 개념이 지원되지 않으므로 IVector\<Platform::Array\<T\>\>를 반환 값 또는 메서드 매개 변수로 전달할 수 없습니다. ABI 전반에서 가변 배열 또는 시퀀스의 시퀀스를 전달하려면 `IVector<IVector<T>^>`를 사용합니다.  
  
 `Vector<T>`는 컬렉션의 항목을 추가, 제거 및 액세스하는 데 필요한 메서드를 제공하며, `IVector<T>`로 암시적으로 변환할 수 있습니다. 또한 `Vector<T>` 인스턴스에서 STL 알고리즘을 사용할 수 있습니다. 다음 예제에서는 몇 가지 기본 사용법을 보여 줍니다. 여기에 사용된 [begin 함수](../cppcx/begin-function.md) 및 [end 함수](../cppcx/end-function.md)는 `Platform::Collections` 네임스페이스가 아니라 `std` 네임스페이스에서 가져온 것입니다.  
  
 [!code-cpp[cx_collections#01](../snippets/cpp/VS_Snippets_Misc/cx_collections/cpp/class1.cpp#01)]  
  
 `std::vector`를 사용하는 기존 코드가 있는 경우 이를 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 구성 요소에서 다시 사용하려면 ABI 너머로 컬렉션을 전달할 때 `Vector` 또는 반복기 쌍을 사용하는 `std::vector` 생성자 중 하나를 사용하여 `Vector`를 생성하기만 하면 됩니다. 다음 예제에서는 효율적인 초기화를 위해 `Vector`에서 `std::vector` 이동 생성자를 사용하는 방법을 보여 줍니다. 이동 작업 후 원래 `vec` 변수는 더 이상 유효하지 않습니다.  
  
 [!code-cpp[cx_collections#02](../snippets/cpp/VS_Snippets_Misc/cx_collections/cpp/class1.cpp#02)]  
  
 이후의 특정 시점에 ABI 너머로 전달해야 하는 문자열의 벡터가 있는 경우 문자열을 처음에 `std::wstring` 형식으로 만들지 아니면 `Platform::String^` 형식으로 만들지를 결정해야 합니다. 문자열에 대한 처리를 많이 수행해야 하면 `wstring`을 사용하고, 그렇지 않으면 문자열을 `Platform::String^` 형식으로 만들고 나중에 변환하는 비용을 방지합니다. 또한 이러한 문자열을 내부적으로 `std:vector`에 넣을지 아니면 `Platform::Collections::Vector`에 넣을지도 결정해야 합니다. 일반적으로 `std::vector`를 사용한 다음 ABI 너머로 컨테이너를 전달해야 할 때만 `Platform::Vector`를 만듭니다.  
  
## Vector의 값 형식  
 [Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md)에 저장될 모든 요소는 암시적으로 또는 제공하는 사용자 지정 [std::equal\_to](../standard-library/equal-to-struct.md) 비교 연산자를 사용하여 같음 비교를 지원해야 합니다. 모든 참조 형식과 모든 스칼라 형식은 같음 비교를 암시적으로 지원합니다.[Windows::Foundation::DateTime](http://msdn.microsoft.com/library/windows/apps/windows.foundation.datetime.aspx)과 같은 스칼라 값이 아닌 형식이나 `objA->UniqueID == objB->UniqueID`와 같은 사용자 지정 비교의 경우 사용자 지정 함수 개체를 제공해야 합니다.  
  
  
  
## VectorProxy 요소  
 [Platform::Collections::VectorIterator](../cppcx/platform-collections-vectoriterator-class.md) 및 [Platform::Collections::VectorViewIterator](../cppcx/platform-collections-vectorviewiterator-class.md)를 사용하면 [IVector\<T\>](http://msdn.microsoft.com/en-us/library/windows/apps/br206631.aspx) 컨테이너에서 [std::sort](http://msdn.microsoft.com/library/9b0a4fc1-5131-4c73-9c2e-d72211f2d0ae)와 같은 `range for` 루프 및 알고리즘을 사용할 수 있습니다. 그러나 `IVector` 요소는 C\+\+ 포인터 역참조를 통해 액세스할 수 없습니다. 이 요소는 [GetAt](http://msdn.microsoft.com/library/windows/apps/br206634.aspx) 및 [SetAt](http://msdn.microsoft.com/library/windows/apps/br206642.aspx) 메서드를 통해서만 액세스할 수 있습니다. 따라서 STL 요구 사항에 맞게 `Platform::Details::VectorProxy<T>`, `Platform::Details::ArrowProxy<T>` 및 `*` 연산자를 통해 개별 요소에 대한 액세스를 제공하기 위해 이러한 반복기에 프록시 클래스 `->` 및 `[]`가 사용됩니다. 엄밀히 말해 `IVector<Person^> vec` 지정 시 `*begin(vec)`의 형식은 `VectorProxy<Person^>`입니다. 그러나 프록시 개체는 사용자 코드에 거의 표시되지 않습니다. 이러한 프록시 개체는 내부적으로 반복기에만 사용되므로 문서화되지 않지만 메커니즘의 작동 방식을 알면 유용합니다.  
  
 `range for` 컨테이너에 대해 `IVector` 루프를 사용할 때는 반복기 변수가 `auto&&` 요소에 올바르게 바인딩되도록 `VectorProxy`를 사용합니다.`auto` 또는 `auto&`를 사용하면 컴파일러 경고 C4239가 발생하고 `VectoryProxy`가 경고 텍스트에 언급됩니다.  
  
 다음 그림에서는 `range for`에 대한 `IVector<Person^>` 루프를 보여 줍니다. 64번 줄의 중단점에서 실행이 중지됩니다.**간략한 조사식** 창에서 반복기 변수 `p`가 실제로는 `VectorProxy<Person^>` 및 `m_v` 멤버 변수가 있는 `m_i`라는 것을 확인할 수 있습니다. 그러나 이 변수에 대해 `GetType`을 호출하면 `Person` 인스턴스 `p2`와 동일한 형식이 반환됩니다.`VectorProxy` 및 `ArrowProxy`는 **간략한 조사식**, 디버거 특정 컴파일러 오류 또는 기타 위치에 나타날 수 있지만 일반적으로 해당 항목을 명시적으로 코딩할 필요는 없습니다.  
  
 ![범위 기반 for 루프의 VectorProxy](../cppcx/media/vectorproxy-1.png "VectorProxy\_1")  
  
 프록시 개체를 코딩해야 하는 시나리오 중 하나는 `dynamic_cast` 요소 컬렉션에서 특정 형식의 XAML 개체를 찾을 때 등에 요소에 대해 `UIElement`를 수행해야 하는 경우입니다. 이 경우 먼저 요소를 [Platform::Object](../cppcx/platform-object-class.md)^으로 캐스팅한 다음 동적 캐스팅을 수행해야 합니다.  
  
```  
  
void FindButton(UIElementCollection^ col)  
{  
    // Use auto&& to avoid warning C4239  
    for (auto&& elem : col)  
    {  
        Button^ temp = dynamic_cast<Button^>(static_cast<Object^>(elem));  
        if (nullptr != temp)  
        {  
            // Use temp...  
        }  
    }  
}  
```  
  
## Map 사용법  
 이 예제에서는 항목을 삽입하고 [Platform::Collections::Map](../cppcx/platform-collections-map-class.md)에서 조회한 다음 `Map`을 읽기 전용 [Windows::Foundation::Collections::IMapView](http://msdn.microsoft.com/library/windows/apps/br226037.aspx) 형식으로 반환하는 방법을 보여 줍니다.  
  
 [!code-cpp[cx_collections#04](../snippets/cpp/VS_Snippets_Misc/cx_collections/cpp/class1.cpp#04)]  
  
 일반적으로 내부 맵 기능에는 성능상 `std::map` 형식을 사용하는 것이 좋습니다. ABI 전반에서 컨테이너를 전달해야 하는 경우 [std::map](../standard-library/map-class.md)에서 [Platform::Collections::Map](../cppcx/platform-collections-map-class.md)을 생성하고 `Map`을 [Windows::Foundation::Collections::IMap](http://msdn.microsoft.com/library/windows/apps/br226042.aspx)으로 반환합니다. 공용 반환 값 또는 매개 변수에서 `Map` 형식을 사용하려고 하면 컴파일러 오류 C3986이 발생합니다.`Map`를 `IMap`로 변경하여 이 오류를 해결할 수 있습니다. 조회 또는 삽입 수가 많지 않고 ABI 너머로 컬렉션을 자주 전달하는 경우 등에는 `Platform::Collections::Map`을 변환할 필요 없이 처음부터 `std::map`을 사용하는 것이 경제적일 수 있습니다. 어떤 경우든, 조회 및 삽입 작업은 세 가지 형식의 성능을 가장 크게 저하시키기 때문에 `IMap`에서 사용하지 않는 것이 좋습니다.`IMap`으로의 변환은 ABI 너머로 컨테이너를 전달할 때만 수행합니다.  
  
## Map의 값 형식  
 [Platform::Collections::Map](../cppcx/platform-collections-map-class.md)의 요소는 정렬됩니다.`Map`에 저장될 모든 요소는 암시적으로 또는 제공하는 사용자 지정 [stl::less](../standard-library/less-struct.md) 비교 연산자를 사용하여 엄격한 강력하지 않은 순서 지정으로 보다 작음 비교를 지원해야 합니다. 스칼라 형식은 암시적으로 비교를 지원합니다.`Windows::Foundation::DateTime`과 같은 스칼라 값이 아닌 형식이나 `objA->UniqueID < objB->UniqueID`와 같은 사용자 지정 비교의 경우 사용자 지정 비교 연산자를 제공해야 합니다.  
  
## 컬렉션 형식  
 컬렉션은 네 가지 범주로 구분됩니다\(수정 가능한 버전 및 읽기 전용 버전의 시퀀스 컬렉션과 연결 컬렉션\). 또한 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]는 컬렉션 액세스를 간소화하는 세 가지 반복기 클래스를 제공하여 컬렉션을 향상시킵니다. 반복기에 대한 간략한 설명은 [반복기](../standard-library/iterators.md)를 참조하세요.  
  
 수정 가능한 컬렉션의 요소는 변경할 수 있지만 읽기 전용 컬렉션\(*뷰*라고 함\)의 요소는 읽을 수만 있습니다.[Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md) 또는 [Platform::Collections::VectorView](../cppcx/platform-collections-vectorview-class.md) 컬렉션의 요소는 반복기 또는 컬렉션의 [Vector::GetAt 메서드](../cppcx/vector-getat-method.md) 및 인덱스를 사용하여 액세스할 수 있습니다. 연결 컬렉션의 요소는 컬렉션의 [Map::Lookup 메서드](../cppcx/map-lookup-method.md) 및 키를 사용하여 액세스할 수 있습니다.  
  
 [Platform::Collections::Map 클래스](../cppcx/platform-collections-map-class.md)  
 수정 가능한 연결 컬렉션입니다. 맵 요소는 키\/값 쌍입니다. 키를 조회하여 연결된 값을 검색하고 모든 키\/값 쌍에서 반복하는 작업이 둘 다 지원됩니다.  
  
 `Map` 및 `MapView`는 `<K, V, C = std::less<K>>` 템플릿 기반이므로 비교 연산자를 사용자 지정할 수 있습니다.  또한 `Vector` 및 `VectorView`는 `<T, E = std::equal_to<T>>` 템플릿 기반이며 `IndexOf()`의 동작을 사용자 지정할 수 있습니다. 이는 주로 값 구조체의 `Vector` 및 `VectorView`에 중요합니다. 예를 들어 Vector\<Windows::Foundation::DateTime\>을 만들려면 DateTime이 \=\= 연산자를 오버로드하지 않으므로 사용자 지정 비교 연산자를 제공해야 합니다.  
  
 [Platform::Collections::MapView 클래스](../cppcx/platform-collections-mapview-class.md)  
 읽기 전용 버전의 `Map`입니다.  
  
 [Platform::Collections::Vector 클래스](../cppcx/platform-collections-vector-class.md)  
 수정 가능한 시퀀스 컬렉션입니다.`Vector<T>`는 constant\-time 임의 액세스 및 amortized\-constant\-time [추가](../cppcx/vector-append-method.md) 작업을 지원합니다.  
  
 [Platform::Collections::VectorView 클래스](../cppcx/platform-collections-vectorview-class.md)  
 읽기 전용 버전의 `Vector`입니다.  
  
 [Platform::Collections::InputIterator 클래스](../cppcx/platform-collections-inputiterator-class.md)  
 STL 입력 반복기의 요구 사항을 충족하는 STL 반복기입니다.  
  
 [Platform::Collections::VectorIterator 클래스](../cppcx/platform-collections-vectoriterator-class.md)  
 STL 변경 가능 임의 액세스 반복기의 요구 사항을 충족하는 STL 반복기입니다.  
  
 [Platform::Collections::VectorViewIterator 클래스](../cppcx/platform-collections-vectorviewiterator-class.md)  
 STL `const` 임의 액세스 반복기의 요구 사항을 충족하는 STL 반복기입니다.  
  
### begin\(\) 및 end\(\) 함수  
 STL을 사용한 `Vector`, `VectorView`, `Map`, `MapView` 및 `Windows::Foundation::Collections` 개체 처리를 간소화하기 위해 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]는 [begin 함수](../cppcx/begin-function.md) 및 [end 함수](../cppcx/end-function.md) 비멤버 함수의 오버로드를 지원합니다.  
  
 다음 표에서는 사용 가능한 반복기 및 함수를 보여 줍니다.  
  
|반복기|함수|  
|---------|--------|  
|[Platform::Collections::VectorIterator\<T\>](../cppcx/platform-collections-vectoriterator-class.md)<br /><br /> \(내부적으로 [Windows::Foundation::Collections:: IVector\<T\>](http://msdn.microsoft.com/library/windows/apps/br206631.aspx) 및 int 저장\)|[begin](../cppcx/begin-function.md)\/ [end](../cppcx/end-function.md)\([Windows::Foundation::Collections:: IVector\<T\>](http://msdn.microsoft.com/library/windows/apps/br206631.aspx)\)|  
|[Platform::Collections::VectorViewIterator\<T\>](../cppcx/platform-collections-vectorviewiterator-class.md)<br /><br /> \(내부적으로 [IVectorView\<T\>](http://msdn.microsoft.com/library/windows/apps/br226058.aspx)^ 및 int 저장\)|[begin](../cppcx/begin-function.md)\/ [end](../cppcx/end-function.md)\([IVectorView\<T\>](http://msdn.microsoft.com/library/windows/apps/br226058.aspx)^\)|  
|[Platform::Collections::InputIterator\<T\>](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> \(내부적으로 [IIterator\<T\>](http://msdn.microsoft.com/library/windows/apps/br226026.aspx)^ 및 T 저장\)|[begin](../cppcx/begin-function.md)\/ [end](../cppcx/end-function.md)\([IIterable\<T\>](http://msdn.microsoft.com/library/windows/apps/br226024.aspx)\)|  
|[Platform::Collections::InputIterator\<IKeyValuePair\<K, V\>^\>](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> \(내부적으로 [IIterator\<T\>](http://msdn.microsoft.com/library/windows/apps/br226026.aspx)^ 및 T 저장\)|[begin](../cppcx/begin-function.md)\/ [end](../cppcx/end-function.md)\([IMap\<K,V\>](http://msdn.microsoft.com/library/windows/apps/br226042.aspx).|  
|[Platform::Collections::InputIterator\<IKeyValuePair\<K, V\>^\>](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> \(내부적으로 [IIterator\<T\>](http://msdn.microsoft.com/library/windows/apps/br226026.aspx)^ 및 T 저장\)|[begin](../cppcx/begin-function.md)\/ [end](../cppcx/end-function.md)\([Windows::Foundation::Collections::IMapView](http://msdn.microsoft.com/library/windows/apps/br226037.aspx)\)|  
  
### 컬렉션 변경 이벤트  
 `Vector` 및 `Map`은 컬렉션 개체가 변경되거나 다시 설정된 경우 또는 컬렉션의 요소가 삽입, 제거 또는 변경된 경우에 발생하는 이벤트를 구현하여 XAML 컬렉션에서 데이터 바인딩을 지원합니다. 데이터 바인딩을 지원하는 고유한 형식을 작성할 수 있지만 이러한 형식이 봉인되기 때문에 `Map` 또는 `Vector`에서 상속할 수는 없습니다.  
  
 [Windows::Foundation::Collections::VectorChangedEventHandler](http://msdn.microsoft.com/library/windows/apps/br206656.aspx) 및 [Windows::Foundation::Collections::MapChangedEventHandler](http://msdn.microsoft.com/library/windows/apps/br206644.aspx) 대리자는 컬렉션 변경 이벤트에 대한 이벤트 처리기의 서명을 지정합니다.[Windows::Foundation::Collections::CollectionChange](http://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.collectionchange.aspx) public enum 클래스와  `Platform::Collection::Details::MapChangedEventArgs` 및 `Platform::Collections::Details::VectorChangedEventArgs` ref 클래스는 이벤트의 원인을 확인하기 위해 이벤트 인수를 저장합니다. \*`EventArgs` 형식은 `Details` 또는 `Map`를 사용할 때 명시적으로 생성하거나 사용할 필요가 없기 때문에 `Vector` 네임스페이스에서 정의됩니다.  
  
## 참고 항목  
 [형식 시스템](../cppcx/type-system-c-cx.md)   
 [Built\-in Types](http://msdn.microsoft.com/ko-kr/acc196fd-09da-4882-b554-6c94685ec75f)   
 [Visual C\+\+ 언어 참조](../cppcx/visual-c-language-reference-c-cx.md)   
 [네임스페이스 참조](../cppcx/namespaces-reference-c-cx.md)
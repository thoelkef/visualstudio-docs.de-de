---
title: "Verwenden von Microsoft.VisualStudio.TestTools.CppUnitTestFramework | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d1ac9188-d79f-407e-9f3a-80dbefa66317
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "mlearned"
manager: "douge"
---
# Verwenden von Microsoft.VisualStudio.TestTools.CppUnitTestFramework
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Thema sind die öffentlichen Member des `Microsoft::VisualStudio::CppUnitTestFramework`\-Namespace auf.  
  
 Die Headerdateien sind im Ordner *VisualStudio2012\[x86\]InstallFolder***\\VC\\UnitTest\\include**.  
  
 Die lib\-Dateien sind im Ordner *VisualStudio2012\[x86\]InstallFolder***\\VC\\UnitTest\\lib**.  
  
##  <a name="BKMK_In_this_topic"></a> In diesem Thema  
 [CppUnitTest.h](#BKMK_CppUnitTest_h)  
  
-   [Erstellen Sie Testklassen und Methoden](#BKMK_Create_test_classes_and_methods)  
  
-   [Initialisierungs- und bereinigen](#BKMK_Initialize_and_cleanup)  
  
    -   [Testmethoden](#BKMK_Test_methods)  
  
    -   [Testklassen](#BKMK_Test_classes)  
  
    -   [Testmodule](#BKMK_Test_modules)  
  
-   [Erstellen Sie Testattribute](#BKMK_Create_test_attributes)  
  
    -   [Testmethodenattribute](#BKMK_Test_method_attributes)  
  
    -   [Testklassenattribute](#BKMK_Test_class_attributes)  
  
    -   [Testmodulattribute](#BKMK_Test_module_attributes)  
  
    -   [Vordefinierte Attribute](#BKMK_Pre_defined_attributes)  
  
     [CppUnitTestAssert.h](#BKMK_CppUnitTestAssert_h)  
  
    -   [Allgemeine Assertionen](#BKMK_General_Asserts)  
  
        -   [Stellen Sie gleich](#BKMK_General_Are_Equal)  
  
        -   [Achten Sie nicht gleich](#BKMK_General_Are_Not_Equal)  
  
        -   [Sind gleich](#BKMK_General_Are_Same)  
  
        -   [Nicht identisch sind](#BKMK_General_Are_Not_Same)  
  
        -   [Ist NULL](#BKMK_General_Is_Null)  
  
        -   [Ist nicht NULL](#BKMK_General_Is_Not_Null)  
  
        -   [Ist "True"](#BKMK_General_Is_True)  
  
        -   [Ist falsch](#BKMK_General_Is_False)  
  
        -   [Fail](#BKMK_General_Fail)  
  
    -   [Windows Runtime-Assertionen](#BKMK_WinRT_Asserts)  
  
        -   [Stellen Sie gleich](#BKMK_WinRT_Are_Equal)  
  
        -   [Sind gleich](#BKMK_WinRT_Are_Same)  
  
        -   [Achten Sie nicht gleich](#BKMK_WinRT_Are_Not_Equal)  
  
        -   [Nicht identisch sind](#BKMK_WinRT_Are_Not_Same)  
  
        -   [Ist NULL](#BKMK_WinRT_Is_Null)  
  
        -   [Ist nicht NULL](#BKMK_WinRT_Is_Not_Null)  
  
    -   [Ausnahme-Assertionen](#BKMK_Exception_Asserts)  
  
        -   [Rechnen Sie Ausnahme](#BKMK_Expect_Exception)  
  
         [CppUnitTestLogger.h](#BKMK_CppUnitTestLogger_h)  
  
        -   [Protokollierung](#BKMK_Logger)  
  
        -   [Nachricht schreiben](#BKMK_Write_Message)  
  
##  <a name="BKMK_CppUnitTest_h"></a> CppUnitTest.h  
  
###  <a name="BKMK_Create_test_classes_and_methods"></a> Erstellen Sie Testklassen und Methoden  
  
```cpp  
TEST_CLASS(className)  
```  
  
 Erforderlich für jede Klasse, Testmethoden enthält.  Identifiziert *className* wie eine Testklasse.  `TEST_CLASS` muss an namescape Gültigkeitsbereich deklariert werden.  
  
```cpp  
TEST_METHOD(methodName)   
{  
    // test method body  
}  
  
```  
  
 Definiert als *methodName* Testmethode.  muss `TEST_METHOD` im Gültigkeitsbereich der Klasse der Methode deklariert ist.  
  
###  <a name="BKMK_Initialize_and_cleanup"></a> Initialisierungs\- und bereinigen  
  
####  <a name="BKMK_Test_methods"></a> Testmethoden  
  
```cpp  
TEST_METHOD_INITIALIZE(methodName)   
{  
    // method initialization code  
}  
  
```  
  
 Definiert *methodName* als Methode, die ausgeführt wird, bevor jede Testmethode ausgeführt wird.  `TEST_METHOD_INITIALIZE` kann in einer Testklasse nur einmal definiert werden und in der Testklasse definiert werden.  
  
```cpp  
TEST_METHOD_CLEANUP(methodName)   
{  
    // test method cleanup  code  
}  
  
```  
  
 Definiert *methodName* als Methode, die ausgeführt wird, wenn jeder Testmethode ausgeführt.  `TEST_METHOD_CLEANUP` kann in einer Testklasse nur einmal definiert werden und muss im Kontext der Testklasse definiert werden.  
  
####  <a name="BKMK_Test_classes"></a> Testklassen  
  
```cpp  
TEST_CLASS_INITIALIZE(methodName)   
{  
    // test class initialization  code  
}  
  
```  
  
 Definiert *methodName* als Methode, wird nach jeder Testklasse erstellt wird.  `TEST_CLASS_INITIALIZE` kann in einer Testklasse nur einmal definiert werden und muss im Kontext der Testklasse definiert werden.  
  
```cpp  
TEST_CLASS_CLEANUP(methodName)   
{  
    // test class cleanup  code  
}  
  
```  
  
 Definiert *methodName* als Methode, wird nach jeder Testklasse erstellt wird.  `TEST_CLASS_CLEANUP` kann in einer Testklasse nur einmal definiert werden und muss im Kontext der Testklasse definiert werden.  
  
####  <a name="BKMK_Test_modules"></a> Testmodule  
  
```cpp  
TEST_MODULE_INITIALIZE(methodName)  
{  
    // module initialization code  
}  
```  
  
 Definiert die *methodName*, die ausgeführt wird, wenn ein Modul geladen wird.  `TEST_MODULE_INITIALIZE` kann in einem Testmodul nur einmal definiert werden und muss am Gültigkeitsbereich deklariert werden.  
  
```cpp  
TEST_MODULE_CLEANUP(methodName)  
```  
  
 Definiert die *methodName*, die ausgeführt wird, wenn ein Modul entladen wird.  `TEST_MODULE_CLEANUP` kann in einem Testmodul nur einmal definiert werden und muss am Gültigkeitsbereich deklariert werden.  
  
###  <a name="BKMK_Create_test_attributes"></a> Erstellen Sie Testattribute  
  
####  <a name="BKMK_Test_method_attributes"></a> Testmethodenattribute  
  
```cpp  
BEGIN_TEST_METHOD_ATTRIBUTE(testMethodName)   
    TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)  
    ...  
END_TEST_METHOD_ATTRIBUTE()  
```  
  
 Fügt den Attribute hinzu, die einem oder mehreren `TEST_METHOD_ATTRIBUTE`\-Makros der Testmethode *testClassName* definiert werden.  
  
 Ein Makro `TEST_METHOD_ATTRIBUTE` definiert ein Attribut mit dem Namen *attributeName* und dem Wert *attributeValue*.  
  
####  <a name="BKMK_Test_class_attributes"></a> Testklassenattribute  
  
```cpp  
BEGIN_TEST_CLASS_ATTRIBUTE(testClassName)   
    TEST_CLASS_ATTRIBUTE(attributeName, attributeValue)  
    ...  
END_TEST_CLASS_ATTRIBUTE()  
```  
  
 Fügt den Attribute hinzu, die einem oder mehreren `TEST_CLASS_ATTRIBUTE`\-Makros der Testklasse *testClassName* definiert werden.  
  
 Ein Makro `TEST_CLASS_ATTRIBUTE` definiert ein Attribut mit dem Namen *attributeName* und dem Wert *attributeValue*.  
  
####  <a name="BKMK_Test_module_attributes"></a> Testmodulattribute  
  
```cpp  
BEGIN_TEST_MODULE_ATTRIBUTE(testModuleName)   
    TEST_MODULE_ATTRIBUTE(attributeName, attributeValue)  
    ...  
END_TEST_MODULE_ATTRIBUTE()  
```  
  
 Fügt den Attribute hinzu, die einem oder mehreren `TEST_MODULE_ATTRIBUTE`\-Makros das Testmodul *testModuleName* definiert werden.  
  
 Ein Makro `TEST_MODULE_ATTRIBUTE` definiert ein Attribut mit dem Namen *attributeName* und dem Wert *attributeValue*.  
  
####  <a name="BKMK_Pre_defined_attributes"></a> Vordefinierte Attribute  
 Diese vordefinierten Attributmakros können für die Makros `TEST_METHOD_ATTRIBUTE`, `TEST_CLASS_ATTRIBUTE` OR `TEST_MODULE_ATTRIBUTE` ersetzt, das oben beschrieben wird.  
  
```cpp  
TEST_OWNER(ownerAlias)  
```  
  
 Definiert ein Attribut mit dem Namen `Owner` und der Attributwert von *ownerAlias*.  
  
```cpp  
TEST_DESCRIPTION(description)  
```  
  
 Definiert ein Attribut mit dem Namen `Description` und der Attributwert von *description*.  
  
```cpp  
TEST_PRIORITY(priority)  
```  
  
 Definiert ein Attribut mit dem Namen `Priority` und der Attributwert von *priority*.  
  
```cpp  
TEST_WORKITEM(workitem)  
```  
  
 Definiert ein Attribut mit dem Namen `WorkItem` und der Attributwert von *workItem*.  
  
```cpp  
TEST_IGNORE()  
```  
  
 Definiert ein Attribut mit dem Namen `Ignore` und der Attributwert von `true`.  
  
##  <a name="BKMK_CppUnitTestAssert_h"></a> CppUnitTestAssert.h  
  
###  <a name="BKMK_General_Asserts"></a> Allgemeine Assertionen  
  
####  <a name="BKMK_General_Are_Equal"></a> Stellen Sie gleich  
 Überprüfen Sie, ob zwei Objekte gleich sind  
  
```cpp  
template<typename T>   
static void AreEqual(  
    const T& expected,   
    const T& actual,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Überprüfen Sie, ob zwei double\-Werte gleich sind  
  
```cpp  
static void AreEqual(  
    double expected,   
    double actual,   
    double tolerance,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Überprüfen Sie, ob zwei unverankert gleich sind  
  
```cpp  
static void AreEqual(  
    float expected,   
    float actual,   
    float tolerance,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Überprüfen Sie, ob zwei Zeichenfolgen übereinstimmen char\*  
  
```cpp  
static void AreEqual(  
    const char* expected,   
    const char* actual,   
    bool ignoreCase = false,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Überprüfen Sie, dass zwei w\_char\* Zeichenfolgen gleich sind  
  
```cpp  
static void AreEqual(  
    const wchar_t* expected,   
    const wchar_t* actual,   
    bool ignoreCase = false,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
####  <a name="BKMK_General_Are_Not_Equal"></a> Achten Sie nicht gleich  
 Überprüfen Sie, ob zwei double\-Werte nicht gleich sind  
  
```cpp  
static void AreNotEqual(  
    double notExpected,   
    double actual,   
    double tolerance,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Überprüfen Sie, ob zwei unverankert nicht gleich sind  
  
```cpp  
static void AreNotEqual(  
    float notExpected,   
    float actual,   
    float tolerance,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Überprüfen Sie, ob zwei char\* Zeichenfolgen nicht gleich sind  
  
```cpp  
static void AreNotEqual(  
    const char* notExpected,   
    const char* actual,   
    bool ignoreCase = false,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Überprüfen Sie, dass zwei w\_char\* Zeichenfolgen nicht gleich sind  
  
```cpp  
static void AreNotEqual(  
    const wchar_t* notExpected,   
    const wchar_t* actual,   
    bool ignoreCase = false,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Überprüfen Sie, ob zwei Verweise nicht auf Grundlage operator\=\= gleich sind.  
  
```cpp  
template<typename T>   
static void AreNotEqual(  
    const T& notExpected,   
    const T& actual,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
####  <a name="BKMK_General_Are_Same"></a> Sind gleich  
 Überprüfen Sie, dass zwei Referenzen über dieselbe Objektinstanz \(Identität\) verweisen.  
  
```cpp  
template<typename T>   
static void AreSame(  
    const T& expected,   
    const T& actual,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
####  <a name="BKMK_General_Are_Not_Same"></a> Nicht identisch sind  
 Überprüfen Sie, ob zwei Verweise nicht dieselbe Objektinstanz \(Identität\) verweisen.  
  
```cpp  
template<typename T>   
static void AreNotSame (  
    const T& notExpected,   
    const T& actual,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
####  <a name="BKMK_General_Is_Null"></a> Ist NULL  
 Überprüfen Sie, dass ein Zeiger NULL ist.  
  
```cpp  
template<typename T>   
static void IsNull(  
    const T* actual,  
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
####  <a name="BKMK_General_Is_Not_Null"></a> Ist nicht NULL  
 Überprüfen Sie, dass ein Zeiger nicht NULL ist  
  
```cpp  
template<typename T>   
static void IsNotNull(  
    const T* actual,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
####  <a name="BKMK_General_Is_True"></a> Ist "True"  
 Überprüfen, ob eine Bedingung zutrifft  
  
```cpp  
static void IsTrue(  
    bool condition,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
####  <a name="BKMK_General_Is_False"></a> Ist falsch  
 Überprüfen, ob eine Bedingung falsch ist  
  
```cpp  
static void IsFalse(  
    bool condition,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
####  <a name="BKMK_General_Fail"></a> Fail  
 Erzwingen Sie das fehlerhaft werden Testfallergebnis,  
  
```cpp  
static void Fail(  
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
###  <a name="BKMK_WinRT_Asserts"></a> Windows Runtime\-Assertionen  
  
####  <a name="BKMK_WinRT_Are_Equal"></a> Stellen Sie gleich  
 Überprüft, ob zwei Windows Runtime\-Zeiger gleich sind.  
  
```  
template<typename T>   
static void AreEqual(  
    T^ expected,   
    T^ actual,   
    Platform::String^ message = nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
 Überprüft, ob zwei Platform::String^\-Zeichenfolgen gleich sind.  
  
```  
template<typename T>   
static void AreEqual(  
    T^ expected,   
    T^ actual,   
    Platform::String^ message= nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
####  <a name="BKMK_WinRT_Are_Same"></a> Sind gleich  
 Überprüft, ob zwei Windows Runtime\-Verweise das gleiche Objekt verweisen.  
  
```  
template<typename T>   
static void AreSame(  
    T% expected,   
    T% actual,   
    Platform::String^ message= nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
####  <a name="BKMK_WinRT_Are_Not_Equal"></a> Achten Sie nicht gleich  
 Überprüft, ob zwei Windows Runtime\-Zeiger nicht gleich sind.  
  
```  
template<typename T>   
static void AreNotEqual(  
    T^ notExpected,   
    T^ actual,   
    Platform::String^ message = nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
 Überprüft, ob zwei Platform::String^\-Zeichenfolgen nicht gleich sind.  
  
```  
static void AreNotEqual(  
    Platform::String^ notExpected,   
    Platform::String^ actual,   
    bool ignoreCase = false,   
    Platform::String^ message= nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
####  <a name="BKMK_WinRT_Are_Not_Same"></a> Nicht identisch sind  
 Überprüft, ob zwei Windows Runtime\-Verweise nicht das gleiche Objekt verweisen.  
  
```  
template<typename T>   
static void AreNotSame(  
    T% notExpected,   
    T% actual,   
    Platform::String^ message= nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
####  <a name="BKMK_WinRT_Is_Null"></a> Ist NULL  
 Überprüft, ob ein Windows Runtime\-Zeiger ein nullptr ist.  
  
```  
template<typename T>   
static void IsNull(  
    T^ actual,  
    Platform::String^ message = nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
####  <a name="BKMK_WinRT_Is_Not_Null"></a> Ist nicht NULL  
 Überprüft, ob ein Windows Runtime\-Zeiger kein nullptr ist.  
  
```  
template<typename T>   
static void IsNotNull(  
    T^ actual,   
    Platform::String^ message= nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
###  <a name="BKMK_Exception_Asserts"></a> Ausnahme\-Assertionen  
  
####  <a name="BKMK_Expect_Exception"></a> Rechnen Sie Ausnahme  
 Überprüfen, ob eine Funktion eine Ausnahme auslöst:  
  
```  
template<typename _EXPECTEDEXCEPTION, typename _FUNCTOR>   
static void ExpectException(  
    _FUNCTOR functor,   
    const wchar_t* message= NULL,   
    const __LineInfo* pLineInfo= NULL)  
```  
  
 Überprüfen, ob eine Funktion eine Ausnahme auslöst:  
  
```  
template<typename _EXPECTEDEXCEPTION, typename _RETURNTYPE>   
    static void ExpectException(  
    _RETURNTYPE (*func)(),   
    const wchar_t* message= NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
##  <a name="BKMK_CppUnitTestLogger_h"></a> CppUnitTestLogger.h  
  
###  <a name="BKMK_Logger"></a> Protokollierung  
 Die Protokollierungsklasse enthält statische Methoden, um zu schreiben  
  
```  
class Logger  
```  
  
###  <a name="BKMK_Write_Message"></a> Nachricht schreiben  
  
```  
static void   
Logger::WriteMessage(const wchar_t* message)  
```  
  
```  
static void   
Logger::WriteMessage(const char* message)  
```  
  
## Beispiel  
 Dieser Code ist ein Beispiel aus  
  
```  
////////////////////////////////////////////////////////////  
/* USAGE EXAMPLE  
// The following is an example of VSCppUnit usage.  
// It includes examples of attribute metadata, fixtures,  
// unit tests with assertions, and custom logging.  
  
#include <CppUnitTest.h>  
  
using namespace Microsoft::VisualStudio::CppUnitTestFramework;  
  
BEGIN_TEST_MODULE_ATTRIBUTE()  
    TEST_MODULE_ATTRIBUTE(L"Date", L"2010/6/12")  
END_TEST_MODULE_ATTRIBUTE()  
  
TEST_MODULE_INITIALIZE(ModuleInitialize)  
{  
    Logger::WriteMessage("In Module Initialize");  
}  
  
TEST_MODULE_CLEANUP(ModuleCleanup)  
{  
    Logger::WriteMessage("In Module Cleanup");  
}  
  
TEST_CLASS(Class1)  
{  
  
public:  
  
    Class1()  
    {  
        Logger::WriteMessage("In Class1");  
    }  
  
    ~Class1()  
    {  
        Logger::WriteMessage("In ~Class1");  
    }  
  
    TEST_CLASS_INITIALIZE(ClassInitialize)  
    {  
        Logger::WriteMessage("In Class Initialize");  
    }  
  
    TEST_CLASS_CLEANUP(ClassCleanup)  
    {  
        Logger::WriteMessage("In Class Cleanup");  
    }  
  
    BEGIN_TEST_METHOD_ATTRIBUTE(Method1)  
        TEST_OWNER(L"OwnerName")  
        TEST_PRIORITY(1)  
    END_TEST_METHOD_ATTRIBUTE()  
  
    TEST_METHOD(Method1)  
    {     
        Logger::WriteMessage("In Method1");  
        Assert::AreEqual(0, 0);  
    }  
  
    TEST_METHOD(Method2)  
    {  
        Assert::Fail(L"Fail");  
    }  
};  
```  
  
## Siehe auch  
 [Komponententest für Code](../test/unit-test-your-code.md)   
 [Unit testing native code with Test Explorer](http://msdn.microsoft.com/de-de/8a09d6d8-3613-49d8-9ffe-11375ac4736c)   
 [Hinzufügen von Komponententests zu vorhandenen C\+\+\-Anwendungen](../test/unit-testing-existing-cpp-applications-with-test-explorer.md)
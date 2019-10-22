---
title: Verwenden von Microsoft.VisualStudio.TestTools.CppUnitTestFramework | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: d1ac9188-d79f-407e-9f3a-80dbefa66317
caps.latest.revision: 10
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c561555df40bc02c3c9f3090ee1de4c0f329bcdc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657172"
---
# <a name="using-microsoftvisualstudiotesttoolscppunittestframework"></a>Verwenden von Microsoft.VisualStudio.TestTools.CppUnitTestFramework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Thema werden die öffentlichen Member des Namespace `Microsoft::VisualStudio::CppUnitTestFramework` aufgeführt.

 Die Headerdateien befinden sich im Ordner _VisualStudio2012[x86]InstallFolder_ **\VC\UnitTest\include**.

 Die Bibliotheksdateien befinden sich im Ordner _VisualStudio2012[x86]InstallFolder_ **\VC\UnitTest\lib**.

## <a name="BKMK_In_this_topic"></a> In diesem Thema
 [CppUnitTest.h](#BKMK_CppUnitTest_h)

- [Erstellen von Testklassen und Methoden](#BKMK_Create_test_classes_and_methods)

- [Initialisieren und Bereinigen](#BKMK_Initialize_and_cleanup)

  - [Testmethoden](#BKMK_Test_methods)

  - [Testklassen](#BKMK_Test_classes)

  - [Testmodule](#BKMK_Test_modules)

- [Erstellen von Testattributen](#BKMK_Create_test_attributes)

  - [Testmethodenattribute](#BKMK_Test_method_attributes)

  - [Testklassenattribute](#BKMK_Test_class_attributes)

  - [Testmodulattribute](#BKMK_Test_module_attributes)

  - [Vordefinierte Attribute](#BKMK_Pre_defined_attributes)

    [CppUnitTestAssert.h](#BKMK_CppUnitTestAssert_h)

  - [Allgemeine Assertionen](#BKMK_General_Asserts)

    - [Gleich](#BKMK_General_Are_Equal)

    - [Ungleich](#BKMK_General_Are_Not_Equal)

    - [Stimmen überein](#BKMK_General_Are_Same)

    - [Stimmen nicht überein](#BKMK_General_Are_Not_Same)

    - [Ist Null](#BKMK_General_Is_Null)

    - [Ist nicht Null](#BKMK_General_Is_Not_Null)

    - [Ist TRUE](#BKMK_General_Is_True)

    - [Ist FALSE](#BKMK_General_Is_False)

    - [Fehler](#BKMK_General_Fail)

  - [Windows-Runtime-Assertionen](#BKMK_WinRT_Asserts)

    - [Gleich](#BKMK_WinRT_Are_Equal)

    - [Stimmen überein](#BKMK_WinRT_Are_Same)

    - [Ungleich](#BKMK_WinRT_Are_Not_Equal)

    - [Stimmen nicht überein](#BKMK_WinRT_Are_Not_Same)

    - [Ist Null](#BKMK_WinRT_Is_Null)

    - [Ist nicht Null](#BKMK_WinRT_Is_Not_Null)

  - [Ausnahme-Assertionen](#BKMK_Exception_Asserts)

    - [Ausnahme erwarten](#BKMK_Expect_Exception)

      [CppUnitTestLogger.h](#BKMK_CppUnitTestLogger_h)

    - [Protokollierung](#BKMK_Logger)

    - [Nachricht schreiben](#BKMK_Write_Message)

## <a name="BKMK_CppUnitTest_h"></a> CppUnitTest.h

### <a name="BKMK_Create_test_classes_and_methods"></a> Erstellen von Testklassen und Methoden

```cpp
TEST_CLASS(className)
```

 Erforderlich für jede Klasse, die Testmethoden enthält. Bezeichnet *className* als Testklasse. `TEST_CLASS` muss im Gültigkeitsbereich des Namespace deklariert werden .

```cpp
TEST_METHOD(methodName)
{
    // test method body
}

```

 Definiert *methodName* als Testmethode. `TEST_METHOD` muss im Gültigkeitsbereich der Klasse der Methode deklariert werden.

### <a name="BKMK_Initialize_and_cleanup"></a> Initialisieren und Bereinigen

#### <a name="BKMK_Test_methods"></a> Testmethoden

```cpp
TEST_METHOD_INITIALIZE(methodName)
{
    // method initialization code
}

```

 Definiert *methodName* als Methode, die vor jeder Testmethode ausgeführt wird. `TEST_METHOD_INITIALIZE` kann in einer Testklasse nur einmal definiert werden und muss in der Testklasse definiert werden.

```cpp
TEST_METHOD_CLEANUP(methodName)
{
    // test method cleanup  code
}

```

 Definiert *methodName* als Methode, die nach jeder Testmethode ausgeführt wird. `TEST_METHOD_CLEANUP` kann in einer Testklasse nur einmal definiert werden und muss im Gültigkeitsbereich der Testklasse definiert werden.

#### <a name="BKMK_Test_classes"></a> Testklassen

```cpp
TEST_CLASS_INITIALIZE(methodName)
{
    // test class initialization  code
}

```

 Definiert *methodName* als Methode, die nach dem Erstellen der einzelnen Testmethoden ausgeführt wird. `TEST_CLASS_INITIALIZE` kann in einer Testklasse nur einmal definiert werden und muss im Gültigkeitsbereich der Testklasse definiert werden.

```cpp
TEST_CLASS_CLEANUP(methodName)
{
    // test class cleanup  code
}

```

 Definiert *methodName* als Methode, die nach dem Erstellen der einzelnen Testmethoden ausgeführt wird. `TEST_CLASS_CLEANUP` kann in einer Testklasse nur einmal definiert werden und muss im Gültigkeitsbereich der Testklasse definiert werden.

#### <a name="BKMK_Test_modules"></a> Testmodule

```cpp
TEST_MODULE_INITIALIZE(methodName)
{
    // module initialization code
}
```

 Definiert die Methode *methodName*, die beim Laden eines Moduls ausgeführt wird. `TEST_MODULE_INITIALIZE` kann in einem Testmodul nur einmal definiert werden und muss im Gültigkeitsbereich des Namespace deklariert werden.

```cpp
TEST_MODULE_CLEANUP(methodName)
```

 Definiert die Methode *methodName*, die beim Entladen eines Moduls ausgeführt wird. `TEST_MODULE_CLEANUP` kann in einem Testmodul nur einmal definiert werden und muss im Gültigkeitsbereich des Namespace deklariert werden.

### <a name="BKMK_Create_test_attributes"></a> Erstellen von Testattributen

#### <a name="BKMK_Test_method_attributes"></a> Testmethodenattribut

```cpp
BEGIN_TEST_METHOD_ATTRIBUTE(testMethodName)
    TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_METHOD_ATTRIBUTE()
```

 Fügt die Attribute hinzu, die mit einem oder mehreren `TEST_METHOD_ATTRIBUTE`-Makros der Testmethode *testClassName* definiert werden.

 Ein `TEST_METHOD_ATTRIBUTE`-Makro definiert ein Attribut mit dem Namen *attributeName* und dem Wert *attributeValue*.

#### <a name="BKMK_Test_class_attributes"></a> Testklassenattribute

```cpp
BEGIN_TEST_CLASS_ATTRIBUTE(testClassName)
    TEST_CLASS_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_CLASS_ATTRIBUTE()
```

 Fügt die Attribute hinzu, die mit einem oder mehreren `TEST_CLASS_ATTRIBUTE`-Makros der Testklasse *testClassName* definiert werden.

 Ein `TEST_CLASS_ATTRIBUTE`-Makro definiert ein Attribut mit dem Namen *attributeName* und dem Wert *attributeValue*.

#### <a name="BKMK_Test_module_attributes"></a> Testmodulattribute

```cpp
BEGIN_TEST_MODULE_ATTRIBUTE(testModuleName)
    TEST_MODULE_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_MODULE_ATTRIBUTE()
```

 Fügt die Attribute hinzu, die mit einem oder mehreren `TEST_MODULE_ATTRIBUTE`-Makros der Testmodule *testModuleName* definiert werden.

 Ein `TEST_MODULE_ATTRIBUTE`-Makro definiert ein Attribut mit dem Namen *attributeName* und dem Wert *attributeValue*.

#### <a name="BKMK_Pre_defined_attributes"></a> Vordefinierte Attribute
 Diese Makros mit vordefinierten Attributen können anstelle der oben beschriebenen Makros `TEST_METHOD_ATTRIBUTE`, `TEST_CLASS_ATTRIBUTE` oder `TEST_MODULE_ATTRIBUTE` verwendet werden.

```cpp
TEST_OWNER(ownerAlias)
```

 Definiert ein Attribut mit dem Namen `Owner` und dem Attributwert *ownerAlias*.

```cpp
TEST_DESCRIPTION(description)
```

 Definiert ein Attribut mit dem Namen `Description` und dem Attributwert *description*.

```cpp
TEST_PRIORITY(priority)
```

 Definiert ein Attribut mit dem Namen `Priority` und dem Attributwert *priority*.

```cpp
TEST_WORKITEM(workitem)
```

 Definiert ein Attribut mit dem Namen `WorkItem` und dem Attributwert *workItem*.

```cpp
TEST_IGNORE()
```

 Definiert ein Attribut mit dem Namen `Ignore` und dem Attributwert `true`.

## <a name="BKMK_CppUnitTestAssert_h"></a> CppUnitTestAssert.h

### <a name="BKMK_General_Asserts"></a> Allgemeine Assertionen

#### <a name="BKMK_General_Are_Equal"></a> Gleich
 Überprüft, ob zwei Objekte gleich sind.

```cpp
template<typename T>
static void AreEqual(
    const T& expected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Überprüft, ob zwei double-Elemente gleich sind.

```cpp
static void AreEqual(
    double expected,
    double actual,
    double tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Überprüft, ob zwei float-Elemente gleich sind.

```cpp
static void AreEqual(
    float expected,
    float actual,
    float tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Überprüft, ob zwei char*-Zeichenfolgen gleich sind.

```cpp
static void AreEqual(
    const char* expected,
    const char* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Überprüft, ob zwei w_char*-Zeichenfolgen gleich sind.

```cpp
static void AreEqual(
    const wchar_t* expected,
    const wchar_t* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="BKMK_General_Are_Not_Equal"></a> Ungleich
 Überprüft, ob zwei double-Elemente ungleich sind.

```cpp
static void AreNotEqual(
    double notExpected,
    double actual,
    double tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Überprüft, ob zwei float-Elemente ungleich sind.

```cpp
static void AreNotEqual(
    float notExpected,
    float actual,
    float tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Überprüft, ob zwei char*-Zeichenfolgen ungleich sind.

```cpp
static void AreNotEqual(
    const char* notExpected,
    const char* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Überprüft, ob zwei w_char*-Zeichenfolgen ungleich sind.

```cpp
static void AreNotEqual(
    const wchar_t* notExpected,
    const wchar_t* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Überprüft mit operator==, ob zwei Verweise ungleich sind.

```cpp
template<typename T>
static void AreNotEqual(
    const T& notExpected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="BKMK_General_Are_Same"></a> Stimmen überein
 Überprüft, ob zwei Verweise auf dieselbe Objektinstanz (Identität) verweisen.

```cpp
template<typename T>
static void AreSame(
    const T& expected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="BKMK_General_Are_Not_Same"></a> Stimmen nicht überein
 Überprüft, ob zwei Verweise nicht auf dieselbe Objektinstanz (Identität) verweisen.

```cpp
template<typename T>
static void AreNotSame (
    const T& notExpected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="BKMK_General_Is_Null"></a> Ist Null
 Überprüft, ob ein Zeiger NULL ist.

```cpp
template<typename T>
static void IsNull(
    const T* actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="BKMK_General_Is_Not_Null"></a> Ist nicht Null
 Überprüft, ob ein Zeiger nicht NULL ist.

```cpp
template<typename T>
static void IsNotNull(
    const T* actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="BKMK_General_Is_True"></a> Ist TRUE
 Überprüft, ob eine Bedingung wahr ist.

```cpp
static void IsTrue(
    bool condition,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="BKMK_General_Is_False"></a> Ist FALSE
 Überprüft, ob eine Bedingung falsch ist.

```cpp
static void IsFalse(
    bool condition,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="BKMK_General_Fail"></a> Fehler
 Setzt durch, dass das Ergebnis des Testfalls als Fehler zählt.

```cpp
static void Fail(
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

### <a name="BKMK_WinRT_Asserts"></a> Windows-Runtime-Assertionen

#### <a name="BKMK_WinRT_Are_Equal"></a> Gleich
 Überprüft, ob zwei Windows-Runtime-Zeiger gleich sind.

```
template<typename T>
static void AreEqual(
    T^ expected,
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

 Überprüft, ob zwei Platform::String^-Zeichenfolgen gleich sind.

```
template<typename T>
static void AreEqual(
    T^ expected,
    T^ actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="BKMK_WinRT_Are_Same"></a> Stimmen überein
 Überprüft, ob zwei Windows-Runtime-Verweise auf dasselbe Objekt verweisen.

```
template<typename T>
static void AreSame(
    T% expected,
    T% actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="BKMK_WinRT_Are_Not_Equal"></a> Ungleich
 Überprüft, ob zwei Windows-Runtime-Zeiger ungleich sind.

```
template<typename T>
static void AreNotEqual(
    T^ notExpected,
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

 Überprüft, ob zwei Platform::String^-Zeichenfolgen ungleich sind.

```
static void AreNotEqual(
    Platform::String^ notExpected,
    Platform::String^ actual,
    bool ignoreCase = false,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="BKMK_WinRT_Are_Not_Same"></a> Stimmen nicht überein
 Überprüft, ob zwei Windows-Runtime-Verweise nicht auf dasselbe Objekt verweisen.

```
template<typename T>
static void AreNotSame(
    T% notExpected,
    T% actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="BKMK_WinRT_Is_Null"></a> Ist Null
 Überprüft, ob ein Windows-Runtime-Zeiger ein „nullptr“ ist.

```
template<typename T>
static void IsNull(
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="BKMK_WinRT_Is_Not_Null"></a> Ist nicht Null
 Überprüft, ob ein Windows-Runtime-Zeiger kein „nullptr“ ist.

```
template<typename T>
static void IsNotNull(
    T^ actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

### <a name="BKMK_Exception_Asserts"></a> Ausnahme-Assertionen

#### <a name="BKMK_Expect_Exception"></a> Ausnahme erwarten
 Überprüft, ob eine Funktion eine Ausnahme auslöst:

```
template<typename _EXPECTEDEXCEPTION, typename _FUNCTOR>
static void ExpectException(
    _FUNCTOR functor,
    const wchar_t* message= NULL,
    const __LineInfo* pLineInfo= NULL)
```

 Überprüft, ob eine Funktion eine Ausnahme auslöst:

```
template<typename _EXPECTEDEXCEPTION, typename _RETURNTYPE>
    static void ExpectException(
    _RETURNTYPE (*func)(),
    const wchar_t* message= NULL,
    const __LineInfo* pLineInfo = NULL)
```

## <a name="BKMK_CppUnitTestLogger_h"></a> CppUnitTestLogger.h

### <a name="BKMK_Logger"></a> Protokollierung
 Die Protokollierungsklasse enthält statische Methoden zum Beschreiben

```
class Logger
```

### <a name="BKMK_Write_Message"></a> Nachricht schreiben

```
static void
Logger::WriteMessage(const wchar_t* message)
```

```
static void
Logger::WriteMessage(const char* message)
```

## <a name="example"></a>Beispiel
 Beispiel für einen Code

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

## <a name="see-also"></a>Siehe auch
 Komponententests für [den Code](../test/unit-test-your-code.md) [Unit Testing Native Code with Test Explorer](https://msdn.microsoft.com/8a09d6d8-3613-49d8-9ffe-11375ac4736c) [Hinzufügen von Komponenten C++ Tests zu vorhandenen Anwendungen](../test/unit-testing-existing-cpp-applications-with-test-explorer.md)

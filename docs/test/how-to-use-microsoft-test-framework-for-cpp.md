---
title: Verwenden des Microsoft-Komponententest-Frameworks für C++
ms.date: 11/15/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: mblome
manager: douge
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: 88265c1ac86b5b1c1cd90ef428c9c2c770d9f2a2
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "53068259"
---
# <a name="use-the-microsoft-unit-testing-framework-for-c-in-visual-studio"></a>Verwenden des Microsoft-Komponententest-Frameworks für C++ in Visual Studio

Das Microsoft-Komponententest-Framework für C++ ist standardmäßig in der Workload **Desktopentwicklung mit C++** enthalten.

##  <a name="separate_project"></a> Schreiben von Komponententests in einem separaten Projekt

In der Regel führen Sie Ihren Testcode in einem eigenen Projekt in derselben Projektmappe aus, in der sich der Code befindet, den Sie testen möchten. Weitere Informationen zum Einrichten und Konfigurieren eines neuen Testprojekts finden Sie unter [Writing Unit Tests for C/C++ (Schreiben von Komponententests für C/C++)](writing-unit-tests-for-c-cpp.md).

##  <a name="same_project"></a> Schreiben von Komponententests im gleichen Projekt

In einigen Fällen (z.B. beim Testen von nicht exportierten Funktionen in einer DLL) sollten Sie die Tests im gleichen Projekt wie das Programm erstellen, das Sie testen. So schreiben Sie Komponententests im gleichen Projekt:

1. Ändern Sie die Projekteigenschaften, um die Header und Bibliotheksdateien einzuschließen, die für die Komponententests erforderlich sind.

   1. Klicken Sie im **Projektmappen-Explorer** erst mit der rechten Maustaste auf den Projektknoten für das Programm, das Sie testen, und klicken Sie dann auf **Eigenschaften** > **Konfigurationseigenschaften** > **VC++-Verzeichnisse**.

   2. Klicken Sie in den folgenden Zeilen auf den Pfeil nach unten, und wählen Sie **<Edit>** aus:


      | Verzeichnis | Eigenschaft |
      |-| - |
      | **Includeverzeichnisse** | **$(VCInstallDir)UnitTest\include;$(IncludePath)** |
      | **Bibliotheksverzeichnisse** | **$(VCInstallDir)UnitTest\lib;$(LibraryPath)** |


2. Fügen Sie eine C++-Komponententestdatei hinzu:

   -   Klicken Sie erst mit der rechten Maustaste auf den Projektknoten im **Projektmappen-Explorer** und dann mit der Linken auf **Hinzufügen** > **Neues Element** > **C++-Komponententest**.

## <a name="write-the-tests"></a>Schreiben der Tests

*CPP*-Dateien mit Testklassen müssen „CppUnitTest.h“ und eine using-Anweisung für `using namespace Microsoft::VisualStudio::CppUnitTestFramework` enthalten. Das Testprojekt ist bereits für Sie konfiguriert. Es enthält ebenfalls eine Namespacedefinition und eine TEST_CLASS mit einer TEST_METHOD für Ihre ersten Schritte. Sie können den Namespacenamen und die Namen ändern, die in den Klassen- und Methodenmakros in Klammern stehen.

Für das Initialisieren von Testmodulen und für das Bereinigen von Ressourcen nach Abschluss des Tests werden spezielle Makros definiert. Diese Makros generieren Code, der vor dem ersten Zugriff auf eine Klasse oder Methode und nach der Ausführung des letzten Tests ausgeführt wird. Weitere Informationen finden Sie unter [Initialize and cleanup (Initialisieren und Bereinigen)](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#Initialize_and_cleanup).

Verwenden Sie die statischen Methoden der [Assert](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#general_asserts)-Klasse, um Testbedingungen zu definieren. Verwenden Sie die [Logger](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#logger)-Klasse, um Nachrichten in das **Ausgabefenster** zu schreiben. Hinzufügen von Attributen zu den Testmethoden

## <a name="run-the-tests"></a>Tests ausführen

1. Klicken Sie im Menü **Test** auf **Windows** > **Test-Explorer**.
2. Wenn Ihre Tests nicht im Fenster angezeigt werden, erstellen Sie das Testprojekt, indem Sie mit der rechten Maustaste auf dessen Knoten im **Projektmappen-Explorer** klicken und **Erstellen** oder **Neu erstellen** auswählen.

3. Klicken Sie im **Test-Explorer** auf **Alle ausführen**, oder wählen Sie die Tests aus, die Sie ausführen möchten. Klicken Sie für weitere Optionen, einschließlich des Ausführens im Debugmodus mit aktivierten Breakpoints, mit der rechten Maustaste auf einen Test.
4. Wählen Sie **Tests** aus dem Dropdownmenü im **Ausgabefenster** aus, um die von der `Logger`-Klasse geschriebenen Meldungen anzuzeigen.

   ![Testmeldungen im C++-Ausgabefenster](media/cpp-test-output-window.png)

## <a name="define-traits-to-enable-grouping"></a>Definieren von Merkmalen für das Aktivieren der Gruppierung

Sie können Merkmale für Testmethoden definieren, um Tests im **Test-Explorer** zu kategorisieren und zu gruppieren. Verwenden Sie zum Definieren eines Merkmals das `TEST_METHOD_ATTRIBUTE` -Makro. Beispiel – Definieren eines Merkmals mit dem Namen `TEST_MY_TRAIT`:

```cpp
#define TEST_MY_TRAIT(traitValue) TEST_METHOD_ATTRIBUTE(L"MyTrait", traitValue)
```

 Verwenden des definierten Merkmals in den Komponententests:

```cpp
BEGIN_TEST_METHOD_ATTRIBUTE(Method1)
    TEST_OWNER(L"OwnerName")
    TEST_PRIORITY(1)
    TEST_MY_TRAIT(L"thisTraitValue")
END_TEST_METHOD_ATTRIBUTE()

TEST_METHOD(Method1)
{
    Logger::WriteMessage("In Method1");
    Assert::AreEqual(0, 0);
}
```

### <a name="c-trait-attribute-macros"></a>C++-Merkmalsattributmakros

Die folgenden vordefinierten Merkmale befinden sich in `CppUnitTest.h`. Weitere Informationen finden Sie unter [Referenz für die C++-API „Microsoft.VisualStudio.TestTools.CppUnitTestFramework“](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md).

|Makro|Beschreibung|
|-|-----------------|
|`TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)`|Verwenden Sie zum Definieren eines Merkmals das TEST_METHOD_ATTRIBUTE-Makro.|
|`TEST_OWNER(ownerAlias)`|Verwenden Sie das vordefinierte Merkmal "Besitzer", um einen Besitzer der Testmethode anzugeben.|
|`TEST_PRIORITY(priority)`|Verwenden Sie das vordefinierte Merkmal "Priorität", um den Testmethoden relative Prioritäten zuzuweisen.|

## <a name="see-also"></a>Siehe auch

- [Schnellstart: Testgesteuerte Entwicklung mit dem Test-Explorer](../test/quick-start-test-driven-development-with-test-explorer.md)

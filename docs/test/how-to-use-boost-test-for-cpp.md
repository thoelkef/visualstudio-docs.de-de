---
title: Verwenden von Boost.Test für C++
description: Verwenden von Boost.Test zum Erstellen von Komponententests in Visual Studio.
ms.date: 01/29/2020
ms.topic: conceptual
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 0a1a621c7ee7175d86b2cbcf9a6e2c02c0aecbb3
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "76922923"
---
# <a name="how-to-use-boosttest-for-c-in-visual-studio"></a>Verwenden von Boost.Test für C++ in Visual Studio

In Visual Studio 2017 und höher ist der Testadapter „Boost.Test“ als Standardkomponente in die Visual Studio-IDE integriert. Es ist eine Komponente der Workload **Desktopentwicklung mit C++** .

![Testadapter für Boost.Test](media/cpp-boost-component.png)

Wenn die Workload **Desktopentwicklung mit C++** nicht installiert ist, öffnen Sie **Visual Studio-Installer**. Wählen Sie zunächst die Workload **Desktopentwicklung mit C++** und anschließend die Schaltfläche **Ändern** aus.

## <a name="install-boost"></a>Installieren von Boost

Boost.Test erfordert [Boost](https://www.boost.org/). Wenn Sie Boost noch nicht installiert haben, sollten Sie den vcpkg-Paket-Manager verwenden.

1. Falls Sie diesen noch nicht installiert haben, holen Sie dies nach, indem Sie die unter [Vcpkg: Ein C++-Paket-Manager für Windows](/cpp/vcpkg) beschriebenen Schritte ausführen.

1. Installieren Sie die dynamische oder statische Bibliothek für Boost.Test:

    - Führen Sie `vcpkg install boost-test` aus, um die dynamische Bibliothek für Boost.Test zu installieren.

       -ODER-

    - Führen Sie `vcpkg install boost-test:x86-windows-static` aus, um die statische Bibliothek für Boost.Test zu installieren.

1. Führen Sie `vcpkg integrate install` aus, um Visual Studio mit der Bibliothek zu konfigurieren und Pfade in den Boost-Headern und Binärdateien einzuschließen.

Sie können entscheiden, wie Sie die Tests in Ihrer Visual Studio-Projektmappe konfigurieren möchten: Sie können den Testcode im zu testenden Projekt ablegen oder ein separates Testprojekt dafür erstellen. Beide Optionen haben Vor- und Nachteile.

## <a name="add-tests-inside-your-project"></a>Hinzufügen von Tests in Ihrem Projekt

In Visual Studio 2017, Version 15.6 und höher, können Sie Ihrem Projekt eine Elementvorlage für Tests hinzufügen. Sowohl die Tests als auch der Code befinden sich im selben Projekt. Zum Generieren eines Testbuilds müssen Sie eine separate Buildkonfiguration erstellen. Außerdem müssen Sie die Tests aus den Debug-und Releasebuilds heraushalten.

Visual Studio 2017 Version 15.5 enthält keine vorkonfigurierten Testprojekte oder Elementvorlagen für Boost.Test. Anhand dieser Anleitungen können Sie ein separates Testprojekt erstellen und konfigurieren.

### <a name="create-a-boosttest-item"></a>Erstellen eines Boost.Test-Elements

1. Sie können eine *CPP*-Datei für Ihre Tests erstellen, indem Sie im **Projektmappen-Explorer** erst mit der rechten Maustaste auf den Projektknoten klicken und anschließend mit der linken auf **Hinzufügen** > **Neues Element**.

1. Erweitern Sie im Dialogfeld **Neues Element hinzufügen** die Optionen **Installiert** > **Visual C++**  > **Testen**. Wählen Sie **Boost.Test** aus, und klicken Sie auf **Hinzufügen**, um *Test.cpp* zu dem Projekt hinzuzufügen.

   ![Boost.Test-Elementvorlage](media/boost_test_item_template.png)

Die neue Datei *Test.cpp* enthält eine Beispieltestmethode. In diese Datei können Sie Ihre eigenen Headerdateien aufnehmen sowie Tests für Ihre App schreiben.

Die Testdatei verwendet außerdem Makros, um eine neue `main`-Routine für Testkonfigurationen zu definieren. Wenn Sie das Projekt jetzt erstellen, wird ein LNK2005-Fehler zurückgegeben, z. B. „_main already defined in main.obj“ (_main ist bereits in main.obj definiert).

### <a name="create-and-update-build-configurations"></a>Erstellen und Aktualisieren von Buildkonfigurationen

1. Zum Erstellen einer Testkonfiguration klicken Sie in der Menüleiste auf **Build** > **Konfigurations-Manager**. Öffnen Sie im Dialogfeld **Konfigurations-Manager** die Dropdownliste unter **Active solution configuration** (Aktive Projektmappenkonfiguration), und klicken Sie auf **Neu**. Geben Sie im Dialogfeld **Active solution configuration** (Aktive Projektmappenkonfiguration) einen Namen wie „Debug UnitTests“ (Debuggen, Komponententests) ein. Wählen Sie unter **Copy settings from** (Einstellungen kopieren aus) **Debug** aus, und klicken Sie **OK**.

1. Schließen Sie den Testcode aus Ihren Debugging- und Releasekonfigurationen aus: Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf die Datei „Test.cpp“, und wählen Sie **Eigenschaften** aus. Öffnen Sie im Dialogfeld **Eigenschaftenseiten** die Dropdownliste **Konfiguration**, und klicken Sie auf **Alle Konfigurationen**. Wählen Sie **Konfigurationseigenschaften** > **Allgemein** aus, und öffnen Sie die Dropdownliste für die Eigenschaft **Vom Build ausgeschlossen**. Wählen Sie **Ja** aus, und klicken Sie dann auf **Übernehmen**, um die Änderungen zu speichern.

1. Wenn Sie möchten, dass der Testcode in der Konfiguration „Debug UnitTests“ (Debuggen, Komponententests) enthalten ist, wählen Sie im Dialogfeld **Eigenschaftenseiten** in der Dropdownliste **Konfiguration** die Konfiguration **Debug UnitTests** (Debuggen, Komponententests) aus. Wählen Sie für die Eigenschaft **Vom Build ausgeschlossen** den Wert **Nein** aus, und klicken Sie auf **OK** aus, um die Änderungen zu speichern.

1. Schließen Sie den Hauptcode aus Ihrer Konfiguration „Debug UnitTests“ (Debuggen, Komponententests) aus. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf die Datei, die Ihre `main`-Funktion enthält, und wählen Sie **Eigenschaften** aus. Öffnen Sie im Dialogfeld **Eigenschaftenseiten** die Dropdownliste **Konfiguration**, und klicken Sie auf **Debug UnitTests** (Debuggen, Komponententests). Wählen Sie **Konfigurationseigenschaften** > **Allgemein** aus, und öffnen Sie die Dropdownliste für die Eigenschaft **Vom Build ausgeschlossen**. Wählen Sie **Ja** aus, und klicken Sie dann auf **OK**, um die Änderungen zu speichern.

1. Legen Sie die Projektmappenkonfiguration auf **Debug UnitTests** (Debuggen, Komponententests) fest, und erstellen Sie dann Ihr Projekt, damit der **Test-Explorer** die Methode ermitteln kann.

Solange der von Ihnen erstellte Konfigurationsname mit den Wörtern „Debug“ oder „Release“ beginnt, werden die entsprechenden Boost.Test-Bibliotheken automatisch erkannt.

In der Elementvorlage wird die Boost.Test-Variante mit einzelner Kopfzeile verwendet, aber Sie können den #include-Pfad ändern, sodass die Variante mit der eigenständigen Bibliothek genutzt wird. Weitere Informationen finden Sie unter [Hinzufügen von include-Anweisungen](#add-include-directives).

## <a name="create-a-separate-test-project"></a>Erstellen eines separaten Testprojekts

Oftmals ist es einfacher, ein separates Projekt für Ihre Tests zu verwenden. So müssen Sie keine besondere Testkonfiguration für das Projekt erstellen oder Testdateien aus Debug- und Releasebuilds ausschließen.

### <a name="to-create-a-separate-test-project"></a>So erstellen Sie ein separates Testprojekt

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Knoten „Projektmappe“ und dann auf **Hinzufügen** > **Neues Projekt**.

1. Wählen Sie im Dialogfeld **Neues Projekt hinzufügen** in den Filter-Dropdownlisten **C++** , **Windows** und **Konsole** aus. Wählen Sie die Vorlage **Konsolen-App**, und klicken Sie anschließend auf **Weiter**.

1. Benennen Sie das Projekt, und klicken Sie auf **Erstellen**.

1. Löschen Sie die `main`-Funktion aus der *CPP*-Datei.

1. Wenn Sie die Boost.Test-Version mit einzelnen Headern oder dynamischen Bibliotheken verwenden, fahren Sie mit dem Abschnitt [Hinzufügen von include-Anweisungen](#add-include-directives) fort. In der Version mit den statischen Bibliotheken müssen Sie jedoch einige zusätzliche Konfigurationsschritte vornehmen:

   a. Entladen Sie die Projektdatei zunächst, damit Sie sie bearbeiten können. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Projekt entladen** aus. Klicken Sie dann mit der rechten Maustaste auf den Projektknoten, und wählen Sie **<name\> bearbeiten.vcxproj** aus.

   b. Fügen Sie der Eigenschaftengruppe **Global** auf folgende Weise zwei Zeilen hinzu:

    ```xml
    <PropertyGroup Label="Globals">
    ....
        <VcpkgTriplet>x86-windows-static</VcpkgTriplet>
        <VcpkgEnabled>true</VcpkgEnabled>
    </PropertyGroup>
    ```

   c. Speichern und schließen Sie die *\*VCXPROJ*-Datei, und laden Sie das Projekt anschließend neu.

   d. Klicken Sie mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Eigenschaften** aus, um **Eigenschaftenseiten** zu öffnen.

   e. Erweitern Sie **C/C++**  > **Codegenerierung**, und wählen Sie anschließend **Laufzeitbibliothek** aus. Wählen Sie **/MTd** aus, um die statische Laufzeitbibliothek zu debuggen, oder **/MT**, um die statische Laufzeitbibliothek freizugeben.

   f. Erweitern Sie **Linker** > **System**. Überprüfen Sie, ob **SubSystem** auf **Konsole** festgelegt ist.

   g. Klicken Sie auf **OK**, um die Eigenschaftenseiten zu schließen.

## <a name="add-include-directives"></a>Hinzufügen von include-Anweisungen

1. Fügen Sie Ihrer *CPP*-Testdatei alle erforderlichen `#include`-Anweisungen hinzu, um die Typen und Funktionen Ihres Programms für den Testcode anzuzeigen. Wenn Sie ein separates Testprojekt verwenden, befindet sich das Programm in der Regel auf einer gleichrangigen Ebene in der Ordnerhierarchie. Wenn Sie `#include "../"` eingeben, wird ein IntelliSense-Fenster angezeigt, und Sie können den vollständigen Pfad zur Headerdatei auswählen.

   ![Hinzufügen von #include-Direktiven](media/cpp-gtest-includes.png)

   Sie können die eigenständige Bibliothek wie folgt verwenden:

   ```cpp
   #include <boost/test/unit_test.hpp>
   ```

   Oder Sie können die Version mit einem einzelnen Header wie folgt verwenden:

   ```cpp
   #include <boost/test/included/unit_test.hpp>
   ```

   Definieren Sie anschließend `BOOST_TEST_MODULE`.

Das folgende Beispiel reicht aus, damit der Test im **Test-Explorer** sichtbar ist:

```cpp
#define BOOST_TEST_MODULE MyTest
#include <boost/test/included/unit_test.hpp\> //single-header
#include "../MyProgram/MyClass.h" // project being tested
#include <string>

BOOST_AUTO_TEST_CASE(my_boost_test)
{
    std::string expected_value = "Bill";

    // assume MyClass is defined in MyClass.h
    // and get_value() has public accessibility
    MyClass mc;
    BOOST_CHECK(expected_value == mc.get_value());
}
```

## <a name="write-and-run-tests"></a>Schreiben und Ausführen von Tests

Nun können Sie Tests für Boost.Test schreiben und ausführen. Weitere Informationen zu den Test-Makros finden Sie in der [Dokumentation zur Boost.Test-Bibliothek](https://www.boost.org/doc/libs/1_71_0/libs/test/doc/html/index.html). Weitere Informationen zum Ermitteln, Ausführen und Gruppieren Ihrer Tests mithilfe des **Test-Explorers** finden Sie unter [Ausführen von Komponententests mit dem Test-Explorer](run-unit-tests-with-test-explorer.md).

## <a name="see-also"></a>Siehe auch

- [Schreiben von Komponententests für C/C++](writing-unit-tests-for-c-cpp.md)

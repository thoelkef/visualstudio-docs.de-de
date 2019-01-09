---
title: Verwenden von Boost.Test für C++
ms.date: 01/29/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 1428efdd19782803e3091e3d09073f2cd8daec0b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53830845"
---
# <a name="how-to-use-boosttest-for-c-in-visual-studio"></a>Verwenden von Boost.Test für C++ in Visual Studio

In **Visual Studio 2017 Version 15.5** und höher ist der Testadapter Boost.Test als Standardkomponente der Workload **Desktopentwicklung mit C++** in die Visual Studio-IDE integriert.

![Testadapter für Boost.Test](media/cpp-boost-component.png)

Wenn die Workload **Desktopentwicklung mit C++** nicht installiert ist, öffnen Sie **Visual Studio-Installer**, und wählen Sie **Ändern** aus. Wählen Sie zunächst die Workload **Desktopentwicklung mit C++** und anschließend die Schaltfläche **Ändern** aus.

## <a name="install-boost"></a>Installieren von Boost

Boost.Test erfordert [Boost](http://www.boost.org/). Wenn Sie Boost noch nicht installiert haben, sollten Sie den vcpkg-Paket-Manager verwenden.

1. Falls Sie diesen noch nicht installiert haben, holen Sie dies nach, indem Sie die unter [Vcpkg: Ein C++-Paket-Manager für Windows](/cpp/vcpkg) beschriebenen Schritte ausführen.

1. Installieren Sie die dynamische oder statische Bibliothek für Boost.Test:

    - Führen Sie **vcpkg install boost-test** aus, um die dynamische Bibliothek für Boost.Test zu installieren.

       -ODER-

    - Führen Sie **vcpkg install boost-test:x86-windows-static** aus, um die dynamische Bibliothek für Boost.Test zu installieren.

1. Führen Sie **vcpkg integrate install** aus, um Visual Studio mit der Bibliothek zu konfigurieren und Pfade in den Boost-Headern und Binärdateien einzuschließen.

## <a name="add-the-item-template-visual-studio-2017-version-156-and-later"></a>Hinzufügen der Elementvorlage (Visual Studio 2017 15.6 und höher)

1. Sie können eine *CPP*-Datei für Ihre Tests erstellen, indem Sie im **Projektmappen-Explorer** erst mit der rechten Maustaste auf den Projektknoten klicken und anschließend mit der Linken auf **Neues Element hinzufügen**.

   ![Boost.Test-Elementvorlage](media/boost_test_item_template.png)

1. Die neue Datei enthält eine Beispieltestmethode. Erstellen Sie Ihr Projekt, damit der **Test-Explorer** die Methode ermitteln kann.

In der Elementvorlage wird die Boost.Test-Variante mit einzelner Kopfzeile verwendet, aber Sie können den #include-Pfad ändern, sodass die Variante mit der eigenständigen Bibliothek genutzt wird. Weitere Informationen finden Sie unter [Hinzufügen von include-Anweisungen](#add-include-directives).

## <a name="create-a-test-project-visual-studio-2017-version-155"></a>Erstellen eines Testprojekts (Visual Studio 2017 Version 15.5)

Visual Studio 2017 Version 15.5 enthält keine vorkonfigurierten Testprojekte oder Elementvorlagen für Boost.Test. Aus diesem Grund müssen Sie ein Konsolenanwendungsprojekt erstellen und konfigurieren, in dem Ihre Tests gespeichert werden können.

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Knoten „Projektmappe“ und dann auf **Hinzufügen** > **Neues Projekt**.

1. Wählen Sie im linken Bereich **Visual C++** > **Windows-Desktop** aus, und klicken Sie dann auf die Vorlage **Windows-Konsolenanwendung**.

1. Benennen Sie das Projekt, und klicken Sie auf **OK**.

1. Löschen Sie die `main`-Funktion aus der *CPP*-Datei.

1. Wenn Sie die Boost.Test-Version mit der einzelnen Kopfzeile bzw. dynamischen Bibliothek verwenden, fahren Sie mit [Hinzufügen von include-Anweisungen](#add-include-directives) fort. Bei Verwendung die statischen Bibliotheksversion müssen Sie einige zusätzliche Konfigurationsschritte vornehmen:

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

   d. Erweitern Sie **C/C++** > **Codegenerierung**, und wählen Sie anschließend **Laufzeitbibliothek** aus. Wählen Sie **/MTd** aus, um die statische Laufzeitbibliothek zu debuggen, oder **/MT**, um die statische Laufzeitbibliothek freizugeben.

   f. Erweitern Sie **Linker** > **System**. Überprüfen Sie, ob **SubSystem** auf **Konsole** festgelegt ist.

   g. Klicken Sie auf **OK**, um die Eigenschaftenseiten zu schließen.

## <a name="add-include-directives"></a>Hinzufügen von include-Anweisungen

1. Fügen Sie Ihrer *CPP*-Testdatei alle erforderlichen `#include`-Anweisungen hinzu, um die Typen und Funktionen Ihres Programms für den Testcode anzuzeigen. In der Regel befindet sich das Programm in der Ordnerhierarchie eine Ebene darüber. Wenn Sie `#include "../"` eingeben, wird ein IntelliSense-Fenster angezeigt, und Sie können den vollständigen Pfad zur Headerdatei auswählen.

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

Nun können Sie Tests für Boost.Test schreiben und ausführen. Weitere Informationen zu den Test-Makros finden Sie in der [Dokumentation zur Boost.Test-Bibliothek](http://www.boost.org/doc/libs/release/libs/test/doc/html/index.html). Weitere Informationen zum Ermitteln, Ausführen und Gruppieren Ihrer Tests mithilfe des **Test-Explorers** finden Sie unter [Ausführen von Komponententests mit dem Test-Explorer](run-unit-tests-with-test-explorer.md).

## <a name="see-also"></a>Siehe auch

- [Schreiben von Komponententests für C/C++](writing-unit-tests-for-c-cpp.md)

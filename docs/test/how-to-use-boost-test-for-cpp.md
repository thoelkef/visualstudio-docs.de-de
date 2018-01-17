---
title: "Verwenden von Boost.Test für C++ in Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 01/05/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bdf772be03f6021f499b9bf777922d6d2743e0dc
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2018
---
# <a name="how-to-use-boosttest-for-c-in-visual-studio"></a>Verwenden von Boost.Test für C++ in Visual Studio

In **Visual Studio 2017 Version 15.5** und höher ist der Testadapter Boost.Test als Standardkomponente der Workload **Desktopentwicklung mit C++** in die Visual Studio-IDE integriert.

![Testadapter für Boost.Test](media/cpp-boost-component.png "Testadapter für die Boot.Test-Komponente")

Wenn die Workload **Desktopentwicklung mit C++** nicht installiert ist, öffnen Sie **Visual Studio-Installer**, und wählen Sie **Ändern** aus. Wählen Sie zunächst die Workload **Desktopentwicklung mit C++** und anschließend die Schaltfläche **Ändern** aus.

## <a name="install-boost"></a>Installieren von Boost

Boost.Test erfordert [Boost](http://www.boost.org/). Wenn Sie Boost noch nicht installiert haben, sollten Sie den vcpkg-Paket-Manager verwenden.

1. Falls Sie diesen noch nicht installiert haben, holen Sie dies anhand der Schritte unter [vcpkg: Ein C++-Paket-Manager für Windows](/cpp/vcpkg) nach.

1. Installieren Sie die dynamische oder statische Bibliothek für Boost.Test:

    - Führen Sie `vcpkg install boost-test` aus, um die dynamische Bibliothek für Boost.Test zu installieren.
    
       -ODER-
       
    - Führen Sie `vcpkg install boost-test:x86-windows-static` aus, um die statische Bibliothek für Boost.Test zu installieren.

1. Führen Sie `vcpkg integrate install` aus, um Visual Studio mit der Bibliothek zu konfigurieren und Pfade in den Boost-Headern und Binärdateien einzuschließen.

## <a name="create-a-project-for-your-tests"></a>Erstellen eines Projekts für Ihre Tests

> [!NOTE]
> Visual Studio 2017 Version 15.5 enthält keine vorkonfigurierten Testprojekte oder Elementvorlagen für Boost.Test. Aus diesem Grund müssen Sie ein Konsolenanwendungsprojekt erstellen, in dem Ihre Tests gespeichert werden können. Testvorlagen für Boost.Test sollen in eine zukünftige Version von Visual Studio mit aufgenommen werden.

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Knoten „Projektmappe“ und dann auf **Hinzufügen** > **Neues Projekt...**.

1. Wählen Sie im linken Bereich **Visual C++** > **Windows-Desktop** aus, und klicken Sie dann auf die Vorlage **Windows-Konsolenanwendung**.

1. Benennen Sie das Projekt, und klicken Sie auf **OK**.

## <a name="link-and-configuration-boost-static-library-only"></a>Verknüpfung und Konfiguration (Nur die statische Bibliothek für Boost)

Konfigurieren Sie das Projekt, sodass es Boost.Test-Tests ausführt.

1. Entladen Sie die Projektdatei zunächst, damit Sie sie bearbeiten können. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Projekt entladen** aus. Klicken Sie dann mit der rechten Maustaste auf den Projektknoten, und wählen Sie **<name\> bearbeiten.vcxproj** aus.

1. Fügen Sie der Eigenschaftengruppe **Global** auf folgende Weise zwei Zeilen hinzu:

    ```xml
    <PropertyGroup Label="Globals">
    ....
        <VcpkgTriplet>x86-windows-static</VcpkgTriplet>
        <VcpkgEnabled>true</VcpkgEnabled>
    </PropertyGroup>
    ```
1. Speichern und schließen Sie die \*VCXPROJ-Datei, und laden Sie das Projekt anschließend neu.

1. Klicken Sie mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Eigenschaften** aus, um **Eigenschaftenseiten** zu öffnen.

1. Erweitern Sie **C/C++** > **Codegenerierung**, und wählen Sie anschließend **Laufzeitbibliothek** aus. Wählen Sie `/MTd` aus, um die statische Laufzeitbibliothek zu debuggen, oder `/MT`, um die statische Laufzeitbibliothek freizugeben.

1. Erweitern Sie **Linker > System**. Überprüfen Sie, ob **SubSystem** auf **Konsole** festgelegt ist.

1. Klicken Sie auf **OK**, um die Eigenschaftenseiten zu schließen.

## <a name="add-include-directives"></a>Hinzufügen von include-Anweisungen

1. Wenn in Ihrer CPP-Testdatei eine `main`-Funktion enthalten ist, löschen Sie diese.

1. Fügen Sie Ihrer CPP-Testdatei alle erforderlichen `#include`-Anweisungen hinzu, um die Typen und Funktionen Ihres Programms für den Testcode sichtbar zu machen. In der Regel befindet sich das Programm in der Ordnerhierarchie eine Ebene darüber. Wenn Sie `#include "../"` eingeben, wird ein IntelliSense-Fenster angezeigt, und Sie können den vollständigen Pfad zur Headerdatei auswählen.

   ![Hinzufügen von #include-Direktiven](media/cpp-gtest-includes.png "Hinzufügen von include-Anweisungen zur CPP-Testdatei")

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

BOOST_AUTO_TEST_CASE(my\_boost_test)
{
    std::string expected_value = "Bill";

    // assume MyClass is defined in MyClass.h
    // and get_value() has public accessibility
    MyClass mc;
    BOOST_CHECK(expected_value == mc.get_value());
}
```

## <a name="write-and-run-tests"></a>Schreiben und Ausführen von Tests
Nun können Sie Tests für Boost.Test schreiben und ausführen. Weitere Informationen zu den Test-Makros finden Sie in der [Dokumentation zur Boost.Test-Bibliothek](http://www.boost.org/doc/libs/1_38_0/libs/test/doc/html/index.html). Weitere Informationen zum Ermitteln, Ausführen und Gruppieren Ihrer Tests mithilfe des **Test-Explorers** finden Sie unter [Ausführen von Komponententests mit dem Test-Explorer](run-unit-tests-with-test-explorer.md).

## <a name="see-also"></a>Siehe auch
[Schreiben von Komponententests für C/C++](writing-unit-tests-for-c-cpp.md)

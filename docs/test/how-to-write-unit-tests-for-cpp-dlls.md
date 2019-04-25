---
title: Schreiben von Komponententests für C++-DLLs
ms.date: 11/04/2017
ms.topic: conceptual
ms.author: mblome
manager: jillfra
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: 7606f9f9b521d4bc752b99ad70237ef4ac6bc30e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62821047"
---
# <a name="write-unit-tests-for-c-dlls-in-visual-studio"></a>Schreiben von Komponententests für C++-DLLs in Visual Studio

 Es gibt einige Möglichkeiten, um DLL-Code zu testen, je nachdem, ob dieser die Funktionen exportiert, die Sie testen möchten. Wählen Sie eine der folgenden Methoden aus:

 **Die Komponententests rufen nur Funktionen auf, die von der DLL exportiert werden:** Fügen Sie wie unter [Schreiben von Komponententests für C/C++ in Visual Studio](writing-unit-tests-for-c-cpp.md) beschrieben ein separates Testprojekt hinzu. Fügen Sie im Testprojekt einen Verweis auf das DLL-Projekt hinzu.

 Rufen Sie die Prozedur [Verweisen auf exportierte Funktionen aus dem DLL-Projekt](#projectRef) auf.

 **Die DLL wird als EXE-Datei erstellt:** Fügen Sie ein separates Testprojekt hinzu. Verknüpfen Sie sie mit der Ausgabeobjektdatei.

 Rufen Sie die Prozedur [So verknüpfen Sie die Tests mit dem Objekt- oder Bibliotheksdateien](#objectRef).

 **Die Komponententests rufen Nicht-Member-Funktionen auf, die nicht von der DLL exportiert werden, und die DLL kann als statische Bibliothek erstellt werden:** Ändern Sie das DLL-Projekt so, dass es in eine *LIB*-Datei kompiliert wird. Fügen Sie ein separates Testprojekt hinzu, das auf das zu testende Projekt verweist.

 Diese Methode hat den Vorteil, dass Ihre Tests nicht exportierte Members verwenden, aber dennoch in einem separaten Projekt verbleiben können.

 Rufen Sie die Prozedur [To change the DLL to a static library (Ändern der DLL in eine statische Bibliothek)](#staticLink) auf.

 **Die Komponententests müssen nicht exportierte Nicht-Member-Funktionen aufrufen, und der Code muss als DLL (Dynamic Link Library) erstellt werden:** Fügen Sie Komponententests im gleichen Projekt wie den Produktcode hinzu.

 Wechseln Sie zum Verfahren [So fügen Sie Komponententests im gleichen Projekt hinzu](#sameProject).

## <a name="create-the-tests"></a>Erstellen der Tests

### <a name="staticLink"></a> Ändern der DLL in eine statische Bibliothek

- Wenn die Tests Members verwenden müssen, die nicht von einem DLL-Projekt exportiert werden, und das zu testende Projekt als dynamische Bibliothek erstellt wird, erwägen Sie, es in eine statische Bibliothek zu konvertieren.

  1. Öffnen Sie im **Projektmappen-Explorer** das Kontextmenü für das zu testende Projekt, und klicken Sie auf **Eigenschaften**. Das Projektfenster **Eigenschaften** wird geöffnet.

  2. Klicken Sie auf **Konfigurationseigenschaften** > **Allgemein**.

  3. Legen Sie den **Konfigurationstyp** auf **Statische Bibliothek (.lib)** fest.

  Fahren Sie mit der Prozedur [So verknüpfen Sie die Tests mit den Objekt- oder Bibliotheksdateien](#objectRef) fort.

### <a name="projectRef"></a> So verweisen Sie auf exportierte DLL-Funktionen aus dem Testprojekt

- Wenn das DLL-Projekt die Funktionen exportiert, die Sie testen möchten, können Sie aus dem Testprojekt einen Verweis auf das Codeprojekt hinzufügen.

  1. Erstellen Sie ein natives Komponententestprojekt.

      1. Klicken Sie im Menü **Datei** auf **Neu** > **Projekt** > **Visual C++** > **Test** > **C++-Komponententestprojekt**.

  2. Öffnen Sie im **Projektmappen-Explorer** das Kontextmenü für das Testprojekt, und klicken Sie auf **Verweise**. Das Projektfenster **Eigenschaften** wird geöffnet.

  3. Klicken Sie auf **Allgemeine Eigenschaften** > **Framework und Verweise** und anschließend auf die Schaltfläche **Neuen Verweis hinzufügen**.

  4. Wählen Sie **Projekte** und dann das zu testende Projekt aus.

       Wählen Sie die Schaltfläche **Hinzufügen** aus.

  5. Fügen Sie in den Eigenschaften des Testprojekts den Speicherort des zu testenden Projekts den Includeverzeichnissen hinzu.

       Klicken Sie auf **Konfigurationseigenschaften** > **VC++-Verzeichnisse** > **Includeverzeichnisse**.

       Wählen Sie **Bearbeiten** aus, und fügen Sie dann das Headerverzeichnis des zu testenden Projekts hinzu.

  Wechseln Sie zu [Schreiben der Komponententests](#addTests).

### <a name="objectRef"></a> So verknüpfen Sie die Tests mit den Objekt- oder Bibliotheksdateien

- Wenn die DLL die Funktionen, die Sie testen möchten, nicht exportiert, können Sie die *OBJ*- oder *LIB*-Ausgabedatei zu den Abhängigkeiten des Testprojekts hinzufügen.

  1. Erstellen Sie ein natives Komponententestprojekt.

      1. Klicken Sie im Menü **Datei** auf **Neu** > **Projekt** > **Visual C++** > **Test** > **Natives Komponententestprojekt**.

  2. Öffnen Sie im **Projektmappen-Explorer** das Kontextmenü des Testprojekts, und klicken Sie auf **Eigenschaften**.

  3. Klicken Sie auf **Konfigurationseigenschaften** > **Linker** > **Eingabe** > **Zusätzliche Abhängigkeiten**.

       Wählen Sie **Bearbeiten** aus, und fügen Sie dann die Namen der **.obj**- oder **.lib**-Dateien hinzu. Verwenden Sie nicht die vollständigen Pfadnamen.

  4. Klicken Sie auf **Konfigurationseigenschaften** > **Linker** > **Allgemein** > **Zusätzliche Bibliotheksverzeichnisse**.

       Wählen Sie **Bearbeiten** aus, und fügen Sie den Verzeichnispfad der **.obj**- oder **.lib**-Dateien hinzu. Der Pfad befindet sich normalerweise im Buildordner des zu testenden Projekts.

  5. Klicken Sie auf **Konfigurationseigenschaften** > **VC++-Verzeichnisse** > **Includeverzeichnisse**.

       Wählen Sie **Bearbeiten** aus, und fügen Sie dann das Headerverzeichnis des zu testenden Projekts hinzu.

  Wechseln Sie zu [Schreiben der Komponententests](#addTests).

### <a name="sameProject"></a> So fügen Sie Komponententests im gleichen Projekt hinzu

1. Ändern Sie die Produktcodeprojekteigenschaften, um die Header und Bibliotheksdateien einzuschließen, die für die Unittests erforderlich sind.

   1. Klicken Sie im **Projektmappen-Explorer** im Kontextmenü für das zu testende Projekt auf **Eigenschaften**. Das Projektfenster **Eigenschaften** wird geöffnet.

   2. Klicken Sie auf **Konfigurationseigenschaften** > **VC++-Verzeichnisse**.

   3. Bearbeiten Sie die Include- und Bibliotheksverzeichnisse:

       |Verzeichnis|Eigenschaft|
       |-|-|
       |**Includeverzeichnisse** | **$(VCInstallDir)UnitTest\include;$(IncludePath)**|
       |**Bibliotheksverzeichnisse** | **$(VCInstallDir)UnitTest\lib;$(LibraryPath)**|

2. Fügen Sie eine C++-Komponententestdatei hinzu:

   - Klicken Sie im **Projektmappen-Explorer** im Kontextmenü des Projekts auf **Hinzufügen** > **Neues Element** > **C++-Komponententest**.

   Wechseln Sie zu [Schreiben der Komponententests](#addTests).

## <a name="addTests"></a> Schreiben der Komponententests

1. Fügen Sie in jeder Komponententestcodedatei eine `#include`-Anweisung für die Header des zu testenden Projekts hinzu.

2. Fügen Sie den Komponententestcodedateien Testklassen und -methoden hinzu. Beispiel:

    ```cpp
    #include "stdafx.h"
    #include "CppUnitTest.h"
    #include "MyProjectUnderTest.h"
    using namespace Microsoft::VisualStudio::CppUnitTestFramework;
    namespace MyTest
    {
      TEST_CLASS(MyTests)
      {
      public:
          TEST_METHOD(MyTestMethod)
          {
              Assert::AreEqual(MyProject::Multiply(2,3), 6);
          }
      };
    }
    ```

## <a name="run-the-tests"></a>Tests ausführen

1. Klicken Sie im Menü **Test** auf **Windows** > **Test-Explorer**.

1. Wenn Ihre Tests nicht im Fenster angezeigt werden, erstellen Sie das Testprojekt, indem Sie mit der rechten Maustaste auf dessen Knoten im **Projektmappen-Explorer** klicken und **Erstellen** oder **Neu erstellen** auswählen.

1. Klicken Sie im **Test-Explorer** auf **Alle ausführen**, oder wählen Sie die Tests aus, die Sie ausführen möchten. Klicken Sie für weitere Optionen, einschließlich des Ausführens im Debugmodus mit aktivierten Breakpoints, mit der rechten Maustaste auf einen Test.

## <a name="see-also"></a>Siehe auch

- [Schreiben von Komponententests für C/C++](writing-unit-tests-for-c-cpp.md)
- [Referenz für die API „Microsoft.VisualStudio.TestTools.CppUnitTestFramework“](../test/microsoft-visualstudio-testtools-cppunittestframework-api-reference.md)
- [Debuggen von nativem Code](../debugger/debugging-native-code.md)
- [Walkthrough: Creating and using a dynamic link library (C++) (Exemplarische Vorgehensweise: Erstellen und Verwenden einer Dynamic Link Library (C++))](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp)
- [Importieren und Exportieren](/cpp/build/importing-and-exporting)
- [Schnellstart: Testgesteuerte Entwicklung mit dem Test-Explorer](../test/quick-start-test-driven-development-with-test-explorer.md)

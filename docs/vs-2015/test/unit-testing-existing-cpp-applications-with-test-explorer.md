---
title: Ausführen von Komponententests für vorhandene C++-Anwendungen mit dem Test-Explorer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7d08de69-c32e-4f0b-89aa-75347b15fb82
caps.latest.revision: 13
ms.author: gewarren
manager: douge
ms.openlocfilehash: 040e3f0a236067a96d107f64f4c9aca06d0706e3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47509804"
---
# <a name="unit-testing-existing-c-applications-with-test-explorer"></a>Ausführen von Unittests für vorhandene C++-Anwendungen mit dem Test-Explorer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Komponententests für vorhandenen C++-Anwendungen mit Test-Explorer](https://docs.microsoft.com/visualstudio/test/unit-testing-existing-cpp-applications-with-test-explorer).  
  
Es wird empfohlen, vor der Änderung einer vorhandenen Anwendung zu überprüfen, ob sie gut mit Komponententests abgedeckt ist. So können Sie sichergehen, dass durch die Änderungen keine Fehler eingeführt werden. Wenn die Anwendung noch nicht über Komponententests verfügt, können Sie diese hinzufügen, indem Sie die in diesem Thema beschriebenen Methoden verwenden. In diesem Thema wird beschrieben, wie Sie Komponententests für vorhandenen Visual C++-Code hinzufügen. Zunächst entscheiden Sie, wie Sie Ihren Code testen möchten. Dann fahren Sie mit dem Erstellen, Schreiben und Ausführen der Tests fort.  
  
## <a name="deciding-how-to-test-your-code"></a>Entscheiden, wie der Code getestet werden soll  
 Öffnen Sie das vorhandene C++-Projekt. Schauen Sie es sich genau an, um zu entscheiden, wie Sie die Komponententests hinzufügen möchten. Eventuell möchten Sie Modellierungstools verwenden, die Ihnen dabei helfen, Abhängigkeiten im Code aufzufinden und zu verstehen, wie diese Teile interagieren. Weitere Informationen finden Sie unter [Visualisieren von Code](../modeling/visualize-code.md).  
  
 Es wird empfohlen, dass Sie Ihre Änderungen in kleine Aufgaben untergliedern und entsprechend trennen. Schreiben Sie vor jeder kleinen Änderung Komponententests zu Aspekten des Verhaltens, das unverändert bleibt. Diese Tests werden dann auch weiterhin erfolgreich sein, nachdem Sie die Änderung vorgenommen haben. Wenn Sie z. B. beabsichtigen, eine Sortierfunktion zu ändern, damit eine Liste mit Personen nach dem Nachnamen und nicht nach dem Vornamen sortiert wird, können Sie einen Komponententest schreiben, der überprüft, ob alle Eingabenamen in der Ausgabe angezeigt werden. Nachdem Sie die Änderung vorgenommen haben, können Sie neue Komponententests für das neue Verhalten hinzufügen.  
  
 Wenn dies möglich ist, sollten viele oder alle Komponententests nur Funktionen verwenden, die exportiert werden. Wenn Sie jedoch nur einen kleinen Teil der gesamten Anwendung ändern, möchten Sie vielleicht Funktionen verwenden, die nicht exportiert werden. Unter Umständen benötigen Sie Tests, die interne Funktionen aufrufen, oder Tests, die Werte aus internen Variablen festlegen und abrufen.  
  
 Es gibt mehrere Methoden, Produktcode zu testen. Dies hängt davon ab, ob die Schnittstellen verfügbar gemacht werden, die Sie testen möchten. Wählen Sie eine der folgenden Methoden aus:  
  
 **Bei den Komponententests werden nur Funktionen verwendet, die vom zu testenden Code exportiert werden:**  
 Fügen Sie ein separates Testprojekt hinzu. Fügen Sie im Testprojekt einen Verweis auf das zu testende Projekt hinzu.  
  
 Rufen Sie die Prozedur [So verweisen Sie auf exportierte Funktionen aus dem Testprojekt](#projectRef) auf.  
  
 **Der zu testende Code wird als EXE-Datei erstellt:**  
 Fügen Sie ein separates Testprojekt hinzu. Verknüpfen Sie sie mit der Ausgabeobjektdatei.  
  
 Rufen Sie die Prozedur [So verknüpfen Sie die Tests mit dem Objekt- oder Bibliotheksdateien](#objectRef).  
  
 **Die Komponententests müssen private Funktionen und Daten verwenden, und der zu testende Code kann als statische Bibliothek erstellt werden:**  
 Ändern Sie das zu testende Projekt so, dass es zu einer LIB-Datei kompiliert wird. Fügen Sie ein separates Testprojekt hinzu, das auf das zu testende Projekt verweist.  
  
 Diese Methode hat den Vorteil, dass Ihre Tests private Member verwenden können, aber dennoch in einem separaten Projekt verbleiben können. Sie eignet sich jedoch möglicherweise nicht für einige Anwendungen, in denen Sie eine Dynamic Link Library (DLL) benötigen.  
  
 Wechseln Sie zum Verfahren [So ändern Sie den zu testenden Code in eine statische Bibliothek](#staticLink).  
  
 **Die Komponententests müssen private Funktionen und Daten verwenden, und der Code muss als Dynamic Link Library (DLL) erstellt werden:**  
 Fügen Sie Komponententests im gleichen Projekt wie den Produktcode hinzu.  
  
 Wechseln Sie zum Verfahren [So fügen Sie Komponententests im gleichen Projekt hinzu](#sameProject).  
  
## <a name="creating-the-tests"></a>Erstellen der Tests  
  
###  <a name="staticLink"></a> So ändern Sie den zu testenden Code in eine statische Bibliothek  
  
-   Wenn die Tests Member verwenden müssen, die nicht von einem zu testenden Projekt exportiert werden, und das zu testende Projekt als dynamische Bibliothek erstellt wird, erwägen Sie, es in eine statische Bibliothek zu konvertieren.  
  
    1.  Öffnen Sie im Projektmappen-Explorer das Kontextmenü für das zu testende Projekt, und wählen Sie **Eigenschaften** aus. Das Fenster mit den Projekteigenschaften wird geöffnet.  
  
    2.  Wählen Sie **Konfigurationseigenschaften** und dann **Allgemein** aus.  
  
    3.  Legen Sie den **Konfigurationstyp** auf **Statische Bibliothek (.lib)** fest.  
  
 Fahren Sie mit der Prozedur [So verknüpfen Sie die Tests mit den Objekt- oder Bibliotheksdateien](#objectRef) fort.  
  
###  <a name="projectRef"></a> So verweisen Sie vom Testprojekt auf exportierte Funktionen  
  
-   Wenn ein zu testendes Projekt die Funktionen, die Sie testen möchten, exportiert, können Sie vom Testprojekt einen Verweis auf das Codeprojekt hinzufügen.  
  
    1.  Erstellen Sie ein C++-Testprojekt.  
  
        1.  Wählen Sie im Menü **Datei** die Optionen **Neu**, **Projekt**, **Visual C++-Test**, **C++-Komponententestprojekt** aus.  
  
    2.  Öffnen Sie im Projektmappen-Explorer das Kontextmenü für das Testprojekt, und wählen Sie **Verweise** aus. Das Fenster mit den Projekteigenschaften wird geöffnet.  
  
    3.  Wählen Sie **Allgemeine Eigenschaften**, **Framework und Verweise** aus, und klicken Sie dann auf die Schaltfläche **Neuen Verweis hinzufügen**.  
  
    4.  Wählen Sie **Projekte** und dann das zu testende Projekt aus.  
  
         Wählen Sie die Schaltfläche **Hinzufügen** aus.  
  
    5.  Fügen Sie in den Eigenschaften des Testprojekts den Speicherort des zu testenden Projekts den Includeverzeichnissen hinzu.  
  
         Wählen Sie **Konfigurationseigenschaften**, **VC++-Verzeichnisse**, **Includeverzeichnisse** aus.  
  
         Wählen Sie **Bearbeiten** aus, und fügen Sie dann das Headerverzeichnis des zu testenden Projekts hinzu.  
  
 Wechseln Sie zu [Schreiben der Komponententests](#addTests).  
  
###  <a name="objectRef"></a> So verknüpfen Sie die Tests mit den Objekt- oder Bibliotheksdateien  
  
-   Wenn der zu testende Code die Funktionen, die Sie testen möchten, nicht exportiert, können Sie die **.obj**- oder **.lib**-Ausgabedatei zu den Abhängigkeiten des Testprojekts hinzufügen.  
  
    1.  Erstellen Sie ein C++-Testprojekt.  
  
        1.  Wählen Sie im Menü **Datei** die Optionen **Neu**, **Projekt**, **Visual C++-Test**, **C++-Komponententestprojekt** aus.  
  
    2.  Öffnen Sie im Projektmappen-Explorer das Kontextmenü für das Testprojekt, und wählen Sie **Eigenschaften** aus. Das Fenster mit den Projekteigenschaften wird geöffnet.  
  
    3.  Wählen Sie **Konfigurationseigenschaften**, **Linker**, **Eingabe**, **Zusätzliche Abhängigkeiten** aus.  
  
         Wählen Sie **Bearbeiten** aus, und fügen Sie dann die Namen der **.obj**- oder **.lib**-Dateien hinzu. Verwenden Sie nicht die vollständigen Pfadnamen.  
  
    4.  Wählen Sie **Konfigurationseigenschaften**, **Linker**, **Allgemein**, **Zusätzliche Bibliotheksverzeichnisse** aus.  
  
         Wählen Sie **Bearbeiten** aus, und fügen Sie den Verzeichnispfad der **.obj**- oder **.lib**-Dateien hinzu. Der Pfad befindet sich normalerweise im Buildordner des zu testenden Projekts.  
  
    5.  Wählen Sie **Konfigurationseigenschaften**, **VC++-Verzeichnisse**, **Includeverzeichnisse** aus.  
  
         Wählen Sie **Bearbeiten** aus, und fügen Sie dann das Headerverzeichnis des zu testenden Projekts hinzu.  
  
 Wechseln Sie zu [Schreiben der Komponententests](#addTests).  
  
###  <a name="sameProject"></a> So fügen Sie Komponententests im gleichen Projekt hinzu  
  
1.  Ändern Sie die Produktcodeprojekteigenschaften, um die Header und Bibliotheksdateien einzuschließen, die für die Unittests erforderlich sind.  
  
    1.  Öffnen Sie im Projektmappen-Explorer das Kontextmenü für das zu testende Projekt, und wählen Sie "Eigenschaften" aus. Das Fenster mit den Projekteigenschaften wird geöffnet.  
  
    2.  Wählen Sie **Konfigurationseigenschaften**, **VC++-Verzeichnisse** aus.  
  
    3.  Bearbeiten Sie die Include- und Bibliotheksverzeichnisse:  
  
        |||  
        |-|-|  
        |**Includeverzeichnisse**|**$(VCInstallDir)UnitTest\include;$(IncludePath)**|  
        |**Bibliotheksverzeichnisse**|**$(VCInstallDir)UnitTest\lib;$(LibraryPath)**|  
  
2.  Fügen Sie eine C++-Komponententestdatei hinzu:  
  
    -   Öffnen Sie im Projektmappen-Explorer das Kontextmenü für das Projekt, und wählen Sie **Hinzufügen**, **Neues Element** und dann **C++-Komponententest** aus.  
  
 Wechseln Sie zu [Schreiben der Komponententests](#addTests).  
  
##  <a name="addTests"></a> Schreiben der Komponententests  
  
1.  Fügen Sie in jeder Komponententestcodedatei eine `#include`-Anweisung für die Header des zu testenden Projekts hinzu.  
  
2.  Fügen Sie den Komponententestcodedateien Testklassen und -methoden hinzu. Zum Beispiel:  
  
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
  
 Weitere Informationen finden Sie unter [Komponententests für nativen Code mit Test-Explorer](http://msdn.microsoft.com/en-us/8a09d6d8-3613-49d8-9ffe-11375ac4736c).  
  
## <a name="run-the-tests"></a>Tests ausführen  
  
1.  Wählen Sie im Menü **Ansicht** die Optionen **Weitere Fenster**, **Test-Explorer**aus.  
  
2.  Wählen Sie im Test-Explorer **Alle ausführen**aus.  
  
 Weitere Informationen finden Sie unter [Testgesteuerte Entwicklung mit dem Test-Explorer](../test/quick-start-test-driven-development-with-test-explorer.md).




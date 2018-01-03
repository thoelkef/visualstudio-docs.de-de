---
title: "Erste Schritte mit Unittests – Erstellen von Testplänen | Microsoft-Dokumentation"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: unit testing, create unit test plans
ms.assetid: 2171CD69-FBB1-4994-9DCC-3BFFDFD26662
caps.latest.revision: "56"
ms.author: douge
manager: douge
ms.workload: multiple
ms.openlocfilehash: bfb37b6ea2c448d0243f72857de0a29fa2d20c87
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="get-started-with-unit-testing"></a>Erste Schritte mit Unittests

Verwenden Sie Visual Studio, um Ihre Unittests zu definieren und auszuführen, um die Integrität Ihres Codes zu gewährleisten, Code Coverage sicherzustellen und Fehler zu finden, bevor diese von Ihren Kunden erkannt werden.

<a name="create-tests"></a>
## <a name="create-unit-tests"></a>Erstellen von Unittests

Erstellen Sie Unittests, und führen Sie sie häufig aus, um sicherzustellen, dass der Code ordnungsgemäß funktioniert.

1. Erstellen Sie ein Unittests.
        
   ![Hinzufügen einer Projektmappe zu einem Unittestprojekt](media/createunittest1.png)
    
1. Geben Sie dem Projekt einen Namen.
        
   ![Vorlage für Unittestprojekte](media/createunittest2.png)
  
   Das Projekt wird Ihrer Projektmappe hinzugefügt.
    
   ![Wählen Sie das Unittestprojekt im Projektmappen-Explorer aus.](media/createunittest5.png)
    
1. Fügen Sie im Unittestprojekt dem zu testenden Projekt eine Referenz hinzu.
        
   ![Hinzufügen eines Verweises zu Ihrem Unittestprojekt.](media/createunittest6.png)
    
1. Wählen Sie das Projekt aus, das den Code enthält, den Sie testen möchten.
        
   ![Auswählen des hinzuzufügenden Verweises](media/createunittest7.png)
    
1. Programmieren Sie den Unittest.

   ![Hinzufügen von Code zu Ihrem Unittest](media/createunittest8.png) 

Sie können zudem Stubs für Unittestmethoden erstellen. Dazu können Sie den [Befehl **Unittests erstellen**](create-unit-tests-menu.md) verwenden.
Alternativ können Sie ein [anderes Framework für Unittests](#frameworks) verwenden, um Tests für unterschiedliche Codesprachen zu verwenden.

![Verwenden des Befehls „Unittests erstellen“](media/createunittestcommand2.png)

## <a name="run-unit-tests"></a>Komponententests ausführen

1. Öffnen Sie den Test-Explorer.
        
   ![Öffnen des Test-Explorers im Menü „Test“](media/rununittest1.png) 

1. Führen Sie Unittests aus.
        
   ![Ausführen von Komponententests im Test-Explorer](media/rununittest2.png) 

   Es werden die Unittests angezeigt, die im Test-Explorer entweder erfolgreich oder mit Fehlern ausgeführt wurden.
      
   ![Überprüfen der Unittestsergebnisse im Test-Explorer](media/rununittest3.png) 

## <a name="view-live-unit-test-results"></a>Anzeigen der Ergebnisse von Liveunittests

Wenn Sie die Testframeworks MSTest, xUnit oder NUnit in Visual Studio 2017 verwenden

1. Aktivieren Sie die Liveunittests im Menü **Test**.

   ![Aktivieren der Liveunittests](media/live-test-results-start.png) 

1. Schauen Sie sich die Ergebnisse der Tests im Fenster des Code-Editors an, während Sie Code schreiben und diesen bearbeiten.

   ![Zeigen und Klicken auf die Testergebnisindikatoren](media/live-test-results-ui.png) 

1. Zeigen Sie und klicken Sie auf die Testergebnisindikatoren, um mehr Informationen anzuzeigen.

   ![Überprüfen der Ergebnisse der Tests](media/live-test-results-details.png) 

Weitere Informationen finden Sie unter [Live Unit Testing in Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/2016/11/18/live-unit-testing-visual-studio-2017-rc/)

<a name="intellitest"></a>
## <a name="generate-unit-tests-with-intellitest"></a>Generieren von Unittests mit IntelliTest

Wenn Sie IntelliTest ausführen, erkennen Sie ohne weiteres, welche Tests zu einem Fehler führen, und können den erforderlichen Code hinzufügen, um die Fehler zu beseitigen. Sie können wählen, welche der generierten Tests in einem Testprojekt gespeichert werden sollen, um eine Regressionsreihe zu erstellen. Wenn Sie den Code ändern, führen Sie IntelliTest erneut aus, damit die generierten Tests mit den Codeänderungen synchronisiert werden. Weitere Informationen finden Sie unter [Generieren von Unittests für Code mit IntelliTest](https://docs.microsoft.com/visualstudio/test/generate-unit-tests-for-your-code-with-intellitest).

![Erzeugen von Unittests mit IntelliTest](media/intellitest.png)

<a name="unit-tests"></a>
## <a name="run-unit-tests-with-test-explorer"></a>Ausführen von Komponententests mit dem Test-Explorer

Mithilfe des Test-Explorers können Sie Komponententests aus Visual Studio oder Testprojekte von Drittanbietern ausführen, Tests in Kategorien gruppieren, die Testliste filtern sowie Testwiedergabelisten erstellen, speichern und ausführen. Zudem können Sie Tests debuggen und die Leistung und Codeabdeckung von Tests analysieren. Weitere Informationen finden Sie unter [Ausführen von Unittests mit dem Test-Explorer](https://docs.microsoft.com/visualstudio/test/run-unit-tests-with-test-explorer).

![Ausführen von Unittests mit dem Test-Explorer](media/testexplorer.png)

<a name="code-coverage"></a>
## <a name="use-code-coverage-to-determine-how-much-code-is-being-tested"></a>Bestimmen des Umfangs des zu testenden Codes mithilfe von Code Coverage

Wenn Sie den Anteil des Projektcodes ermitteln möchten, der in codierten Tests wie Komponententests tatsächlich getestet wird, verwenden Sie die Code Coverage-Funktion von Visual Studio. Um sich effektiv vor Fehlern zu schützen, sollten Sie die Tests für den Großteil Ihres Codes ausführen bzw. diesen "abdecken". Weitere Informationen finden Sie unter [Bestimmen des Umfangs des zu testenden Codes mithilfe von Code Coverage](https://docs.microsoft.com/visualstudio/test/using-code-coverage-to-determine-how-much-code-is-being-tested).

![Bestimmen des Umfangs des zu testenden Codes mithilfe von Code Coverage](media/codecoverage.png)

## <a name="q--a"></a>Fragen und Antworten

<!-- BEGINSECTION class="m-qanda" -->

<a name="frameworks"></a>
####F: Kann ich in Visual Studio Unittests ausführen, wenn ich ein anderes Unittestframework verwende?

A: Ja. Verwenden Sie das Plug-In für das Framework, damit der Testlauf von Visual Studio mit dem Framework arbeiten kann. Hier sehen Sie die [Framework-Plug-Ins der Unittests für Visual Studio](http://go.microsoft.com/fwlink/?LinkID=246630), die zurzeit zur Verfügung stehen.

1. Laden Sie das Plug-In über den Erweiterungs-Manager von Visual Studio herunter.
        
   ![Auswählen von Unittest-Plug-Ins von Drittanbietern mit dem Erweiterungs-Manager](media/install3rdpartyunittestframeworks1.png) 

1. Laden Sie das Plug-In aus der Visual Studio Gallery unter „Tools/Testen“ herunter, oder führen Sie eine Suche durch, wenn Sie den Namen kennen.
        
   ![Herunterladen des Plug-Ins](media/install3rdpartyunittestframeworks2.png) 

1. Erstellen Sie ein Klassenbibliotheksprojekt.
        
   ![Erstellen eines Klassenbibliotheksprojekts](media/create3rdpartyunittest1.png) 

   Fügen Sie der Projektmappe das Projekt hinzu.
    
   ![Benennen Sie das Klassenbibliotheksprojekt und fügen Sie es hinzu](media/create3rdpartyunittest3.png) 

1. Führen Sie im Klassenbibliotheksprojekt NuGet aus, um das Plug-In zu installieren.

   ![Verwalten von NuGet-Paketen zum Installieren des Plug-Ins](media/create3rdpartyunittest3a.png) 

   [NuGet](https://www.nuget.org/) ist eine Erweiterung von Visual Studio, mit der Sie Bibliotheken und Tools für Ihre Projekte hinzufügen und aktualisieren können.

1. Installieren Sie das Plug-In. Wenn Sie den Namen kennen, können Sie online danach suchen.

   ![Installieren des Frameworks des Drittanbieters](media/create3rdpartyunittest4.png) 

   In Ihrem Projekt wird auf das Framework verwiesen.
        
   ![Der Verweis für das Unittestframework des Drittanbieters wird Ihrer Projektmappe hinzugefügt.](media/create3rdpartyunittest6.png) 

1. Fügen Sie im Klassenbibliotheksprojekt dem zu testenden Projekt eine Referenz hinzu.
        
   ![Fügen Sie einen Verweis auf das Projekt hinzu.](media/createunittest6.png) 

1. Wählen Sie das Projekt aus, das den Code enthält, den Sie testen möchten.
        
   ![Wählen Sie das Codeprojekt aus, das Sie testen möchten.](media/createunittest7.png) 

1. Programmieren Sie den Unittest.

   ![Hinzufügen von Code zu Ihrem Unittest](media/create3rdpartyunittest7.png)   

<!-- ENDSECTION -->

## <a name="see-also"></a>Siehe auch

* [Create Unit Tests command (Befehl „Komponententests erstellen“)](create-unit-tests-menu.md)
* [Generieren von Tests mit IntelliTest](generate-unit-tests-for-your-code-with-intellitest.md)
* [Ausführen von Unittests mit dem Test-Explorer](run-unit-tests-with-test-explorer.md)
* [Bestimmen von Code Coverage](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
* [Verbessern der Codequalität](improve-code-quality.md)

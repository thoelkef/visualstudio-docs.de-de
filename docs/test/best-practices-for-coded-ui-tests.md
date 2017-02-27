---
title: "Empfohlene Vorgehensweisen f&#252;r Tests der codierten UI | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Tests für codierte UI, Bewährte Methoden"
ms.assetid: d5aef766-a24c-4f1f-ac9b-e5462b6627d4
caps.latest.revision: 39
ms.author: "mlearned"
manager: "douge"
caps.handback.revision: 39
---
# Empfohlene Vorgehensweisen f&#252;r Tests der codierten UI
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Thema werden die besten Verfahren zur Entwicklung von Tests der codierten UI beschrieben.  
  
 **Anforderungen**  
  
-   Visual Studio Enterprise  
  
## Bewährte Methoden  
 Halten Sie sich an die folgenden Richtlinien, um einen flexiblen Test der codierten UI zu erstellen.  
  
-   Verwenden Sie wenn möglich den **Test\-Generator für codierte UI**.  
  
-   Ändern Sie die `UIMap.designer.cs`\-Datei nicht direkt.  Andernfalls werden die an der Datei vorgenommenen Änderungen überschrieben.  
  
-   Erstellen Sie den Test als Sequenz aufgezeichneter Methoden.  Weitere Informationen über die Aufzeichnung einer Methode finden Sie unter [Erstellen von Tests der codierten UI](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate).  
  
-   Jede aufgezeichnete Methode sollte auf eine einzelne Seite, ein einzelnes Formular oder Dialogfeld einwirken.  Erstellen Sie eine neue Testmethode für jede neue Seite, jedes neue Formular oder Dialogfeld.  
  
-   Wenn Sie eine Methode erstellen, verwenden Sie statt des Standardnamens einen aussagekräftigen Methodennamen.  Ein aussagekräftiger Name hilft dabei, den Zweck der Methode zu erkennen.  
  
-   Beschränken Sie jede aufgezeichnete Methode wenn möglich auf weniger als 10 Aktionen.  Dieser modulare Ansatz erleichtert es, eine Methode zu ersetzen, wenn sich die Benutzeroberfläche ändert.  
  
-   Erstellen Sie jede Assertion mithilfe des **Test\-Generators für codierte UI**, der automatisch eine Assertionsmethode zur `UIMap.Designer.cs`\-Datei hinzufügt.  
  
-   Wenn sich die Benutzeroberfläche \(User Interface, UI\) ändert, zeichnen Sie die Testmethoden oder die Assertionsmethoden erneut auf, oder zeichnen Sie die betroffenen Abschnitte einer vorhandenen Testmethode erneut auf.  
  
-   Erstellen Sie eine separate <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>\-Datei für jedes Modul in der getesteten Anwendung.  Weitere Informationen finden Sie unter [Testing a Large Application with Multiple UI Maps](../test/testing-a-large-application-with-multiple-ui-maps.md).  
  
-   Verwenden Sie in der getesteten Anwendung aussagekräftige Namen, wenn Sie Benutzeroberflächen\-Steuerelemente erstellen.  Dadurch wird die Aussagekraft und die Benutzerfreundlichkeit der automatisch generierten Steuerelementnamen erhöht.  
  
-   Wenn Sie Assertionen durch Codierung mit der API erstellen, erstellen Sie eine Methode für jede Assertion in dem Teil der <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>\-Klasse, der sich in der `UIMap.cs`\-Datei befindet.  Rufen Sie diese Methode aus der Testmethode auf, um die Assertion auszuführen.  
  
-   Wenn Sie direkt mit der API codieren, verwenden Sie so oft wie möglich die Eigenschaften und Methoden in den Klassen, die in der `UIMap.Designer.cs`\-Datei in Ihrem Code generiert wurden.  Diese Klassen machen Ihre Arbeit einfacher und zuverlässiger und helfen Ihnen, produktiver zu sein.  
  
 Tests der codierten UI werden automatisch an zahlreiche Änderungen in der Benutzeroberfläche angepasst.  Wenn z. B. ein Benutzeroberflächenelement Position oder Farbe geändert hat, wird beim Test der codierten UI in den meisten Fällen dennoch das richtige Element gefunden.  
  
 Während eines Testlaufs werden die UI\-Steuerelemente vom Testframework mithilfe eines Satzes von Sucheigenschaften gesucht, die für jede Steuerelementklasse in den Definitionen angewendet werden, die durch den **Test\-Generator für codierte UI** in der `UIMap.Designer.cs`\-Datei erstellt werden.  Die Sucheigenschaften enthalten Name\-Wert\-Paare von Eigenschaftennamen und Eigenschaftenwerte, die verwendet werden können, um das Steuerelement zu identifizieren, z. B. die <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.FriendlyName%2A>\-, <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.Name%2A>\- und <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.ControlType%2A>\-Eigenschaften des Steuerelements.  Wenn die Sucheigenschaften unverändert sind, findet der Test der codierten UI erfolgreich das Steuerelement in der Benutzeroberfläche.  Wenn die Sucheigenschaften geändert wurden, findet ein intelligenter Vergleichsalgorithmus der Tests der codierten UI anhand von Heuristik Steuerelemente und Fenster in der Benutzeroberfläche.  Wenn die Benutzeroberfläche geändert wurde, können Sie möglicherweise die Sucheigenschaften von zuvor identifizierten Elementen ändern, um sicherstellen, dass sie gefunden werden.  
  
## Vorgehensweise bei geänderter Benutzeroberfläche  
 Benutzeroberflächen werden während der Entwicklung häufig geändert.  Nachfolgend finden Sie einige Möglichkeiten, um die Auswirkungen dieser Änderungen zu reduzieren:  
  
-   Suchen Sie die aufgezeichnete Methode, die auf dieses Steuerelement verweist, und verwenden Sie den **Test\-Generator für codierte UI**, um die Aktionen für diese Methode erneut aufzuzeichnen.  Sie können den gleichen Namen für die Methode verwenden, um die vorhandenen Aktionen zu überschreiben.  
  
-   Wenn ein Steuerelement über eine Assertion verfügt, die nicht mehr gültig ist:  
  
    -   Löschen Sie die Methode, die die Assertion enthält.  
  
    -   Entfernen Sie den Aufruf dieser Methode aus der Testmethode.  
  
    -   Fügen Sie eine neue Assertion hinzu, indem Sie die Fadenkreuz\-Schaltfläche auf das UI\-Steuerelement ziehen, die UI\-Zuordnung öffnen und die neue Assertion hinzufügen.  
  
 Weitere Informationen über das Aufzeichnen von Tests der codierten UI finden Sie unter [Verwenden von Benutzeroberflächenautomatisierung zum Testen des Codes ](../test/use-ui-automation-to-test-your-code.md).  
  
## Vorgehensweise, wenn ein Hintergrundprozess abgeschlossen werden muss, bevor der Test fortgesetzt werden kann  
 Möglicherweise müssen Sie warten, bis ein Prozess beendet wird, bevor Sie mit der nächsten Benutzeroberflächen\-Aktion fortfahren können.  Hierzu können Sie wie im folgenden Beispiel <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.WaitForReadyLevel%2A> verwenden, um zu warten, bevor der Test fortgesetzt wird.  
  
```  
// Set the playback to wait for all threads to finish  
Playback.PlaybackSettings.WaitForReadyLevel = WaitForReadyLevel.AllThreads;  
  
// Press the submit button  
this.UIMap.ClickSubmit();  
  
// Reset the playback to wait only for the UI thread to finish  
Playback.PlaybackSettings.WaitForReadyLevel = WaitForReadyLevel.UIThreadOnly;  
```  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting>   
 [Verwenden von Benutzeroberflächenautomatisierung zum Testen des Codes ](../test/use-ui-automation-to-test-your-code.md)   
 [Erstellen von Tests der codierten UI](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)   
 [Testing a Large Application with Multiple UI Maps](../test/testing-a-large-application-with-multiple-ui-maps.md)   
 [Unterstützte Konfigurationen und Plattformen für Tests der codierten UI und Aktionsaufzeichnungen](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
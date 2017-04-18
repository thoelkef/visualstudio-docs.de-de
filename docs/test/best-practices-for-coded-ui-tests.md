---
title: "Empfohlene Vorgehensweisen für Tests der programmierten UI | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- coded UI tests, best practices
ms.assetid: d5aef766-a24c-4f1f-ac9b-e5462b6627d4
caps.latest.revision: 39
ms.author: douge
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5ab78b6b8eaa8156ed2c8a807b1d8a80e75afa84
ms.openlocfilehash: 444f6bf46c3eac65a2771655616fd67d8ed83b32
ms.lasthandoff: 04/04/2017

---
# <a name="best-practices-for-coded-ui-tests"></a>Empfohlene Vorgehensweisen für Tests der programmierten UI
In diesem Thema werden die besten Verfahren zur Entwicklung von Tests der programmierten UI beschrieben.  
  
 **Anforderungen**  
  
-   Visual Studio Enterprise  
  
## <a name="best-practices"></a>Bewährte Methoden  
 Halten Sie sich an die folgenden Richtlinien, um einen flexiblen Test der programmierten UI zu erstellen.  
  
-   Verwenden Sie wenn möglich den **Test-Generator der programmierten UI**.  
  
-   Ändern Sie die `UIMap.designer.cs`-Datei nicht direkt. Andernfalls werden die an der Datei vorgenommenen Änderungen überschrieben.  
  
-   Erstellen Sie den Test als Sequenz aufgezeichneter Methoden. Weitere Informationen über die Aufzeichnung einer Methode finden Sie unter [Erstellen von Tests der programmierten UI](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate).  
  
-   Jede aufgezeichnete Methode sollte auf eine einzelne Seite, ein einzelnes Formular oder Dialogfeld einwirken. Erstellen Sie eine neue Testmethode für jede neue Seite, jedes neue Formular oder Dialogfeld.  
  
-   Wenn Sie eine Methode erstellen, verwenden Sie statt des Standardnamens einen aussagekräftigen Methodennamen. Ein aussagekräftiger Name hilft dabei, den Zweck der Methode zu erkennen.  
  
-   Beschränken Sie jede aufgezeichnete Methode wenn möglich auf weniger als 10 Aktionen. Dieser modulare Ansatz erleichtert es, eine Methode zu ersetzen, wenn sich die Benutzeroberfläche ändert.  
  
-   Erstellen Sie jede Assertion mithilfe des **Test-Generators der programmierten UI**, der automatisch eine Assertionsmethode zur `UIMap.Designer.cs`-Datei hinzufügt.  
  
-   Wenn sich die Benutzeroberfläche (User Interface, UI) ändert, zeichnen Sie die Testmethoden oder die Assertionsmethoden erneut auf, oder zeichnen Sie die betroffenen Abschnitte einer vorhandenen Testmethode erneut auf.  
  
-   Erstellen Sie eine separate <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>-Datei für jedes Modul in Ihrer getesteten Anwendung. Weitere Informationen finden Sie unter [Testing a Large Application with Multiple UI Maps (Testen einer großen Anwendung mit mehreren UI-Zuordnungen)](../test/testing-a-large-application-with-multiple-ui-maps.md).  
  
-   Verwenden Sie in der getesteten Anwendung aussagekräftige Namen, wenn Sie Benutzeroberflächen-Steuerelemente erstellen. Dadurch wird die Aussagekraft und die Benutzerfreundlichkeit der automatisch generierten Steuerelementnamen erhöht.  
  
-   Wenn Sie Assertionen durch Codierung mit der API erstellen, erstellen Sie eine Methode für jede Assertion in dem Teil der <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>-Klasse, der sich in der `UIMap.cs`-Datei befindet. Rufen Sie diese Methode aus der Testmethode auf, um die Assertion auszuführen.  
  
-   Wenn Sie direkt mit der API codieren, verwenden Sie so oft wie möglich die Eigenschaften und Methoden in den Klassen, die in der `UIMap.Designer.cs`-Datei in Ihrem Code generiert wurden. Diese Klassen machen Ihre Arbeit einfacher und zuverlässiger und helfen Ihnen, produktiver zu sein.  
  
 Tests der codierten UI werden automatisch an zahlreiche Änderungen in der Benutzeroberfläche angepasst. Wenn z. B. ein Benutzeroberflächenelement Position oder Farbe geändert hat, wird beim Test der programmierten UI in den meisten Fällen dennoch das richtige Element gefunden.  
  
 Während eines Testlaufs werden die UI-Steuerelemente vom Testframework mithilfe eines Satzes von Sucheigenschaften gesucht, die für jede Steuerelementklasse in den Definitionen angewendet werden, die durch den **Test-Generator der programmierten UI** in der `UIMap.Designer.cs`-Datei erstellt werden. Die Sucheigenschaften enthalten Name/Wert-Paare von Eigenschaftennamen und Eigenschaftswerten, die zur Identifizierung des Steuerelements verwendet werden können, z.B. die Eigenschaften <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.FriendlyName%2A>, <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.Name%2A> und <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.ControlType%2A> des Steuerelements. Wenn die Sucheigenschaften unverändert sind, findet der Test der programmierten UI erfolgreich das Steuerelement in der Benutzeroberfläche. Wenn die Sucheigenschaften geändert wurden, findet ein intelligenter Vergleichsalgorithmus der Tests der codierten UI anhand von Heuristik Steuerelemente und Fenster in der Benutzeroberfläche. Wenn die Benutzeroberfläche geändert wurde, können Sie möglicherweise die Sucheigenschaften von zuvor identifizierten Elementen ändern, um sicherstellen, dass sie gefunden werden.  
  
## <a name="what-to-do-if-your-user-interface-changes"></a>Vorgehensweise bei geänderter Benutzeroberfläche  
 Benutzeroberflächen werden während der Entwicklung häufig geändert. Nachfolgend finden Sie einige Möglichkeiten, um die Auswirkungen dieser Änderungen zu reduzieren:  
  
-   Suchen Sie die aufgezeichnete Methode, die auf dieses Steuerelement verweist, und verwenden Sie den **Test-Generator der programmierten UI**, um die Aktionen für diese Methode erneut aufzuzeichnen. Sie können den gleichen Namen für die Methode verwenden, um die vorhandenen Aktionen zu überschreiben.  
  
-   Wenn ein Steuerelement über eine Assertion verfügt, die nicht mehr gültig ist:  
  
    -   Löschen Sie die Methode, die die Assertion enthält.  
  
    -   Entfernen Sie den Aufruf dieser Methode aus der Testmethode.  
  
    -   Fügen Sie eine neue Assertion hinzu, indem Sie die Fadenkreuz-Schaltfläche auf das UI-Steuerelement ziehen, die UI-Zuordnung öffnen und die neue Assertion hinzufügen.  
  
 Weitere Informationen über das Aufzeichnen von Tests der programmierten UI finden Sie unter [Verwenden von Benutzeroberflächenautomatisierung zum Testen des Codes ](../test/use-ui-automation-to-test-your-code.md).  
  
## <a name="what-to-do-if-a-background-process-needs-to-complete-before-the-test-can-continue"></a>Vorgehensweise, wenn ein Hintergrundprozess abgeschlossen werden muss, bevor der Test fortgesetzt werden kann  
 Möglicherweise müssen Sie warten, bis ein Prozess beendet wird, bevor Sie mit der nächsten Benutzeroberflächen-Aktion fortfahren können. Hierzu können Sie <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.WaitForReadyLevel%2A> verwenden, um zu warten, bevor der Test wie im folgenden Beispiel fortgeführt wird.  
  
```  
// Set the playback to wait for all threads to finish  
Playback.PlaybackSettings.WaitForReadyLevel = WaitForReadyLevel.AllThreads;  
  
// Press the submit button  
this.UIMap.ClickSubmit();  
  
// Reset the playback to wait only for the UI thread to finish  
Playback.PlaybackSettings.WaitForReadyLevel = WaitForReadyLevel.UIThreadOnly;  
```  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting>   
 [Verwenden von Benutzeroberflächenautomatisierung zum Testen des Codes](../test/use-ui-automation-to-test-your-code.md)   
 [Erstellen von Tests der programmierten UI](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)   
 [Testing a Large Application with Multiple UI Maps (Testen einer großen Anwendung mit mehreren UI-Zuordnungen)](../test/testing-a-large-application-with-multiple-ui-maps.md)   
 [Unterstützte Konfigurationen und Plattformen für Tests der programmierten UI und Aktionsaufzeichnungen](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)


---
title: Live Unit Testing in Visual Studio| Microsoft-Dokumentation
ms.date: 2017-03-07
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing
ms.assetid: 5b51fb96-94f4-4926-92b9-262156c05b85
author: rpetrusha
ms.author: ronpet
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: b699132bf1a31d3ef9dc3ba5af3f99c22890c632
ms.contentlocale: de-de
ms.lasthandoff: 05/13/2017

---

# <a name="live-unit-testing-with-visual-studio-2017"></a>Live Unit Testing mit Visual Studio 2017

Wenn Sie eine Anwendung entwickeln, führt Live Unit Testing automatisch alle betroffenen Komponententests im Hintergrund aus und zeigt die Ergebnisse und die Codeabdeckung in der Visual Studio-IDE in Echtzeit live an. Wenn Sie Ihren Code ändern, bietet Live Unit Testing Feedback dazu, welche Auswirkungen Ihre Änderungen auf vorhandene Tests haben und ob der neue von Ihnen hinzugefügte Code von einem oder mehreren vorhandenen Tests abgedeckt wird. So werden Sie daran erinnert, Komponententests zu schreiben, während Sie Fehler beheben oder neue Funktionen hinzufügen.

> [!NOTE]
> Live Unit Testing steht für C#- und Visual Basic-Projekte zur Verfügung, die auf .NET Framework in der Enterprise-Edition von Visual Studio 2017 ausgerichtet sind. Derzeit ist diese Funktion nicht für .NET Core verfügbar.

## <a name="supported-test-frameworks"></a>Unterstützte Testframeworks

Live Unit Testing kann mit den drei gängigen Frameworks für Komponententests verwendet werden, die in der folgenden Tabelle aufgeführt sind. Die unterstützte Mindestversion der Adapter und Frameworks ist ebenfalls in der Tabelle aufgeführt. Die Frameworks für Komponententests sind auf „NuGet.org“ verfügbar.
 
<table> 
<tr>
   <th>Testframework</th>
   <th>Mindestversion des Visual Studio-Adapters</th>
   <th>Mindestversion des Frameworks</th>
</tr>
<tr>
   <td>xUnit.net</td>
   <td> xunit.runner.visualstudio, Version 2.2.0-beta3-build1187</td>
   <td>xunit 2.0</td> 
</tr>
<tr>
   <td>NUnit</td>
   <td>NUnit3TestAdapter, Version 3.5.1</td>  
   <td>NUnit, Version 3.5.0</td>
</tr>
<tr>
   <td>MSTest</td>
   <td>MSTest.TestAdapter 1.1.4-preview</td>
   <td>MSTest.TestFramework 1.0.5-preview</td>
</tr>
</table>

Wenn in vorhandenen Projekten Verweise auf ältere Adapter und Testframeworks vorliegen, müssen Sie diese entfernen. (Stellen Sie sicher, dass Sie den Verweis auf `Microsoft.VisualStudio.QualityTools.UnitTestFramework` entfernen, wenn Sie MSTest verwenden.) Fügen Sie die neuen Versionen hinzu, wenn Live Unit Testing bei Ihnen nicht funktioniert. 

In einigen Fällen müssen Sie explizit die NuGet-Pakete wiederherstellen, auf die die Projekte in der Projektmappe verweisen, damit Live Unit Testing funktioniert. Hierzu können Sie entweder die Projektmappe explizit erstellen (wählen Sie im obersten Visual Studio-Menü **Erstellen** und dann **Projektmappe neu erstellen** aus) oder Pakete in der Projektmappe wiederherstellen (klicken Sie mit der rechten Maustaste auf die Projektmappe, und wählen Sie **NuGet-Pakete wiederherstellen** aus), bevor Sie Living Unit Testing aktivieren. 

#    <a name="configuring-live-unit-testing"></a>Konfigurieren von Live Unit Testing

Sie können Live Unit Testing konfigurieren, indem Sie im obersten Visual Studio-Menü **Extras**, **Optionen** und dann im Dialogfeld **Optionen** im linken Bereich **Live Unit Testing** auswählen. Die folgende Abbildung zeigt die verfügbaren Konfigurationsoptionen für Live Unit Testing in dem Dialogfeld.

  ![Bild](~/test/media/lut-options.png)

Die konfigurierbaren Optionen umfassen Folgendes:

- Ob Live Unit Testing automatisch ausgeführt wird, wenn eine Projektmappe geöffnet wird.
- Ob Live Unit Testing angehalten wird, wenn eine Projektmappe erstellt und gedebuggt wird oder wenn die Akkuleistung des Systems unter einen bestimmten Schwellenwert sinkt.
- Das Intervall, nach dem eine Zeitüberschreitung für einen Testfall auftritt. Der Standardwert ist 30 Sekunden. 
- Die Anzahl der Testläufe, die Live Unit Testing erstellt. 
- Den Umfang an Informationen, der in das Live Unit Testing-Fenster **Ausgabe** geschrieben wird. Mögliche Optionen sind: Keine Protokollierung („Keine“), nur Fehlermeldungen („Fehler“), Fehler- und Informationsmeldungen („Info“, die Standardeinstellung) oder alle Details („Ausführlich“).

Sie können auch eine ausführlichen Ausgabe im Live Unit Testing-Fenster **Ausgabe** anzeigen, indem Sie einer Umgebungsvariablen auf Benutzerebene mit dem Namen `VS_UTE_DIAGNOSTICS` den Wert „1“ zuweisen und Visual Studio neu starten. 

Um detaillierte MSBuild-Protokollmeldungen von Live Unit Testing in einer Datei aufzuzeichnen, legen Sie die `LiveUnitTesting_BuildLog`-Umgebungsvariable auf Benutzerebene auf den Namen der Datei fest, die das Protokoll enthalten soll.

## <a name="starting-pausing-and-stopping-live-unit-testing"></a>Starten, Anhalten und Beenden von Live Unit Testing

Sie aktivieren Live Unit Testing, indem Sie im obersten Visual Studio-Menü **Test**, **Live Unit Testing** und dann **Starten** auswählen. Wenn Live Unit Testing aktiviert ist, ändern sich die verfügbaren Optionen im **Live Unit Testing**-Menü von dem einzelnen Element **Starten** zu **Anhalten**, **Beenden** und **Neu starten**.

Sie können Live Unit Testing jederzeit vorübergehend anhalten oder vollständig beenden. Sie könnten sich beispielsweise dann dazu entschließen, wenn Sie gerade ein Refactoring ausführen und wissen, dass die Tests für eine Weile gestört sind. Die drei Menüoptionen sind:

- **Anhalten**: Unterbricht Live Unit Testing vorübergehend. 
    Wenn Live Unit Testing angehalten wird, wird die Abdeckungsvisualisierung nicht im Editor dargestellt, aber alle gesammelten Daten bleiben erhalten. Um Live Unit Testing fortzusetzen, wählen Sie im Live Unit Testing-Menü „Weiter“ aus. Live Unit Testing führt die notwendigen Schritte aus, um alle Änderungen nachzuholen, die vorgenommen wurden, während Live Unit Testing angehalten war, und die Glyphen werden entsprechend aktualisiert. 
- **Beenden**: Beendet Live Unit Testing vollständig. Live Unit Testing verwirft alle Daten, die gesammelt wurden.
- **Neu starten**: Dies entspricht dem Auswählen von **Beenden** gefolgt von **Starten** aus dem **Live Unit Testing**-Menü.

##    <a name="viewing-coverage-visualization-in-the-editor-as-you-type"></a>Anzeigen der Abdeckungsvisualisierung im Editor während der Eingabe

Nach der Aktivierung aktualisiert Live Unit Testing alle Codezeilen im Visual Studio-Editor, um Ihnen zu zeigen, ob der Code, den Sie schreiben, von Komponententests abgedeckt ist, und ob die Tests, die ihn abdecken, erfolgreich sind.  Die folgende Abbildung zeigt Codezeilen mit erfolgreichen und fehlgeschlagenen Tests sowie Codezeilen, die nicht durch Tests abgedeckt sind. Zeilen mit einem grünen „✓“ werden nur durch erfolgreiche Tests abgedeckt, Zeilen mit einem roten „🞩“ werden von einem oder mehreren fehlgeschlagenen Tests abgedeckt, und Zeilen mit einem blauen „–“ werden nicht von Tests abgedeckt.

  ![Bild](~/ide/media/lut-codewindow.png)

Die Abdeckungsvisualisierung von Live Unit Testing wird sofort aktualisiert, wenn Sie Code im Code-Editor ändern. Während der Verarbeitung der Änderungen wird die Visualisierung geändert, um anzugeben, dass die Daten nicht auf dem neuesten Stand sind. Dazu wird ein rundes Uhrensymbol unterhalb der Symbole für erfolgreiche, fehlgeschlagene und nicht abgedeckte Test angezeigt, wie in der folgenden Abbildung dargestellt.

  ![Bild](~/test/media/lut-codeupdating.png)
 
## <a name="getting-information-on-successful-or-failed-tests"></a>Abrufen von Informationen zu erfolgreichen oder fehlgeschlagenen Tests

Wenn Sie den Mauszeiger im Codefenster über das Symbol für erfolgreiche oder fehlgeschlagene Tests bewegen, können Sie sehen, wie viele Tests diese Zeile betreffen. Wenn Sie auf das Symbol klicken, sehen Sie den Status der einzelnen Tests, wie in der folgenden Abbildung dargestellt.
 
  ![Bild](~/test/media/lut-failedinfo.png) 

Wenn Sie den Mauszeiger über den fehlgeschlagenen Test in der QuickInfo bewegen, wird sie erweitert, und es werden zusätzliche Informationen zu diesem Fehler bereitgestellt, wie in der folgenden Abbildung dargestellt. Wenn Sie in der QuickInfo auf den fehlgeschlagenen Test klicken, können Sie direkt zum Test navigieren.

  ![Bild](~/test/media/lut-failedmsg.png) 

## <a name="diagnosing-and-correcting-test-failures"></a>Diagnose und Korrektur von fehlgeschlagenen Tests

Über den fehlgeschlagenen Test können Sie problemlos den Produktcode debuggen, ihn bearbeiten und die Entwicklung Ihrer Anwendung fortsetzen. Da Live Unit Testing im Hintergrund ausgeführt wird, müssen Sie Live Unit Testing beim Debuggen, Bearbeiten und Fortsetzen des Zyklus nicht beenden und neu starten.

Beispiel: Der in der obigen Abbildung dargestellte fehlgeschlagene Test wurde durch die falsche Annahme in der Testmethode verursacht, dass nicht alphabetische Zeichen `true` zurückgeben, wenn sie an die [Char.IsLower](xref:System.Char.IsLower(System.Char))-Methode übergeben werden. Nachdem wir die Testmethode korrigiert haben, stellen wir fest, dass alle Tests erfolgreich sind. Währenddessen müssen wir Live Unit Testing nicht anhalten oder beenden.

## <a name="live-unit-testing-and-test-explorer"></a>Live Unit Testing und Test-Explorer

Normalerweise stellt der **Test-Explorer** die Schnittstelle bereit, mit der Sie Tests ausführen und debuggen und Testergebnisse analysieren können. Live Unit Testing ist in den **Test-Explorer** integriert. Wenn Live Unit Testing nicht aktiviert ist oder beendet wurde, zeigt der **Test-Explorer** den Status von Komponententests an, als zuletzt ein Test ausgeführt wurde. Änderungen am Quellcode erfordern, dass Sie die Tests erneut ausführen. Wenn Live Unit Testing dagegen aktiviert ist, wird der Status der Komponententests im **Test-Explorer** sofort aktualisiert. Sie müssen Komponententests nicht mehr explizit ausführen. 

Es gibt jedoch einige Unterschiede zwischen dem automatischen Ausführen und Aktualisieren der Testergebnisse durch Live Unit Testing und dem expliziten Ausführen von Tests im **Test-Explorer**. Dazu gehören:

- Beim Ausführen oder Debuggen von Tests im Test-Explorer-Fenster werden reguläre Binärdateien ausgeführt. Live Unit Testing führt dagegen instrumentierte Binärdateien aus. 
- Live Unit Testing erstellt keine neue Anwendungsdomäne zum Ausführen von Tests, sondern führt Tests mit der Standarddomäne aus. Tests, die über das **Test-Explorer**-Fenster ausgeführt werden, erstellen eine neue Anwendungsdomäne.
- Live Unit Testing führt Tests in allen Testassemblys nacheinander aus. Wenn Sie mehrere Tests im **Test-Explorer**-Fenster ausführen und die Schaltfläche **Tests parallel ausführen** ausgewählt ist, werden Tests parallel ausgeführt.

## <a name="including-and-excluding-test-projects-and-test-methods"></a>Einschließen und Ausschließen von Testprojekten und Testmethoden

Bei Projektmappen mit vielen Testprojekten können Sie steuern, welche Projekte und welche einzelnen Methoden in einem Projekt von Live Unit Testing berücksichtigt werden. 

Wenn Sie z.B. eine Projektmappe mit Hunderten von Testprojekten haben, können Sie eine bestimmte Reihe von Testprojekten für Live Unit Testing auswählen. Um die einzelnen Projekte in Komponententests auszuwählen, gehen Sie nach dem Start von Live Unit Testing wie folgt vor:

1.    Klicken Sie mit der rechten Maustaste im Projektmappen-Explorer auf die Projektmappe, und wählen Sie **Livetests** und dann **Ausschließen** aus, um die gesamte Projektmappe auszuschließen.
2.    Klicken Sie mit der rechten Maustaste auf jedes Testprojekt, das Sie in die Tests einschließen möchten, und wählen Sie **Livetests** und dann **Einschließen** aus.
 
Verwenden Sie das Code-Editor-Fenster zum Einschließen oder Ausschließen einzelner Testmethoden. Klicken Sie mit der rechten Maustaste auf die Signatur der Testmethode im Code-Editor-Fenster, und wählen Sie **Livetests** und **Einschließen** oder **Livetests** und **Ausschließen** aus. 

Alternativ können Sie auch das [<ExcludeFromCodeCoverage>](https://msdn.microsoft.com/library/system.diagnostics.codeanalysis.excludefromcodecoverageattribute.aspx)-Attribut anwenden, damit Methoden, Klassen oder Strukturen ihre Abdeckung nicht programmgesteuert in Live Unit Testing melden.

Live Unit Testing speichert den Status für das Einschließen/Ausschließen als Benutzereinstellung, wenn eine Projektmappe geschlossen und erneut geöffnet wird. 

## <a name="see-also"></a>Siehe auch

[Live Unit Testing-Blog](https://go.microsoft.com/fwlink/?linkid=842514)   
[Live Unit Testing – häufig gestellte Fragen](live-unit-testing-faq.md)    
[Channel 9 Video: Live Unit Testing in Visual Studio 2017](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T105)



---
title: "Ermitteln von Änderungen am Code und anderer Verläufe mit CodeLens | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b454893c2d68b23d130d6ff38be493d988dfb1fe
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="find-code-changes-and-other-history-with-codelens"></a>Ermitteln von Änderungen am Code und andere Verläufe mit CodeLens

Konzentrieren Sie sich ganz auf Ihre Arbeit, während Sie ermitteln, was mit Ihrem Code geschehen ist. Dazu müssen Sie nicht einmal den Editor schließen. Suchen Sie Codeverweise und -änderungen, verknüpfte Fehler, Arbeitsaufgaben, Codeüberprüfungen und Komponententests.

> [!NOTE]
> CodeLens steht nur in Visual Studio Enterprise- und Visual Studio Professional-Versionen zur Verfügung. Es ist nicht in Visual Studio Community verfügbar.  

Sehen Sie, wo und wie die einzelnen Codeausschnitte in der Projektmappe verwendet werden:  

![CodeLens-Indikatoren im Code-Editor](../ide/media/codelensoverview.png "CodeLensOverview")  

Diskutieren Sie die Codeänderungen mit Ihrem Team, ohne den Editor verlassen zu müssen:  

![CodeLens: Kontaktaufnahme mit dem Team](../ide/media/codelensovervew2.png "CodeLensOvervew2")  

Um die Indikatoren auswählen, die Sie anzeigen möchten, oder CodeLens zu aktivieren bzw. deaktivieren, gehen Sie zu **Tools**, **Optionen**, **Text-Editor**, **Alle Sprachen**, **CodeLens**.  

## <a name="FindReferences"></a> Referenzen zu Ihrem Code finden

Sie benötigen Folgendes:

-  Visual Studio Professional und Visual Studio Enterprise

-  Visual C# .NET- oder Visual Basic .NET-Code

Wählen Sie den Indikator **Verweise** aus (**Alt+2**). Wenn **0 Verweise**angezeigt werden, bedeutet dies lediglich, dass Sie über keine Verweise aus Visual C#- oder Visual Basic-Code verfügen. Dies beinhaltet keine Verweise aus anderen Elementen wie XAML- und ASPX-Dateien.

![CodeLens: Auswählen des Verweisindikators](../ide/media/codelensviewreferenceslist.png "CodeLensViewReferencesList")  

Um den verweisenden Code anzuzeigen, bewegen Sie den Mauszeiger über den Verweis.  

![CodeLens: Peek auf Verweis](../ide/media/codelensviewreferencespeekreference.png "CodeLensViewReferencesPeekReference")  

Doppelklicken Sie zum Öffnen der Datei mit dem Verweis auf den Verweis.  

Um Beziehungen zwischen diesem Code und seinen Verweisen anzuzeigen, [erstellen Sie eine Code Map](../modeling/map-dependencies-across-your-solutions.md), und wählen Sie im Code Map-Kontextmenü die Option **alle Verweise anzeigen** .

![CodeLens: Verweise in Code Map](../ide/media/codelensmappedreferences.png "CodeLensMappedReferences")  

## <a name="FindCodeHistory"></a> Ermitteln des Codeverlaufs und der verknüpften Elemente

Überprüfen Sie den Codeverlauf, um ermitteln zu können, was mit Ihrem Code geschehen ist. Sie können die Änderungen auch überprüfen, bevor sie mit Ihrem Code zusammengeführt werden. Auf diese Weise können Sie besser beurteilen, wie sich Änderungen in anderen Verzweigungen möglicherweise auf Ihren Code auswirken.

Sie benötigen Folgendes:

- Visual Studio Professional und Visual Studio Enterprise

- Team Foundation Server 2013 oder höher, Visual Studio Team Services oder Git

- [Lync 2010 oder höher oder Skype for Business](http://technet.microsoft.com/en-us/lync)für das Kontaktieren Ihres Teams aus dem Code-Editor  

Detaillierte Informationen zu CodeLens für Visual C# .NET- oder Visual Basic .NET-Code, der mit Team Foundation-Versionskontrolle (TFVC) oder Git gespeichert ist, finden Sie auf den Klassen- und Methodenebenen (*Codeindikatoren auf Elementebene* ). Wenn Ihr Git-Repository in TfGit gehostet ist, finden Sie auch Links zu TFS-Arbeitsaufgaben.  

![Codeelement: Ebenenindikatoren](../ide/media/codelenselementlevelindicators.png "CodeLensElementLevelIndicators")  

Bei alle anderen Dateitypen, die Sie im Visual Studio-Editor öffnen können, finden Sie detaillierte Informationen zu CodeLens für die gesamte Datei am unteren Rand des Fensters (*Indikatoren auf Dateiebene* ).

![Dateiebene: CodeLens-Indikatoren](../ide/media/almcodelensfilelevelindicators.png "ALMCodeLensFileLevelIndicators")  

Drücken Sie zum Verwenden der Tastatur zum Auswählen von Indikatoren die **ALTTASTE** , um die zugehörigen Nummerntasten anzuzeigen.  

![Drücken Sie die ALT-TASTE, um die Tastaturzugriffsnummern einzublenden](../ide/media/codelensaltkeyindicators.png "CodeLensAltKeyIndicators")  

### <a name="find-changes-in-your-code"></a>Suchen nach Änderungen im Code

Finden Sie in den Codeindikatoren auf Elementebene heraus, wer welche Änderungen an Ihrem Code vorgenommen hat. Dies sehen Sie, wenn Sie die Team Foundation-Versionskontrolle (TFVC) in Team Foundation Server oder Visual Studio Team Services verwenden.  

![CodeLens: Abrufen des Änderungsverlaufs für ihren Code in TFVC](../ide/media/codelenscodechanges.png "CodeLensCodeChanges")  

Der Standardzeitraum umfasst die letzten 12 Monate. Wenn Ihr Code in Team Foundation Server gespeichert ist, können Sie diesen Wert ändern, indem Sie den [TFSConfig-Befehl](http://msdn.microsoft.com/en-us/94424190-3b6b-4f33-a6b6-5807f4225b62) mit dem [CodeIndex-Befehl](../ide/codeindex-command.md) und dem **/indexHistoryPeriod** -Flag ausführen.  

Zum Anzeigen eines ausführlichen Verlaufs aller Änderungen, einschließlich der von vor mehr als einem Jahr, wählen Sie **Alle Dateiänderungen anzeigen**.  

![Anzeigen aller Codeänderungen](../ide/media/codelensshowsallchanges.png "CodeLensShowsAllChanges")  

Daraufhin wird das Verlaufsfenster für die Changesets geöffnet.  

![Verlaufsfenster für alle Codeänderungen](../ide/media/codelenscodechangeshistory.png "CodeLensCodeChangesHistory")  

Wenn sich Ihre Dateien in einem Git-Repository befinden und Sie den Änderungsindikator für die Code-Elementebene auswählen, wird dies angezeigt.  

![CodeLens: Abrufen des Änderungsverlaufs für ihren Code in Git](../ide/media/codelenscodechangesgit.png "CodeLensCodeChangesGit")  

Suchen Sie in den Indikatoren auf Dateiebene am unteren Rand des Fensters nach Änderungen für eine gesamte Datei (mit Ausnahme von C#- und Visual Basic-Dateien).  

![CodeLens: Abrufen von Codedateidetails](../ide/media/codelensfilelevel.png "CodeLensFileLevel")  

Um weitere Details zu einer Änderung zu erhalten, klicken Sie mit der rechten Maustaste auf dieses Element. Abhängig davon, ob Sie TFVC oder Git verwenden, stehen Ihnen zahlreiche Optionen zum Vergleichen der Dateiversionen, zum Anzeigen detaillierter Informationen und Nachverfolgen von Änderungen, zum Abrufen der ausgewählten Dateiversion und zum Senden einer E-Mail an den Autor zur Verfügung, um ihn über diese Änderung zu informieren. Ein Teil dieser detaillierten Informationen wird in Team Explorer angezeigt.  

Sie können auch sehen, wer den Code in einem bestimmten Zeitraum geändert hat. Dadurch können Sie Muster bei den Änderungen Ihres Teams erkennen und ihre Auswirkung bewerten.  

![CodeLens: Anzeigen des Verlaufs von Codeänderungen als Diagramm](../ide/media/codelens.png "CodeLens")  

#### <a name="find-changes-in-your-current-branch"></a>Änderungen in der aktuellen Verzweigung finden

Angenommen, Ihr Team hat mehrere Verzweigungen – eine Hauptverzweigung und eine untergeordnete Entwicklung –, dann tun Sie Folgendes, um das Risiko von Schäden an stabilem Code zu senken:  

![CodeLens: Sehen, wann Ihr Code gebrancht wurde](../ide/media/codelensfirstbranchconceptual.png "CodeLensFirstBranchConceptual")  

So finden Sie heraus, wie viele Personen Ihren Code geändert haben und wie viele Änderungen in der Hauptverzweigung vorgenommen wurden (**ALT + 6**):  

![CodeLens: Ermitteln der Anzahl der Änderungen in Ihrem Branch](../ide/media/codelensbranchchanges.png "CodeLensBranchChanges")  

#### <a name="find-when-your-code-was-branched"></a>Sehen, wann Ihr Code verzweigt wurde

Gehen Sie in die untergeordnete Verzweigung des Codes und dort zur Verzweigung Dev. Wählen Sie den Änderungsindikator aus (**Alt + 6**):  

![CodeLens: Sehen, wann Ihr Code gebrancht wurde](../ide/media/codelensfirstbranchscreenshot.png "CodeLensFirstBranchScreenshot")  

#### <a name="find-incoming-changes-from-other-branches"></a>Eingehende Änderungen aus anderen Verzweigungen sehen

![CodeLens: Ermitteln von Codeänderungen in anderen Branches](../ide/media/codelensbranchchangecheckinconceptual.png "CodeLensBranchChangeCheckinConceptual")  

... wie diese Fehlerbehebung hier in der Verzweigung Dev:

![CodeLens: Aktiviertes in anderen Branch ändern](../ide/media/codelensbranchchangedevscreenshot.png "CodeLensBranchChangeDevScreenshot")  

Sie können die Änderung überprüfen, ohne die aktuelle Verzweigung zu verlassen (Hauptverzweigung):  

![CodeLens: Eingehende Änderung aus einem anderen Branch anzeigen](../ide/media/codelensbranchchangemainscreenshot.png "CodeLensBranchChangeMainScreenshot")  

#### <a name="find-when-changes-got-merged"></a>Herausfinden, wann Änderungen zusammengeführt wurden

So können Sie sehen, welche Änderungen in Ihrer Verzweigung enthalten sind:  

![CodeLens: Gemergte Änderungen zwischen Branches](../ide/media/codelensbranchmergedconceptual.png "CodeLensBranchMergedConceptual")  

Zum Beispiel hat der Code in der Hauptverzweigung jetzt die Fehlerkorrektur der Verzweigung Dev:  

![CodeLens: Gemergte Änderungen zwischen Branches](../ide/media/codelensbranchmergedscreenshot.png "CodeLensBranchMergedScreenshot")  

#### <a name="compare-an-incoming-change-with-your-local-version-shift--f10"></a>Vergleichen einer eingehenden Änderung mit der lokalen Version (Umschalt + F10)

![CodeLens: Vergleichen einer eingehenden Änderung mit der lokalen Version](../ide/media/codelensbranchincomingchangemenu.png "CodeLensBranchIncomingChangeMenu")  

Sie können auch auf das Changeset doppelklicken.

#### <a name="what-do-the-icons-mean"></a>Was bedeuten die Symbole?

|**Symbol**|**Woher stammt die Änderung?**|  
|--------------|-----------------------------------------|  
|![CodeLens: Symbol für Änderung aus dem aktuellen Branch](../ide/media/codelensbranchcurrenticon.png "CodeLensBranchCurrentIcon")|Die aktuelle Verzweigung|  
|![CodeLens: Symbol für Änderung aus dem übergeordneten Branch](../ide/media/codelensbranchparenticon.png "CodeLensBranchParentIcon")|Die übergeordnete Verzweigung|  
|![CodeLens: Symbol für Änderung aus einem untergeordneten Branch](../ide/media/codelensbranchchildicon.png "CodeLensBranchChildIcon")|Eine untergeordnete Verzweigung|  
|![CodeLens: Symbol für Änderung aus einem Peerbranch](../ide/media/codelensbranchpeericon.png "CodeLensBranchPeerIcon")|Eine Peerverzweigung|  
|![CodeLens: Symbol für Änderung aus einem weiter entfernten Branch](../ide/media/codelensbranchfurtherawayicon.png "CodeLensBranchFurtherAwayIcon")|Eine Verzweigung, die sich weiter entfernt befindet als über- oder untergeordnet und Peer|  
|![CodeLens: Symbol für Merge aus dem übergeordneten Branch](../ide/media/codelensbranchmergefromparenticon.png "CodeLensBranchMergeFromParentIcon")|Eine Zusammenführung von der übergeordneten zu einer untergeordneten Verzweigung|
|![CodeLens: Symbol für Merge aus einem untergeordneten Branch](../ide/media/codelensbranchmergefromchildicon.png "CodeLensBranchMergeFromChildIcon")|Eine Zusammenführung von der untergeordneten zu einer übergeordneten Verzweigung|  
|![CodeLens: Symbol für Merge aus einem nicht zugeordneten Branch](../ide/media/codelensbranchmergefromunrelatedicon.png "CodeLensBranchMergeFromUnrelatedIcon")|Eine Zusammenführung von einer nicht verwandten Verzweigung (Zusammenführung ohne Basis)|  

### <a name="find-linked-work-items"></a>Suchen von verknüpften Arbeitsaufgaben

![CodeLens: Ermitteln von Arbeitsaufgaben für bestimmten Code](../ide/media/codelensworkitems.png "CodeLensWorkItems")  

### <a name="find-linked-code-reviews"></a>Verknüpfte Codeüberprüfungen suchen

![CodeLens: Code Review-Anforderungen anzeigen](../ide/media/codelenscodereviews.png "CodeLensCodeReviews")  

### <a name="find-linked-bugs"></a>Verknüpfte Fehler suchen

![CodeLens: Suchen von mit Changesets verknüpften Fehlern](../ide/media/codelensbugschangesets.png "CodeLensBugsChangesets")  

### <a name="contact-the-owner-of-an-item"></a>Den Besitzer eines Elements kontaktieren

![Kontaktaufnahme mit dem Besitzer eines Elements](../ide/media/codelenscontactitemowner.png "CodeLensContactItemOwner")  

Öffnen Sie das Kontextmenü für ein Element, um die Kontaktoptionen anzuzeigen. Wenn Sie Lync oder Skype for Business installiert haben, werden folgende Optionen angezeigt:  

![Kontaktoptionen für ein Element](../ide/media/codelensitemcontactmenu.png "CodeLensItemContactMenu")  

##  <a name="FindRunUnitTests"></a> Komponententests für Ihren Code suchen

Weitere Informationen zu Komponententests, die für Ihren Code vorhanden sind, ohne Test-Explorer zu öffnen. Sie benötigen Folgendes:  

-   Visual Studio Professional und Visual Studio Enterprise  
  
-   Visual C# .NET- oder Visual Basic .NET-Code  
  
-   Ein [Komponententestprojekt](../test/unit-test-your-code.md) , das über Komponententests für Ihren Anwendungscode verfügt  
  
1.  Wechseln Sie zum Anwendungscode, der über Komponententests verfügt.  
  
2.  Überprüfen Sie die Tests für diesen Code (**ALT + 3**).  
  
     ![CodeLens: Auswählen des Teststatus im Code-Editor](../ide/media/codelenschoosetestindicator.png "CodeLensChooseTestIndicator")  
  
3.  Wenn Sie ein Warnsymbol ![CodeLens – Warnung für noch nicht ausgeführte Komponententests](../ide/media/codelenstestwarningicon.png "CodeLensTestWarningIcon") sehen, die Tests ausführen.  
  
     ![CodeLens: Ausführen von noch nicht ausgeführten Komponententests](../ide/media/codelenstestsnotyetrun.png "CodeLensTestsNotYetRun")  
  
4.  Zum Überprüfen der Definition eines Tests doppelklicken Sie im CodeLens-Indikatorfenster auf das Testelement, um die Codedatei im Editor zu öffnen.  
  
     ![CodeLens: Wechseln zur Komponententestdefinition](../ide/media/codelensunittestdefinition.png "CodeLensUnitTestDefinition")  
  
5.  Überprüfen Sie die Testergebnisse. Wählen Sie den Teststatusindikator (![CodeLens: Symbol für Fehler bei Komponententest](../ide/media/codelenstestfailedicon.png "CodeLensTestFailedIcon") oder ![CodeLens: Symbol für bestandenen Komponententest](../ide/media/codelenstestpassedicon.png "CodeLensTestPassedIcon")) aus, oder drücken Sie **ALT+1**.  
  
     ![CodeLens: Anzeigen des Komponententestergebnisses](../ide/media/codelensunittestresult.png "CodeLensUnitTestResult")  
  
6.  Zum Überprüfen, wie viele Personen diesen Test geändert haben, wer ihn geändert hat oder wie viele Änderungen an diesem Test durchgeführt wurden, [Den Verlauf Ihres Codes und verwandte Themen suchen](#FindCodeHistory).

##  <a name="QA"></a> Fragen und Antworten

###  <a name="ChangeOrTurnOff"></a> F: Wie kann ich CodeLens aktivieren oder deaktivieren? Oder wie kann ich auswählen, welche Indikatoren angezeigt werden?

**A:**  Sie können die Indikatoren aktivieren und deaktivieren, mit Ausnahme des Verweisindikators. Gehen Sie zu **Tools**, **Optionen**, **Text-Editor**, **Alle Sprachen**, **CodeLens**.  
  
 Wenn die Indikatoren aktiviert wurden, können Sie die CodeLens-Optionen auch über die Indikatoren öffnen.  
  
 ![CodeLens: Indikatoren aktivieren oder deaktivieren](../ide/media/codelensturnoffonindicatorsfromcode.png "CodeLensTurnOffOnIndicatorsFromCode")  
  
 Aktivieren bzw. deaktivieren Sie CodeLens-Indikatoren auf Dateiebene mithilfe der Chevron-Symbole unten im Editor-Fenster.  
  
 ![Aktivieren und Deaktivieren von Indikatoren auf Dateiebene](../ide/media/codelensfilelevelonandoff.png "CodeLensFileLevelOnAndOff")  
  
###  <a name="NoIndicators"></a>F: Wo befindet sich CodeLens?

**A:** CodeLens wird  in Visual C# .NET- und Visual Basic .NET-Code auf der Methoden-, Klassen-, Indexer- und Eigenschaftsebene angezeigt. CodeLens wird auf Dateiebene für alle anderen Dateitypen angezeigt.

- Stellen Sie sicher, dass CodeLens aktiviert ist. Gehen Sie zu **Tools**, **Optionen**, **Text-Editor**, **Alle Sprachen**, **CodeLens**.  
  
- Wenn Ihr Code in TFS gespeichert ist, stellen Sie sicher, dass die Codeindizierung aktiviert ist. Verwenden Sie hierzu den [CodeIndex-Befehl](../ide/codeindex-command.md) mit dem [TFSConfig-Befehl](http://msdn.microsoft.com/en-us/94424190-3b6b-4f33-a6b6-5807f4225b62).  

- TFS-bezogene Indikatoren werden nur angezeigt, wenn Arbeitsaufgaben mit dem Code verknüpft sind und wenn Sie über Berechtigungen zum Öffnen verknüpfter Arbeitsaufgaben verfügen. [Überprüfen Sie, ob Sie über Teammitgliedsberechtigungen verfügen.](http://msdn.microsoft.com/en-us/f58805de-ba61-4d09-8f2d-d3ab9662ecfd)  

- Komponententestindikatoren werden nicht angezeigt, wenn der Anwendungscode nicht über Komponententests verfügt. Teststatusindikatoren werden automatisch in Testprojekten angezeigt. Wenn Sie, dass der Anwendungscode über Komponententests verfügt, die Testindikatoren jedoch nicht angezeigt werden, versuchen Sie, die Projektmappe (**STRG+UMSCHALT+B**) zu erstellen.  

### <a name="q-why-dont-i-see-the-work-item-details-for-a-commit"></a>F: Warum sehe ich keine Arbeitsaufgabendetails für einen Commit?

**A:** Dies kann passieren, wenn CodeLens die Arbeitsaufgaben in TFS nicht finden kann. Überprüfen Sie, dass Sie mit dem Teamprojekt verbunden sind, das die Arbeitsaufgaben beinhaltet und dass Sie zum Anzeigen dieser Arbeitsaufgaben berechtigt sind. Dies kann auch vorkommen, wenn die Commit-Beschreibung falsche Informationen über die Arbeitsaufgaben-IDs in TFS enthält.  

###  <a name="NoLync"></a> F: Warum sehe ich keine Lync- bzw. Skype-Indikatoren?

**A:** Wenn Sie nicht bei Lync oder Skype for Business angemeldet sind, es nicht installiert haben oder über keine unterstützte Konfiguration verfügen, werden diese Indikatoren nicht angezeigt. Sie können jedoch weiterhin E-Mails senden:  

![CodeLens: Kontaktaufnahme mit dem Besitzer des Changesets per E-Mail](../ide/media/codelenscodesendmailchangesetnolync1.png "CodeLensCodeSendMailChangesetNoLync1")  

 **Welche Lync- und Skype-Konfigurationen werden unterstützt?**

-   Skype for Business(32-Bit- oder 64-Bit)  

-   Lync 2010 oder höher allein (32-Bit- oder 64-Bit), aber nicht Lync Basic 2013 mit Windows 8.1  

CodeLens unterstützt nicht die Installation verschiedener Versionen von Lync oder Skype. Sie sind möglicherweise nicht für alle lokalisierten Versionen von Visual Studio lokalisiert.  

### <a name="q-how-do-i-change-the-font-and-color-for-codelens"></a>F: Wie ändere ich Schriftart und Farbe für CodeLens?

**A:** Wechseln zu **Extras**, **Optionen**, **Umgebung**, **Schriftarten und Farben**.  

![CodeLens: Ändern der Schriftart- und Farbeinstellungen](../ide/media/codelensoptionsfontscolorssettings.png "CodeLensOptionsFontsColorsSettings")  

So verwenden Sie die Tastatur:

1.  Drücken Sie **ALT+T+O** , um das Feld **Optionen** zu öffnen.  

2.  Drücken Sie die **NACH-OBEN-TASTE** oder die **NACH-UNTEN-TASTE** , um zum Knoten **Umgebung** zu wechseln, und dann die **NACH-LINKS-TASTE** , um den Knoten zu erweitern.  

3.  Drücken Sie die **NACH-UNTEN-TASTE** , um zu **Schriftarten und Farben**zu wechseln.  

4.  Drücken Sie die **TAB-TASTE** , um zur Liste **Einstellungen anzeigen für** zu wechseln, und drücken Sie dann die **NACH-UNTEN-TASTE** , um **CodeLens**auszuwählen.  

### <a name="q-can-i-move-the-codelens-heads-up-display"></a>F: Kann ich das CodeLens-Heads-up-Display verschieben?

**A:** Ja, wählen Sie ![CodeLens als Fenster andocken](../ide/media/codelensdockwindow.png "CodeLensDockWindow") aus, um CodeLens als Fenster anzudocken.  

![Andocken des CodeLens-Indikatorfensters](../ide/media/codelensselectdockwindow.png "CodeLensSelectDockWindow")  

![Das angedockte CodeLens-Verweisfenster](../ide/media/codelensreferencesdockedwindow.png "CodeLensReferencesDockedWindow")  

### <a name="q-how-do-i-refresh-the-indicators"></a>F: Wie aktualisiere ich die Indikatoren?

**A:** Dies hängt vom Indikator ab:  

-   **Verweise**: Dieser Indikator wird bei einer Änderung des Codes automatisch aktualisiert. Wenn Sie den Indikator als separates Fenster verankert haben, aktualisieren Sie den Indikator hier manuell:  

     ![CodeLens: als Fenster andocken](../ide/media/codelensviewreferencesdocked.png "CodeLensViewReferencesDocked")  

-   **Team**: Aktualisieren Sie diese Indikatoren hier manuell:  

     ![CodeLens: Aktualisieren von Indikatoren](../ide/media/codelensrefreshindicatorsfromcode.png "CodeLensRefreshIndicatorsFromCode")  

-   **Test**: [Komponententests für Ihren Code zu suchen](#FindRunUnitTests) zum Aktualisieren dieses Indikators.  

###  <a name="LocalVersion"></a> F: Was bedeutet „Lokale Version“?

**A:** Der Pfeil **Lokale Version** zeigt auf das neueste Changeset in der lokalen Version dieser Datei. Wenn der Server über neuere Changesets verfügt, werden sie je nach Reihenfolge, in der sie sortiert sind, über oder unter dem Pfeil **Lokale Version** angezeigt.  

### <a name="q-can-i-manage-how-codelens-processes-code-to-show-history-and-linked-items"></a>F: Kann ich verwalten, wie CodeLens den Code verarbeitet, um den Verlauf und verknüpfte Elemente anzuzeigen?

**A:** Ja, wenn sich der Code in TFS befindet, können Sie hierzu den [CodeIndex-Befehl](../ide/codeindex-command.md) mit dem [TFSConfig-Befehl](http://msdn.microsoft.com/en-us/94424190-3b6b-4f33-a6b6-5807f4225b62)verwenden.

## <a name="see-also"></a>Siehe auch

[Schreiben von Code im Editor](../ide/writing-code-in-the-code-and-text-editor.md)
---
title: Ermitteln von Änderungen am Code und anderer Verläufe mit CodeLens | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: f697d7b4-704e-4cac-b13a-bc57d2ff8318
caps.latest.revision: 134
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8876a0a3c2b978443ee4bc74097dbc9fdd410b8b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656004"
---
# <a name="find-code-changes-and-other-history-with-codelens"></a>Ermitteln von Änderungen am Code und andere Verläufe mit CodeLens
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Konzentrieren Sie sich ganz auf Ihre Arbeit, während Sie ermitteln, was mit Ihrem Code geschehen ist. Dazu müssen Sie nicht einmal den Editor schließen. Suchen Sie Codeverweise und -änderungen, verknüpfte Fehler, Arbeitselemente, Codeüberprüfungen und Komponententests.

> [!NOTE]
> CodeLens steht nur in Visual Studio Enterprise- und Visual Studio Professional-Versionen zur Verfügung. Es ist nicht in Visual Studio Community verfügbar.

 Sehen Sie, wo und wie die einzelnen Codeausschnitte in der Projektmappe verwendet werden:

 ![Codelta ens-Indikatoren im Code-Editor](../ide/media/codelensoverview.png "Codelta-soverview")

 Diskutieren Sie die Codeänderungen mit Ihrem Team, ohne den Editor verlassen zu müssen:

 ![Codelta ens &#45; wenden Sie sich an Ihr Team](../ide/media/codelensovervew2.png "CodeLensOvervew2")

 Um die Indikatoren auswählen, die Sie anzeigen möchten, oder CodeLens zu aktivieren bzw. deaktivieren, gehen Sie zu **Tools**, **Optionen**, **Text-Editor**, **Alle Sprachen**, **CodeLens**.

## <a name="FindReferences"></a> Referenzen zu Ihrem Code finden
 Sie benötigen Folgendes:

- Visual Studio Professional und Visual Studio Enterprise

- Visual C# .NET- oder Visual Basic .NET-Code

  Wählen Sie den Indikator **Verweise** aus (**Alt+2**). Wenn **0 Verweise**angezeigt werden, bedeutet dies lediglich, dass Sie über keine Verweise aus Visual C#- oder Visual Basic-Code verfügen. Dies beinhaltet keine Verweise aus anderen Elementen wie XAML- und ASPX-Dateien.

  ![Codelta ens &#45; auswählen des Verweis Indikators](../ide/media/codelensviewreferenceslist.png "Codelta-viewreferenceslist")

  Um den verweisenden Code anzuzeigen, bewegen Sie den Mauszeiger über den Verweis.

  ![Codelta ens &#45; -Peek-Referenz](../ide/media/codelensviewreferencespeekreference.png "Codelta-viewreferencespeekreferenzierung")

  Doppelklicken Sie zum Öffnen der Datei mit dem Verweis auf den Verweis.

  Um Beziehungen zwischen diesem Code und seinen Verweisen anzuzeigen, [erstellen Sie eine Code Map](../modeling/map-dependencies-across-your-solutions.md), und wählen Sie im Code Map-Kontextmenü die Option **alle Verweise anzeigen** .

  ![Codelta ens &#45; -Verweise auf Code Map](../ide/media/codelensmappedreferences.png "Codelta-mappeer-ferences")

## <a name="FindCodeHistory"></a> Ermitteln des Codeverlaufs und der verknüpften Elemente
 Überprüfen Sie den Codeverlauf, um ermitteln zu können, was mit Ihrem Code geschehen ist. Sie können die Änderungen auch überprüfen, bevor sie mit Ihrem Code zusammengeführt werden. Auf diese Weise können Sie besser beurteilen, wie sich Änderungen in anderen Verzweigungen möglicherweise auf Ihren Code auswirken.

 Sie benötigen Folgendes:

- Visual Studio Professional und Visual Studio Enterprise

- Team Foundation Server 2013 oder höher, Visual Studio Team Services oder Git

- [Lync 2010 oder höher oder Skype for Business](https://technet.microsoft.com/lync)für das Kontaktieren Ihres Teams aus dem Code-Editor

  Detaillierte Informationen zu CodeLens für Visual C# .NET- oder Visual Basic .NET-Code, der mit Team Foundation-Versionskontrolle (TFVC) oder Git gespeichert ist, finden Sie auf den Klassen- und Methodenebenen (*Codeindikatoren auf Elementebene* ). Wenn Ihr Git-Repository in TfGit gehostet ist, finden Sie auch Links zu TFS-Arbeitselementen.

  ![Indikatoren auf&#45;Code Element Ebene](../ide/media/codelenselementlevelindicators.png "Codelta enselementlevelindicator")

  Bei alle anderen Dateitypen, die Sie im Visual Studio-Editor öffnen können, finden Sie detaillierte Informationen zu CodeLens für die gesamte Datei am unteren Rand des Fensters (*Indikatoren auf Dateiebene* ).

  ![Codelta ens-Indikatoren auf Datei&#45;Ebene](../ide/media/almcodelensfilelevelindicators.png "Almcodelta-filelevelindicator")

  Drücken Sie zum Verwenden der Tastatur zum Auswählen von Indikatoren die **ALTTASTE** , um die zugehörigen Nummerntasten anzuzeigen.

  ![Drücken Sie alt, um die Tastenkombinationen anzuzeigen.](../ide/media/codelensaltkeyindicators.png "Einzublenden codelensaltkeyindicators")

### <a name="find-changes-in-your-code"></a>Suchen nach Änderungen im Code
 Finden Sie in den Codeindikatoren auf Elementebene heraus, wer welche Änderungen an Ihrem Code vorgenommen hat. Dies sehen Sie, wenn Sie die Team Foundation-Versionskontrolle (TFVC) in Team Foundation Server oder Visual Studio Team Services verwenden.

 ![Codelta ens: Ändern des Änderungs Verlaufs für Ihren Code in tfvc](../ide/media/codelenscodechanges.png "Codelta-codechanges")

 Der Standardzeitraum umfasst die letzten 12 Monate. Wenn Ihr Code in Team Foundation Server gespeichert ist, können Sie diesen Wert ändern, indem Sie den [TFSConfig-Befehl](https://msdn.microsoft.com/94424190-3b6b-4f33-a6b6-5807f4225b62) mit dem [CodeIndex-Befehl](../ide/codeindex-command.md) und dem **/indexHistoryPeriod** -Flag ausführen.

 Zum Anzeigen eines ausführlichen Verlaufs aller Änderungen, einschließlich der von vor mehr als einem Jahr, wählen Sie **Alle Dateiänderungen anzeigen**.

 ![Alle Codeänderungen anzeigen](../ide/media/codelensshowsallchanges.png "Codelta-showsallchanges")

 Daraufhin wird das Verlaufsfenster für die Changesets geöffnet.

 ![Fenster "Versionsgeschichte" für alle Codeänderungen](../ide/media/codelenscodechangeshistory.png "Codelta-codechangeshistory")

 Wenn sich Ihre Dateien in einem Git-Repository befinden und Sie den Änderungsindikator für die Code-Elementebene auswählen, wird dies angezeigt.

 ![Codelta ens: Ändern des Änderungs Verlaufs für Ihren Code in git](../ide/media/codelenscodechangesgit.png "Codelta-codechangesgit")

 Suchen Sie in den Indikatoren auf Dateiebene am unteren Rand des Fensters nach Änderungen für eine gesamte Datei (mit Ausnahme von C#- und Visual Basic-Dateien).

 ![Codelta ens: Code Dateidetails erhalten](../ide/media/codelensfilelevel.png "Codelta-FileLevel")

 Um weitere Details zu einer Änderung zu erhalten, klicken Sie mit der rechten Maustaste auf dieses Element. Abhängig davon, ob Sie TFVC oder Git verwenden, stehen Ihnen zahlreiche Optionen zum Vergleichen der Dateiversionen, zum Anzeigen detaillierter Informationen und Nachverfolgen von Änderungen, zum Abrufen der ausgewählten Dateiversion und zum Senden einer E-Mail an den Autor zur Verfügung, um ihn über diese Änderung zu informieren. Ein Teil dieser detaillierten Informationen wird in Team Explorer angezeigt.

 Sie können auch sehen, wer den Code in einem bestimmten Zeitraum geändert hat. Dadurch können Sie Muster bei den Änderungen Ihres Teams erkennen und ihre Auswirkung bewerten.

 ![Codelta ens: siehe Verlauf der Codeänderungen als Diagramm](../ide/media/codelens.png "CodeLens")

#### <a name="find-changes-in-your-current-branch"></a>Änderungen in der aktuellen Verzweigung finden
 Angenommen, Ihr Team hat mehrere Verzweigungen – eine Hauptverzweigung und eine untergeordnete Entwicklung –, dann tun Sie Folgendes, um das Risiko von Schäden an stabilem Code zu senken:

 ![Codelta ens: ermitteln, wann Ihr Code verzweigt wurde](../ide/media/codelensfirstbranchconceptual.png "Codelta-firstbranchkonzeptionelle")

 So finden Sie heraus, wie viele Personen Ihren Code geändert haben und wie viele Änderungen in der Hauptverzweigung vorgenommen wurden (**ALT + 6**):

 ![Codelta ens: Ermitteln der Anzahl der Änderungen in Ihrem Branch](../ide/media/codelensbranchchanges.png "Codelta-branchchanges")

#### <a name="find-when-your-code-was-branched"></a>Sehen, wann Ihr Code verzweigt wurde
 Gehen Sie in die untergeordnete Verzweigung des Codes und dort zur Verzweigung Dev. Wählen Sie den Änderungsindikator aus (**Alt + 6**):

 ![Codelta ens: ermitteln, wann Ihr Code verzweigt wurde](../ide/media/codelensfirstbranchscreenshot.png "Codelta-firstbranchscreenshot")

#### <a name="find-incoming-changes-from-other-branches"></a>Eingehende Änderungen aus anderen Verzweigungen sehen
 ![Codelta ens: Codeänderungen in anderen Verzweigungen suchen](../ide/media/codelensbranchchangecheckinconceptual.png "Codelta-branchchangecheckinkonzeptionelle")

 ... wie diese Fehlerbehebung hier in der Verzweigung Dev:

 ![Codelta ens: eingecheckt in eine andere Verzweigung ändern](../ide/media/codelensbranchchangedevscreenshot.png "Codelta-branchchangedev-Bildschirmfoto")

 Sie können die Änderung überprüfen, ohne die aktuelle Verzweigung zu verlassen (Hauptverzweigung):

 ![Codelta ens: eingehende Änderung von einer anderen Verzweigung anzeigen](../ide/media/codelensbranchchangemainscreenshot.png "Codelta-branchchangemainscreenshot")

#### <a name="find-when-changes-got-merged"></a>Herausfinden, wann Änderungen zusammengeführt wurden
 So können Sie sehen, welche Änderungen in Ihrer Verzweigung enthalten sind:

 ![Codelta- &#45; zusammengeführte Änderungen zwischen branches](../ide/media/codelensbranchmergedconceptual.png "Codelta-branchmergedkonzeptionelle")

 Zum Beispiel hat der Code in der Hauptverzweigung jetzt die Fehlerkorrektur der Verzweigung Dev:

 ![Codelta ens &#45; hat Änderungen zwischen branches zusammengeführt.](../ide/media/codelensbranchmergedscreenshot.png "CodeLensBranchMergedScreenshot")

#### <a name="compare-an-incoming-change-with-your-local-version-shift--f10"></a>Vergleichen einer eingehenden Änderung mit der lokalen Version (Umschalt + F10)
 ![Codelta ens: eingehende Änderung mit lokalem Vergleich vergleichen](../ide/media/codelensbranchincomingchangemenu.png "Codelta-branchincomingchangemenu")

 Sie können auch auf das Changeset doppelklicken.

#### <a name="what-do-the-icons-mean"></a>Was bedeuten die Symbole?

|**Symbol**|**Woher stammt die Änderung?**|
|--------------|-----------------------------------------|
|![Codelta ens: Ändern von Current Branch (Symbol)](../ide/media/codelensbranchcurrenticon.png "Codelta-branchhappticon")|Die aktuelle Verzweigung|
|![Symbol "codelta ens &#45; von übergeordnetem Branch ändern"](../ide/media/codelensbranchparenticon.png "Codelta-branchparameenticon")|Die übergeordnete Verzweigung|
|![Codelta ens: vom Symbol für untergeordnete Verzweigung ändern](../ide/media/codelensbranchchildicon.png "Codelta-branchchilatoron")|Eine untergeordnete Verzweigung|
|![Codelta ens &#45; Änderung von peerbranch (Symbol)](../ide/media/codelensbranchpeericon.png "Codelta-branchpeer")|Eine Peerverzweigung|
|![Codelta ens &#45; ändert sich von Verzweigungs Symbol "weiter entfernt"](../ide/media/codelensbranchfurtherawayicon.png "Codelta-branchförderawayicon")|Eine Verzweigung, die sich weiter entfernt befindet als über- oder untergeordnet und Peer|
|![Codelta ens: Zusammenführen von übergeordnetem Symbol](../ide/media/codelensbranchmergefromparenticon.png "Codelta-branchmergefromparamechmergefromparameenticon")|Eine Zusammenführung von der übergeordneten zu einer untergeordneten Verzweigung|
|![Codelta ens: vom Symbol für untergeordnete Verzweigung zusammenführen](../ide/media/codelensbranchmergefromchildicon.png "Codelta-branchmergefromchildidaktion")|Eine Zusammenführung von der untergeordneten zu einer übergeordneten Verzweigung|
|![Codelta ens: vom Symbol für nicht verknüpfte Verzweigung zusammenführen](../ide/media/codelensbranchmergefromunrelatedicon.png "Codelta-branchmergefromunrelatedicon")|Eine Zusammenführung von einer nicht verwandten Verzweigung (Zusammenführung ohne Basis)|

### <a name="find-linked-work-items"></a>Suchen von verknüpften Arbeitselementen
 ![Codelta ens &#45; findet Arbeitsaufgaben für bestimmten Code](../ide/media/codelensworkitems.png "Codelta-Workitems")

### <a name="find-linked-code-reviews"></a>Verknüpfte Codeüberprüfungen suchen
 ![Codelta ens &#45; -Ansicht Code Review Anforderungen](../ide/media/codelenscodereviews.png "Codelta-Codereviews")

### <a name="find-linked-bugs"></a>Verknüpfte Fehler suchen
 ![Codelta ens &#45; finden von Fehlern, die mit Changesets verknüpft sind](../ide/media/codelensbugschangesets.png "Codelta-bugschangesets")

### <a name="contact-the-owner-of-an-item"></a>Den Besitzer eines Elements kontaktieren
 ![Wenden Sie sich an den Besitzer eines Elements.](../ide/media/codelenscontactitemowner.png "Codelta-contactitemuwner")

 Öffnen Sie das Kontextmenü für ein Element, um die Kontaktoptionen anzuzeigen. Wenn Sie Lync oder Skype for Business installiert haben, werden folgende Optionen angezeigt:

 ![Kontaktoptionen für ein Element](../ide/media/codelensitemcontactmenu.png "Codelta ensitemcontactmenu")

## <a name="FindRunUnitTests"></a> Komponententests für Ihren Code suchen
 Weitere Informationen zu Komponententests, die für Ihren Code vorhanden sind, ohne Test-Explorer zu öffnen. Sie benötigen Folgendes:

- Visual Studio Professional und Visual Studio Enterprise

- Visual C# .NET- oder Visual Basic .NET-Code

- Ein [Komponententestprojekt](../test/unit-test-your-code.md) , das über Komponententests für Ihren Anwendungscode verfügt

1. Wechseln Sie zum Anwendungscode, der über Komponententests verfügt.

2. Überprüfen Sie die Tests für diesen Code (**ALT + 3**).

     ![Codelta ens &#45; wählen Sie den Test Status im Code-Editor aus.](../ide/media/codelenschoosetestindicator.png "Codelta-schooctestindicator")

3. Führen Sie die Tests aus, wenn das Warnsymbol ![codelta ens &#45; Unit Tests noch nicht ausgeführt](../ide/media/codelenstestwarningicon.png "Codelta-stestwarningicon")wird angezeigt wird.

     ![Codelta ens &#45; -Ansichts Komponententests werden noch nicht ausgeführt](../ide/media/codelenstestsnotyetrun.png "Codelta-stestsnotyetrun")

4. Zum Überprüfen der Definition eines Tests doppelklicken Sie im CodeLens-Indikatorfenster auf das Testelement, um die Codedatei im Editor zu öffnen.

     ![Codelta ens &#45; gehe zu Komponenten Test Definition](../ide/media/codelensunittestdefinition.png "Codelta-unittestdefinition")

5. Überprüfen Sie die Testergebnisse. Wählen Sie den Test Status Indikator aus (![codelta ens &#45; ](../ide/media/codelenstestfailedicon.png "Codelta-stestfailedidaktion") -Komponenten Test-Fehler Symbol oder ![codelta ens &#45; ](../ide/media/codelenstestpassedicon.png "Codelta-stestpassedikaton")-Komponenten Test-Symbol), oder drücken Sie **alt + 1**.

     ![Codelta ens &#45; siehe Komponenten Testergebnis](../ide/media/codelensunittestresult.png "Codelta-unittestresult")

6. Zum Überprüfen, wie viele Personen diesen Test geändert haben, wer ihn geändert hat oder wie viele Änderungen an diesem Test durchgeführt wurden, [Den Verlauf Ihres Codes und verwandte Themen suchen](#FindCodeHistory).

## <a name="QA"></a> Fragen und Antworten

### <a name="ChangeOrTurnOff"></a> F: Wie kann ich CodeLens aktivieren oder deaktivieren? Oder wie kann ich auswählen, welche Indikatoren angezeigt werden?
 **A:**  Sie können die Indikatoren aktivieren und deaktivieren, mit Ausnahme des Verweisindikators. Gehen Sie zu **Tools**, **Optionen**, **Text-Editor**, **Alle Sprachen**, **CodeLens**.

 Wenn die Indikatoren aktiviert wurden, können Sie die CodeLens-Optionen auch über die Indikatoren öffnen.

 ![Codelta ens &#45; -Indikatoren aktivieren oder deaktivieren](../ide/media/codelensturnoffonindicatorsfromcode.png "Codelumsturnoffonindikatorsfromcode")

 Aktivieren bzw. deaktivieren Sie CodeLens-Indikatoren auf Dateiebene mithilfe der Chevron-Symbole unten im Editor-Fenster.

 ![Aktivieren und&#45;Deaktivieren von dateiebenenindikatoren](../ide/media/codelensfilelevelonandoff.png "Codelta-filelevelonandoff")

### <a name="NoIndicators"></a>F: Wo befindet sich CodeLens?
 **A:** CodeLens wird  in Visual C# .NET- und Visual Basic .NET-Code auf der Methoden-, Klassen-, Indexer- und Eigenschaftsebene angezeigt. CodeLens wird auf Dateiebene für alle anderen Dateitypen angezeigt.

- Stellen Sie sicher, dass CodeLens aktiviert ist. Gehen Sie zu **Tools**, **Optionen**, **Text-Editor**, **Alle Sprachen**, **CodeLens**.

- Wenn Ihr Code in TFS gespeichert ist, stellen Sie sicher, dass die Codeindizierung aktiviert ist. Verwenden Sie hierzu den [CodeIndex-Befehl](../ide/codeindex-command.md) mit dem [TFSConfig-Befehl](https://msdn.microsoft.com/94424190-3b6b-4f33-a6b6-5807f4225b62).

- TFS-bezogene Indikatoren werden nur angezeigt, wenn Arbeitselemente mit dem Code verknüpft sind und wenn Sie über Berechtigungen zum Öffnen verknüpfter Arbeitselemente verfügen. [Überprüfen Sie, ob Sie über Teammitgliedsberechtigungen verfügen.](/azure/devops/organizations/security/view-permissions)

- Komponententestindikatoren werden nicht angezeigt, wenn der Anwendungscode nicht über Komponententests verfügt. Teststatusindikatoren werden automatisch in Testprojekten angezeigt. Wenn Sie, dass der Anwendungscode über Komponententests verfügt, die Testindikatoren jedoch nicht angezeigt werden, versuchen Sie, die Projektmappe (**STRG+UMSCHALT+B**) zu erstellen.

### <a name="q-why-dont-i-see-the-work-item-details-for-a-commit"></a>F: Warum sehe ich keine Arbeitselementdetails für einen Commit?
 **A:** Dies kann passieren, wenn CodeLens die Arbeitselemente in TFS nicht finden kann. Überprüfen Sie, dass Sie mit dem Teamprojekt verbunden sind, das die Arbeitselemente beinhaltet und dass Sie zum Anzeigen dieser Arbeitselemente berechtigt sind. Dies kann auch vorkommen, wenn die Commit-Beschreibung falsche Informationen über die Arbeitselement-IDs in TFS enthält.

### <a name="NoLync"></a> F: Warum sehe ich keine Lync- bzw. Skype-Indikatoren?
 **A:** Wenn Sie nicht bei Lync oder Skype for Business angemeldet sind, es nicht installiert haben oder über keine unterstützte Konfiguration verfügen, werden diese Indikatoren nicht angezeigt. Sie können jedoch weiterhin E-Mails senden:

 ![Codelta ens &#45; kontaktieren Sie den Besitzer des Changesets per e-Mail.](../ide/media/codelenscodesendmailchangesetnolync1.png "CodeLensCodeSendMailChangesetNoLync1")

 **Welche Lync- und Skype-Konfigurationen werden unterstützt?**

- Skype for Business(32-Bit- oder 64-Bit)

- Lync 2010 oder höher allein (32-Bit- oder 64-Bit), aber nicht Lync Basic 2013 mit Windows 8.1

  CodeLens unterstützt nicht die Installation verschiedener Versionen von Lync oder Skype. Sie sind möglicherweise nicht für alle lokalisierten Versionen von Visual Studio lokalisiert.

### <a name="q-how-do-i-change-the-font-and-color-for-codelens"></a>F: Wie ändere ich Schriftart und Farbe für CodeLens?
 **A:** Wechseln zu **Extras**, **Optionen**, **Umgebung**, **Schriftarten und Farben**.

 ![Codelta ens &#45; ändern von Schriftart-und Farbeinstellungen](../ide/media/codelensoptionsfontscolorssettings.png "Codelta-optionsfontscolorssettings")

 So verwenden Sie die Tastatur:

1. Drücken Sie **ALT+T+O** , um das Feld **Optionen** zu öffnen.

2. Drücken Sie die **NACH-OBEN-TASTE** oder die **NACH-UNTEN-TASTE** , um zum Knoten **Umgebung** zu wechseln, und dann die **NACH-LINKS-TASTE** , um den Knoten zu erweitern.

3. Drücken Sie die **NACH-UNTEN-TASTE** , um zu **Schriftarten und Farben**zu wechseln.

4. Drücken Sie die **TAB-TASTE** , um zur Liste **Einstellungen anzeigen für** zu wechseln, und drücken Sie dann die **NACH-UNTEN-TASTE** , um **CodeLens**auszuwählen.

### <a name="q-can-i-move-the-codelens-heads-up-display"></a>F: Kann ich das CodeLens-Heads-up-Display verschieben?
 **A:** Ja, ![codelta ens &#45; als Fenster Andocken](../ide/media/codelensdockwindow.png "Codelta-dockwindow") , um codelta ens als Fenster Andocken zu können.

 ![Andocken des codelta ens-Indikator Fensters](../ide/media/codelensselectdockwindow.png "Codelta ensselectdockwindow")

 ![Das angedockte codelta ens-Referenz Fenster](../ide/media/codelensreferencesdockedwindow.png "Codelta-referencesdockedwindow")

### <a name="q-how-do-i-refresh-the-indicators"></a>F: Wie aktualisiere ich die Indikatoren?
 **A:** Dies hängt vom Indikator ab:

- **Verweise**: Dieser Indikator wird bei einer Änderung des Codes automatisch aktualisiert. Wenn Sie den Indikator als separates Fenster verankert haben, aktualisieren Sie den Indikator hier manuell:

     ![Codelta ens &#45; als Fenster Andocken](../ide/media/codelensviewreferencesdocked.png "Codelta-viewreferencesangedockt")

- **Team**: Aktualisieren Sie diese Indikatoren hier manuell:

     ![Codelta ens &#45; -Aktualisierungs Indikatoren](../ide/media/codelensrefreshindicatorsfromcode.png "Codelta-Aktualisierungsverzeichnis")

- **Test**: [Komponententests für Ihren Code zu suchen](#FindRunUnitTests) zum Aktualisieren dieses Indikators.

### <a name="LocalVersion"></a> F: Was bedeutet „Lokale Version“?
 **A:** Der Pfeil **Lokale Version** zeigt auf das neueste Changeset in der lokalen Version dieser Datei. Wenn der Server über neuere Changesets verfügt, werden sie je nach Reihenfolge, in der sie sortiert sind, über oder unter dem Pfeil **Lokale Version** angezeigt.

### <a name="q-can-i-manage-how-codelens-processes-code-to-show-history-and-linked-items"></a>F: Kann ich verwalten, wie CodeLens den Code verarbeitet, um den Verlauf und verknüpfte Elemente anzuzeigen?
 **A:** Ja, wenn sich der Code in TFS befindet, können Sie hierzu den [CodeIndex-Befehl](../ide/codeindex-command.md) mit dem [TFSConfig-Befehl](https://msdn.microsoft.com/94424190-3b6b-4f33-a6b6-5807f4225b62)verwenden.

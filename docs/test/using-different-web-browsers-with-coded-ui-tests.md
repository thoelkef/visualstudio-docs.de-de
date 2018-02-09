---
title: Verwenden verschiedener Webbrowser mit Tests der programmierten UI | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 4573d87bbb7d5f447bf6d2038cec310132a0c9f7
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2018
---
# <a name="using-different-web-browsers-with-coded-ui-tests"></a>Verwenden verschiedener Webbrowser mit Tests der programmierten UI
Tests der programmierten UI können Tests für Webanwendungen durch Aufzeichnen Ihrer Tests mit Internet Explorer automatisieren. Sie können den Test anschließend anpassen und diesen entweder mit Internet Explorer oder anderen Browsertypen für diese Webanwendungen wiedergeben.  
  
 **Anforderungen**  
  
-   Visual Studio Enterprise  
  
-   Betriebssysteme:  
  
    -   Microsoft Windows 7  
  
    -   Microsoft Windows 8  
  
    -   Microsoft Windows Server 2008 R2 SP1  
  
-   Webbrowserversionen:  
  
    -   Windows Internet Explorer 9  
  
    -   Windows Internet Explorer 10  
  
    -   Unterstützte Versionen von Mozilla Firefox und Google Chrome finden Sie [hier](http://visualstudiogallery.msdn.microsoft.com/11cfc881-f8c9-4f96-b303-a2780156628d/).  
  
-   Installieren Sie die [Selenium-Komponenten für browserübergreifende Coded UI-Tests](http://visualstudiogallery.msdn.microsoft.com/11cfc881-f8c9-4f96-b303-a2780156628d/).  
  
 **Was wird von allen Webbrowsern unterstützt?**  
  
-   [Hinzufügen von benutzerdefiniertem Code für Steuerfunktionen](http://blogs.msdn.com/b/visualstudioalm/archive/2012/12/10/coded-ui-test-configuring-search-properties-while-recording-on-internet-explorer.aspx) wie Eigenschaften, Suche und Playback-Waiter  
  
-   Popups und Dialogfelder  
  
-   [Ausführen von einfachem JavaScript ohne Rückgabetyp](http://blogs.msdn.com/b/visualstudioalm/archive/2013/01/18/introducing-jscript-execution-on-internetexplorer-and-crossbrowser-in-coded-ui-test.aspx)  
  
-   Flexibilität der Suche (mithilfe der intelligenten Übereinstimmung) und [Leistungsverbesserungen](http://blogs.msdn.com/b/visualstudioalm/archive/2012/02/01/guidelines-on-improving-performance-of-coded-ui-test-playback.aspx)  
  
## <a name="why-should-i-use-coded-ui-tests-across-multiple-web-browser-types"></a>Warum sollte ich Tests der programmierten UI in mehreren Webbrowsertypen durchführen?  
 Durch das Testen der Webanwendung in verschiedenen Webbrowsertypen können Sie die UI-Benutzerfreundlichkeit besser für Benutzer emulieren, die möglicherweise andere Browser verwenden. Zum Beispiel könnte die Anwendung Steuerelemente oder Code in Internet Explorer enthalten, die nicht mit anderen Webbrowsern kompatibel sind. Indem Sie Coded UI-Tests mit anderen Browsern ausführen, können Sie Probleme erkennen und korrigieren, bevor sich diese auf Ihre Kunden auswirken.  
  
## <a name="how-do-i-record-and-play-back-coded-ui-tests-on-web-applications-using-the-supported-web-browsers"></a>Wie kann ich Tests der programmierten UI zu Webanwendungen, in denen die unterstützten Webbrowser verwendet werden, aufzeichnen und wiedergeben?  
 **Aufzeichnung:** Sie müssen den Coded UI-Test-Generator verwenden, um den Webanwendungstest mit Internet Explorer aufzuzeichnen. Optional können Sie den getesteten Steuerelementen Validierungscode und benutzerdefinierten Code mit einem vordefinierten Satz von Eigenschaften hinzufügen, wie Sie dies normalerweise für Tests der programmierten UI tun. Weitere Informationen finden Sie unter [Verwenden von Benutzeroberflächenautomatisierung zum Testen des Codes ](../test/use-ui-automation-to-test-your-code.md).  
  
> [!NOTE]
>  Tests der programmierten UI können nicht mit den Browsern Google Chrome oder Mozilla Firefox aufgezeichnet werden.  
  
 **Wiedergabe mit Internet Explorer:** Wird kein Browser explizit angegeben, werden Tests standardmäßig in Internet Explorer ausgeführt. Sie können den zu verwendenden Browser explizit angeben, indem Sie die **BrowserWindow.CurrentBrowser**-Eigenschaft im Testcode festlegen. Zur Verwendung von Internet Explorer sollte diese Eigenschaft auf **IE** oder **Internet Explorer** festgelegt werden.  
  
 **Wiedergabe mit anderen Webbrowsern als Internet Explorer:** Ändern Sie die Eigenschaft „BrowserWindow.CurrentBrowser“ im Testcode auf **Firefox** oder **Chrome** zur Wiedergabe mit anderen Webbrowsern als Internet Explorer.  
  
 Um Tests auf Nicht-IE-Webbrowser wiederzugeben, müssen Sie die **Selenium-Komponenten für browserübergreifende Coded UI-Tests**.  
  
#### <a name="installing-selenium-components"></a>Installieren von Selenium-Komponenten  
  
1.  Wählen Sie im Menü **Tools** **Erweiterungen und Updates**aus.  
  
2.  Suchen Sie im Dialogfeld „Erweiterungen und Updates“ für `Selenium components for Cross Browser Testing`.  
  
3.  Heben Sie die Erweiterung hervor, und wählen Sie **Herunterladen** aus.  
  
    > [!TIP]
    >  Sie können die Selenium-Komponenten für browserübergreifende Coded UI-Tests [hier](http://visualstudiogallery.msdn.microsoft.com/11cfc881-f8c9-4f96-b303-a2780156628d/) herunterladen.  
  
 Weitere Informationen zum Erstellen und Verwenden von Tests der programmierten UI finden Sie unter [Erstellen von Tests der programmierten UI](../test/use-ui-automation-to-test-your-code.md).  
  
### <a name="enable-debugging"></a>Debuggen aktivieren  
 Um das Debuggen der Webanwendung zu aktivieren, müssen Sie die folgenden Konfigurationsoptionen ausführen:  
  
1.  Nur meinen Code aktivieren:  
  
    1.  Klicken Sie im Menü **Tools** auf **Optionen**, und wählen Sie dann **Debuggen** aus.  
  
    2.  Wählen Sie **Nur meinen Code aktivieren** aus.  
  
2.  Deaktivieren der CLR-Ausnahmen:  
  
    1.  Wählen Sie im Menü **Debuggen** die Option **Ausnahmen** aus.  
  
    2.  Deaktivieren Sie in den **Common Language Runtime-Ausnahmen** die Option **Vom Benutzercode unbehandelt**.  
  
##  <a name="generate"></a> *Die Option zum Ändern von „BrowserWindow.CurrentBrowser“ wird im Test der programmierten UI nicht angezeigt.*  
 Möglicherweise verwenden Sie eine Version von [!INCLUDE[vs2011_first](../test/includes/vs2011_first_md.md)], die Coded UI-Tests mit verschiedenen Webbrowsern nicht unterstützt. Zum Erstellen von Tests der programmierten UI müssen Sie Visual Studio Enterprise verwenden.  
  
 *Was sollte ich noch wissen?*  
 **Notizen**  
  
-   ![Erforderliche Komponente](../test/media/prereq.png "Prereq") Der Webbrowser Apple Safari wird nicht unterstützt.  
  
-   ![Erforderliche Komponente](../test/media/prereq.png "Prereq") Die Aktion zum Starten des Webbrowsers muss Teil des Tests der programmierten UI sein.  
  
     Wenn Sie einen Webbrowser bereits geöffnet haben und Schritte darin ausführen möchten, schlägt die Wiedergabe fehl, sofern Sie nicht Internet Explorer verwenden. Eine bewährte Methode ist daher, den Start des Webbrowsers in die Tests der programmierten UI einzubinden.  
  
-   ![Erforderliche Komponente](../test/media/prereq.png "Prereq") Das Automatisieren von browserspezifischen UI-Aktionen, wie Maximieren, Minimieren und Wiederherstellen wird nicht unterstützt.  
  
 **Tipps**  
  
-   ![Tipp](../test/media/tip.png "Tip") Sie können die Ausgabe so konfigurieren, dass Screenshots in den Coded UI-Protokollen enthalten sind. Hierzu müssen einige Konfigurationseinstellungen in der Datei "QTAgent32.exe.config" festgelegt werden. Standardmäßig wird diese Datei an folgendem Speicherort installiert:  
  
     **C:\Programme (x86)\Microsoft Visual Studio 11.0\Common7\IDE“**  
  
     Geben Sie die folgenden Werte an:  
  
    -   `EqtTraceLevel` im Abschnitt `system.diagnostics`.  
  
    -   `<add name="EqtTraceLevel" value="4" />`  
  
         Durch Festlegen des Werts auf 3 oder höher werden für jede Aktion Screenshots aufgezeichnet. Wenn der Wert auf 1 oder 2 festgelegt ist, werden Screenshots nur für Fehleraktionen aufgezeichnet.  
  
     Weitere Informationen finden Sie unter [Analyzing Coded UI Tests Using Coded UI Test Logs (Analysieren von Tests der programmierten UI mithilfe der Testprotokolle der programmierten UI)](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md).  
  
## <a name="external-resources"></a>Externe Ressourcen  
  
### <a name="videos"></a>Videos  
 [Aufzeichnen mit IE und unabhängige Wiedergabe](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!183&authkey=!ANqaLtCZbtJrImU)  
  
 [Erstellen von browserübergreifenden Tests mit dem Coded UI-Test-Generator](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!184&authkey=!AKG8CSow_qmeTq8)  
  
 [Erstellen von browserübergreifenden Tests mit einfacher Handcodierung ohne UI-Zuordnung](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!186&authkey=!AJaEvxJnsefyAT4)  
  
 [Sequenzielles Ausführen von browserübergreifenden Tests auf mehreren Browsern](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!187&authkey=!ADI8eCQkxHnpOR8)  
  
 [Beheben von Fehlern in browserübergreifenden Tests](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!182&authkey=!AEpS48i295B49FI)  
  
### <a name="guidance"></a>Empfehlungen  
 [Testing for Continuous Delivery with Visual Studio 2012 - Chapter 2: Unit Testing: Testing the Inside (Tests für fortlaufende Übermittlung mit Visual Studio 2012 – Kapitel 2: Komponententests – Interne Tests)](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
 [Testing for Continuous Delivery with Visual Studio 2012 - Chapter 5: Automating System Tests (Tests für fortlaufende Übermittlung mit Visual Studio 2012 – Kapitel 5 Automatisieren von Systemtests)](http://go.microsoft.com/fwlink/?LinkID=255196)  
  
### <a name="faq"></a>FAQ  
 [Tests der codierten UI – FAQ 1](http://go.microsoft.com/fwlink/?LinkID=230576)  
  
 [Tests der codierten UI – FAQ 2](http://go.microsoft.com/fwlink/?LinkID=230578)  
  
### <a name="forum"></a>Forum  
 [Visual Studio UI Automation Testing (includes CodedUI) (Tests der Benutzeroberflächenautomatisierung (einschließlich programmierte UI) in Visual Studio)](http://go.microsoft.com/fwlink/?LinkID=224497)  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von Benutzeroberflächenautomatisierung zum Testen des Codes](../test/use-ui-automation-to-test-your-code.md)   
 [Unterstützte Konfigurationen und Plattformen für Tests der programmierten UI und Aktionsaufzeichnungen](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)   
 [Analysieren von Tests der programmierten UI mithilfe der Testprotokolle der programmierten UI](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md)

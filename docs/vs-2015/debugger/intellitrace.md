---
title: IntelliTrace | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.historicaldebug.overview
helpviewer_keywords:
- debugger, recording execution history
- debugging, recording execution history
- IntelliTrace [Visual Studio ALM]
- IntelliTrace, debugging applications
- debugger, (See also IntelliTrace [Visual Studio ALM])
- debugging, (See also IntelliTrace [Visual Studio ALM])
- IntelliTrace, collecting data from Test Manager
- IntelliTrace
- Test Manager, debugging with IntelliTrace
- IntelliTrace, debugging after a crash
ms.assetid: 486bfec2-39bd-4d78-892a-42352128ee52
caps.latest.revision: 142
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: db7430d03bbce065b75e890736253c6ba05752d0
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298920"
---
# <a name="intellitrace"></a>IntelliTrace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IntelliTrace](https://docs.microsoft.com/visualstudio/debugger/intellitrace) .  
  
Durch die Verwendung von IntelliTrace zum Erfassen und Nachverfolgen Ihres Codeausführungsverlaufs können Sie beim Debuggen Ihrer Anwendung Zeit sparen. Sie können leicht Fehler finden, da mit IntelliTrace Folgendes möglich ist:  
  
- Aufzeichnen bestimmter Ereignisse  
  
   Sie können ähnlichen Code sowie im Fenster **Lokal** während der Debugger-Ereignisse angezeigte Daten, und Funktionsaufrufinformationen überprüfen.  
  
- Schwer nachstellbare oder während der Bereitstellung auftretende Fehler beim Debuggen  
  
  Sie können IntelliTrace in der Visual Studio Enterprise Edition verwenden(jedoch nicht in der Professional oder Community Edition).  
  
## <a name="what-do-you-want-to-do"></a>Was möchten Sie tun?  
  
|||  
|-|-|  
|**Meine Anwendung mit IntelliTrace debuggen:**<br /><br /> -Ich habe vergangene Ereignisse angezeigt.<br />-Hiermit werden Informationen zum Anruf in früheren Ereignissen angezeigt.<br />-IntelliTrace-Sitzung speichern.<br />-Steuern der Daten, die IntelliTrace sammelt.|-   [Exemplarische Vorgehensweise: Verwenden von IntelliTrace](../debugger/walkthrough-using-intellitrace.md)<br />     [IntelliTrace-Funktionen](../debugger/intellitrace-features.md)<br />[IntelliTrace -   konfigurieren](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e)<br />-   [Verlaufsbezogenes Debuggen](../debugger/historical-debugging.md)|  
|**Sammeln von IntelliTrace-Daten während einer Testsitzung im Test Manager**|-   [Sammeln weiterer Diagnosedaten in manuellen Tests](https://msdn.microsoft.com/library/bb5a2cc0-84f5-4dfe-9560-ca3d313aefd2)|  
|**Erfassen IntelliTrace-Daten aus bereitgestellten Anwendungen**|-   [Verwenden des eigenständigen IntelliTrace-Collectors](../debugger/using-the-intellitrace-stand-alone-collector.md)|  
|**Starten Sie das Debuggen von einer IntelliTrace-Protokolldatei (ITRACE-Datei).**|-   [Verwenden gespeicherter IntelliTrace-Daten](../debugger/using-saved-intellitrace-data.md)|  
  
## <a name="IntelliTraceSupport"></a>Welche Anwendungen kann ich mit IntelliTrace debuggen?  
  
|||  
|-|-|  
|**Unterstützt**|-Visual Basic und visuelle C# Anwendungen, die .NET Framework 2,0 oder höhere Versionen verwenden.<br />     Sie können die meisten Anwendungen debuggen, einschließlich ASP.NET, Microsoft Azure, Windows Forms, WCF, WPF, Windows Workflow, SharePoint 2010, SharePoint 2013 und 64-Bit-Anwendungen.<br />     Informationen zum Debuggen von SharePoint-Anwendungen mit IntelliTrace finden Sie unter Exemplarische Vorgehensweise [: Debuggen einer SharePoint-Anwendung mit IntelliTrace](https://msdn.microsoft.com/library/4bd80d2f-f680-4bf4-81c3-f14e8185f6a4)<br />     Informationen zum Debuggen Microsoft Azure-apps mit IntelliTrace finden Sie unter [Debuggen eines veröffentlichten clouddiensts mit IntelliTrace und Visual Studio](../azure/vs-azure-tools-intellitrace-debug-published-cloud-services.md).|  
|**Eingeschränkte Unterstützung**|- F# apps auf experimentelle Basis<br />-Windows Store-Apps werden nur für Ereignisse unterstützt|  
|**Nicht unterstützt**|- C++, andere Sprachen und Skripts<br />-Windows-Dienste, Silverlight, Xbox oder [!INCLUDE[winmobile](../includes/winmobile-md.md)]-apps|  
  
> [!NOTE]
> IntelliTrace kann nicht verwendet werden, um einen Prozess zu debuggen, der bereits ausgeführt wird. Sie müssen IntelliTrace zu Beginn des Prozesses starten.  
  
## <a name="IntelliTraceVSTraditional"></a> Warum sollte ich mit IntelliTrace debuggen?  
 Herkömmliche oder *Live*-Debugvorgänge zeigen nur den aktuellen Status der Anwendung mit eingeschränkten Informationen zu vergangenen Ereignissen. Sie müssen diese Ereignisse entweder auf Grundlage des aktuellen Anwendungsstatus ableiten, oder Sie müssen diese Ereignisse neu erstellen, indem Sie die Anwendung erneut ausführen.  
  
 IntelliTrace erweitert diese herkömmlichen Debuggenvorgänge, indem bestimmte Ereignisse und Daten an diesen Zeitpunkten erfasst werden. Somit können Sie auch ohne Neustart der Anwendung die Ereignisse verfolgen und finden auch bereits aufgetretene Fehler. IntelliTrace ist standardmäßig während des herkömmlichen Debuggen aktiviert, sodass Daten automatisch und unsichtbar erfasst werden. Sie können also zwischen dem herkömmlichen Debuggen und dem IntelliTrace-Debuggen problemlos wechseln, um die aufgezeichneten Informationen abzurufen. Weitere Informationen finden Sie unter [IntelliTrace-Features](../debugger/intellitrace-features.md) und [welche Daten werden von IntelliTrace erfasst?](#WhatData)  
  
 IntelliTrace hilft Ihnen außerdem beim Debuggen von Fehlern, die schwer reproduzierbar sind oder die bei der Bereitstellung auftreten. Sie können IntelliTrace-Daten sammeln und in einer IntelliTrace-Protokolldatei (ITRACE-Datei) speichern. Eine ITRACE-Datei enthält Details über Ausnahmen, Leistungsereignisse, Webanforderungen, Testdaten, Threads, Module und andere Systeminformationen. Sie können diese Datei in Visual Studio Enterprise öffnen, ein Element auswählen und das Debuggen mit IntelliTrace starten. Sie können also zu jedem beliebigen Ereignis in der Datei gehen und bestimmte Einzelheiten über die Anwendung an diesem Punkt anzeigen lassen.  
  
 IntelliTrace-Daten können aus den folgenden Quellen gespeichert werden:  
  
- Eine IntelliTrace-Sitzung in Visual Studio 2015 Enterprise oder früheren Versionen von Visual Studio Ultimate.  
  
- Eine Testsitzung in Microsoft Test Manager  
  
- Auf IIS gehostete ASP.NET-Anwendungen oder SharePoint 2010- und SharePoint 2013-Anwendungen, die bei der Bereitstellung ausgeführt werden, wenn Sie Microsoft Monitoring Agent verwenden, entweder allein oder mit System Center 2012. Weitere Informationen finden [Sie unter Verwenden des eigenständigen IntelliTrace Collector und der](../debugger/using-the-intellitrace-stand-alone-collector.md) [Überwachung mit Microsoft Monitoring Agent](https://technet.microsoft.com/library/dn465153.aspx).  
  
  Im Folgenden werden einige Beispiele aufgeführt, die den Nutzen von IntelliTrace beim Debuggen veranschaulichen:  
  
- Ihre Anwendung hat eine Datendatei beschädigt, doch Sie wissen nicht, wann das passiert ist.  
  
   Ohne IntelliTrace müssten Sie den Code auf alle möglichen Dateizugriffe durchsuchen, Haltepunkte für diese Zugriffe festlegen und die Anwendung dann erneut ausführen, um die Stelle ausfindig zu machen, an der das Problem aufgetreten ist. Mit IntelliTrace können Sie alle erfassten Dateizugriffsereignisse und bestimmte Details über die Anwendung finden, wenn Ereignisse auftreten.  
  
- Eine Ausnahme tritt auf.  
  
   Ohne IntelliTrace erhalten Sie zwar eine Meldung über eine Ausnahme, aber Sie bekommen kaum Informationen über die Ereignisse, die zu der Ausnahme geführt haben. Sie können in der Aufrufliste die Kette der Aufrufe untersuchen, die zur Ausnahme geführt haben, aber Sie können nicht die Ereignisabfolge während dieser Aufrufe einsehen. Mit IntelliTrace können Sie die Ereignisse untersuchen, die vor der Ausnahme auftraten.  
  
- Die Anwendung stürzt auf einem Testcomputer ab, wird jedoch auf einem Entwicklungscomputer erfolgreich ausgeführt.  
  
   Sie können IntelliTrace-Daten vom Microsoft Test Manager sammeln, die Daten in einer ITRACE-Datei speichern und diese Datei später einem Team Foundation Server-Arbeitselement für die Untersuchung hinzufügen. [Weitere Informationen finden Sie unter Sammeln von weiteren Diagnosedaten in manuellen Tests](https://msdn.microsoft.com/library/bb5a2cc0-84f5-4dfe-9560-ca3d313aefd2) und [Verwenden gespeicherter IntelliTrace-Daten](../debugger/using-saved-intellitrace-data.md).  
  
- Ein Fehler oder ein Absturz geschieht in einer bereitgestellten Anwendung.  
  
   Für Microsoft Azure-basierte Apps können Sie die IntelliTrace-Datenerfassung vor der Veröffentlichung Ihrer App konfigurieren. Während die App ausgeführt wird, werden von IntelliTrace Daten in einer iTrace-Datei gespeichert. Weitere Informationen finden Sie unter [Debuggen eines veröffentlichten Clouddiensts mit IntelliTrace und Visual Studio](../azure/vs-azure-tools-intellitrace-debug-published-cloud-services.md).  
  
   Für ASP.NET-Webanwendungen, die auf IIS 7.0, 7,5 und 8,0 gehostet werden, sowie für SharePoint 2010- oder SharePoint 2013-Anwendungen verwenden Sie Microsoft Monitoring Agent, entweder alleine oder mit System Center 2012, um IntelliTrace-Daten in einer ITRACE-Datei zu speichern.  
  
   Dies ist hilfreich, wenn Sie Probleme mit Apps in der Bereitstellung diagnostizieren möchten. Weitere Informationen finden [Sie unter Verwenden des eigenständigen IntelliTrace-Sammlers](../debugger/using-the-intellitrace-stand-alone-collector.md).  
  
## <a name="WhatData"></a> Welche Daten erfasst IntelliTrace?  
 **Sammeln von Ereignis Informationen**  
  
 Standardmäßig erfasst IntelliTrace nur IntelliTrace-Ereignisse: Debuggerereignisse, Ausnahmen, .NET Framework-Ereignisse und andere Systemereignisse, die beim Debuggen hilfreich sein können. Sie können die IntelliTrace-Ereignisse auswählen, die Sie sammeln möchten. Debuggerereignisse und -ausnahmen werden allerdings immer gesammelt. Siehe [Konfigurieren von IntelliTrace](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
- **Debuggerereignisse**  
  
   IntelliTrace zeichnet alle Ereignisse auf, die im Visual Studio-Debugger stattfinden. Der Anwendungsstart ist beispielsweise ein Debuggerereignis. Weitere Debuggerereignisse sind Beenden-Ereignissen, die zur Unterbrechung der Anwendungsausführung führen. Zum Beispiel wenn das Programm einen Haltepunkt oder einen Ablaufverfolgungspunkt erreicht oder einen **Schritt**befehl ausführt.  
  
   Für optimale Leistung werden nicht alle möglichen Werte für ein Debuggerereignis von IntelliTrace aufgezeichnet. Stattdessen werden folgende Werte aufgezeichnet:  
  
  - Werte im Fenster **Lokal**. Lassen Sie das Fenster **Lokal** geöffnet, um diese Werte anzuzeigen.  
  
  - Werte im Fenster **Auto**, wenn das Fenster **Auto** geöffnet ist  
  
  - Werte in DataTips, die angezeigt werden, wenn Sie den Mauszeiger über eine Variable im Quellcodefenster bewegen, um den Wert anzuzeigen. IntelliTrace erfasst keine Werte in angehefteten DataTips.  
  
- **Ausnahmen**  
  
   IntelliTrace zeichnet den Ausnahmetyp und die Meldung für diese Ausnahmen auf:  
  
  - Bearbeitete Ausnahmen, in denen die Ausnahme ausgelöst und abgefangen wird  
  
  - Ausnahmefehler  
  
- **.NET Framework-Ereignisse**  
  
   IntelliTrace zeichnet standardmäßig die häufigsten .NET Framework-Ereignisse auf. Beispiel:  
  
  - Für ein Dateizugriffsereignis erfasst IntelliTrace den Dateinamen.  
  
  - Für ein Checkbox-Aktivierungsereignis erfasst IntelliTrace den Kontrollkästchenzustand und den Text.  
  
- **SharePoint 2010- und SharePoint 2013-Anwendungsereignisse**  
  
   Sie können Benutzerprofilereignisse und eine Teilmenge von einheitlichen Ereignissen des Protokollierungs-Systems (ULS) für SharePoint 2010- und 2013-Anwendungen erfassen, die außerhalb von Visual Studio ausgeführt werden. Sie können diese Ereignisse in einer ITRACE-Datei speichern. Erfordert Visual Studio Enterprise 2015, eine frühere Version von Visual Studio Ultimate oder [Microsoft Monitoring Agent](https://go.microsoft.com/fwlink/?LinkId=320384) , die im Ablauf **Verfolgungs** Modus ausgeführt wird.  
  
   Wenn Sie die ITRACE-Datei öffnen, geben Sie eine SharePoint-Korrelations-ID ein, um die entsprechenden Webanforderung zu suchen, die aufgezeichneten Ereignisse anzuzeigen und das Debuggen von einem bestimmten Ereignis aus zu starten. Wenn die Datei Ausnahmefehler enthält, können Sie eine Korrelations-ID auswählen, um das Debuggen einer Ausnahme zu starten.  
  
   Thema  
  
  - [Verwenden des eigenständigen IntelliTrace-Collectors](../debugger/using-the-intellitrace-stand-alone-collector.md)  
  
  - [Verwenden gespeicherter IntelliTrace-Daten](../debugger/using-saved-intellitrace-data.md)  
  
  - [Exemplarische Vorgehensweise: Debuggen einer SharePoint-Anwendung mithilfe von IntelliTrace](https://msdn.microsoft.com/library/4bd80d2f-f680-4bf4-81c3-f14e8185f6a4)  
  
  **Sammeln von Funktions aufrufsinformationen**  
  
  Sie können IntelliTrace so konfigurieren, dass Aufrufinformationen für Funktionen gesammelt werden. Anhand dieser Informationen können Sie den Aufruflistenverlauf anzeigen und die Aufrufe im Code vorwärts und rückwärts durchlaufen. Für jeden Funktionsaufruf werden die folgenden Daten von IntelliTrace aufgezeichnet:  
  
- Funktionsname  
  
- Werte primitiver Datentypen, die als Parameter an Funktionseinstiegspunkten übergeben und an Funktionsendpunkten zurückgegeben werden  
  
- Werte von automatischen Eigenschaften, wenn sie gelesen oder geändert werden  
  
- Zeiger auf untergeordnete Objekte auf der obersten Ebene ohne Werte (außer NULL oder keine)  
  
> [!NOTE]
> IntelliTrace erfasst nur die ersten 256 Objekte in Arrays und die ersten 256 Zeichen von Zeichenfolgen.  
  
 Siehe [Konfigurieren von IntelliTrace](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
 **Sammeln von Modul Informationen**  
  
 Um zu steuern, wie viel Aufrufsinformationen IntelliTrace erfasst, legen Sie nur die Module fest, die für Sie von Bedeutung sind. Das kann dabei helfen, die Anwendungsleistung während der Erfassung zu verbessern. Siehe [Konfigurieren von IntelliTrace](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
## <a name="AffectPerformance"></a> Verlangsamt IntelliTrace meine Anwendung?  
 Standardmäßig werden von IntelliTrace nur Daten für ausgewählte IntelliTrace-Ereignisse gesammelt. Das kann, abhängig von der Struktur und der Organisation Ihres Codes, eventuell die Anwendung verlangsamen. Wenn IntelliTrace beispielsweise oft ein Ereignis protokolliert, kann dies die Anwendung verlangsamen. Erwägen Sie, eine Umgestaltung Ihrer Anwendung vorzunehmen.  
  
 Das Sammeln der Aufrufsinformationen verlangsamt die App möglicherweise erheblich. Außerdem erhöht sich dadurch möglicherweise die Größe aller auf dem Datenträger gespeicherter IntelliTrace-Protokolldateien (ITRACE-Dateien). Um diese Auswirkungen zu minimieren, sammeln Sie Aufrufinformationen nur für die Module, die Sie interessieren.  Um die maximale Größe der ITRACE-Dateien zu ändern, wechseln Sie zu **Tools**, **Optionen**, **IntelliTrace**, **Erweitert**. Siehe [Konfigurieren von IntelliTrace](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [IntelliTrace-Funktionen](../debugger/intellitrace-features.md)  
  
 [Konfigurieren von IntelliTrace](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e)  
  
 [Einschließen von Diagnose Ablauf Verfolgungs Daten mit Fehlern, die schwer zu reproduzieren sind](https://msdn.microsoft.com/library/944ae9af-5a55-4c58-b520-0108c03b3564)  
  
 [Diagnostizieren von Problemen nach der Bereitstellung](../debugger/diagnose-problems-after-deployment.md)  
  
 [Verwenden gespeicherter IntelliTrace-Daten](../debugger/using-saved-intellitrace-data.md)  
  
### <a name="blogs"></a>Blogs  
 [Visual Studio Alm + Team Foundation Server](https://go.microsoft.com/fwlink/?LinkID=201340)  
  
### <a name="forums"></a>Foren  
 [Visual Studio-Diagnose](https://go.microsoft.com/fwlink/?LinkId=262263)

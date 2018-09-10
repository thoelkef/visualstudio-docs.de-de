---
title: IntelliTrace | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/18/2017
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 972338fa4b52a61024cabd098c29cd0f5d9c8a4f
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2018
ms.locfileid: "44280778"
---
# <a name="intellitrace"></a>IntelliTrace

Durch die Verwendung von IntelliTrace zum Erfassen und Nachverfolgen Ihres Codeausführungsverlaufs können Sie beim Debuggen Ihrer Anwendung Zeit sparen. Sie können leicht Fehler finden, da mit IntelliTrace Folgendes möglich ist:

- Aufzeichnen bestimmter Ereignisse

     Überprüfen von verknüpftem Code, die in angezeigten Daten den **"lokal"** Fenster während der Debugger-Ereignisse und Informationen zu Funktionsaufrufen

- Schwer nachstellbare oder während der Bereitstellung auftretende Fehler beim Debuggen

Sie können IntelliTrace in der Visual Studio Enterprise Edition verwenden(jedoch nicht in der Professional oder Community Edition).

## <a name="what-do-you-want-to-do"></a>Wie möchten Sie vorgehen?

|||
|-|-|
|**Meine Anwendung mit IntelliTrace zu debuggen:**<br /><br /> – Vergangene Ereignisse.<br />-Anzeigen Aufrufinformationen mit vergangenen Ereignissen.<br />-Speichern Sie IntelliTrace-Sitzung.<br />-Steuerelement, die von IntelliTrace gesammelten Daten.|- [Exemplarische Vorgehensweise: Verwenden von IntelliTrace](../debugger/walkthrough-using-intellitrace.md)<br />- [IntelliTrace-Funktionen](../debugger/intellitrace-features.md)<br />- [Verlaufsbezogenes Debugging](../debugger/historical-debugging.md)<br />- [Anzeigen von Momentaufnahmen mithilfe von IntelliTrace ein Schritt zurück](../debugger/how-to-use-intellitrace-step-back.md)|
|**Sammeln von IntelliTrace-Daten in einer testsitzung im Test-Manager**|- [Sammeln Sie weiterer Diagnosedaten in manuellen tests](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests)|
|**Sammeln von IntelliTrace-Daten bereitgestellter Anwendungen**|- [Verwenden den eigenständigen IntelliTrace collector](../debugger/using-the-intellitrace-stand-alone-collector.md)|
|**Debuggen von einer IntelliTrace-Protokolldatei (ITRACE-Datei) aus.**|- [Verwenden gespeicherter IntelliTrace-Daten](../debugger/using-saved-intellitrace-data.md)|

## <a name="IntelliTraceSupport"></a> Welche apps kann ich mit IntelliTrace Debuggen?

|||
|-|-|
|**Unterstützt**|– Visual Basic und Visual C#-Anwendungen, die .NET Framework 2.0 oder höher verwenden.<br/>Sie können die meisten Anwendungen debuggen, einschließlich ASP.NET, Microsoft Azure, Windows Forms, WCF, WPF, Windows Workflow, SharePoint 2010, SharePoint 2013 und 64-Bit-Anwendungen.<br/>Zum Debuggen von SharePoint-Anwendungen mit IntelliTrace finden Sie unter [Exemplarische Vorgehensweise: Debuggen einer SharePoint-Anwendung durch Verwenden von IntelliTrace](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md).<br/> Um Microsoft Azure-apps mit IntelliTrace zu debuggen, finden Sie unter [Debuggen eines veröffentlichten Clouddiensts mit IntelliTrace und Visual Studio](/azure/vs-azure-tools-intellitrace-debug-published-cloud-services).|
|**Eingeschränkte Unterstützung**|– .NET Core und ASP.NET Core-apps unterstützt für bestimmte Ereignisse nur (MVC-Controller, ADO.NET und HTTPClicent) beim lokalen Debuggen. Der eigenständige Collector wird für .NET Core- oder ASP.NET Core-apps nicht unterstützt.<br />– F#-apps versuchsweise<br />-UWP apps, die nur für Ereignisse unterstützt|
|**Nicht unterstützt**|-C++, andere Sprachen und Skript<br />-Windows Dienste, Silverlight, Xbox oder [!INCLUDE[winmobile](../debugger/includes/winmobile_md.md)] apps|

> [!NOTE]
> Wenn Sie möchten einen Prozess zu debuggen, der bereits ausgeführt wird, können Sie nur IntelliTrace-Ereignisse (keine Aufrufinformationen) erfassen. Sie können zu einem 32-Bit oder 64-Bit-Prozess nur auf dem lokalen Computer anfügen. Ereignisse, die auftreten, bevor Sie sich an den Prozess anfügen, werden nicht gesammelt.

##  <a name="IntelliTraceVSTraditional"></a> Warum mit IntelliTrace Debuggen?

Herkömmliche oder *live* debuggenvorgänge zeigen nur Ihre Anwendung den aktuellen Zustand, mit eingeschränkten Informationen zu vergangenen Ereignissen. Sie müssen diese Ereignisse entweder auf Grundlage des aktuellen Anwendungsstatus ableiten, oder Sie müssen diese Ereignisse neu erstellen, indem Sie die Anwendung erneut ausführen.

IntelliTrace erweitert diese herkömmlichen Debuggenvorgänge, indem bestimmte Ereignisse und Daten an diesen Zeitpunkten erfasst werden. Somit können Sie auch ohne Neustart der Anwendung die Ereignisse verfolgen und finden auch bereits aufgetretene Fehler. IntelliTrace ist standardmäßig während des herkömmlichen Debuggen aktiviert, sodass Daten automatisch und unsichtbar erfasst werden. Sie können also zwischen dem herkömmlichen Debuggen und dem IntelliTrace-Debuggen problemlos wechseln, um die aufgezeichneten Informationen abzurufen. Finden Sie unter [IntelliTrace-Funktionen](../debugger/intellitrace-features.md) und [welche Daten erfasst IntelliTrace?](#WhatData)

IntelliTrace hilft Ihnen außerdem beim Debuggen von Fehlern, die schwer reproduzierbar sind oder die bei der Bereitstellung auftreten. Sie können IntelliTrace-Daten sammeln und in einer IntelliTrace-Protokolldatei (ITRACE-Datei) speichern. Eine ITRACE-Datei enthält Details über Ausnahmen, Leistungsereignisse, Webanforderungen, Testdaten, Threads, Module und andere Systeminformationen. Sie können diese Datei in Visual Studio Enterprise öffnen, ein Element auswählen und das Debuggen mit IntelliTrace starten. Sie können also zu jedem beliebigen Ereignis in der Datei gehen und bestimmte Einzelheiten über die Anwendung an diesem Punkt anzeigen lassen.

IntelliTrace-Daten können aus den folgenden Quellen gespeichert werden:

- Eine IntelliTrace-Sitzung in Visual Studio 2017 Enterprise, Visual Studio 2015 Enterprise oder früheren Versionen von Visual Studio Ultimate.

- Eine Testsitzung in Microsoft Test Manager

- Auf IIS gehostete ASP.NET-Anwendungen oder SharePoint 2010- und SharePoint 2013-Anwendungen, die bei der Bereitstellung ausgeführt werden, wenn Sie Microsoft Monitoring Agent verwenden, entweder allein oder mit System Center 2012. Finden Sie unter [verwenden Sie den eigenständigen IntelliTrace Collector](../debugger/using-the-intellitrace-stand-alone-collector.md) und [Überwachen mit Microsoft Monitoring Agent](http://technet.microsoft.com/library/dn465153.aspx).

 Im Folgenden werden einige Beispiele aufgeführt, die den Nutzen von IntelliTrace beim Debuggen veranschaulichen:

- Ihre Anwendung hat eine Datendatei beschädigt, doch Sie wissen nicht, wann das passiert ist.

     Ohne IntelliTrace müssten Sie den Code auf alle möglichen Dateizugriffe durchsuchen, Haltepunkte für diese Zugriffe festlegen und die Anwendung dann erneut ausführen, um die Stelle ausfindig zu machen, an der das Problem aufgetreten ist. Mit IntelliTrace können Sie alle erfassten Dateizugriffsereignisse und bestimmte Details über die Anwendung finden, wenn Ereignisse auftreten.

- Eine Ausnahme tritt auf.

     Ohne IntelliTrace Sie erhalten eine Meldung zu einer Ausnahme, aber Sie müssen nicht viele Informationen zu den Ereignissen, die auf die Ausnahme geführt hat. Sehen Sie die Aufrufliste die Kette der Aufrufe angezeigt, die auf die Ausnahme geführt hat, aber die Abfolge der Ereignisse, die Ereignisabfolge während dieser Aufrufe nicht angezeigt. Mit IntelliTrace können Sie die Ereignisse untersuchen, die vor der Ausnahme auftraten.

- Die Anwendung stürzt auf einem Testcomputer ab, wird jedoch auf einem Entwicklungscomputer erfolgreich ausgeführt.

     Sie können IntelliTrace-Daten vom Microsoft Test Manager sammeln, die Daten in einer ITRACE-Datei speichern und diese Datei später einem Team Foundation Server-Arbeitselement für die Untersuchung hinzufügen. Finden Sie unter [Sammeln weiterer Diagnosedaten in manuellen Tests](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests) und [Verwenden gespeicherter IntelliTrace-Daten](../debugger/using-saved-intellitrace-data.md).

- Ein Fehler oder ein Absturz geschieht in einer bereitgestellten Anwendung.

     Für Microsoft Azure-basierte Apps können Sie die IntelliTrace-Datenerfassung vor der Veröffentlichung Ihrer App konfigurieren. Während die App ausgeführt wird, werden von IntelliTrace Daten in einer iTrace-Datei gespeichert. Finden Sie unter [Debuggen ein veröffentlichten Clouddiensts mit IntelliTrace und Visual Studio](http://go.microsoft.com/fwlink/?LinkID=262248).

     Für ASP.NET-Webanwendungen, die auf IIS 7.0, 7,5 und 8,0 gehostet werden, sowie für SharePoint 2010- oder SharePoint 2013-Anwendungen verwenden Sie Microsoft Monitoring Agent, entweder alleine oder mit System Center 2012, um IntelliTrace-Daten in einer ITRACE-Datei zu speichern.

     Dies ist hilfreich, wenn Sie Probleme mit Apps in der Bereitstellung diagnostizieren möchten. Finden Sie unter [verwenden Sie den eigenständigen IntelliTrace Collector](../debugger/using-the-intellitrace-stand-alone-collector.md).

##  <a name="WhatData"></a> Welche Daten erfasst IntelliTrace?

**Sammeln von Ereignisinformationen**

Standardmäßig erfasst IntelliTrace nur IntelliTrace-Ereignisse: Debuggerereignisse, Ausnahmen, .NET Framework-Ereignisse und andere Systemereignisse, die beim Debuggen hilfreich sein können. Sie können die IntelliTrace-Ereignisse auswählen, die Sie sammeln möchten. Debuggerereignisse und -ausnahmen werden allerdings immer gesammelt. Finden Sie unter [IntelliTrace-Funktionen](../debugger/intellitrace-features.md).

- **Debugger-Ereignissen**

     IntelliTrace zeichnet alle Ereignisse auf, die im Visual Studio-Debugger stattfinden. Der Anwendungsstart ist beispielsweise ein Debuggerereignis. Weitere Debuggerereignisse sind Beenden-Ereignissen, die zur Unterbrechung der Anwendungsausführung führen. Beispielsweise das Programm einen Haltepunkt, einen Ablaufverfolgungspunkt erreicht oder führt eine **Schritt** Befehl.

     In der Standardeinstellung keine optimale Leistung, IntelliTrace alle möglichen Werte für ein Debuggerereignis aufgezeichnet. Stattdessen werden folgende Werte aufgezeichnet:

    - Werte in der **"lokal"** Fenster. Behalten Sie die **"lokal"** Fenster geöffnet, um diese Werte anzuzeigen.

    - Werte in der **"Auto"** Fenster, wenn die **"Auto"** Fenster geöffnet ist.

    - Werte in DataTips, die angezeigt werden, wenn Sie den Mauszeiger über eine Variable im Quellcodefenster bewegen, um den Wert anzuzeigen. IntelliTrace erfasst keine Werte in angehefteten DataTips.

    Wenn IntelliTrace-Ereignisse und Momentaufnahmen-Modus aktiviert ist, IntelliTrace wird eine Momentaufnahme der der Anwendungsprozess an jeden Debugger **Haltepunkt** und **Schritt** Ereignis. Dies wird aufgezeichnet, Werte in der **"lokal"**, **"Auto"**, und **Überwachen** Windows, unabhängig davon, ob die Fenster geöffnet oder nicht sind. Datenwerten als Datentipps alle angehefteten werden ebenfalls erfasst.

- **Ausnahmen**

     IntelliTrace zeichnet den Ausnahmetyp und die Meldung für diese Ausnahmen auf:

    - Bearbeitete Ausnahmen, in denen die Ausnahme ausgelöst und abgefangen wird

    - Ausnahmefehler

- **.NET Framework-Ereignisse**

     IntelliTrace zeichnet standardmäßig die häufigsten .NET Framework-Ereignisse auf. Zum Beispiel:

    - Für ein Checkbox-Aktivierungsereignis erfasst IntelliTrace den Kontrollkästchenzustand und den Text.

- **SharePoint 2010 und SharePoint 2013-Anwendungsereignisse**

     Sie können Benutzerprofilereignisse und eine Teilmenge von einheitlichen Ereignissen des Protokollierungs-Systems (ULS) für SharePoint 2010- und 2013-Anwendungen erfassen, die außerhalb von Visual Studio ausgeführt werden. Sie können diese Ereignisse in einer ITRACE-Datei speichern. Erfordert Visual Studio Enterprise 2017, Visual Studio Enterprise 2015, eine frühere Version von Visual Studio Ultimate oder [Microsoft Monitoring Agent](http://go.microsoft.com/fwlink/?LinkId=320384) auf **Ablaufverfolgung** Modus.

     Wenn Sie die ITRACE-Datei öffnen, geben Sie eine SharePoint-Korrelations-ID ein, um die entsprechenden Webanforderung zu suchen, die aufgezeichneten Ereignisse anzuzeigen und das Debuggen von einem bestimmten Ereignis aus zu starten. Wenn die Datei Ausnahmefehler enthält, können Sie eine Korrelations-ID auswählen, um das Debuggen einer Ausnahme zu starten.

     Thema

    - [Verwenden des eigenständigen IntelliTrace-Collectors](../debugger/using-the-intellitrace-stand-alone-collector.md)

    - [Verwenden gespeicherter IntelliTrace-Daten](../debugger/using-saved-intellitrace-data.md)

    - [Exemplarische Vorgehensweise: Debuggen einer SharePoint-Anwendung mithilfe von IntelliTrace](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)

**Erfassen von Momentaufnahmen**

Sie können konfigurieren, dass IntelliTrace zum Aufzeichnen von Momentaufnahmen an jedem Haltepunkt und debugger Schrittereignis. IntelliTrace zeichnet die vollständigem Anwendungszustand auf jede Momentaufnahme, in dem Sie komplexe Variablen anzeigen und zum Auswerten von Ausdrücken kann.

Finden Sie unter [Anzeigen von Momentaufnahmen mithilfe von IntelliTrace Rückschritt](../debugger/how-to-use-intellitrace-step-back.md).

**Sammeln von funktionsaufrufinformationen**

Sie können IntelliTrace so konfigurieren, dass Aufrufinformationen für Funktionen gesammelt werden. Anhand dieser Informationen können Sie den Aufruflistenverlauf anzeigen und die Aufrufe im Code vorwärts und rückwärts durchlaufen. Für jeden Funktionsaufruf werden die folgenden Daten von IntelliTrace aufgezeichnet:

- Funktionsname
- Werte primitiver Datentypen, die als Parameter an Funktionseinstiegspunkten übergeben und an Funktionsendpunkten zurückgegeben werden
- Werte von automatischen Eigenschaften, wenn sie gelesen oder geändert werden
- Zeiger auf untergeordnete Objekte auf der obersten Ebene ohne Werte (außer NULL oder keine)

> [!NOTE]
> IntelliTrace erfasst nur die ersten 256 Objekte in Arrays und die ersten 256 Zeichen von Zeichenfolgen.

Finden Sie unter [untersuchen Ihrer app mit verlaufsbezogenem debugging](../debugger/historical-debugging-inspect-app.md).

**Sammeln von Modulinformationen**

Um zu steuern, wie viel Aufrufsinformationen IntelliTrace erfasst, legen Sie nur die Module fest, die für Sie von Bedeutung sind. Das kann dabei helfen, die Anwendungsleistung während der Erfassung zu verbessern. Finden Sie im Abschnitt [steuern, wie viele Informationen, die IntelliTrace erfasst](../debugger/intellitrace-features.md#ControlCallData) im IntelliTrace-Funktionen.

## <a name="AffectPerformance"></a> Meine Anwendung verlangsamt IntelliTrace?

Standardmäßig werden von IntelliTrace nur Daten für ausgewählte IntelliTrace-Ereignisse gesammelt. Das kann, abhängig von der Struktur und der Organisation Ihres Codes, eventuell die Anwendung verlangsamen. Wenn IntelliTrace beispielsweise oft ein Ereignis protokolliert, kann dies die Anwendung verlangsamen. Erwägen Sie, eine Umgestaltung Ihrer Anwendung vorzunehmen.

Das Sammeln der Aufrufsinformationen verlangsamt die App möglicherweise erheblich. Außerdem erhöht sich dadurch möglicherweise die Größe aller auf dem Datenträger gespeicherter IntelliTrace-Protokolldateien (ITRACE-Dateien). Um diese Auswirkungen zu minimieren, sammeln Sie Aufrufinformationen nur für die Module, die Sie interessieren.  Um die maximale Größe der ITRACE-Dateien zu ändern, wechseln Sie zu **Tools**, **Optionen**, **IntelliTrace**, **erweitert**. 

## <a name="in-this-section"></a>In diesem Abschnitt

[IntelliTrace-Funktionen](../debugger/intellitrace-features.md)
[Diagnostizieren von Problemen nach der Bereitstellung](../debugger/diagnose-problems-after-deployment.md)
[Verwenden gespeicherter IntelliTrace-Daten](../debugger/using-saved-intellitrace-data.md)

### <a name="blogs"></a>Blogs

[Microsoft DevOps](https://blogs.msdn.microsoft.com/devops/)

### <a name="forums"></a>Foren

[Visual Studio-Diagnose](http://go.microsoft.com/fwlink/?LinkId=262263)

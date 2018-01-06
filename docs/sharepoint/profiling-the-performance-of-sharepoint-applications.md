---
title: "Profilerstellung für die Leistung von SharePoint-Anwendungen | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.Profiling.SilverlightWebPartOnly
- VS.SharePointTools.Profiling.DotNetTrustLevel
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, profiling
- performance testing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, performance testing
- profiling [SharePoint development in Visual Studio]
ms.assetid: 61ae02e7-3f37-4230-bae1-54a498c2fae8
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 58e2d02b32a17cf23e95639077c26b6b41dae00f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="profiling-the-performance-of-sharepoint-applications"></a>Profilerstellung für die Leistung von SharePoint-Anwendungen
  Wenn die SharePoint-Anwendungen langsam oder ineffizient ausgeführt werden, können Sie die Profilerstellungsfunktionen in Visual Studio verwenden, um problematischen Code und andere Elemente zu identifizieren. Mithilfe der Auslastungstestfunktion können Sie ermitteln, wie eine SharePoint-Anwendung unter Belastung ausgeführt wird, beispielweise wenn viele Benutzer gleichzeitig auf die Anwendung zugreifen. Durch Ausführung von Webleistungstests können Sie messen, wie die Anwendung im Web ausgeführt wird. Anhand von Tests der programmierten UI können Sie überprüfen, ob die ganze SharePoint-Anwendung, einschließlich der Benutzeroberfläche, ordnungsgemäß funktioniert. Mithilfe dieser Tests können Sie Leistungsprobleme identifizieren, bevor Sie die Anwendung bereitstellen.  
  
## <a name="profiling-tools-overview"></a>Übersicht über Profilerstellungstools  
 Profilerstellung bezieht sich auf die Beobachtung und Erfassung des Leistungsverhaltens der Anwendung während sie ausgeführt wird. Durch die Profilerstellung für die Anwendung können Sie Probleme wie Engpässe, ineffizienten Code und Speicherbelegungsprobleme erkennen, die dazu führen, dass Anwendungen langsamer ausgeführt werden oder zu viel Arbeitsspeicher verwenden. Beispielsweise können Sie anhand der Profilerstellung Hotspots in Ihrem Code ermitteln, die Segmente des Codes sind, die häufig aufgerufen werden und die Gesamtleistung der Anwendung verlangsamen können. Nachdem Sie Hotspots identifiziert haben, können Sie sie häufig optimieren oder entfernen.  
  
 Sie können mehrere Profilerstellungstools in der integrierten Entwicklungsumgebung (IDE) verwenden, um diese Arten von Leistungsproblemen zu identifizieren und zu suchen. Diese Tools funktionieren für SharePoint-Projekte ebenso wie für andere Arten von Visual Studio-Projekten. Der Leistungs-Assistent der Profilerstellungstools führt Sie durch die Erstellung einer Leistungssitzung, die die angegebenen Tests verwendet. Eine leistungssitzung ist ein Satz von Konfigurationsdaten, die zum Sammeln von Leistungsinformationen aus einer Anwendung, zusammen mit den Ergebnissen einer oder mehrerer profilerstellungsausführungen verwendet wird. Leistungssitzungen werden im Projektordner gespeichert, und sehen Sie diese in **Leistungs-Explorer**. Weitere Informationen finden Sie unter [Grundlagen zu Profilerstellungsmethoden](/visualstudio/profiling/understanding-performance-collection-methods).  
  
 Nachdem Sie eine Profilanalyse für die Anwendung erstellt und ausgeführt haben, werden die entsprechenden Leistungsdetails in einem Bericht bereitgestellt. Dieser Bericht kann Elemente wie ein Diagramm der CPU-Auslastung im Zeitverlauf, eine hierarchische Funktionsaufrufliste oder eine Aufrufstruktur enthalten. Der genaue Inhalt des Berichts kann, je nach ausgeführtem Testtyp, z. B. Sampling oder Instrumentierung, variieren. Weitere Informationen finden Sie unter [Profiling Tools Berichtsübersicht](http://go.microsoft.com/fwlink/?LinkId=224689).  
  
## <a name="performance-session-process"></a>Leistungssitzungsprozess  
 Um die Profilerstellung einer Anwendung auszuführen, erstellen Sie zunächst eine Leistungssitzung mit dem Leistungs-Assistent der Profilerstellungstools. Wählen Sie in der Menüleiste **analysieren**, **Leistungs-Assistenten starten**. Nachdem Sie den Assistenten abgeschlossen haben, geben Sie die erforderlichen Informationen für die Leistungssitzung ein, z. B. die gewünschte Profilmethode und die Anwendung, für die Sie ein Profil erstellen möchten. Weitere Informationen finden Sie unter [Vorgehensweise: Profilerstellung für eine Website oder Web-Anwendung mithilfe Leistungs-Assistenten](http://go.microsoft.com/fwlink/?LinkId=224692). Alternativ können Sie Befehlszeilenoptionen verwenden, um eine Leistungssitzung zu installieren und auszuführen. Weitere Informationen finden Sie unter [mithilfe der Profilerstellung Tools From the Command](http://go.microsoft.com/fwlink/?LinkId=224703). Wenn Sie alle Aspekte einer leistungssitzung manuell konfigurieren möchten, finden Sie unter [Vorgehensweise: Manuelles Erstellen von Leistungssitzungen mit den Profilerstellungstools](http://go.microsoft.com/fwlink/?LinkId=224691). Sie können auch eine leistungssitzung aus Erstellen eines Komponententests, in der **Testergebnisse** Fenster, öffnen das Kontextmenü für den Komponententest aus, und drücken Sie dann die **Leistungssitzung erstellen**.  
  
 Nachdem Sie eine Leistungssitzung eingerichtet haben, wird die Sitzungskonfiguration gespeichert, wird der Server so konfiguriert, dass Profilerstellungsdaten bereitgestellt werden, und wird die Anwendung ausgeführt. Während Sie die Anwendung verwenden, werden Leistungsdaten in eine Protokolldatei geschrieben. Leistungssitzungen werden im aufgeführt **Leistungs-Explorer** unter der **Ziele** Ordner. Nachdem eine leistungssitzung beendet wurde, der Bericht wird angezeigt, der **Berichte** Ordner **Leistungs-Explorer**. Um den Bericht anzuzeigen, öffnen Sie es in **Leistungs-Explorer**. Zum Anzeigen oder konfigurieren Sie die Eigenschaften einer leistungssitzung, öffnen Sie das Kontextmenü im **Leistungs-Explorer**, und wählen Sie dann **Eigenschaften**. Weitere Informationen zu bestimmten Eigenschaften einer leistungssitzung finden Sie unter [Konfigurieren von Leistungssitzungen für Profilerstellungstools](http://go.microsoft.com/fwlink/?LinkId=224694). Informationen zum Interpretieren der Ergebnisse einer leistungssitzung finden Sie unter [Analyse der Profilerstellungsdaten für Tools](http://go.microsoft.com/fwlink/?LinkId=224704).  
  
## <a name="stress-testing"></a>Belastungstest  
 Sie können die Belastungsleistung der Anwendung analysieren, indem Sie Auslastungstests und Webleistungstests in Visual Studio Ultimate erstellen. Wenn Sie einen Auslastungstest in Visual Studio erstellen, geben Sie eine Kombination von Faktoren, ein so genanntes Szenario, an, gegen das die Anwendung getestet werden soll. Diese Faktoren enthalten Auslastungsmuster, Testmischungsmodell, Testmischung, Netzwerkmischung und Browsermix. Auslastungstestszenarien können sowohl Komponententests als auch Webleistungstests enthalten.  
  
 Abbildung 1: Beispiel für Auslastungstestergebnisse  
  
 ![Laufender Auslastungstest Diagrammansicht](../sharepoint/media/load-webgraphs.png "Diagrammansicht des Auslastungstest ausgeführt wird")  
  
 Webleistungstests simulieren die mögliche Interaktion eines Endbenutzers mit einer SharePoint-Anwendung. Sie können Webleistungstests erstellen, durch die HTTP-Anforderungen in eine Browsersitzung aufzeichnen oder mithilfe der **Webtestaufzeichnung**. Die webanforderungen werden in der **Webleistungstest-Editor** , nachdem die Browsersitzung beendet wurde. Sie können dann Debuggen, die Ergebnisse in die **Webleistungstest-Ergebnisviewer**. Sie können Webleistungstests auch manuell erstellen, mit der **Webleistungstest-Editor**.  
  
## <a name="testing-user-interfaces"></a>Testen von Benutzeroberflächen  
 Tests der codierten UI steuern automatisch die SharePoint-Anwendung über die Benutzeroberfläche (UI). Diese Tests decken UI-Steuerelemente, wie Schaltflächen und Menüs, ab, um zu überprüfen, ob sie ordnungsgemäß funktionieren. Diese Art von Tests sind besonders bei der Überprüfung oder einer anderen Logik der Benutzeroberfläche hilfreich, beispielsweise einer Webseite. Sie können auch Tests der codierten UI verwenden, um manuelle Tests zu automatisieren. Sie erstellen Tests der programmierten UI für die SharePoint-Anwendungen auf die gleiche Weise wie Sie Tests für andere Anwendungstypen erstellen. Weitere Informationen finden Sie unter [Testen von SharePoint 2010-Anwendungen mit Tests der codierten UI](/visualstudio/test/testing-sharepoint-2010-applications-with-coded-ui-tests).  
  
## <a name="related-topics"></a>Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[Exemplarische Vorgehensweise: Profilerstellung für eine SharePoint-Anwendung](../sharepoint/walkthrough-profiling-a-sharepoint-application.md)|Veranschaulicht, wie eine Samplingsprofilanalyse für eine SharePoint-Anwendung ausgeführt wird.|  
|[Testen der Leistung Ihrer App vor der Freigabe](https://www.visualstudio.com/docs/test/performance-testing/run-performance-tests-app-before-release)|Beschreibt, wie Auslastungstests erstellt werden, mit deren Hilfe Sie Belastungstests für SharePoint-Anwendungen durchführen.|  
|[Komponententest für Code](/visualstudio/test/unit-test-your-code)|Beschreibt, wie logische Fehler in Ihrem Code anhand von Komponententests gesucht werden.|  
|[Testen von SharePoint 2010-Anwendungen mit Tests der programmierten UI](/visualstudio/test/testing-sharepoint-2010-applications-with-coded-ui-tests)|Beschreibt, wie die Benutzeroberfläche Ihrer SharePoint-Anwendungen getestet wird.|  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen und Debuggen von SharePoint-Lösungen](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Testen der Anwendung](/devops-test-docs/test/test-apps-early-and-often)   
 [Verbessern der Codequalität](/visualstudio/test/improve-code-quality)  
  
  
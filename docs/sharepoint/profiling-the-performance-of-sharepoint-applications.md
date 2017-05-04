---
title: "Profilerstellung f&#252;r die Leistung von SharePoint-Anwendungen | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.Profiling.SilverlightWebPartOnly"
  - "VS.SharePointTools.Profiling.DotNetTrustLevel"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Leistungstest [SharePoint-Entwicklung in Visual Studio]"
  - "Profilerstellung [SharePoint-Entwicklung in Visual Studio]"
  - "SharePoint-Entwicklung in Visual Studio, Leistungstest"
  - "SharePoint-Entwicklung in Visual Studio, Profilerstellung"
ms.assetid: 61ae02e7-3f37-4230-bae1-54a498c2fae8
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Profilerstellung f&#252;r die Leistung von SharePoint-Anwendungen
  Wenn die SharePoint\-Anwendungen langsam oder ineffizient ausgeführt werden, können Sie die Profilerstellungsfunktionen in Visual Studio verwenden, um problematischen Code und andere Elemente zu identifizieren.  Mithilfe der Auslastungstestfunktion können Sie ermitteln, wie eine SharePoint\-Anwendung unter Belastung ausgeführt wird, beispielweise wenn viele Benutzer gleichzeitig auf die Anwendung zugreifen.  Durch Ausführung von Webleistungstests können Sie messen, wie die Anwendung im Web ausgeführt wird.  Anhand von Tests der codierten UI können Sie überprüfen, ob die ganze SharePoint\-Anwendung, einschließlich der Benutzeroberfläche, ordnungsgemäß funktioniert.  Mithilfe dieser Tests können Sie Leistungsprobleme identifizieren, bevor Sie die Anwendung bereitstellen.  
  
## Übersicht über Profilerstellungstools  
 Profilerstellung bezieht sich auf die Beobachtung und Erfassung des Leistungsverhaltens der Anwendung während sie ausgeführt wird.  Durch die Profilerstellung für die Anwendung können Sie Probleme wie Engpässe, ineffizienten Code und Speicherbelegungsprobleme erkennen, die dazu führen, dass Anwendungen langsamer ausgeführt werden oder zu viel Arbeitsspeicher verwenden.  Beispielsweise können Sie anhand der Profilerstellung Hotspots in Ihrem Code ermitteln, die Segmente des Codes sind, die häufig aufgerufen werden und die Gesamtleistung der Anwendung verlangsamen können.  Nachdem Sie Hotspots identifiziert haben, können Sie sie häufig optimieren oder entfernen.  
  
 Sie können mehrere Profilerstellungstools in der integrierten Entwicklungsumgebung \(IDE\) verwenden, um diese Arten von Leistungsproblemen zu identifizieren und zu suchen.  Diese Tools funktionieren für SharePoint\-Projekte ebenso wie für andere Arten von Visual Studio\-Projekten.  Der Leistungs\-Assistent der Profilerstellungstools führt Sie durch die Erstellung einer Leistungssitzung, die die angegebenen Tests verwendet.  Eine Leistungssitzung ist ein Satz von Konfigurationsdaten, der zum Sammeln von Leistungsinformationen aus einer Anwendung zusammen mit den Ergebnissen einer oder mehrerer Profilerstellungsausführungen verwendet wird.  Leistungssitzungen werden im Projektordner gespeichert, und Sie können sie im **Leistungs\-Explorer** anzeigen.  Weitere Informationen finden Sie unter [Grundlagen zu Profilerstellungsmethoden](../profiling/understanding-performance-collection-methods.md).  
  
 Nachdem Sie eine Profilanalyse für die Anwendung erstellt und ausgeführt haben, werden die entsprechenden Leistungsdetails in einem Bericht bereitgestellt.  Dieser Bericht kann Elemente wie ein Diagramm der CPU\-Auslastung im Zeitverlauf, eine hierarchische Funktionsaufrufliste oder eine Aufrufstruktur enthalten.  Der genaue Inhalt des Berichts kann, je nach ausgeführtem Testtyp, z. B. Sampling oder Instrumentation, variieren.  Weitere Informationen finden Sie unter [Übersicht über Profilerstellungstool\-Berichte](http://go.microsoft.com/fwlink/?LinkId=224689).  
  
## Leistungssitzungsprozess  
 Um die Profilerstellung einer Anwendung auszuführen, erstellen Sie zunächst eine Leistungssitzung mit dem Leistungs\-Assistent der Profilerstellungstools.  Wählen Sie im Menü **Analyse** die Option **Leistungs\-Assistenten starten** aus.  Nachdem Sie den Assistenten abgeschlossen haben, geben Sie die erforderlichen Informationen für die Leistungssitzung ein, z. B. die gewünschte Profilmethode und die Anwendung, für die Sie ein Profil erstellen möchten.  Weitere Informationen finden Sie unter [Gewusst wie: Erstellen eines Profils für eine Website oder eine Webanwendung mit dem Leistungs\-Assistent](http://go.microsoft.com/fwlink/?LinkId=224692).  Alternativ können Sie Befehlszeilenoptionen verwenden, um eine Leistungssitzung zu installieren und auszuführen.  Weitere Informationen finden Sie unter [Verwenden der Profilerstellungstools von der Befehlszeile](http://go.microsoft.com/fwlink/?LinkId=224703).  Wenn Sie jeden Aspekt einer Leistungssitzung manuell konfigurieren möchten, finden Sie weitere Informationen unter [Gewusst wie: Manuelles Erstellen von Leistungs\-Sitzungen mit den Profilerstellungstools](http://go.microsoft.com/fwlink/?LinkId=224691).  Sie können eine Leistungssitzung auch über einen Komponententest erstellen, indem Sie im Fenster **Testergebnisse** das Kontextmenü für den Komponententests öffnen und dann **Leistungssitzung erstellen** auswählen.  
  
 Nachdem Sie eine Leistungssitzung eingerichtet haben, wird die Sitzungskonfiguration gespeichert, wird der Server so konfiguriert, dass Profilerstellungsdaten bereitgestellt werden, und wird die Anwendung ausgeführt.  Während Sie die Anwendung verwenden, werden Leistungsdaten in eine Protokolldatei geschrieben.  Leistungssitzungen werden im **Leistungs\-Explorer** unter dem Ordner **Ziele** aufgeführt.  Nachdem eine Leistungssitzung beendet wurde, wird ihr Bericht im Ordner **Berichte** im **Leistungs\-Explorer** angezeigt.  Um den Bericht anzuzeigen, öffnen Sie sie im **Leistungs\-Explorer**.  Um die Eigenschaften einer Leistungssitzung anzuzeigen oder zu konfigurieren, öffnen Sie das Kontextmenü im **Leistungs\-Explorer**, und wählen Sie dann **Eigenschaften** aus.  Weitere Informationen zu bestimmten Eigenschaften einer Leistungssitzung, finden Sie unter [Konfigurieren von Leistungs\-Sitzungen für Profilerstellungstools](http://go.microsoft.com/fwlink/?LinkId=224694).  Informationen zur Interpretation der Ergebnisse einer Leistungssitzung, finden Sie unter [Analysieren der Daten von Profilerstellungstools](http://go.microsoft.com/fwlink/?LinkId=224704).  
  
## Belastungstest  
 Sie können die Belastungsleistung der Anwendung analysieren, indem Sie Auslastungstests und Webleistungstests in Visual Studio Ultimate erstellen.  Wenn Sie einen Auslastungstest in Visual Studio erstellen, geben Sie eine Kombination von Faktoren, ein so genanntes Szenario, an, gegen das die Anwendung getestet werden soll.  Diese Faktoren enthalten Auslastungsmuster, Testmischungsmodell, Testmischung, Netzwerkmischung und Browsermischung.  Auslastungstestszenarien können sowohl Komponententests als auch Webleistungstests enthalten.  
  
 Abbildung 1: Beispiel für Auslastungstestergebnisse  
  
 ![Diagramm für die Ausführung von Auslastungstests](../sharepoint/media/load-webgraphs.png "Diagramm für die Ausführung von Auslastungstests")  
  
 Webleistungstests simulieren die mögliche Interaktion eines Endbenutzers mit einer SharePoint\-Anwendung.  Sie können Webleistungstests durch Aufzeichnen der HTTP\-Anforderungen in einer Browsersitzung mithilfe der **Webleistungstest\-Aufzeichnung** erstellen.  Die Webanforderungen werden im **Webleistungstest\-Editor** angezeigt, nachdem die Browsersitzung beendet wurde.  Sie können dann im **Webleistungstest\-Ergebnisviewer** die Ergebnisse debuggen.  Sie können Webleistungstests jedoch auch manuell mit dem **Webleistungstest\-Editor** erstellen.  
  
## Testen von Benutzeroberflächen  
 Tests der codierten UI steuern automatisch die SharePoint\-Anwendung über die Benutzeroberfläche \(UI\).  Diese Tests decken UI\-Steuerelemente, wie Schaltflächen und Menüs, ab, um zu überprüfen, ob sie ordnungsgemäß funktionieren.  Diese Art von Tests sind besonders bei der Überprüfung oder einer anderen Logik der Benutzeroberfläche hilfreich, beispielsweise einer Webseite.  Sie können auch Tests der codierten UI verwenden, um manuelle Tests zu automatisieren.  Sie erstellen Tests der codierten UI für die SharePoint\-Anwendungen auf die gleiche Weise wie Sie Tests für andere Anwendungstypen erstellen.  Weitere Informationen finden Sie unter [Testen von SharePoint 2010-Anwendungen mit Tests der codierten UI](../test/testing-sharepoint-2010-applications-with-coded-ui-tests.md).  
  
## Verwandte Themen  
  
|Titel|**Beschreibung**|  
|-----------|----------------------|  
|[Walkthrough: Profiling a SharePoint Application](../sharepoint/walkthrough-profiling-a-sharepoint-application.md)|Veranschaulicht, wie eine Samplingsprofilanalyse für eine SharePoint\-Anwendung ausgeführt wird.|  
|[Create and run a load test](http://msdn.microsoft.com/de-de/7041cbcf-9ab1-4579-98ff-8f296aeaded4)|Beschreibt, wie Auslastungstests erstellt werden, mit deren Hilfe Sie Belastungstests für SharePoint\-Anwendungen durchführen.|  
|[Creating and Editing Web Performance Tests](http://msdn.microsoft.com/de-de/8bf5f2a7-c693-47d6-9282-5946480151dc)|Beschreibt, wie Webleistungstests erstellt werden, mit deren Hilfe Sie simulieren, wie ein Benutzer mit der SharePoint\-Website im Web interagiert.|  
|[Komponententest für Code](../test/unit-test-your-code.md)|Beschreibt, wie logische Fehler in Ihrem Code anhand von Komponententests gesucht werden.|  
|[Testen von SharePoint 2010-Anwendungen mit Tests der codierten UI](../test/testing-sharepoint-2010-applications-with-coded-ui-tests.md)|Beschreibt, wie die Benutzeroberfläche Ihrer SharePoint\-Anwendungen getestet wird.|  
  
## Siehe auch  
 [Erstellen und Debuggen von SharePoint-Lösungen](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Testen der Anwendung](http://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)   
 [Verbessern der Codequalität](../test/improve-code-quality.md)  
  
  
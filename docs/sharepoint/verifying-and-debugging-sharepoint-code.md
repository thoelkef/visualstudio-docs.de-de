---
title: "&#220;berpr&#252;fen und Debuggen von SharePoint-Code"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Komponententests [SharePoint-Entwicklung in Visual Studio]"
  - "IntelliTrace [SharePoint-Entwicklung in Visual Studio]"
  - "SharePoint-Entwicklung in Visual Studio, IntelliTrace"
  - "SharePoint-Entwicklung in Visual Studio, Komponententests"
ms.assetid: b5f3bce2-6a51-41b1-a292-9e384bae420c
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# &#220;berpr&#252;fen und Debuggen von SharePoint-Code
  Mit IntelliTrace und Komponententests können Sie die SharePoint\-Lösungen leichter debuggen und sicherstellen, dass jede Methode in ihnen ordnungsgemäß funktioniert.  Sie können diese Funktionen für SharePoint\-Projekte in [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] verwenden, indem Sie die gleichen Prozeduren wie für andere Typen von Projekten ausführen.  
  
## IntelliTrace  
 Mit IntelliTrace können Sie nicht nur den aktuellen Zustand der SharePoint\-Lösung bestimmen, sondern auch in der Vergangenheit aufgetretene Ereignisse sowie den Kontext, in dem sie aufgetreten sind.  Sie können zwischen verschiedenen Zeitpunkten in Ihrer SharePoint\-Lösung, an denen relevante Ereignisse erfasst wurden, hin und her navigieren und die Zustände und Werte von Variablen an jedem Punkt überprüfen.  Indem Sie diese dynamische Navigation verwenden, können Sie die SharePoint\-Lösungen schneller und einfacher debuggen, ohne zahlreiche Haltepunkte festzulegen.  Sie können auch die Debugsitzung in einer IntelliTrace\-Protokoll\-\(.iTrace\)\-Datei speichern, diese später in Visual Studio Ultimate öffnen und Debugging nach einem Absturz ausführen.  Die ITRACE\-Datei enthält ausführliche Informationen darüber, wann und wo bestimmte SharePoint\-Fehler aufgetretenen sind, damit Sie leichter ermitteln können, was die Fehler verursacht.  Die Informationen in der ITRACE\-Datei sind eine Teilmenge des vollständigen Fehlerprotokolls, das das ULS \(Unified Logging System, Vereinheitlichter Protokollierungsdienst\) in SharePoint erstellt.  Diese Informationen umfassen Ereignisse, die für SharePoint spezifisch sind, wie z. B. wenn ein Benutzerprofil geöffnet oder geschlossen wird und wenn Eigenschaften in einem SharePoint\-Projekt geladen, gelesen oder geändert werden.  Sie können konfigurieren, welche Ereignisse IntelliTrace aufzeichnet.  Weitere Informationen finden Sie unter [Verwenden gespeicherter IntelliTrace-Daten](../debugger/using-saved-intellitrace-data.md) und [Konfigurieren von IntelliTrace zum Sammeln von Debuginformationen](http://msdn.microsoft.com/de-de/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
 Wenn ein Fehler in SharePoint auftritt, zeigt das Fehlerdialogfeld einen "Korrelations\-ID"\-Bezeichner für diesen speziellen Fehler an.  Sie können auch Korrelations\-IDs von Ereignissen abrufen, die in der ITRACE\-Datei aufgeführt werden.  Um eine Liste aller Ereignisse anzuzeigen die bei einer angegebenen Korrelations\-ID aufgetretenen sind, können Sie die ID im Abschnitt **Analyse** der Seite "IntelliTrace\-Zusammenfassung" eingeben.  In diesem Abschnitt können Sie auswählen, ob nur die Namen der aufgetretenen Ereignisse angezeigt werden sollen oder die Namen der Ereignisse zusammen mit ihren Aufrufinformationen, wie z. B. der Funktionsname, die Beendigungs\- und Einstiegspunkte, Parameter und Rückgabewerte.  
  
 Sie können Visual Studio\-Ereignisse in IntelliTrace abrufen, indem Sie die **F5**\-TASTE auswählen.  Um für SharePoint spezifische Ereignisse abzurufen, müssen Sie jedoch IntelliTrace\-Daten in SharePoint\-Lösungen sammeln, indem Sie Microsoft Monitoring Agent verwenden.  Dieses Tool sammelt IntelliTrace\-Daten und erstellt ITRACE\-Dateien für Anwendungen, die außerhalb von Visual Studio bereitgestellt werden.  Weitere Informationen finden Sie unter [IntelliTrace-Features](../debugger/intellitrace-features.md) und [Verwenden des eigenständigen IntelliTrace-Collectors](../debugger/using-the-intellitrace-stand-alone-collector.md).  
  
## Komponententests  
 Sie können Fehler im Code leichter finden, indem Sie Komponententests ausführen, bei denen Sie Testcode in Testmethoden schreiben und ausführen.  Diese Methoden enthalten leere Variablen und eine Assert\-Anweisung, die Sie verwenden können, um die Logik und die Funktionalität des Projekts auf Grundlage des SharePoint\-Objektmodells zu überprüfen.  Weitere Informationen finden Sie unter [Komponententest für Code](../test/unit-test-your-code.md).  
  
### Unterstützung für Microsoft Fakes\-Framework  
 SharePoint\-Projekte unterstützen Microsoft Fakes, ein Isolationsframework, in dem Sie delegatbasierte Test\-Stubs und \-Shims in Anwendungen erstellen können, die auf .NET Framework basieren.  Mithilfe des Fakes Framework können Sie Platzhalterimplementierungen in Ihren Komponententests erstellen, verwalten und einfügen.  Diese Stubs und Shims isolieren die Komponententests von der Umgebung.  Sie können Stubs erstellen, um Code zu testen, der Schnittstellen oder nicht versiegelte Klassen mit überschreibbaren Methoden verwendet.  Sie können Shims erstellen, um hartcodierte Aufrufe von versiegelten Klassen mit statischen oder nicht überschreibbaren Methoden zu einer alternativen Shim\-Implementierung umzuleiten.  Sie können auch Delegate mit Stub\-Typen und Shim\-Typen verwenden, um das Verhalten einzelner Stub\-Member dynamisch anzupassen.  Weitere Informationen finden Sie unter [Isolieren von getestetem Code mithilfe von Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md).  
  
## Verwandte Themen  
  
|Titel|**Beschreibung**|  
|-----------|----------------------|  
|[Verwenden von IntelliTrace](../debugger/intellitrace.md)|Beschreibt, wie Visual Studio\-Projektmappen mithilfe von IntelliTrace leichter zu debuggen sind.|  
|[Exemplarische Vorgehensweise: Debuggen einer SharePoint-Anwendung mithilfe von IntelliTrace](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)|Veranschaulicht, wie IntelliTrace verwendet wird, um Codefehler in einem SharePoint\-Projekt zu suchen.|  
|[Komponententest für Code](../test/unit-test-your-code.md)|Beschreibt, wie logische Fehler in Ihrem Code anhand von Komponententests gesucht werden.|  
  
## Siehe auch  
 [Verbessern der Codequalität](../test/improve-code-quality.md)  
  
  
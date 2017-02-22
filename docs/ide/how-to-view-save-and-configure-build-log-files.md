---
title: "Gewusst wie: Anzeigen, Speichern und Konfigurieren von Buildprotokolldateien | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 75d38b76-26d6-4f43-bbe7-cbacd7cc81e7
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Gewusst wie: Anzeigen, Speichern und Konfigurieren von Buildprotokolldateien
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nachdem Sie ein Projekt in der Visual Studio\-IDE erstellen, können Sie Informationen zu diesen Build **Ausgabe** im Fenster anzeigen.  Wenn Sie diese Informationen verwenden, können Sie einen Buildfehler beispielsweise beheben.  Für C\+\+\-Projekte können Sie dieselben Informationen in einer Datei .txt\- auch anzeigen, die automatisch erstellt und gespeichert wird.  Bei Projekten mit verwaltetem Code können Sie kopieren und einfügen **Ausgabe** die Informationen aus dem Fenster in eine Datei .txt\- und sie zu speichern.  Sie können die IDE auch verwenden, um anzugeben, welche Arten von Informationen Sie zu jedem Build anzeigen möchten.  
  
 Wenn Sie eine Art Projekt erstellen, indem Sie MSBuild verwenden, können Sie eine Datei .txt\- erstellen, um Informationen über den Build zu speichern.  Weitere Informationen finden Sie unter [Erhalten von Buildprotokollen](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
### Um die Buildprotokolldatei für eine C\+\+\-Datei angezeigt werden  
  
1.  In **Windows\-Explorer** oder in **Datei\-Explorer** öffnen Sie die folgende Datei: \\...  \\Visual Studio *Version*\\Projects\\*Projektname*\\*Projektname*\\Debug\\*Projektname*.txt  
  
### So fügen Sie eine Buildprotokolldatei für ein Projekt erstellen mit verwaltetem Code  
  
1.  Klicken Sie auf der Menüleiste wählen Sie **Build**, **Projektmappe erstellen** aus.  
  
2.  Im Fenster **Ausgabe** markieren Sie die Informationen aus dem Build, und kopieren Sie anschließend in die Zwischenablage.  
  
3.  Öffnen Sie einen Text\-Editor, wie Editor, Einfügen die Informationen in die Datei, und speichern Sie diese.  
  
### Um die Informationsmenge ändern enthalten in das Buildprotokoll  
  
1.  Klicken Sie auf der Menüleiste wählen Sie **Tools**, **Optionen** aus.  
  
2.  **Projekte und Projektmappen** auf der Seite die Seite **Erstellen und Ausführen** aus.  
  
3.  In der Liste **Ausführlichkeit der MSBuild\-Projektbuildausgabe** einen der folgenden Werte aus, und wählen Sie dann die Schaltfläche **OK** aus.  
  
    |Ausführlichkeitsgrad|Beschreibung|  
    |--------------------------|------------------|  
    |Quiet|Zeigt eine Zusammenfassung des nur Build an.|  
    |Minimal|Zeigt eine Zusammenfassung des Build und der Fehler, der Warnungen und der Meldungen an, die kategorisiert werden, wie äußerst wichtig.|  
    |Normal|Zeigt eine Zusammenfassung des Build an; Fehler, Warnungen und Meldungen, die kategorisiert werden, wie äußerst wichtig; und die Hauptschritte im Build.  Sie verwenden dieses Detailgrad sehr häufig.|  
    |Detailed|Zeigt eine Zusammenfassung des Build an; Fehler, Warnungen und Meldungen, die kategorisiert werden, wie äußerst wichtig; alle Schritte des Build; und Meldungen, die ab normaler Wichtigkeit kategorisiert werden.|  
    |Diagnose|Zeigt alle Daten, die für den Build verfügbar ist.  Sie können dieses Detailgrad verwenden, um Probleme mit benutzerdefinierten Buildskripts Debug\- und anderen Buildproblemen zu unterstützen.|  
  
     Weitere Informationen finden Sie unter [Optionen \(Dialogfeld\), Projekte und Projektmappen, Erstellen und Ausführen](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md) und <xref:Microsoft.Build.Framework.LoggerVerbosity>.  
  
    > [!IMPORTANT]
    >  Sie müssen das Projekt neu erstellen, damit die Änderungen im Fenster **Ausgabe** \(alle Projekte\) und in der Datei *Projektname*.txt wirksam werden \(nur C\+\+\-Projekte\).  
  
## Siehe auch  
 [Erhalten von Buildprotokollen](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [Erstellen und Bereinigen von Projekten und Projektmappen in Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)   
 [Anwendungen in Visual Studio erstellen](../ide/compiling-and-building-in-visual-studio.md)
---
title: "Vorgehensweise: Sammeln von Leistungsdaten f&#252;r eine Website | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vsperf.url.url"
  - "vsperf.chooseurl"
  - "vs.performance.wizard.asppage"
  - "vsperf.url.ok"
  - "vsperf.url.cancel"
helpviewer_keywords: 
  - "Profilerstellungstools, ASP.NET-Profilerstellung"
  - "Websites, Leistungsprofilerstellung"
  - "ASP.NET, Leistungsprofilerstellung"
ms.assetid: a62d27fd-a966-4065-bebe-6874195a71fb
caps.latest.revision: 33
caps.handback.revision: 33
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Vorgehensweise: Sammeln von Leistungsdaten f&#252;r eine Website
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können den **Leistungs\-Assistenten** zum Sammeln von Leistungsdaten einer [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web\-Anwendung verwenden. Sie können ein Profil einer Webanwendung erstellen, die in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] geöffnet ist, oder Sie können ein Profil einer [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Website erstellen, die sich auf dem lokalen Computer befindet und nicht in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE geöffnet ist.  
  
> [!NOTE]
>  Der **Leistungs\-Assistent** ermöglicht Ihnen das Hinzufügen von Ebeneninteraktionsdaten \(TIP\) und\/oder JScript\-Leistungsdaten zu den gesammelten Profilerstellungsdaten. Die Option TIP sammelt Daten von serverseitigen Prozessen. Die JScript\-Profilerstellung sammelt Daten aus Skripts, die auf einer lokalen oder Remotewebsite ausgeführt werden. In den meisten Fällen sollten Sie nur eine der Optionen auswählen.  
  
 Je nach Benutzerzugriffsberechtigungs\-Einstellungen, die ein Administrator zur Verfügung gestellt hat, kann ein einzelner Benutzer über die Sicherheitsberechtigung zur Erstellung einer Profilersitzung auf dem Computer verfügen, der den ASP.NET\-Prozess hostet. Die folgenden Beispiele veranschaulichen mögliche Unterschiede zwischen Benutzern:  
  
-   Einige Benutzer können auf erweiterte Profilerstellungsfeatures zugreifen, wenn der Administrator Treiber und Dienst gestartet hat.  
  
-   Domänenbenutzer können nur auf Beispiel\-Profilerstellung zugreifen.  
  
-   Einige Benutzer können den Zugriff auf Profilerstellung für alle anderen Benutzer verweigern.  
  
 Weitere Informationen finden Sie unter [Profilerstellung und Sicherheit in Windows Vista](../profiling/profiling-and-windows-vista-security.md) und in den ADMIN\-Optionen in [VSPerfCmd](../profiling/vsperfcmd.md).  
  
### Profilieren eines Websiteprojekts  
  
1.  Öffnen Sie das [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Webprojekt in [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] oder [!INCLUDE[vsUltShort](../code-quality/includes/vsultshort_md.md)].  
  
2.  Klicken Sie im Menü **Analyse** auf **Leistungs\-Assistenten starten**.  
  
3.  Auf der ersten Seite des Assistenten, wählen Sie eine Profilerstellungsmethode, und klicken Sie dann auf **Weiter**. Weitere Informationen zu Profilerstellungsmethoden finden Sie unter [Grundlagen zu Profilerstellungsmethoden](../profiling/understanding-performance-collection-methods.md). Beachten Sie, dass die Parallelitätsschnellansicht Profilerstellungsmethode nicht für Webanwendungen verfügbar ist.  
  
4.  In der Dropdownliste **Welche Anwendung soll für die Profilerstellung als Ziel festgelegt werden?** stellen Sie sicher, dass das aktuelle Projekt ausgewählt ist, und klicken Sie dann auf **Weiter**.  
  
5.  Sie können auf der dritten Seite des Assistenten die Profilerstellungsdaten für Ebeneninteraktion \(TIP; tier interaction profiling\), Daten aus JavaScript auf Webseiten oder beides hinzufügen.  
  
    -   Wählen Sie das Kontrollkästchen **Profilerstellung für Ebeneninteraktion aktivieren** aus, um Ebeneninteraktionen zu erfassen.  
  
    -   Wählen Sie zum Sammeln von Daten aus JavaScript auf Webseiten das Kontrollkästchen **Profilerstellung für JavaScript** aus.  
  
6.  Klicken Sie auf **Weiter**.  
  
7.  Klicken Sie auf der vierten Seite des Assistenten auf **Fertig stellen**.  
  
8.  Eine Leistungssitzung wird für die [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Anwendung erstellt und die Website wird im Browser gestartet. Verwenden Sie die Funktionen, für die eine Profilerstellung erfolgen soll, und schließen Sie dann den Browser.  
  
     Der Profiler generiert die Datendatei und zeigt die Zusammenfassungsansicht der Daten im [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Hauptfenster.  
  
### Profilieren einer Website ohne ein Projekt in Visual Studio zu öffnen  
  
1.  Öffnen Sie [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] oder [!INCLUDE[vsUltShort](../code-quality/includes/vsultshort_md.md)].  
  
2.  Klicken Sie im Menü **Analyse** auf **Leistungs\-Assistenten starten**.  
  
3.  Auf der ersten Seite des Assistenten, wählen Sie eine Profilerstellungsmethode, und klicken Sie dann auf **Weiter**. Weitere Informationen finden Sie unter [Grundlagen zu Profilerstellungsmethoden](../profiling/understanding-performance-collection-methods.md).  
  
4.  Wählen Sie auf der zweiten Seite des Assistenten die Option **Profil einer ASP.NET\- oder JavaScript\-Anwendung erstellen** und klicken Sie dann auf **Weiter**.  
  
5.  Geben Sie im Feld **Auf welcher URL oder welchem Pfad wird die Webanwendung ausgeführt?** auf der dritten Seite des Assistenten die URL der Startseite der Anwendung ein und klicken Sie dann auf **Weiter**.  
  
    -   Für eine serverbasierte IIS\-Website geben Sie eine URL ein, z.B. **http:\/\/localhost\/MySite\/default.aspx**. Dies bewirkt, dass für die [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Anwendung auf dem lokalen Computer beim Anwendungsstamm von MySite ein Profil erstellt wird und die Seite default.aspx dieser Site im Internet Explorer geöffnet wird, um die Sitzung zu starten.  
  
    -   Für eine dateibasierte Website geben Sie einen Pfad ein, zum Beispiel file\/\/\/**c:\\WebSites\\MySite\\default.aspx**. Dies bewirkt, dass von der [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Anwendung in „c:\\webSites\\MySite“ ein Profil erstellt wird und die Seite http:\/\/localhost:nnnn\/MySite\/default.aspx im Internet Explorer zum Beginn der Sitzung gestartet wird.  
  
    -   Von externen Websites, deren JavaScript\-Daten gesammelt werden sollen, geben Sie die URL ein, z.B. http:\/\/www.contoso.com.  
  
     Weitere Informationen finden Sie auf den Eigenschaftenseiten für eine [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Zielbinärdatei.  
  
6.  Sie können auf der dritten Seite des Assistenten die Profilerstellungsdaten für Ebeneninteraktion \(TIP; tier interaction profiling\), Daten aus JavaScript auf Webseiten oder beides hinzufügen.  
  
    -   Wählen Sie das Kontrollkästchen **Profilerstellung für Ebeneninteraktion aktivieren** aus, um Ebeneninteraktionen zu erfassen.  
  
    -   Wählen Sie zum Sammeln von Daten aus JavaScript auf Webseiten das Kontrollkästchen **Profilerstellung für JavaScript** aus.  
  
7.  Klicken Sie auf **Weiter**.  
  
8.  Klicken Sie auf der vierten Seite des Assistenten auf **Fertig stellen**.  
  
9. Eine Leistungssitzung wird für die ASP.NET\-Anwendung erstellt und die Website wird im Browser gestartet. Verwenden Sie die Funktionen, für die eine Profilerstellung erfolgen soll, und schließen Sie dann den Browser.  
  
     Der Profiler generiert die Datendatei und zeigt die Zusammenfassungsansicht der Daten im [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Hauptfenster.  
  
## Siehe auch  
 [Übersichten](../profiling/overviews-performance-tools.md)   
 [Konfigurieren von Leistungssitzungen](../profiling/configuring-performance-sessions.md)   
 [Grundlagen zu Instrumentationsdatenwerten](../profiling/understanding-instrumentation-data-values.md)   
 [Grundlagen zu Samplingdatenwerten](../profiling/understanding-sampling-data-values.md)
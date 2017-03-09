---
title: "Hinzuf&#252;gen von Ebeneninteraktionsdaten &#252;ber die Befehlszeile | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Ebeneninteraktions-Profilerstellungsmethode"
  - "Profilerstellungstools, Ebeneninteraktionsmethode"
ms.assetid: 5a35647f-03f2-4555-8eeb-fda7e0080e67
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Hinzuf&#252;gen von Ebeneninteraktionsdaten &#252;ber die Befehlszeile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Profilerstellung für Ebeneninteraktion stellt weitere Informationen zu den Ausführungszeiten synchroner [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)]\-Aufrufe in Funktionen von Anwendungen mit mehreren Ebenen bereit, von denen mit mindestens einer Datenbank kommuniziert wird.  
  
 **Windows 8 und Windows Server 2012**  
  
 Um Ebeneninteraktionsdaten auf Windows 8\-Desktop\-Apps und Windows Server 2012\-Apps zu sammeln müssen Sie die Instrumentationsmethode verwenden.  Das Sammeln der Ebeneninteraktionsdaten auf Windows Store\-Apps wird nicht unterstützt.  
  
 **Visual Studio\-Editionen**  
  
 Profilerstellungsdaten für die Ebeneninteraktion können mit [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] oder [!INCLUDE[vs_pro_current_short](../profiling/includes/vs_pro_current_short_md.md)] erfasst werden.  Allerdings können Profilerstellungsdaten für die Ebeneninteraktion nur in [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)] und [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] angezeigt werden.  
  
 **Sammeln von TIP\-Daten auf einem Remotecomputer**  
  
 Um Ebeneninteraktionsdaten auf einem Remotecomputer zu sammeln, müssen Sie die Datei **vs\_profiler\_***\<Platform\>***\_***\<Language\>***.exe** aus dem Ordner *%VSInstallDir%***\\Team Tools\\Performance Tools\\Setups** eines Visual Studio\-Computers auf den Remotecomputer kopieren und dort installieren.  Sie können nicht die Profilerstellungstools im Downloadpaket der [Visual Studio\-Remotetools](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md) verwenden.  
  
 **TIP\-Berichte**  
  
 Ebeneninteraktionsdaten können nur in der [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)]\-IDE angezeigt werden.  Dateibasierte Ebeneninteraktionsberichte über [VSPerfReport](../profiling/vsperfreport.md) sind nicht verfügbar.  
  
## Hinzufügen von Ebeneninteraktionsdaten mithilfe von "VSPerfCmd"  
 Beim Befehlszeilentool "VSPerfASPNETCmd" stehen Ihnen sämtliche Funktionen der Profilerstellungstools zur Verfügung.  Wenn Sie den unter Verwendung von "VSPerfCmd" gesammelten Profilerstellungsdaten Ebeneninteraktionsdaten hinzufügen möchten, müssen die Umgebungsvariablen, mit denen die Ebeneninteraktionsdaten aktiviert werden, mithilfe des Hilfsprogramms **VSPerfCLREnv** festgelegt und entfernt werden.  Die anzugebenden Optionen und die für die Datensammlung erforderlichen Prozeduren hängen davon ab, für welche Art von Anwendung die Profilerstellung ausgeführt wird.  
  
### Profilerstellung für eigenständige Anwendungen  
 Wenn Sie einer Anwendung, die nicht von einem anderen Prozess ausgeführt wird – also beispielsweise einer Windows\-Desktopanwendung mit synchronen [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)]\-Aufrufen einer SQL Server\-Datenbank –, Ebeneninteraktionsdaten hinzufügen möchten, verwenden Sie die Option **VSPerfClrEnv \/InteractionOn**, um die Umgebungsvariablen festzulegen, und die Option **VSPerfClrEnv \/InteractionOff**, um sie zu entfernen.  
  
 Im folgenden Beispiel wird ein Profil für eine Windows\-Desktopanwendung erstellt, indem die Instrumentationsmethode und Ebeneninteraktionsdaten werden gesammelt.  
  
##### Beispiel: Profilerstellung für eine Windows\-Desktopanwendung  
  
1.  Öffnen Sie ein Eingabeaufforderungsfenster mit Administratorrechten.  Klicken Sie auf **Start**, zeigen Sie auf **Alle Programme**, und zeigen Sie anschließend auf **Zubehör**.  Klicken Sie mit der rechten Maustaste auf **Eingabeaufforderung**, und klicken Sie anschließend auf **Als Administrator ausführen**.  
  
2.  Initialisieren Sie .NET\-EinProfil erstellen und die TIPP\-Umgebungsvariablen.  Geben Sie die folgenden Befehle ein:  
  
    ```  
    vsperfclrenv /traceon  
    vsperfclrenv /interactionon  
    ```  
  
3.  Starten Sie den Profiler.  Geben Sie folgenden Befehl ein:  
  
    ```  
    vsperfcmd /start:trace /output:Desktop_tip.vsp   
    ```  
  
4.  Starten Sie die Anwendung mit "VSPerfCmd".  Geben Sie folgenden Befehl ein:  
  
    ```  
    vsperfcmd /launch:DesktopApp.exe  
    ```  
  
5.  Verwenden Sie die Anwendung, um Profilerstellungsdaten zu sammeln, und schließen Sie die Anwendung anschließend mit dem regulären Verfahren.  
  
6.  Löschen Sie die TIP\-Umgebungsvariablen.  Geben Sie folgenden Befehl ein:  
  
    ```  
    vsperfclrenv /off  
    ```  
  
 Weitere Informationen finden Sie unter [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md).  
  
### Profilerstellung für Dienste  
 Verwenden Sie zum Erstellen eines Profils für Dienste \(einschließlich [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Anwendungen\) die Option **VSPerfClrEnv \/GlobalInteractionOn**, um die Umgebungsvariablen festzulegen, und die Option **VSPerfClrEnv \/GlobalInteractionOff**, um sie zu entfernen.  
  
 Bei der Profilerstellung für Dienste und [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Webanwendungen muss der Computer häufig neu gestartet werden, um die Profilerstellung zu aktivieren.  
  
 Im folgenden Beispiel wird ein Profil für einen Windows\-Dienst erstellt, indem die instrumenation Methode \- und Ebeneninteraktionsdaten werden gesammelt.  
  
##### Beispiel: Profilerstellung für einen Windows\-Dienst  
  
1.  Installieren Sie den Dienst, falls notwendig.  
  
2.  Öffnen Sie ein Eingabeaufforderungsfenster mit Administratorrechten.  Klicken Sie auf **Start**, zeigen Sie auf **Alle Programme**, und zeigen Sie anschließend auf **Zubehör**.  Klicken Sie mit der rechten Maustaste auf **Eingabeaufforderung**, und klicken Sie anschließend auf **Als Administrator ausführen**.  
  
3.  Initialisieren Sie die .NET\-Umgebungsvariablen für die Profilerstellung.  Geben Sie folgenden Befehl ein:  
  
    ```  
    vsperfclrenv /globaltraceon  
    ```  
  
4.  Initialisieren Sie die TIP\-Umgebungsvariablen.  Geben Sie folgenden Befehl ein:  
  
    ```  
    vsperfclrenv /globalinteractionon  
    ```  
  
5.  Starten Sie den Computer neu, um die Umgebungsvariablen zu registrieren.  
  
6.  Öffnen Sie ein Eingabeaufforderungsfenster mit Administratorrechten.  
  
7.  Starten Sie den Profiler.  Geben Sie folgenden Befehl ein:  
  
    ```  
    vsperfcmd /start:trace /output:MiddleTier_tip.vsp /user:SYSTEM /crosssession   
    ```  
  
8.  Starten Sie den Dienst bei Bedarf.  
  
9. Fügen Sie den Profiler an den Dienst an.  Geben Sie folgenden Befehl ein:  
  
    ```  
    vsperfcmd /attach:MiddleTier.exe /output:MyService_tip.vsp /user:SYSTEM /crosssession   
    ```  
  
10. Verwenden Sie den Dienst, um Profilerstellungsdaten zu sammeln.  
  
11. Beenden Sie den Profiler.  Geben Sie folgenden Befehl ein:  
  
     `vsperfcmd /detach`  
  
12. Löschen Sie die .NET\- und die TIP\-Umgebungsvariablen für die Profilerstellung.  Geben Sie folgenden Befehl ein:  
  
    ```  
    vsperfclrenv /globaloff  
    ```  
  
13. Starten Sie den Computer neu, um die gelöschten Umgebungsvariablen zu registrieren.  
  
 Weitere Informationen finden Sie in einem der folgenden Themen:  
  
 [Profilerstellung für ASP.NET\-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)  
  
 [Profilerstellungsdienste](../profiling/command-line-profiling-of-services.md)  
  
## Hinzufügen von Ebeneninteraktionsdaten mithilfe von "VSPerfASPNETCmd"  
 Mithilfe des Befehlszeilentools "VSPerfASPNETCmd" lassen sich auf einfache Weise Profile für [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Webanwendungen erstellen.  Verglichen mit dem Befehlszeilentool **VSPerfCmd** stehen weniger Optionen zur Verfügung, es müssen keine Umgebungsvariablen festgelegt werden, und der Computer muss nicht neu gestartet werden.  Diese Funktionen von "VSPerfASPNETCmd" machen das Sammeln von Ebeneninteraktionsdaten besonders einfach.  
  
 Fügen Sie der Befehlszeile die Option **\/TIP** hinzu, um den mithilfe von "VSPerfASPNETCmd" gesammelten Profilerstellungsdaten Ebeneninteraktionsdaten hinzuzufügen.  Verwenden Sie beispielsweise die folgende Befehlszeile, um Ebeneninteraktionsdaten für eine [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] \- Webanwendung zu sammeln, indem Sie die Instrumentationsmethode verwenden:  
  
```  
vsperfaspnetcmd /tip /trace http://localhost/MyWebApp  
```  
  
 Weitere Informationen zu "VSPerfASPNETCmd" finden Sie unter [Schnelle Website\-Profilerstellung mit VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).
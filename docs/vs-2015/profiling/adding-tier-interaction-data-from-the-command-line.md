---
title: Hinzufügen von Ebeneninteraktionsdaten über die Befehlszeile | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tier interaction profiling method
- profiling tools,tier interaction method
ms.assetid: 5a35647f-03f2-4555-8eeb-fda7e0080e67
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f7ac10e62c1c982f1b2357fcaea17b6b54865dec
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49872069"
---
# <a name="adding-tier-interaction-data-from-the-command-line"></a>Hinzufügen von Ebeneninteraktionsdaten über die Befehlszeile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Profilerstellung für Ebeneninteraktion stellt weitere Informationen zu den Ausführungszeiten der [!INCLUDE[vstecado](../includes/vstecado-md.md)]-Aufrufe von Anwendungen mit mehreren Ebenen, die mit einer oder mehreren Datenbanken kommunizieren.  
  
 **Windows 8 und Windows Server 2012**  
  
 Um Ebeneninteraktionsdaten für Windows 8-Desktop-Apps und Windows Server 2012-Apps zu erfassen, müssen Sie die Instrumentierungsmethode verwenden. Das Erfassen von Ebeneninteraktionsdaten in Windows Store-Apps wird nicht unterstützt.  
  
 **Visual Studio-Editionen**  
  
 Profilerstellungsdaten für die Ebeneninteraktion können mit [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] oder [!INCLUDE[vs_pro_current_short](../includes/vs-pro-current-short-md.md)] erfasst werden. Allerdings können Profilerstellungsdaten für die Ebeneninteraktion nur in [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] und [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] angezeigt werden.  
  
 **Sammeln von TIP-Daten auf einem Remotecomputer**  
  
 Um Ebeneninteraktionsdaten auf einem Remotecomputer zu sammeln, müssen Sie kopieren die **Vs\_Profiler\_**_\<Plattform >_ **\_**  _\<Sprache >_**.exe** -Datei aus dem _%VSInstallDir%_**\Team Tools\Performance Tools\Setups**Ordner eines Visual Studio-Computers auf dem Remotecomputer und installieren Sie es. Sie können nicht die Profilerstellungstools im Downloadpaket der [Visual Studio-Remotetools](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) verwenden.  
  
 **TIP-Berichte**  
  
 Ebeneninteraktionsdaten können nur in der [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)]-IDE angezeigt werden. Dateibasierte Ebeneninteraktionsberichte über [VSPerfReport](../profiling/vsperfreport.md) sind nicht verfügbar.  
  
## <a name="adding-tier-interaction-data-with-vsperfcmd"></a>Hinzufügen von Ebeneninteraktionsdaten mit VSPerfCmd  
 Mit dem Befehlszeilentool VSPerfASPNETCmd können Sie auf die vollständige, im Profilerstellungstool verfügbare Funktionalität zugreifen. Sie können den mit VSPerfCmd erfassten Profilerstellungsdaten Interaktionsebene hinzufügen, indem Sie das Hilfsprogramm **VSPerfCLREnv** verwenden, um Umgebungsvariablen festzulegen oder zu entfernen. Dieses Programm aktiviert Ebeneninteraktionsdaten. Die von Ihnen vorgenommenen Optionen und die für das Erfassen von Daten erforderlichen Prozeduren sind von der Art der Anwendung, für die Sie gerade ein Profil erstellen, abhängig.  
  
### <a name="profiling-stand-alone-applications"></a>Profilerstellung für eigenständige Anwendungen  
 Um Ebeneninteraktionsdaten einer Anwendung hinzuzufügen, die nicht von einem anderen Prozess, wie z.B. einer Windows-Desktopanwendung, die synchrone [!INCLUDE[vstecado](../includes/vstecado-md.md)]-Aufrufe an eine SQLServer-Datenbank durchführt, ausgeführt wird, verwenden Sie die Option **VSPerfClrEnv /InteractionOn**, um Umgebungsvariablen festzulegen, und die Option **VSPerfClrEnv /InteractionOff**, um diese zu entfernen.  
  
 Im folgenden Beispiel wird das Profil mithilfe der Instrumentierungsmethode für eine Windows-Desktopanwendung erstellt und Ebeneninteraktionsdaten werden erfasst.  
  
##### <a name="profiling-a-windows-desktop-application-example"></a>Beispiel für die Profilerstellung einer Windows-Desktopanwendung  
  
1. Öffnen Sie die Eingabeaufforderungsfenster mit Administratorrechten. Klicken Sie auf **Start**, zeigen Sie auf **Alle Programme**, und zeigen Sie dann auf **Zubehör**. Klicken Sie mit der rechten Maustaste auf **Eingabeaufforderung**, und klicken Sie dann auf **Als Administrator ausführen**.  
  
2. Initialisieren Sie die .TIP-Umgebungsvariablen für die .NET-Profilerstellung. Geben Sie folgende Befehle ein:  
  
   ```  
   vsperfclrenv /traceon  
   vsperfclrenv /interactionon  
   ```  
  
3. Starten Sie den Profiler. Geben Sie folgenden Befehl ein:  
  
   ```  
   vsperfcmd /start:trace /output:Desktop_tip.vsp   
   ```  
  
4. Starten Sie die Anwendung mit VSPerfCmd. Geben Sie folgenden Befehl ein:  
  
   ```  
   vsperfcmd /launch:DesktopApp.exe  
   ```  
  
5. Führen Sie die Anwendung aus, um Profilerstellungsdaten zu erfassen; schließen Sie dann die Anwendung wie gewohnt.  
  
6. Löschen Sie die TIP-Umgebungsvariablen. Geben Sie folgenden Befehl ein:  
  
   ```  
   vsperfclrenv /off  
   ```  
  
   Weitere Informationen finden Sie unter [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md).  
  
### <a name="profiling-services"></a>Erstellen von Dienstprofilen  
 Um Dienstprofile, einschließlich [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Anwendungen, zu erstellen,verwenden Sie die Option **VSPerfClrEnv /GlobalInteractionOn**, um Umgebungsvariablen festzulegen, und verwenden Sie die Option **VSPerfClrEnv /GlobalInteractionOff**, um diese zu entfernen.  
  
 Während Sie Dienstprofile erstellen, einschließlich [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Webanwendungen, müssen Sie wahrscheinlich den Computer neu starten, um die Profilerstellung zu aktivieren.  
  
 Im folgenden Beispiel wird mithilfe der Instrumentierungsmethode ein Profil für einen Windows-Dienst erstellt und Ebeneninteraktionsdaten werden erfasst.  
  
##### <a name="profiling-a-windows-service-example"></a>Profilerstellung für einen Windows-Dienst  
  
1. Installieren Sie den Dienst, falls notwendig.  
  
2. Öffnen Sie die Eingabeaufforderungsfenster mit Administratorrechten. Klicken Sie auf **Start**, zeigen Sie auf **Alle Programme**, und zeigen Sie dann auf **Zubehör**. Klicken Sie mit der rechten Maustaste auf **Eingabeaufforderung**, und klicken Sie dann auf **Als Administrator ausführen**.  
  
3. Initialisieren Sie die .NET-Umgebungsvariablen für die Profilerstellung. Geben Sie folgenden Befehl ein:  
  
   ```  
   vsperfclrenv /globaltraceon  
   ```  
  
4. Initialisieren Sie die TIP-Umgebungsvariablen. Geben Sie folgenden Befehl ein:  
  
   ```  
   vsperfclrenv /globalinteractionon  
   ```  
  
5. Starten Sie den Computer neu, damit die Umgebungsvariablen registriert werden.  
  
6. Öffnen Sie die Eingabeaufforderungsfenster mit Administratorrechten.  
  
7. Starten Sie den Profiler. Geben Sie folgenden Befehl ein:  
  
   ```  
   vsperfcmd /start:trace /output:MiddleTier_tip.vsp /user:SYSTEM /crosssession   
   ```  
  
8. Starten Sie den Dienst bei Bedarf.  
  
9. Fügen Sie den Profiler an den Dienst an. Geben Sie folgenden Befehl ein:  
  
    ```  
    vsperfcmd /attach:MiddleTier.exe /output:MyService_tip.vsp /user:SYSTEM /crosssession   
    ```  
  
10. Führen Sie den Dienst aus, und erfassen Sie Profilerstellungsdaten.  
  
11. Beenden der Profilerstellung. Geben Sie folgenden Befehl ein:  
  
     `vsperfcmd /detach`  
  
12. Löschen Sie die Umgebungsvariablen für die .NET- und TIP-Profilerstellung. Geben Sie folgenden Befehl ein:  
  
    ```  
    vsperfclrenv /globaloff  
    ```  
  
13. Starten Sie den Computer neu, damit die gelöschten Umgebungsdaten registriert werden.  
  
    Weitere Informationen finden Sie in einem der folgenden Themen:  
  
    [Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)  
  
    [Erstellen von Dienstprofilen](../profiling/command-line-profiling-of-services.md)  
  
## <a name="adding-tier-interaction-data-with-vsperfaspnetcmd"></a>Hinzufügen von Ebeneninteraktionsdaten mit VSPerfASPNETCmd  
 Mit dem Befehlszeilentool VSPerfASPNETCmd können Sie problemlos Profile für [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Webanwendungen erstellen. Verglichen mit dem Befehlszeilentool **VSPerfCmd** stehen weniger Optionen zur Verfügung, es müssen keine Umgebungsvariablen festgelegt werden, und ein Neustart des Computers ist nicht erforderlich. Die Features von VSPerfASPNETCmd ermöglichen ein besonders einfaches Erfassen von Ebeneninteraktionsdaten.  
  
 Um den Profilerstellungsdaten mithilfe von VSPerfASPNETCmd erfasste Ebeneninteraktionsdaten hinzuzufügen, fügen Sie die Option **/TIP** in die Befehlszeile ein. Sie können z.B. folgende Befehlszeile verwenden, um Ebeneninteraktionsdaten für eine [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Webanwendung mithilfe der Instrumentierungsmethode hinzuzufügen:  
  
```  
vsperfaspnetcmd /tip /trace http://localhost/MyWebApp  
```  
  
 Weitere Informationen zu VSPerfASPNETCmd finden Sie unter [Schnelle Website-Profilerstellung mit VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).




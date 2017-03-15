---
title: "Fehler: Das Debuggen kann auf dem Webserver nicht gestartet werden | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.http"
  - "vwd.nonadmin.error."
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Debugger, Webanwendungsfehler"
  - "Debuggen [Visual Studio], Fehler"
  - "Debuggen von ASP.NET-Webanwendungen, Debuggen kann nicht gestartet werden (Fehler)"
  - "Fehler [Debugger], Debuggen kann nicht gestartet werden"
  - "HTTP-Server, Debuggen eines Fehlers"
  - "IIS, Debuggen von DLLs"
  - "Remotedebuggen, Fehler"
  - "Sicherheit [Debugger], Webanwendungen"
  - "Sicherheitseinstellungen, Überprüfen auf Standardwebsites"
  - "Debuggen kann nicht gestartet werden (Fehler)"
ms.assetid: f62e378a-3a99-4f78-9d97-8bb63a4da181
caps.latest.revision: 31
caps.handback.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Fehler: Das Debuggen kann auf dem Webserver nicht gestartet werden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn Sie versuchen, eine ASP.NET\-Anwendung auf einem Webserver zu debuggen, erhalten Sie möglicherweise folgende Fehlermeldung: „Das Debuggen kann auf dem Webserver nicht gestartet werden“.  
  
 In den meisten Fällen tritt dieser Fehler auf, weil IIS nicht ordnungsgemäß konfiguriert ist.  
  
##  <a name="vxtbshttpservererrorsthingstocheck"></a> Stellen Sie sicher, dass IIS ordnungsgemäß konfiguriert ist.  
 Informationen zur Bereitstellung in IIS 8 mit einer MVC 5\-Anwendung finden Sie unter [Publishing to IIS](https://docs.asp.net/en/latest/publishing/iis.html).  
  
 Informationen zur Bereitstellung in IIS 7.5 finden Sie unter [Remotedebuggen von ASP.NET auf einem Remotecomputer mit IIS 7.5](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).  
  
##  <a name="vxtbshttpservererrorswebapplicationsonremoteservers"></a> Stellen Sie sicher, dass die Visual Studio\-Remotetools installiert sind.  
 Wenn Sie auf einem Remotewebserver versuchen zu debuggen, müssen die Visual Studio\-Remotetools installiert sein. Informationen zum Herunterladen und Installieren der Remotetools finden Sie unter [Remotedebugging](../debugger/remote-debugging.md).  
  
##  <a name="vxtbshttpservererrorsanchor2"></a> Stellen Sie sicher, dass ASP.NET installiert ist.  
 **IIS 8**  
  
 IIS 8: Installieren Sie ASP.NET als Teil von IIS.  
  
1.  Wählen Sie in der Kachel **Server\-Manager** die Option **Dashboard** aus, und klicken Sie auf **Rollen und Features hinzufügen**.  
  
2.  Wählen Sie auf der Seite **Installationstyp** die Option **Rollenbasierte oder featurebasierte Installation** aus, und klicken Sie auf **Weiter**.  
  
3.  Wählen Sie auf der Seite **Zielserver auswählen** die Option **Einen Server aus dem Serverpool auswählen** aus, wählen Sie Ihren Server aus, und klicken Sie auf **Weiter**.  
  
4.  Wählen Sie auf der Seite **Serverrollen auswählen** die Option **Webserver \(IIS\)** aus, und klicken Sie auf **Weiter**.  
  
5.  Klicken Sie auf der Seite **Features auswählen** auf **Weiter**.  
  
6.  Klicken Sie auf der Seite **Webserverrolle \(IIS\)** auf **Weiter**.  
  
7.  Notieren Sie sich auf der Seite **Rollendienste auswählen** die vorab ausgewählten Rollendienste, die standardmäßig installiert werden, erweitern Sie die Knoten **Anwendungsserver** und **.NET Framework 4.5**, und wählen Sie dann **ASP.NET 4.5** aus. \(Wenn Sie .NET 3.5 installiert haben, wählen Sie auch **ASP.NET 3.5** aus.\)  
  
8.  Klicken Sie auf der Seite **Installationsauswahl bestätigen** auf **Installieren**.  
  
9. Vergewissern Sie sich auf der Seite **Installationsstatus**, dass die Installation der Rolle „Webserver \(IIS\)“ und der erforderlichen Rollendienste erfolgreich abgeschlossen wurde, und klicken Sie dann auf **Schließen**.  
  
 **IIS 7.5 und früher**  
  
 IIS 7.5 und früher: Führen Sie in einem Eingabeaufforderungsfenster den folgenden Befehl aus:  
  
```  
systemroot\Microsoft.NET\Framework\ versionNumber \aspnet_regiis -i   
```  
  
## Standardproblembehandlung  
 Mithilfe der folgenden Schritte können Sie sicherstellen, dass Ihre ASP.NET\-Anwendung ordnungsgemäß bereitgestellt wurde.  
  
## Öffnen Sie die localhost\-Seite im Browser.  
 Wenn IIS nicht ordnungsgemäß installiert wurde, sollten Fehler angezeigt werden, wenn Sie `http://localhost` in einem Browser eingeben.  
  
## Öffnen Sie die Webseite im Browser.  
 Starten Sie einen Webbrowser, und geben Sie die URL der Seite ein, die Sie debuggen möchten \(z. B. `http://localhost/MyWebApplication`\). Wenn IIS nicht richtig konfiguriert oder die ASP.NET\-Anwendung nicht ordnungsgemäß bereitgestellt wurde, sollten Fehler angezeigt werden, mit deren Hilfe Sie die Fehler in der IIS\-Konfiguration und der ASP.NET\-Bereitstellung beheben können.  
  
## Erstellen Sie eine einfache ASP.NET\-Anwendung auf dem Server.  
 Erstellen Sie eine einfache ASP.NET\-Anwendung auf dem lokalen Server, und versuchen Sie, diese zu debuggen.  
  
## Beheben Sie Authentifizierungsfehler, wenn Sie nur die IP\-Adresse verwenden  
 Zum Debuggen eines Webservers ist eine NTLM\-Authentifizierung erforderlich. Standardmäßig wird davon ausgegangen, dass IP\-Adressen dem Internet zuzuordnen sind, während die NTLM\-Authentifizierung nicht über das Internet vorgenommen wird. Um dieses Problem zu beheben, können Sie den Namen des Remotecomputers angeben.  
  
##  <a name="vxtbshttpservererrorsmanuallyattaching"></a> Manuelles Anhängen an den Prozess  
 Wenn Sie beim Starten des Debuggens weiterhin eine Fehlermeldung erhalten, sollten Sie versuchen, die Anwendung durch manuelles Anhängen an den Prozess zu debuggen.  
  
-   Starten Sie die Anwendung ohne Debugfunktion. \(Klicken Sie im Menü **Debuggen** auf **Starten ohne Debuggen**.  
  
-   Klicken Sie auf **Debuggen\/An den Prozess anhängen**.  Wenn das Fenster angezeigt wird, aktivieren Sie **Prozesse aller Benutzer anzeigen**.  
  
-   Suchen Sie den entsprechenden Prozess, und hängen Sie die Anwendung an. Bei ASP.NET\-Anwendungen vor MVC 5 ist der Prozess „w3wp.exe“. Informationen zu MVC 5 finden Sie unter [Publishing to IIS](https://docs.asp.net/en/latest/publishing/iis.html).  
  
## Siehe auch  
 [Debuggen von Webanwendungen: Fehler und Problembehandlung](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
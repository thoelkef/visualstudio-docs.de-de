---
title: 'Fehler: Fehler beim Debuggen, da die integrierte Windows-Authentifizierung nicht aktiviert ist | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.webdbg_ntlm_authn_not_enabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
- aspx
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f56cca9fa637efaa66b6dcab4716d4a1900aa61d
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2018
ms.locfileid: "44278644"
---
# <a name="error-debugging-failed-because-integrated-windows-authentication-is-not-enabled"></a>Fehler: Fehler beim Debuggen, da die integrierte Windows-Authentifizierung nicht aktiviert ist
Der Benutzer, der die Debuganforderung gestellt hat, konnte aufgrund eines Authentifizierungsfehlers nicht authentifiziert werden. Dies kann beim Versuch, eine Webanwendung oder einen XML-Webdienst in Einzelschritten auszuführen, auftreten. Eine Ursache dieses Fehlers besteht darin, dass die integrierte Windows-Authentifizierung nicht aktiviert ist. Um sie zu aktivieren, führen Sie die Schritte in "So aktivieren Sie die integrierte Windows-Authentifizierung" aus.  
  
 Wenn Sie die integrierte Windows-Authentifizierung aktiviert haben, und dieser Fehler weiterhin angezeigt wird, ist es möglich, dass dieser Fehler verursacht wird, da **Digest-Authentifizierung für Windows-Domänenserver** aktiviert ist. In diesem Fall sollten Sie sich mit dem Netzwerkadministrator in Verbindung setzen.  
  
### <a name="to-enable-integrated-windows-authentication"></a>So aktivieren Sie die integrierte Windows-Authentifizierung  
  
1.  Melden Sie sich über ein Administratorkonto beim Webserver an.  
  
2.  Klicken Sie auf **starten** , und klicken Sie dann auf **Systemsteuerung**.  
  
3.  In **Systemsteuerung**, doppelklicken Sie auf **Verwaltung**.  
  
4.  Doppelklicken Sie auf **Internetinformationsdienste**.  
  
5.  Klicken Sie auf den Webserverknoten.  
  
     Ein **Websites** Ordner unterhalb des Servernamens wird geöffnet.  
  
6.  Sie können die Authentifizierung für alle Websites oder für einzelne Websites konfigurieren. Zum Konfigurieren der Authentifizierung für alle Websites Maustaste der **Websites** Ordner, und klicken Sie dann auf **Eigenschaften**. Öffnen Sie zum Konfigurieren der Authentifizierung für eine einzelne Website die **Websites** , mit der rechten Maustaste in die gewünschte Website, und klicken Sie dann auf **Eigenschaften**.  
  
     Die **Eigenschaften** Dialogfeld wird angezeigt.  
  
7.  Klicken Sie auf die **Verzeichnissicherheit** Registerkarte.  
  
8.  In der **Steuerung des anonymen Zugriffs und der Authentifizierung** auf **bearbeiten**.  
  
     Die **Authentifizierungsmethoden** Dialogfeld wird angezeigt.  
  
9. Klicken Sie unter **ein authentifizierter Zugriff**Option **integrierte Windows-Authentifizierung**.  
  
10. Klicken Sie auf **OK** schließen die **Authentifizierungsmethoden** Dialogfeld.  
  
11. Klicken Sie auf **OK** schließen die **Eigenschaften** Dialogfeld.  
  
12. Schließen der **Internet Information Services** Fenster.  
  
### <a name="to-enable-integrated-windows-authentication-in-windows-vistaiis-7"></a>So aktivieren Sie die integrierte Windows-Authentifizierung unter Windows Vista/IIS 7  
  
1.  Melden Sie sich über ein Administratorkonto beim Webserver an.  
  
2.  Aktivieren Sie die Windows-Authentifizierung und die IIS6-Verwaltungskompatibilität, wenn diese nicht bereits aktiviert wurden, indem Sie folgende Schritte ausführen:  
  
    1.  Klicken Sie auf **starten**, klicken Sie auf **Systemsteuerung** , und klicken Sie dann auf **Programme**.  
  
    2.  Klicken Sie unter **Programme und Funktionen**, klicken Sie auf **Aktivieren von Windows-Funktionen ein- oder ausschalten**.  
  
         Das Dialogfeld Benutzerzugriffssteuerung wird angezeigt und fordert Ihre Bestätigung zum Fortfahren an.  
  
    3.  Klicken Sie auf **Weiter**.  
  
         Das Dialogfeld Windows-Funktionen wird angezeigt.  
  
    4.  Erweitern Sie in der Liste der Features, die **Internet Information Services** Knoten.  
  
    5.  Klicken Sie unter **Internet Information Services**, erweitern Sie die **WWW-Dienste** Knoten.  
  
    6.  Klicken Sie unter **WWW-Dienste**, klicken Sie auf **Sicherheit**.  
  
    7.  Klicken Sie auf **Windows-Authentifizierung**.  
  
    8.  Klicken Sie unter **Internet Information Services**, erweitern Sie die **Webverwaltungstools** Knoten.  
  
    9. Klicken Sie unter **Webverwaltungstools**, erweitern Sie die **IIS 6-Verwaltungskompatibilität** Knoten, und wählen die **IIS 6-Metabasis und IIS 6-Konfigurationskompatibilität** Kontrollkästchen.  
  
    10. Klicken Sie unter **Webverwaltungstools**Option **IIS-Verwaltungskonsole** , und klicken Sie auf **OK.**  
  
    11. Starten Sie den Computer neu, damit die Änderungen wirksam werden.  
  
3.  Klicken Sie auf **starten** , und klicken Sie auf **Systemsteuerung**.  
  
4.  Klicken Sie auf **klassische Ansicht**, und doppelklicken Sie dann auf **Verwaltung**.  
  
5.  In der **Namen** Spalte, und doppelklicken Sie auf **(Internet Information Services, IIS) Manager**.  
  
6.  In der **Verbindungen** Spalte erweitern Sie den Knoten für Ihren Server.  
  
     Ein **Websites** Ordner unterhalb des Servernamens wird geöffnet.  
  
7.  Erweitern Sie die **Websites** Knoten, und klicken Sie auf der Website für die Sie die integrierte Windows-Authentifizierung aktivieren möchten.  
  
8.  Der Titel des mittleren Bereichs wird in den Namen der ausgewählten Website geändert. In diesem Bereich unter der **IIS** Doppelklicken Sie mit der Überschrift auf **Authentifizierung**.  
  
     Der Titel des Bereichs ändert sich zu **Authentifizierung**.  
  
9. In der **Authentifizierung** Bereich, in der **Namen** Spalte mit der rechten Maustaste **Windows-Authentifizierung** , und klicken Sie dann auf **aktivieren**.  
  
10. Schließen der **(Internet Information Services, IIS) Manager** Fenster.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von Webanwendungen: Fehler und Problembehandlung](../debugger/debugging-web-applications-errors-and-troubleshooting.md)   
 [Microsoft-Digestauthentifizierung](http://go.microsoft.com/fwlink/?LinkId=77938)   
 [Ausführen von Webanwendungen unter Windows Vista mit IIS 7.0- und Visual Studio](https://msdn.microsoft.com/Library/262a82ac-dd0e-4096-86c6-fb463e88be66)
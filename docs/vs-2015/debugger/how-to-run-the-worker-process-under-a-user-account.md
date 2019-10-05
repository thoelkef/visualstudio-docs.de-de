---
title: 'Vorgehensweise: Ausführen des Workerprozesses unter einem Benutzerkonto | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- user accounts, aspnet_wp.exe
- ASP.NET, debugging Web applications
- tools, aspnet_wp.exe
- ASP.NET, tools
- aspnet_wp.exe
ms.assetid: b58e97b1-e62a-4318-aea4-52276ea20735
caps.latest.revision: 35
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ebb8ec1fe10f6fbc5c367cb0ed127e048351b0e4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68157872"
---
# <a name="how-to-run-the-worker-process-under-a-user-account"></a>Vorgehensweise: Ausführen des Workerprozesses unter einem Benutzerkonto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Um Ihren Computer so einzurichten, dass der [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Arbeitsprozess (aspnet_wp.exe oder w3wp.exe) unter einem Benutzerkonto ausgeführt werden kann, führen Sie folgende Schritte aus:  
  
## <a name="procedure"></a>Prozedur  
  
#### <a name="to-run-aspnetwpexe-under-a-user-account"></a>So führen Sie "aspnet_wp.exe" unter einem Benutzerkonto aus  
  
1. Öffnen Sie die Datei machine.config. Sie befindet sich auf dem Computer im Ordner CONFIG und wurde unter demselben Pfad gespeichert, unter dem die Laufzeit installiert wurde.  
  
2. Suchen Sie den Abschnitt &lt;processModel&gt;, und verwenden Sie für die Attribute „user“ und „password“ den Benutzernamen und das Kennwort des Benutzerkontos, unter dem „aspnet_wp.exe“ ausgeführt werden soll.  
  
3. Speichern Sie die Datei machine.config.  
  
4. Unter [!INCLUDE[winxpsvr](../includes/winxpsvr-md.md)] wird IIS 6.0 standardmäßig installiert. Der entsprechende Arbeitsprozess ist "w3wp.exe". Führen Sie folgende Schritte aus, um "aspnet_wp.exe" als Arbeitsprozess im IIS 6.0-Modus auszuführen:  
  
    1. Klicken Sie auf **Start** und dann auf **Verwaltung**. Wählen Sie anschließend **Internetinformationsdienste** aus.  
  
    2. Klicken Sie im Dialogfeld **Internetinformationsdienste** mit der rechten Maustaste auf den Ordner **Web Sites** (Websites), und wählen Sie **Eigenschaften** aus.  
  
    3. Wählen Sie im Dialogfeld **Web Sites Properties**  (Eigenschaften von Websites) die Option **Service** (Dienst) aus.  
  
    4. Wählen Sie **Run WWW service in IIS6.0 isolation mode** (WWW-Dienst im IIS 6.0-Isolationsmodus ausführen) aus.  
  
    5. Schließen Sie das Dialogfeld **Eigenschaften** und den **Internetdienste-Manager**.  
  
5. Öffnen Sie eine Eingabeaufforderung von Windows, und setzen Sie den Server zurück, indem Sie Folgendes ausführen:  
  
    ```  
    iisreset  
    ```  

    \- oder -  
  
    ```  
    net stop iisadmin /y  
    net start w3svc  
    ```  
  
6. Suchen Sie den Ordner Temporary [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Files. Er sollte sich im selben Pfad befinden wie der Ordner CONFIG. Klicken Sie mit der rechten Maustaste auf den Ordner „Temporäre [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Dateien“, und wählen Sie im Kontextmenü die Option **Eigenschaften** aus.  
  
7. Klicken Sie im Dialogfeld **Temporary ASP.NET Files Properties** (Eigenschaften temporärer ASP.NET-Dateien) auf die Registerkarte **Sicherheit**.  
  
8. Klicken Sie auf **Erweitert**.  
  
9. Klicken Sie im Dialogfeld **Advanced Security Settings for Temporary ASP.Net Files** (Erweiterte Sicherheitseinstellungen für temporäre ASP.NET-Dateien) auf **Hinzufügen**.  
  
    Das Dialogfeld **Select User, Computer, or Group** (Benutzer, Computer oder Gruppen auswählen) wird angezeigt.  
  
10. Geben Sie den Benutzernamen in das Feld **Namen des auszuwählenden Objekts eingeben** ein, und klicken Sie auf **OK**. Der Benutzername muss das folgende Format aufweisen: Domänenname\benutzername.  
  
11. Gewähren Sie dem Benutzer im Dialogfeld **Permission Entry for Temporary ASP.NET Files** (Berechtigungseintrag für temporäre ASP.NET-Dateien) **Full Control** (Vollzugriff), und klicken Sie dann auf **OK**, um das Dialogfeld **Entry for Temporary ASP.NET Files** (Eintrag für temporäre ASP.NET-Dateien) zu schließen.  
  
12. Das Dialogfeld **Sicherheit** wird angezeigt, und Sie werden gefragt, ob Sie wirklich die Berechtigungen für einen Systemordner ändern möchten. Klicken Sie auf **Ja**.  
  
13. Klicken Sie auf **OK**, um das Dialogfeld **Temporary ASP.NET Files Properties** (Eigenschaften temporärer ASP.NET-Dateien) zu schließen.  
  
## <a name="see-also"></a>Siehe auch  
[ASP.NET-Debugging: Systemanforderungen](../debugger/aspnet-debugging-system-requirements.md)  

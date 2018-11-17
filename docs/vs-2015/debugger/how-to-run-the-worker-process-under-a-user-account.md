---
title: 'Vorgehensweise: Ausführen des Workerprozesses unter einem Benutzerkonto | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: d5d9e9cbadd2b7154eeb84bad99239e0b026eecd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51734459"
---
# <a name="how-to-run-the-worker-process-under-a-user-account"></a>Gewusst wie: Ausführen des Workerprozesses unter einem Benutzerkonto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Um Ihren Computer so einzurichten, dass der [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Arbeitsprozess (aspnet_wp.exe oder w3wp.exe) unter einem Benutzerkonto ausgeführt werden kann, führen Sie folgende Schritte aus:  
  
## <a name="procedure"></a>Prozedur  
  
#### <a name="to-run-aspnetwpexe-under-a-user-account"></a>So führen Sie "aspnet_wp.exe" unter einem Benutzerkonto aus  
  
1.  Öffnen Sie die Datei machine.config. Sie befindet sich auf dem Computer im Ordner CONFIG und wurde unter demselben Pfad gespeichert, unter dem die Laufzeit installiert wurde.  
  
2.  Suchen der &lt;ProcessModel&gt; Abschnitt, und ändern Sie die Attribute für Benutzernamen und Kennwort des mit dem Namen und das Kennwort des Benutzerkontos aspnet_wp.exe unter ausgeführt werden soll.  
  
3.  Speichern Sie die Datei machine.config.  
  
4.  Unter [!INCLUDE[winxpsvr](../includes/winxpsvr-md.md)] wird IIS 6.0 standardmäßig installiert. Der entsprechende Arbeitsprozess ist "w3wp.exe". Führen Sie folgende Schritte aus, um "aspnet_wp.exe" als Arbeitsprozess im IIS 6.0-Modus auszuführen:  
  
    1.  Klicken Sie auf **starten**, klicken Sie auf **Verwaltung** und wählen Sie dann **Internet Information Services**.  
  
    2.  In der **Internet Information Services** im Dialogfeld mit der rechten Maustaste die **Websites** Ordner, und wählen Sie **Eigenschaften**.  
  
    3.  In der **Websiteeigenschaften** Dialogfeld wählen **Service**.  
  
    4.  Wählen Sie **ausführen WWW-Dienst in IIS 6.0-Isolationsmodus**.  
  
    5.  Schließen der **Eigenschaften** Dialogfeld und **Internetdienste-Manager**.  
  
5.  Öffnen Sie eine Eingabeaufforderung von Windows, und setzen Sie den Server zurück, indem Sie Folgendes ausführen:  
  
    ```  
    iisreset  
    ```  
    - oder -  
  
    ```  
    net stop iisadmin /y  
    net start w3svc  
    ```  
  
6.  Suchen Sie den Ordner Temporary [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Files. Er sollte sich im selben Pfad befinden wie der Ordner CONFIG. Mit der rechten Maustaste in des temporäres [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Ordner für Aktualisierungsdateien, und wählen Sie **Eigenschaften** im Kontextmenü auf.  
  
7.  In der **Eigenschaften von Temporary ASP.NET Files** Dialogfeld klicken Sie auf die **Sicherheit** Registerkarte.  
  
8.  Klicken Sie auf **erweiterte**.  
  
9. In der **erweiterte Sicherheitseinstellungen für Temporary ASP.Net Files** Dialogfeld klicken Sie auf **hinzufügen**.  
  
    Die **im Dialogfeld Benutzer, Computer oder Gruppe** angezeigt wird.  
  
10. Geben Sie den Benutzernamen in der **Geben Sie den zu verwendenden Objektnamen** ein, und klicken Sie dann auf **OK**. Der Benutzername muss folgendes Format aufweisen: Domänenname\Benutzername.  
  
11. In der **Berechtigungseintrag für temporäre ASP.NET-Dateien** Dialogfeld gewähren Sie den Benutzer **Vollzugriff**, und klicken Sie dann auf **OK** zu schließen die **Eintrag für temporäre ASP .NET Dateien** Dialogfeld.  
  
12. Ein **Sicherheit** Dialogfeld wird angezeigt, und fragt, ob Sie wirklich die Berechtigungen für einen Systemordner ändern möchten. Klicken Sie auf **Ja**.  
  
13. Klicken Sie auf **OK** schließen die **Eigenschaften von Temporary ASP.NET Files** Dialogfeld.  
  
## <a name="see-also"></a>Siehe auch  
[ASP.NET-Debugging: Systemanforderungen](../debugger/aspnet-debugging-system-requirements.md)  
  





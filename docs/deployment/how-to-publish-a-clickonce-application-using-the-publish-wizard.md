---
title: 'Vorgehensweise: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, publishing
- deploying applications [ClickOnce], Publish wizard
- Windows applications, ClickOnce deployments
- publishing, ClickOnce
ms.assetid: 2e4aa67c-4445-4f7b-9e03-9acb95829127
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 762ef9813232b282b4f140e9c01e8d722a42bf3d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-publish-a-clickonce-application-using-the-publish-wizard"></a>Gewusst wie: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten
Wenn Sie eine ClickOnce-Anwendung für Benutzer bereitstellen möchten, müssen Sie sie auf einer Dateifreigabe oder unter einem Dateipfad, auf einem FTP-Server oder einem Wechselmedium veröffentlichen. Sie können die Anwendung mit dem Webpublishing-Assistenten veröffentlichen; zusätzliche Eigenschaften, die im Zusammenhang mit der Veröffentlichung stehen für die **veröffentlichen** auf der Seite der **Projekt-Designer**. Weitere Informationen finden Sie unter [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md).  
  
 Bevor Sie den Webpublishing-Assistenten ausführen, sollten Sie die Veröffentlichungseigenschaften entsprechend festlegen. Z. B. Wenn Sie einen Schlüssel zum Signieren der ClickOnce-Anwendung angeben möchten, können Sie dies also auf die **Signierung** auf der Seite der **Projekt-Designer**. Weitere Informationen finden Sie unter [Sichern von ClickOnce-Anwendungen](../deployment/securing-clickonce-applications.md).  
  
> [!NOTE]
>  Wenn Sie mit ClickOnce mehrere Versionen einer Anwendung installieren, verschiebt die Installation ältere Versionen der Anwendung in einen Ordner mit dem Namen Archiv in dem von Ihnen angegebenen Veröffentlichungsort. Durch dieses Archivieren älterer Versionen wird sichergestellt, dass im Installationsverzeichnis keine Ordner älterer Versionen verbleiben.  
  
> [!NOTE]
>  Die angezeigten Dialogfelder und Menübefehle können sich je nach den aktiven Einstellungen oder der verwendeten Version von den in der Hilfe beschriebenen unterscheiden. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-publish-to-a-file-share-or-path"></a>So veröffentlichen Sie auf einer Dateifreigabe oder unter einem Pfad  
  
1.  In **Projektmappen-Explorer**, wählen Sie das Anwendungsprojekt.  
  
2.  Auf der **erstellen** Menü klicken Sie auf **veröffentlichen**`Projectname`.  
  
     Der Webpublishing-Assistent wird angezeigt.  
  
3.  In der **Wo möchten Sie die Anwendung veröffentlichen?** Seite Geben Sie eine gültige FTP-Server-Adresse oder einen gültigen Dateipfad mithilfe eines der gezeigten Formate, und klicken Sie dann auf **Weiter**.  
  
4.  In der **wie Benutzer die Anwendung installiert?** Seite, wählen Sie den Speicherort, in dem Benutzer werden zur Installation der Anwendung:  
  
    -   Wenn Benutzer von einer Website installieren, klicken Sie auf **von einer Website** , und geben Sie eine URL, entspricht der im vorherigen Schritt eingegebenen Dateipfad. Klicken Sie auf **Weiter**. (Diese Option wird normalerweise verwendet, wenn eine FTP-Adresse als Veröffentlichungsort angegeben werden soll. Der direkte Download per FTP wird nicht unterstützt. Daher müssen Sie hier eine URL eingeben.)  
  
    -   Wenn Benutzer die Anwendung direkt von der Dateifreigabe installieren, klicken Sie auf **von UNC-Pfad oder Dateifreigabe**, und klicken Sie dann auf **Weiter**. (Dies ist für die Veröffentlichung von Standorten, von dem Format c:\deploy\myapp oder \\\server\myapp.)  
  
    -   Wenn Benutzer von Wechselmedien installieren, klicken Sie auf **von CD-ROM oder DVD-ROM**, und klicken Sie dann auf **Weiter**.  
  
5.  Auf der **wird die Anwendung offline verfügbar sein?** Seite, klicken Sie auf die entsprechende Option:  
  
    -   Aktivieren Sie die Anwendung ausgeführt werden sollen. wenn der Benutzer wird vom Netzwerk getrennt, klicken Sie auf **Ja, diese Anwendung stehen dann online oder offline**. Eine Verknüpfung auf der **starten** Menü für die Anwendung erstellt werden.  
  
    -   Wenn Sie die Anwendung direkt vom Ort Veröffentlichung ausführen möchten, klicken Sie auf **Nein, diese Anwendung ist nur online verfügbar**. Eine Verknüpfung auf der **starten** Menü wird nicht erstellt werden.  
  
     Klicken Sie auf **Weiter**, um fortzufahren.  
  
6.  Klicken Sie auf **Fertig stellen** veröffentlichen die Anwendung.  
  
     Der Veröffentlichungsstatus wird im Statusinfobereich angezeigt.  
  
### <a name="to-publish-to-a-cd-rom-or-dvd-rom"></a>So veröffentlichen Sie auf einer CD-ROM oder DVD-ROM  
  
1.  In **Projektmappen-Explorer**mit der rechten Maustaste auf das Anwendungsprojekt, und klicken Sie auf **Eigenschaften**.  
  
     Der **Projekt-Designer** wird angezeigt.  
  
2.  Klicken Sie auf die **veröffentlichen** Registerkarte Öffnen der **veröffentlichen** auf der Seite der **Projekt-Designer**, und klicken Sie auf die **Veröffentlichungs-Assistenten** Schaltfläche.  
  
     Der Webpublishing-Assistent wird angezeigt.  
  
3.  In der **Wo möchten Sie die Anwendung veröffentlichen?** Seite, geben Sie den Dateipfad oder den FTP-Speicherort, in dem die Anwendung veröffentlicht, d:\deploy. Klicken Sie dann auf **Weiter** um den Vorgang fortzusetzen.  
  
4.  Auf der **wie Benutzer die Anwendung installiert?** Seite, klicken Sie auf eine **CD-ROM oder DVD-ROM**, und klicken Sie dann auf **Weiter**.  
  
    > [!NOTE]
    >  Wenn Sie die Installation automatisch ausgeführt werden soll bei der CD-ROM-eingefügt wird das Laufwerk, öffnen die **veröffentlichen** auf der Seite der **Projekt-Designer** , und klicken Sie auf die **Optionen** Schaltfläche, und klicken Sie dann in der **Veröffentlichungsoptionen** Assistenten **für CD-Installationen automatisch Setup starten, wenn CD eingelegt wird**.  
  
5.  Wenn Sie Ihre Anwendung auf einer CD-ROM veröffentlichen, können Sie dennoch Updates auf einer Website zur Verfügung stellen. In der **wird, in dem die Anwendung nach Updates suchen.?** Seite, und wählen Sie eine Aktualisierungsoption aus:  
  
    -   Wenn die Anwendung nach Updates sucht, klicken Sie auf **der Anwendung überprüft folgenden Speicherort auf Updates** und geben Sie den Speicherort, in denen Updates veröffentlicht werden. Der Speicherort kann ein Dateipfad, eine Website oder ein FTP-Server sein.  
  
    -   Wenn die Anwendung nicht nach Updates sucht, klicken Sie auf **die Anwendung wird nicht nach Updates suchen**.  
  
     Klicken Sie auf **Weiter**, um fortzufahren.  
  
6.  Klicken Sie auf **Fertig stellen** veröffentlichen die Anwendung.  
  
     Der Veröffentlichungsstatus wird im Statusinfobereich angezeigt.  
  
    > [!NOTE]
    >  Wenn die Veröffentlichung abgeschlossen ist, benötigen Sie einen CD-Rekorder oder einen DVD-Rekorder, um die Dateien von dem in Schritt 3 angegebenen Speicherort auf CD-ROM oder DVD-ROM zu kopieren.  
  
## <a name="see-also"></a>Siehe auch  
 [ClickOnce-Sicherheit und -Bereitstellung](../deployment/clickonce-security-and-deployment.md)   
 [Sichern von ClickOnce-Anwendungen](../deployment/securing-clickonce-applications.md)   
 [Bereitstellen einer Office-Projektmappe mithilfe von ClickOnce](/office-dev/office-dev/deploying-an-office-solution-by-using-clickonce)
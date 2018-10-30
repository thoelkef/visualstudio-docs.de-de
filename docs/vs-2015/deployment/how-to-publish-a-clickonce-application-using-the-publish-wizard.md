---
title: 'Gewusst wie: Veröffentlichen einer ClickOnce-Anwendung, die mit dem Webpublishing-Assistenten | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: f8708658e5daf90e24a0336040ba2b766d5ae975
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49862826"
---
# <a name="how-to-publish-a-clickonce-application-using-the-publish-wizard"></a>Gewusst wie: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie eine ClickOnce-Anwendung für Benutzer bereitstellen möchten, müssen Sie sie auf einer Dateifreigabe oder unter einem Dateipfad, auf einem FTP-Server oder einem Wechselmedium veröffentlichen. Sie können die Anwendung veröffentlichen, mit dem Webpublishing-Assistenten. zusätzliche Eigenschaften, die im Zusammenhang mit der Veröffentlichung stehen für die **veröffentlichen** auf der Seite die **Projekt-Designer**. Weitere Informationen finden Sie unter [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md).  
  
 Bevor Sie den Webpublishing-Assistenten ausführen, sollten Sie die Veröffentlichungseigenschaften entsprechend festlegen. Z. B. Wenn Sie einen Schlüssel zum Signieren der ClickOnce-Anwendung angeben möchten, erreichen Sie so die **Signierung** auf der Seite die **Projekt-Designer**. Weitere Informationen finden Sie unter [Sichern von ClickOnce-Anwendungen](../deployment/securing-clickonce-applications.md).  
  
> [!NOTE]
>  Wenn Sie mit ClickOnce mehrere Versionen einer Anwendung installieren, verschiebt die Installation ältere Versionen der Anwendung in einen Ordner mit dem Namen Archiv in dem von Ihnen angegebenen Veröffentlichungsort. Durch dieses Archivieren älterer Versionen wird sichergestellt, dass im Installationsverzeichnis keine Ordner älterer Versionen verbleiben.  
  
> [!NOTE]
>  Die angezeigten Dialogfelder und Menübefehle können sich je nach den aktiven Einstellungen oder der verwendeten Version von den in der Hilfe beschriebenen unterscheiden. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-publish-to-a-file-share-or-path"></a>So veröffentlichen Sie auf einer Dateifreigabe oder unter einem Pfad  
  
1. In **Projektmappen-Explorer**, wählen Sie das Anwendungsprojekt.  
  
2. Auf der **erstellen** Menü klicken Sie auf **veröffentlichen**`Projectname`.  
  
    Der Webpublishing-Assistent wird angezeigt.  
  
3. In der **Wo möchten Sie die Anwendung veröffentlichen?** Seite Geben Sie eine gültige FTP-Serveradresse oder einen gültigen Dateipfad mithilfe eines der gezeigten Formate, und klicken Sie dann auf **Weiter**.  
  
4. In der **wie werden Benutzer die Anwendung installieren?** Seite, wählen Sie den Speicherort, in denen Benutzer aufrufen, die um die Anwendung zu installieren:  
  
   -   Wenn der Benutzer auf einer Website installieren, klicken Sie auf **von einer Website** , und geben Sie eine URL, entspricht der im vorherigen Schritt eingegebenen Dateipfad. Klicken Sie auf **Weiter**. (Diese Option wird normalerweise verwendet, wenn eine FTP-Adresse als Veröffentlichungsort angegeben werden soll. Der direkte Download per FTP wird nicht unterstützt. Daher müssen Sie hier eine URL eingeben.)  
  
   -   Wenn der Benutzer die Anwendung direkt von der Dateifreigabe installieren, klicken Sie auf **von UNC-Pfad oder Dateifreigabe**, und klicken Sie dann auf **Weiter**. (Dies ist für die Veröffentlichung von Standorten, von dem Format c:\deploy\myapp oder \\\server\myapp.)  
  
   -   Wenn der Benutzer von Wechselmedien installieren, klicken Sie auf **von CD-ROM oder DVD-ROM**, und klicken Sie dann auf **Weiter**.  
  
5. Auf der **wird die Anwendung offline verfügbar sein?** klicken Sie auf die entsprechende Option:  
  
   - Sollten Sie die Anwendung ausgeführt werden kann bei der Benutzer wird getrennt vom Netzwerk aus, klicken Sie auf **Ja, diese Anwendung stehen online oder offline**. Eine Verknüpfung auf die **starten** Menü für die Anwendung erstellt werden.  
  
   - Wenn Sie die Anwendung direkt vom Ort Veröffentlichung ausführen möchten, klicken Sie auf **Nein, diese Anwendung ist nur online verfügbar**. Eine Verknüpfung auf die **starten** Menü wird nicht erstellt werden.  
  
     Klicken Sie auf **Weiter**, um fortzufahren.  
  
6. Klicken Sie auf **Fertig stellen** zum Veröffentlichen der Anwendung.  
  
    Der Veröffentlichungsstatus wird im Statusinfobereich angezeigt.  
  
### <a name="to-publish-to-a-cd-rom-or-dvd-rom"></a>So veröffentlichen Sie auf einer CD-ROM oder DVD-ROM  
  
1. In **Projektmappen-Explorer**mit der rechten Maustaste auf das Anwendungsprojekt, und klicken Sie auf **Eigenschaften**.  
  
    Der **Projekt-Designer** wird angezeigt.  
  
2. Klicken Sie auf die **veröffentlichen** Registerkarte Öffnen der **veröffentlichen** auf der Seite die **Projekt-Designer**, und klicken Sie auf die **Veröffentlichungs-Assistenten** Schaltfläche.  
  
    Der Webpublishing-Assistent wird angezeigt.  
  
3. In der **Wo möchten Sie die Anwendung veröffentlichen?** Seite, geben Sie den Dateipfad oder den FTP-Speicherort, in dem die Anwendung veröffentlicht werden, d:\deploy. Klicken Sie dann auf **Weiter** um den Vorgang fortzusetzen.  
  
4. Auf der **wie werden Benutzer die Anwendung installieren?** Seite, klicken Sie auf eine **CD-ROM oder DVD-ROM-**, und klicken Sie dann auf **Weiter**.  
  
   > [!NOTE]
   >  Wenn die Installation automatisch ausgeführt werden sollen beim die CD-ROM einfügen in das Laufwerk, das Öffnen der **veröffentlichen** auf der Seite die **Projekt-Designer** , und klicken Sie auf die **Optionen** Schaltfläche, und klicken Sie dann in der **Veröffentlichungsoptionen** Assistenten **für CD-Installationen automatisch Setup starten, wenn CD eingelegt wird**.  
  
5. Wenn Sie Ihre Anwendung auf einer CD-ROM veröffentlichen, können Sie dennoch Updates auf einer Website zur Verfügung stellen. In der **, in dem die Anwendung sucht nach Updates?** Seite, wählen Sie eine Updateoption:  
  
   - Wenn die Anwendung nach Updates suchen soll, klicken Sie auf **der Anwendung überprüft folgenden Speicherort auf Updates** und geben Sie den Speicherort, in denen Updates veröffentlicht werden. Der Speicherort kann ein Dateipfad, eine Website oder ein FTP-Server sein.  
  
   - Wenn die Anwendung nicht nach Updates suchen soll, klicken Sie auf **die Anwendung wird nicht nach Updates suchen**.  
  
     Klicken Sie auf **Weiter**, um fortzufahren.  
  
6. Klicken Sie auf **Fertig stellen** zum Veröffentlichen der Anwendung.  
  
    Der Veröffentlichungsstatus wird im Statusinfobereich angezeigt.  
  
   > [!NOTE]
   >  Wenn die Veröffentlichung abgeschlossen ist, benötigen Sie einen CD-Rekorder oder einen DVD-Rekorder, um die Dateien von dem in Schritt 3 angegebenen Speicherort auf CD-ROM oder DVD-ROM zu kopieren.  
  
## <a name="see-also"></a>Siehe auch  
 [ClickOnce-Sicherheit und -Bereitstellung](../deployment/clickonce-security-and-deployment.md)   
 [Sichern von ClickOnce-Anwendungen](../deployment/securing-clickonce-applications.md)   
 [Bereitstellen einer Office-Projektmappe mithilfe von ClickOnce](http://msdn.microsoft.com/library/feb516b3-5e4d-449a-9fd2-347d08d90252)




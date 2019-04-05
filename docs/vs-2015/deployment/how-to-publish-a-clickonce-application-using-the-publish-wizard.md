---
title: 'Vorgehensweise: Veröffentlichen einer ClickOnce-Anwendung, die mit dem Webpublishing-Assistenten | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 45ca2bd23c6da7d86b65cc05c0b0dee670e2718f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58958084"
---
# <a name="how-to-publish-a-clickonce-application-using-the-publish-wizard"></a>Vorgehensweise: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie eine ClickOnce-Anwendung für Benutzer bereitstellen möchten, müssen Sie sie auf einer Dateifreigabe oder unter einem Dateipfad, auf einem FTP-Server oder einem Wechselmedium veröffentlichen. Sie können die Anwendung mit dem Veröffentlichungs-Assistenten veröffentlichen. Für die Veröffentlichung stehen im **Projekt-Designer** auf der Seite **Veröffentlichen** zusätzliche Eigenschaften zur Verfügung. Weitere Informationen finden Sie unter [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md).  
  
 Bevor Sie den Webpublishing-Assistenten ausführen, sollten Sie die Veröffentlichungseigenschaften entsprechend festlegen. Wenn Sie z.B. einen Schlüssel zum Signieren der ClickOnce-Anwendung angeben möchten, können Sie dies im **Projekt-Designer** auf der Seite **Signierung** vornehmen. Weitere Informationen finden Sie unter [Sichern von ClickOnce-Anwendungen](../deployment/securing-clickonce-applications.md).  
  
> [!NOTE]
>  Wenn Sie mit ClickOnce mehrere Versionen einer Anwendung installieren, verschiebt die Installation ältere Versionen der Anwendung in einen Ordner mit dem Namen Archiv in dem von Ihnen angegebenen Veröffentlichungsort. Durch dieses Archivieren älterer Versionen wird sichergestellt, dass im Installationsverzeichnis keine Ordner älterer Versionen verbleiben.  
  
> [!NOTE]
>  Die angezeigten Dialogfelder und Menübefehle können sich je nach den aktiven Einstellungen oder der verwendeten Version von den in der Hilfe beschriebenen unterscheiden. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-publish-to-a-file-share-or-path"></a>So veröffentlichen Sie auf einer Dateifreigabe oder unter einem Pfad  
  
1. Wählen Sie im **Projektmappen-Explorer** das Anwendungsprojekt aus.  
  
2. Auf der **erstellen** Menü klicken Sie auf **veröffentlichen**`Projectname`.  
  
    Der Webpublishing-Assistent wird angezeigt.  
  
3. Geben Sie auf der Seite **Wo möchten Sie die Anwendung veröffentlichen?** eine gültige FTP-Server-Adresse oder einen gültigen Dateipfad mithilfe eines der gezeigten Formate ein, und klicken Sie dann auf **Weiter**.  
  
4. Wählen Sie auf der Seite **Wie werden Benutzer die Anwendung installieren?** den Speicherort aus, auf den Benutzer beim Installieren der Anwendung zugreifen:  
  
   -   Wenn die Installation über eine Website durchgeführt werden soll, klicken Sie auf **Von einer Website**, und geben Sie eine URL ein, die dem im vorherigen Schritt eingegebenen Dateipfad entspricht. Klicken Sie auf **Weiter**. (Diese Option wird normalerweise verwendet, wenn eine FTP-Adresse als Veröffentlichungsort angegeben werden soll. Der direkte Download per FTP wird nicht unterstützt. Daher müssen Sie hier eine URL eingeben.)  
  
   -   Wenn die Installation direkt über die Dateifreigabe durchgeführt werden soll, klicken Sie auf **Von UNC-Pfad oder Dateifreigabe**, und klicken Sie dann auf **Weiter**. (Dies ist für die Veröffentlichung von Standorten, von dem Format c:\deploy\myapp oder \\\server\myapp.)  
  
   -   Wenn die Installation über Wechselmedien durchgeführt werden soll, klicken Sie auf **Von CD-ROM oder DVD-ROM**, und klicken Sie dann auf **Weiter**.  
  
5. Wählen Sie auf der Seite **Wird die Anwendung offline verfügbar sein?** die gewünschte Option aus:  
  
   - Falls die Anwendung auch ausgeführt werden soll, wenn der Benutzer vom Netzwerk getrennt ist, klicken Sie auf **Yes, this application will be available online or offline** (Ja, diese Anwendung ist online und offline verfügbar). Im **Startmenü** wird eine Verknüpfung für die Anwendung erstellt.  
  
   - Wenn die Anwendung direkt vom Ort der Veröffentlichung gestartet werden soll, klicken Sie auf **Nein, diese Anwendung ist nur online verfügbar.** Es wird keine Verknüpfung im **Startmenü** erstellt.  
  
     Klicken Sie auf **Weiter**, um fortzufahren.  
  
6. Klicken Sie auf **Fertig stellen**, um die Anwendung zu veröffentlichen.  
  
    Der Veröffentlichungsstatus wird im Statusinfobereich angezeigt.  
  
### <a name="to-publish-to-a-cd-rom-or-dvd-rom"></a>So veröffentlichen Sie auf einer CD-ROM oder DVD-ROM  
  
1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Anwendungsprojekt, und klicken Sie dann auf **Eigenschaften**.  
  
    Der **Projekt-Designer** wird angezeigt.  
  
2. Klicken Sie auf die Registerkarte **Veröffentlichen**, um im **Projekt-Designer** die Seite **Veröffentlichen** zu öffnen, und klicken Sie auf die Schaltfläche **Veröffentlichungs-Assistent**.  
  
    Der Webpublishing-Assistent wird angezeigt.  
  
3. In der **Wo möchten Sie die Anwendung veröffentlichen?** Seite, geben Sie den Dateipfad oder den FTP-Speicherort, in dem die Anwendung veröffentlicht werden, d:\deploy. Klicken Sie dann zum Fortfahren auf **Weiter**.  
  
4. Klicken Sie auf der Seite **Wie werden Benutzer die Anwendung installieren?** auf **Von CD-ROM oder DVD-ROM**, und klicken Sie dann auf **Weiter**.  
  
   > [!NOTE]
   >  Falls Sie die Installation ausgeführt werden soll, wenn die CD-ROM in das Laufwerk eingelegt wird, öffnen Sie im **Projekt-Designer** die Seite **Veröffentlichen** und klicken auf die Schaltfläche **Optionen**. Wählen Sie in den **Veröffentlichungsoptionen** des Assistenten dann die Option **Bei CD-Installationen automatisch Setup starten, wenn CD eingelegt wird** aus.  
  
5. Wenn Sie Ihre Anwendung auf einer CD-ROM veröffentlichen, können Sie dennoch Updates auf einer Website zur Verfügung stellen. Wählen Sie auf der Seite **Die Anwendung überprüft folgenden Speicherort auf Updates** eine Updateoption aus:  
  
   - Wenn die Anwendung nach Updates sucht, klicken Sie auf **Die Anwendung überprüft folgenden Speicherort auf Updates** und geben den Speicherort ein, an dem Updates veröffentlicht werden. Der Speicherort kann ein Dateipfad, eine Website oder ein FTP-Server sein.  
  
   - Wenn die Anwendung nicht nach Updates sucht, klicken Sie auf **Anwendung sucht nicht nach Updates**.  
  
     Klicken Sie auf **Weiter**, um fortzufahren.  
  
6. Klicken Sie auf **Fertig stellen**, um die Anwendung zu veröffentlichen.  
  
    Der Veröffentlichungsstatus wird im Statusinfobereich angezeigt.  
  
   > [!NOTE]
   >  Wenn die Veröffentlichung abgeschlossen ist, benötigen Sie einen CD-Rekorder oder einen DVD-Rekorder, um die Dateien von dem in Schritt 3 angegebenen Speicherort auf CD-ROM oder DVD-ROM zu kopieren.  
  
## <a name="see-also"></a>Siehe auch  
 [ClickOnce-Sicherheit und -Bereitstellung](../deployment/clickonce-security-and-deployment.md)   
 [Sichern von ClickOnce-Anwendungen](../deployment/securing-clickonce-applications.md)   
 [Bereitstellen einer Office-Projektmappe mithilfe von ClickOnce](http://msdn.microsoft.com/library/feb516b3-5e4d-449a-9fd2-347d08d90252)

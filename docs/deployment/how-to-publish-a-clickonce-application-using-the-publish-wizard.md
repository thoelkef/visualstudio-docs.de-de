---
title: "How to: Publish a ClickOnce Application using the Publish Wizard | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce deployment, publishing"
  - "deploying applications [ClickOnce], Publish wizard"
  - "Windows applications, ClickOnce deployments"
  - "publishing, ClickOnce"
ms.assetid: 2e4aa67c-4445-4f7b-9e03-9acb95829127
caps.latest.revision: 25
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 25
---
# How to: Publish a ClickOnce Application using the Publish Wizard
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn Sie eine ClickOnce\-Anwendung für Benutzer bereitstellen möchten, müssen Sie sie auf einer Dateifreigabe oder unter einem Dateipfad, auf einem FTP\-Server oder einem Wechselmedium veröffentlichen.  Sie können die Anwendung mit dem Webpublishing\-Assistenten veröffentlichen. Für die Veröffentlichung stehen im **Projekt\-Designer** auf der Seite **Veröffentlichen** zusätzliche Eigenschaften zur Verfügung.  Weitere Informationen finden Sie unter [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md).  
  
 Bevor Sie den Webpublishing\-Assistenten ausführen, sollten Sie die Veröffentlichungseigenschaften entsprechend festlegen.  Wenn Sie z. B. einen Schlüssel zum Signieren der ClickOnce\-Anwendung angeben möchten, können Sie dies im **Projekt\-Designer** auf der Seite **Signierung** vornehmen.  Weitere Informationen finden Sie unter [Sichern von ClickOnce\-Anwendungen](../deployment/securing-clickonce-applications.md).  
  
> [!NOTE]
>  Wenn Sie mit ClickOnce mehrere Versionen einer Anwendung installieren, verschiebt die Installation ältere Versionen der Anwendung in einen Ordner mit dem Namen Archiv in dem von Ihnen angegebenen Veröffentlichungsort.  Durch dieses Archivieren älterer Versionen wird sichergestellt, dass im Installationsverzeichnis keine Ordner älterer Versionen verbleiben.  
  
> [!NOTE]
>  Die angezeigten Dialogfelder und Menübefehle können sich je nach den aktiven Einstellungen oder der verwendeten Version von den in der Hilfe beschriebenen unterscheiden.  Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren**, um die Einstellungen zu ändern.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### So veröffentlichen Sie auf einer Dateifreigabe oder unter einem Pfad  
  
1.  Wählen Sie im **Projektmappen\-Explorer** das Anwendungsprojekt aus.  
  
2.  Klicken Sie im Menü **Erstellen** auf `Projectname` **veröffentlichen**.  
  
     Der Webpublishing\-Assistent wird angezeigt.  
  
3.  Geben Sie auf der Seite **Wo möchten Sie die Anwendung veröffentlichen?** eine gültige FTP\-Server\-Adresse oder einen gültigen Dateipfad mithilfe eines der gezeigten Formate ein, und klicken Sie dann auf **Weiter**.  
  
4.  Wählen Sie auf der Seite **Wie werden Benutzer die Anwendung installieren?** den Speicherort aus, auf den Benutzer beim Installieren der Anwendung zugreifen:  
  
    -   Wenn die Benutzer von einer Website installieren, klicken Sie auf **Von einer Website** und geben eine URL ein, die dem im vorhergehenden Schritt eingegebenen Dateipfad entspricht.  Klicken Sie auf **Weiter**.  \(Diese Option wird normalerweise verwendet, wenn eine FTP\-Adresse als Veröffentlichungsort angegeben werden soll.  Der direkte Download per FTP wird nicht unterstützt.  Daher müssen Sie hier eine URL eingeben.\)  
  
    -   Wenn die Benutzer die Anwendung direkt von der Dateifreigabe installieren, klicken Sie auf **Von UNC\-Pfad oder Dateifreigabe** und anschließend auf **Weiter**.  \(Hiermit können Veröffentlichungsorte im Format c:\\deploy\\myapp oder \\\\server\\myapp verwendet werden.\)  
  
    -   Wenn die Benutzer von Wechselmedien installieren, klicken Sie auf **Von CD\-ROM oder DVD\-ROM** und dann auf **Weiter**.  
  
5.  Klicken Sie auf der Seite **Wird die Anwendung offline verfügbar sein?** auf die gewünschte Option:  
  
    -   Falls die Anwendung auch ausgeführt werden soll, wenn der Benutzer vom Netzwerk getrennt ist, klicken Sie auf **Ja, diese Anwendung ist online und offline verfügbar**.  Im **Startmenü** wird eine Verknüpfung für die Anwendung erstellt.  
  
    -   Wenn die Anwendung direkt vom Ort der Veröffentlichung gestartet werden soll, klicken Sie auf **Nein, diese Anwendung ist nur online verfügbar**.  Es wird keine Verknüpfung im **Startmenü** erstellt.  
  
     Klicken Sie auf **Weiter**.  
  
6.  Klicken Sie auf **Fertig stellen**, um die Anwendung zu veröffentlichen.  
  
     Der Veröffentlichungsstatus wird im Statusinfobereich angezeigt.  
  
### So veröffentlichen Sie auf einer CD\-ROM oder DVD\-ROM  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf das Anwendungsprojekt, und klicken Sie dann auf **Eigenschaften**.  
  
     Der **Projekt\-Designer** wird angezeigt.  
  
2.  Klicken Sie auf die Registerkarte **Veröffentlichen**, um im **Projekt\-Designer** die Seite **Veröffentlichen** zu öffnen, und klicken Sie auf die Schaltfläche **Webpublishing\-Assistent**.  
  
     Der Webpublishing\-Assistent wird angezeigt.  
  
3.  Geben Sie auf der Seite **Wo möchten Sie die Anwendung veröffentlichen?** den Dateipfad oder den FTP\-Speicherort an, an dem die Anwendung veröffentlicht wird. Beispiel: d:\\deploy.  Klicken Sie zum Fortfahren auf **Weiter**.  
  
4.  Klicken Sie auf der Seite **Wie werden Benutzer die Anwendung installieren?** auf **Von CD\-ROM oder DVD\-ROM** und dann auf **Weiter**.  
  
    > [!NOTE]
    >  Falls Sie die Installation ausgeführt werden soll, wenn die CD\-ROM in das Laufwerk eingelegt wird, öffnen Sie im **Projekt\-Designer** die Seite **Veröffentlichen** und klicken auf die Schaltfläche **Optionen**. Wählen Sie im Assistenten **Veröffentlichungsoptionen** dann die Option **Bei CD\-Installationen automatisch Setup starten, wenn CD eingelegt wird** aus.  
  
5.  Wenn Sie Ihre Anwendung auf einer CD\-ROM veröffentlichen, können Sie dennoch Updates auf einer Website zur Verfügung stellen.  Wählen Sie auf der Seite **Die Anwendung überprüft folgenden Speicherort auf Updates** eine Aktualisierungsoption aus:  
  
    -   Wenn die Anwendung eine Quelle auf Updates überprüft, klicken Sie auf **Die Anwendung überprüft folgenden Speicherort auf Updates** und geben den Speicherort der Updateveröffentlichung ein.  Der Speicherort kann ein Dateipfad, eine Website oder ein FTP\-Server sein.  
  
    -   Wenn die Anwendung nicht nach Updates sucht, klicken Sie auf **Anwendung sucht nicht nach Updates**.  
  
     Klicken Sie auf **Weiter**.  
  
6.  Klicken Sie auf **Fertig stellen**, um die Anwendung zu veröffentlichen.  
  
     Der Veröffentlichungsstatus wird im Statusinfobereich angezeigt.  
  
    > [!NOTE]
    >  Wenn die Veröffentlichung abgeschlossen ist, benötigen Sie einen CD\-Rekorder oder einen DVD\-Rekorder, um die Dateien von dem in Schritt 3 angegebenen Speicherort auf CD\-ROM oder DVD\-ROM zu kopieren.  
  
## Siehe auch  
 [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md)   
 [Sichern von ClickOnce\-Anwendungen](../deployment/securing-clickonce-applications.md)   
 [Bereitstellen einer Office\-Lösung mithilfe von ClickOnce](/office-dev/office-dev/deploying-an-office-solution-by-using-clickonce)
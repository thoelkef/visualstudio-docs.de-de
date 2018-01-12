---
title: "Bereitstellen, veröffentlichen und Aktualisieren von SharePoint-Lösungspaketen | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.Project.SharePointProjectPropertyTab
- VS.SharePointTools.Project.Publishing
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 5990ab0f6ff6ec02131921f54197dd28e7f4e6ff
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="deploying-publishing-and-upgrading-sharepoint-solution-packages"></a>Bereitstellen, Veröffentlichen und Aktualisieren von SharePoint-Lösungspaketen
  Nachdem Sie eine SharePoint-Lösung in Visual Studio entwickelt haben, können Sie die Paketdatei (.wsp) auf einer lokalen SharePoint-Server bereitstellen oder auf einem Remote- oder lokalen SharePoint-Server zu veröffentlichen. Wenn Sie die Dateien bereitstellen, können Sie anpassen, wie die Paketdateien (.wsp) bereitgestellt werden.  
  
> [!NOTE]  
>  Derzeit können nur sandkastenlösungen an remote-SharePoint-Server veröffentlicht werden. Weitere Informationen finden Sie unter [Überlegungen zu Sandkastenlösungen](../sharepoint/sandboxed-solution-considerations.md).  
  
## <a name="deploying-publishing-and-upgrading"></a>Bereitstellen, veröffentlichen und aktualisieren  
 *Bereitstellen von* bezieht sich auf eine SharePoint-Projektmappendatei, die aus einem SharePoint-Projekt in Visual Studio erstellt werden, um einen lokalen Host zu kopieren. In einer bereitgestellten Lösung können Sie konfigurieren die Schritten zur Bereitstellung, z. B. Wiederverwendung der Anwendungspool (Internet Information Services, IIS) aktivieren die Projektmappe nach der Bereitstellung und so weiter. Verwenden Sie zum Bereitstellen der **bereitstellen** Befehl die **erstellen** Menü. Weitere Informationen finden Sie unter [wie: Bearbeiten einer SharePoint-Bereitstellungskonfiguration](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) und [Vorgehensweise: Bereitstellen und veröffentlichen Sie eine SharePoint-Lösung in einer lokalen SharePoint-Website](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).  
  
 *Veröffentlichen von* bezieht sich bis zum Hochladen von einer Sandbox Projektmappendatei für SharePoint auf einem remote-SharePoint-Website, d. h. auf einer Website auf einem anderen System. Sie können auch eine SharePoint-sandkastenlösungen-Datei auf einer lokalen SharePoint-Website veröffentlichen unabhängig davon, ob die Website veröffentlicht lokal oder remote ist, Sie konfigurieren, nicht aber seine Bereitstellungsschritte.  
  
 *Aktualisieren von* bezieht sich auf das Aktualisieren einer vorhandenen Remote oder lokal veröffentlichte SharePoint-Lösung. Nach Änderungen an der SharePoint-Lösung in Visual Studio vorgenommen werden, Sie Dateiname des Pakets die Projektmappe ändern, veröffentlichen Sie die Projektmappe erneut, und klicken Sie dann die Projektmappe zu aktualisieren, nachdem er erfolgreich erneut veröffentlicht. Wenn Sie eine lokal veröffentlichte Projektmappe erneut veröffentlichen, können Sie die vorhandene Projektmappendatei überschreiben.  
  
## <a name="deploying-packages"></a>Bereitstellen von Paketen  
 Auf Ihrem Entwicklungscomputer testen und Debuggen können Sie Paketdateien auf dem SharePoint-Server bereitstellen. Sie können auch erstellen, eine Paketdatei, die Sie auf einem anderen Computer, indem Sie auswählen installieren können der **Veröffentlichen im Dateisystem** Optionsfeld in der **veröffentlichen** (Dialogfeld). Das Paket erstellt und in die angegebene lokale Pfad kopiert. Verwenden Sie zum Bereitstellen einer SharePoint-Lösung mit dem lokalen Server der **bereitstellen** Befehl die **erstellen** Menü. Weitere Informationen finden Sie unter [Vorgehensweise: Bereitstellen und veröffentlichen Sie eine SharePoint-Lösung in einer lokalen SharePoint-Website](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).  
  
 Zum Bereitstellen einer Listendefinition, Ereignisempfänger hinzufügen und Verwenden der Funktion und Paket-Designer finden Sie unter [Exemplarische Vorgehensweise: Bereitstellen einer Aufgabenlistendefinition Projekt](../sharepoint/walkthrough-deploying-a-project-task-list-definition.md).  
  
## <a name="customizing-the-deployment-process"></a>Anpassen des Bereitstellungsprozesses  
 Die folgende Tabelle zeigt die beiden Bereitstellungskonfigurationen, die Sie beim Debuggen und eine SharePoint-Lösung bereitstellen verwenden können.  
  
|Bereitstellungskonfiguration|Beschreibung|  
|------------------------------|-----------------|  
|Standard|Die Standardkonfiguration für die Bereitstellung. Die folgenden Bereitstellungsschritte werden ausgeführt:<br /><br /> 1.  Führen Sie vor der Bereitstellung-Befehl.<br />2.  Starten Sie IIS-Anwendungspool neu.<br />3.  Lösung zurückziehen.<br />4.  Fügen Sie die Projektmappe hinzu.<br />5.  Aktivieren von Funktionen.<br />6.  Führen Sie nach der Bereitstellung-Befehl.<br /><br /> Wenn ein Paket deinstalliert wird, werden die folgenden zurückziehen Schritte ausgeführt.<br /><br /> 1.  Starten Sie IIS-Anwendungspool neu.<br />2.  Lösung zurückziehen.|  
|Keine Aktivierung|Diese Bereitstellungskonfiguration die gleichen Schritte als die Standardkonfiguration wird jedoch der Aktivierungsschritt überspringt.|  
  
 Sie können eigene Bereitstellungskonfigurationen, um zu einen einzigen Schritt abschließen, oder Ändern der Reihenfolge der Schritte im Bereitstellungsprozess erstellen. Weitere Informationen finden Sie unter [wie: Bearbeiten einer SharePoint-Bereitstellungskonfiguration](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).  
  
 Sie können auch vor und nach der Bereitstellung auszuführenden Befehle hinzufügen. Weitere Informationen finden Sie unter [Vorgehensweise: Festlegen von SharePoint-Bereitstellungsbefehlen](../sharepoint/how-to-set-sharepoint-deployment-commands.md).  
  
## <a name="publishing-packages-to-a-remote-or-local-server"></a>Veröffentlichen von Paketen auf einem Remote- oder lokalen Server  
 So veröffentlichen Sie eine Sandbox-SharePoint-Lösung auf einem Remoteserver, auf der Menüleiste wählen Sie **erstellen**, **veröffentlichen**, und klicken Sie dann in der **veröffentlichen** Dialogfeld Wählen Sie die **In SharePoint-Website veröffentlichen** Optionsfeld, z. B. Bereitstellen von remote-Server-URL **https://someremoteserver.sharepoint.microsoftonline.com**.  
  
 So veröffentlichen Sie eine SharePoint-Lösung auf einem lokalen Server in der **veröffentlichen** Dialogfeld Wählen Sie die **Veröffentlichen im Dateisystem** Optionsfeld, ein lokaler Dateisystempfad bereitstellen.  
  
 Nachdem eine Projektmappe erfolgreich in SharePoint veröffentlicht, die Projektmappe wird in der **Solution Gallery** , wo Sie sie aktivieren können. Weitere Informationen finden Sie unter [Vorgehensweise: bereitstellen, veröffentlichen und Aktualisieren von SharePoint-Lösungen auf einem Remoteserver](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).  
  
### <a name="upgrading-published-packages"></a>Veröffentlichte Pakete aktualisieren  
 Wenn Sie nach der Veröffentlichung auf einem SharePoint-Projekt in Visual Studio die Änderungen vornehmen, muss das veröffentlichte Paket aktualisiert werden, um die Änderungen einzubeziehen. Um erfolgreich zu aktualisieren, müssen ein Paket einen eindeutigen Namen verfügen. Wenn ein Paket mit dem gleichen Namen auf der SharePoint-Website gefunden wird - die auftreten kann, wenn Sie eine vorhandene Anwendung aktualisieren – eine fehlerwarnungen, die Sie auf den Dateinamen in Konflikt stehen und können Sie das Paket umbenennen. Nach erneut veröffentlicht wird, wird das neue Paket wird auf der SharePoint-Website angezeigt und kann aktualisiert werden. Ein aktualisiertes Paket mit Daten aus dem älteren Paket aktualisiert die Projektmappe, und klicken Sie dann die Projektmappe in SharePoint aktiviert. Weitere Informationen finden Sie unter [Vorgehensweise: bereitstellen, veröffentlichen und Aktualisieren von SharePoint-Lösungen auf einem Remoteserver](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Verpacken und Bereitstellen von SharePoint-Projektmappen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  
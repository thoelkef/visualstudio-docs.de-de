---
title: Bereitstellen, Veröffentlichen & Aktualisieren von SharePoint-Lösungspaketen
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.SharePointProjectPropertyTab
- VS.SharePointTools.Project.Publishing
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d8e55b01173e749395f60d189366a08907bdaccd
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444969"
---
# <a name="deploy-publish-and-upgrade-sharepoint-solution-packages"></a>Bereitstellen, Veröffentlichen und Aktualisieren von SharePoint-Lösungspaketen
  Nachdem Sie eine SharePoint-Lösung in Visual Studio entwickelt haben, können Sie die Paketdatei (.wsp) entweder auf einem lokalen SharePoint-Server bereitstellen oder auf einem Remote- oder lokalen SharePoint-Server veröffentlichen. Wenn Sie die Dateien bereitstellen, können Sie anpassen, wie die Paketdateien (.wsp) bereitgestellt werden.

> [!NOTE]
> Derzeit können nur Sandkastenlösungen auf Remote-SharePoint-Servern veröffentlicht werden. Weitere Informationen finden Sie unter [Überlegungen zur Sandkastenlösung](../sharepoint/sandboxed-solution-considerations.md).

## <a name="deploy-publish-and-upgrade"></a>Bereitstellen, Veröffentlichen und Aktualisieren
 *Bereitstellen* bezieht sich auf das Kopieren einer SharePoint-Projektmappendatei, die aus einem SharePoint-Projekt in Visual Studio erstellt wurde, auf einen lokalen Host. In einer bereitgestellten Lösung können Sie die Bereitstellungsschritte konfigurieren, z. B. das Recycling des IIS-Pools (Internet Information Services), das Aktivieren der Lösung nach der Bereitstellung usw. Verwenden Sie zum Bereitstellen den Befehl **Bereitstellen** im Menü **Erstellen.** Weitere Informationen finden Sie unter [Gewusst wie: Bearbeiten einer SharePoint-Bereitstellungskonfiguration](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) und [Anleitung: Bereitstellen und Veröffentlichen einer SharePoint-Lösung auf einer lokalen SharePoint-Website](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).

 *Veröffentlichen* bezieht sich auf das Hochladen einer Sandkasten-SharePoint-Lösungsdatei auf eine Remote-SharePoint-Website. d. h. ein Standort, der sich auf einem anderen System befindet. Sie können eine SharePoint-Sandkastenlösungsdatei auch auf einer lokalen SharePoint-Website veröffentlichen, aber unabhängig davon, ob die Website, auf der veröffentlicht wurde, lokal oder remote ist, können Sie die Bereitstellungsschritte nicht konfigurieren.

 *Das Aktualisieren* bezieht sich auf das Aktualisieren einer vorhandenen Remote- oder lokal veröffentlichten SharePoint-Lösung. Nachdem Änderungen an der SharePoint-Lösung in Visual Studio vorgenommen wurden, ändern Sie den Paketdateinamen der Projektmappe, veröffentlichen die Projektmappe erneut und aktualisieren die Projektmappe nach erfolgreicher erneuter Veröffentlichung. Wenn Sie eine lokal veröffentlichte Projektmappe erneut veröffentlichen, können Sie die vorhandene Projektmappendatei überschreiben.

## <a name="deploy-packages"></a>Bereitstellen von Paketen
 Sie können Paketdateien auf dem SharePoint-Server auf Ihrem Entwicklungscomputer zum Testen und Debuggen bereitstellen. Sie können auch eine Paketdatei erstellen, die Sie auf einem anderen Computer installieren können, indem Sie im Dialogfeld **Veröffentlichen** die Schaltfläche In **Dateisystem veröffentlichen** auswählen. Das Paket wird erstellt und in den angegebenen lokalen Dateipfad kopiert. Um eine SharePoint-Lösung auf dem lokalen Server bereitzustellen, verwenden Sie den Befehl **Bereitstellen** im Menü **Erstellen.** Weitere Informationen finden Sie unter [Gewusst wie: Bereitstellen und Veröffentlichen einer SharePoint-Lösung auf einer lokalen SharePoint-Website](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).

 Informationen zum Bereitstellen einer Listendefinition, Zum Hinzufügen eines Ereignisempfängers und zum Verwenden des Feature-Designers und des Paket-Designers finden Sie unter [Exemplarische Vorgehensweise: Bereitstellen einer Projektaufgabenlistendefinition](../sharepoint/walkthrough-deploying-a-project-task-list-definition.md).

## <a name="customize-the-deployment-process"></a>Anpassen des Bereitstellungsprozesses
 Die folgende Tabelle zeigt die beiden Bereitstellungskonfigurationen, die Sie beim Debuggen und Bereitstellen einer SharePoint-Lösung verwenden können.

|Bereitstellungskonfiguration|BESCHREIBUNG|
|------------------------------|-----------------|
|Standard|Die Standardbereitstellungskonfiguration. Die folgenden Bereitstellungsschritte werden ausgeführt:<br /><br /> 1. Führen Sie den Befehl vor der Bereitstellung aus.<br />2. Recyceln Sie iIS-Anwendungspool.<br />3. Lösung zurückziehen.<br />4. Fügen Sie die Lösung hinzu.<br />5. Aktivieren Sie Funktionen.<br />6. Führen Sie den Befehl nach der Bereitstellung aus.<br /><br /> Wenn ein Paket deinstalliert wird, werden die folgenden Rückzugsschritte ausgeführt.<br /><br /> 1. Recyceln Sie den IIS-Anwendungspool.<br />2. Lösung zurückziehen.|
|Keine Aktivierung|Diese Bereitstellungskonfiguration führt die gleichen Schritte wie die Standardkonfiguration aus, überspringt jedoch den Aktivierungsschritt.|

 Sie können eigene Bereitstellungskonfigurationen erstellen, um einen einzelnen Schritt abzuschließen oder die Reihenfolge der Schritte im Bereitstellungsprozess zu ändern. Weitere Informationen finden Sie unter [Gewusst wie: Bearbeiten einer SharePoint-Bereitstellungskonfiguration](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).

 Sie können auch Befehle hinzufügen, die vor und nach der Bereitstellung ausgeführt werden sollen. Weitere Informationen finden Sie unter [Gewusst wie: Festlegen von SharePoint-Bereitstellungsbefehlen](../sharepoint/how-to-set-sharepoint-deployment-commands.md).

## <a name="publish-packages-to-a-remote-or-local-server"></a>Veröffentlichen von Paketen auf einem Remote- oder lokalen Server
 Um eine SharePoint-Lösung mit Sandkasten auf einem Remoteserver zu veröffentlichen, wählen Sie in der Menüleiste **Build**, **Publish**aus, und wählen Sie dann im Dialogfeld **Veröffentlichen** die Schaltfläche Auf **SharePoint-Website veröffentlichen** aus, die die URL des Remoteservers bereitstellt, z. `https://someremoteserver.sharepoint.microsoftonline.com`B. .

 Um eine SharePoint-Lösung auf einem lokalen Server zu veröffentlichen, wählen Sie im Dialogfeld **Veröffentlichen** die Schaltfläche In **Dateisystem veröffentlichen** aus, um einen lokalen Systempfad bereitzustellen.

 Nachdem eine Lösung erfolgreich in SharePoint veröffentlicht wurde, wird die Lösung im **Lösungskatalog** angezeigt, wo Sie sie aktivieren können. Weitere Informationen finden Sie unter [Gewusst wie: Bereitstellen, Veröffentlichen und Aktualisieren von SharePoint-Lösungen auf einem Remoteserver](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).

### <a name="upgrade-published-packages"></a>Upgrade veröffentlichter Pakete
 Wenn Sie nach der Veröffentlichung Änderungen an einem SharePoint-Projekt in Visual Studio vornehmen, muss das veröffentlichte Paket aktualisiert werden, um die Änderungen einzuschließen. Um ein erfolgreiches Upgrade durchführen zu können, muss ein Paket einen eindeutigen Namen haben. Wenn auf der SharePoint-Website ein Paket mit demselben Namen gefunden wird , das beim Aktualisieren einer vorhandenen Anwendung auftreten kann , wird Sie mit einem Fehler auf den Dateinamenkonflikt hingewiesen und Sie können das Paket umbenennen. Nach der erneuten Veröffentlichung wird das neue Paket auf der SharePoint-Website angezeigt und kann aktualisiert werden. Ein aktualisiertes Paket aktualisiert die Lösung mithilfe von Daten aus dem älteren Paket und aktiviert dann die Lösung in SharePoint. Weitere Informationen finden Sie unter [Gewusst wie: Bereitstellen, Veröffentlichen und Aktualisieren von SharePoint-Lösungen auf einem Remoteserver](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).

## <a name="see-also"></a>Weitere Informationen
- [Paketieren und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)

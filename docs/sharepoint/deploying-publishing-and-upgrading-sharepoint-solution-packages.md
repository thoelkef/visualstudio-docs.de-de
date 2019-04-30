---
title: Bereitstellen, veröffentlichen und Aktualisieren von SharePoint-Lösungspaketen | Microsoft-Dokumentation
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
ms.openlocfilehash: a49ad82cc6cbb2eef8a8746b2c94575925ab1ddd
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436734"
---
# <a name="deploy-publish-and-upgrade-sharepoint-solution-packages"></a>Bereitstellen, veröffentlichen und Aktualisieren von SharePoint-Lösungspakete
  Nachdem Sie eine SharePoint-Lösung in Visual Studio entwickelt haben, können Sie die Paketdatei (.wsp) auf einem lokalen SharePoint-Server bereitstellen oder veröffentlichen es auf einem Remote- oder lokalen SharePoint-Server. Wenn Sie die Dateien bereitstellen, können Sie anpassen, wie die Paketdateien (.wsp) bereitgestellt werden.

> [!NOTE]
> Derzeit können nur Sandbox-Lösungen auf remote-SharePoint-Server veröffentlicht werden. Weitere Informationen finden Sie unter [Überlegungen zu sandkastenlösungen](../sharepoint/sandboxed-solution-considerations.md).

## <a name="deploy-publish-and-upgrade"></a>Bereitstellen, veröffentlichen und aktualisieren
 *Bereitstellen von* bezieht sich auf einer SharePoint-Lösungsdatei, die aus einem SharePoint-Projekt in Visual Studio erstellt werden, um einen lokalen Host kopieren. Sie können in einer bereitgestellten Lösung konfigurieren die Schritten zur Bereitstellung, z. B. Wiederverwendung Pool (Internet Information Services, IIS) aktivieren die Projektmappe nach der Bereitstellung und so weiter. Verwenden Sie zum Bereitstellen der **bereitstellen** Befehl die **erstellen** Menü. Weitere Informationen finden Sie unter [Vorgehensweise: Bearbeiten einer SharePoint-Bereitstellungskonfiguration](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) und [Vorgehensweise: Bereitstellen und veröffentlichen Sie eine SharePoint-Lösung auf einer lokalen SharePoint-Website](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).

 *Veröffentlichen von* bezieht sich auf eine Sandbox SharePoint-Lösungsdatei hochladen, um eine remote-SharePoint-Website, d. h. auf einer Website auf einem anderen System. Sie können auch eine SharePoint-Sandbox-Lösung-Datei auf einer lokalen SharePoint-Website veröffentlichen, aber unabhängig davon, ob die Website veröffentlicht lokal oder remote ist, können nicht konfiguriert werden die Bereitstellungsschritte.

 *Aktualisieren von* bezieht sich auf das Aktualisieren einer vorhandenen Remote oder lokal veröffentlichten SharePoint-Lösung. Nach dem alle Änderungen an der SharePoint-Lösung in Visual Studio vorgenommen werden, Sie ändern Paketdateiname der Projektmappe, veröffentlichen Sie die Projektmappe erneut, und klicken Sie dann die Projektmappe zu aktualisieren, nachdem erfolgreich dann. Wenn Sie eine lokal veröffentlichte Lösung erneut veröffentlichen, können Sie die vorhandene Projektmappendatei überschreiben.

## <a name="deploy-packages"></a>Bereitstellen von Paketen
 Sie können den Paketdateien auf dem SharePoint-Server auf dem Entwicklungscomputer zum Testen und Debuggen bereitstellen. Sie können auch eine Paketdatei, die Sie auf einem anderen Computer, durch Auswahl installieren können erstellen die **im Dateisystem veröffentlichen** Optionsfeld in der **veröffentlichen** Dialogfeld. Das Paket erstellt und in der angegebenen Dateipfad kopiert. Verwenden Sie zum Bereitstellen einer SharePoint-Lösung auf dem lokalen Server die **bereitstellen** Befehl die **erstellen** Menü. Weitere Informationen finden Sie unter [Vorgehensweise: Bereitstellen und veröffentlichen eine SharePoint-Lösung auf einer lokalen SharePoint-Website](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).

 Um weitere Informationen zum Bereitstellen einer Listendefinition, einen Ereignisempfänger hinzufügen und verwenden Sie die Funktions-Designer und die Paket-Designer, finden Sie unter [Exemplarische Vorgehensweise: Bereitstellen eine Aufgabenlistendefinition für Projekt](../sharepoint/walkthrough-deploying-a-project-task-list-definition.md).

## <a name="customize-the-deployment-process"></a>Anpassen des Bereitstellungsprozesses
 Die folgende Tabelle zeigt die Bereitstellung auf zwei Konfigurationen, die Sie beim Debuggen und eine SharePoint-Lösung bereitstellen verwenden können.

|Bereitstellungskonfiguration|Beschreibung|
|------------------------------|-----------------|
|Standard|Die Standardkonfiguration für die Bereitstellung. Die folgenden Bereitstellungsschritte werden ausgeführt:<br /><br /> 1.  Führen Sie vor der Bereitstellung-Befehl.<br />2.  Wiederverwenden Sie IIS-Anwendungspool.<br />3.  Lösung zurückziehen.<br />4.  Hinzufügen der Lösung.<br />5.  Aktivieren von Funktionen.<br />6.  Führen Sie nach der Bereitstellung-Befehl.<br /><br /> Wenn ein Paket deinstalliert wird, werden die folgenden zurückziehungsschritte ausgeführt.<br /><br /> 1.  Wiederverwenden Sie IIS-Anwendungspool.<br />2.  Lösung zurückziehen.|
|Keine Aktivierung|Diese Bereitstellungskonfiguration wird Sie als die Standardkonfiguration die gleichen Schritte ausgeführt, aber überspringt der Aktivierungsschritt ausführen.|

 Sie können Ihre eigenen Bereitstellungskonfigurationen, um einen einzelnen Schritt auszuführen, oder Ändern der Reihenfolge der Schritte im Bereitstellungsprozess erstellen. Weitere Informationen finden Sie unter [Vorgehensweise: Bearbeiten einer SharePoint-Bereitstellungskonfiguration](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).

 Sie können auch vor und nach der Bereitstellung auszuführenden Befehle hinzufügen. Weitere Informationen finden Sie unter [Vorgehensweise: Festlegen von SharePoint-Bereitstellungsbefehlen](../sharepoint/how-to-set-sharepoint-deployment-commands.md).

## <a name="publish-packages-to-a-remote-or-local-server"></a>Veröffentlichen von Paketen auf einem Remote- oder lokalen server
 Wählen Sie zum Veröffentlichen einer SharePoint-Sandbox-Lösung mit einem Remoteserver, auf der Menüleiste **erstellen**, **veröffentlichen**, und dann auf die **veröffentlichen** Dialogfeld auf die **In SharePoint-Website veröffentlichen** Optionsfeld aus, geben Sie die Remoteserver-URL, z. B. **https://someremoteserver.sharepoint.microsoftonline.com**.

 Zum Veröffentlichen einer SharePoint-Lösung mit einem lokalen Server, in der **veröffentlichen** Dialogfeld auf die **im Dateisystem veröffentlichen** Optionsfeld aus, die einen Pfad des lokalen Systems bereitstellen.

 Nachdem eine Projektmappe erfolgreich in SharePoint veröffentlicht hat, die Projektmappe wird in der **Lösungskatalog** , wo Sie sie aktivieren können. Weitere Informationen finden Sie unter [Vorgehensweise: Bereitstellen, veröffentlichen und Aktualisieren von SharePoint-Projektmappen auf einem Remoteserver](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).

### <a name="upgrade-published-packages"></a>Veröffentlichte Pakete aktualisieren
 Wenn Sie nach der Veröffentlichung auf einer SharePoint-Projekt in Visual Studio Änderungen vornehmen, muss das veröffentlichte Paket aktualisiert werden, damit die Änderungen übernommen werden. Um erfolgreich zu aktualisieren, müssen ein Paket einen eindeutigen Namen verfügen. Wenn ein Paket mit dem gleichen Namen auf der SharePoint-Website gefunden wird – was auftreten kann, wenn Sie eine vorhandene Anwendung aktualisieren – eine fehlerwarnungen Sie an den Dateinamen in Konflikt stehen und ermöglicht Ihnen das Benennen Sie des Pakets. Nach erneut veröffentlicht wird, wird das neue Paket wird auf der SharePoint-Website angezeigt, und Sie können aktualisiert werden. Ein aktualisiertes Paket aktualisiert die Lösung mithilfe von Daten aus dem älteren Paket und aktiviert dann die Projektmappe in SharePoint. Weitere Informationen finden Sie unter [Vorgehensweise: Bereitstellen, veröffentlichen und Aktualisieren von SharePoint-Projektmappen auf einem Remoteserver](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).

## <a name="see-also"></a>Siehe auch
- [Packen und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)

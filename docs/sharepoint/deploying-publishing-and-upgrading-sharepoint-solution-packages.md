---
title: "Bereitstellen, Ver&#246;ffentlichen und Aktualisieren von SharePoint-L&#246;sungspaketen | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.Project.SharePointProjectPropertyTab"
  - "VS.SharePointTools.Project.Publishing"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Bereitstellen [SharePoint-Entwicklung in Visual Studio]"
  - "SharePoint-Entwicklung in Visual Studio, Bereitstellen"
ms.assetid: 5efc1d99-2bd2-4f1a-a7b0-86c3b8f533f0
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Bereitstellen, Ver&#246;ffentlichen und Aktualisieren von SharePoint-L&#246;sungspaketen
  Nachdem Sie eine SharePoint\-Lösung in Visual Studio entwickeln, können Sie die Datei dem Paket \(.wsp\) zu einem lokalen SharePoint\-Server bereitstellen oder sie auf einem Remotewebserver oder lokalen SharePoint\-Server veröffentlichen.  Wenn Sie die Dateien bereitstellen, können Sie anpassen, wie die Paketdateien \(.wsp\) bereitgestellt werden.  
  
> [!NOTE]  
>  Derzeit können nur Sandkastenlösungen auf die Remoterollen SharePoint\-Servern veröffentlicht werden.  Weitere Informationen finden Sie unter [Überlegungen zu Sandkastenlösungen](../sharepoint/sandboxed-solution-considerations.md).  
  
## Bereitstellen, beim Veröffentlichen und Aktualisieren  
 *Das Bereitstellen* verweist das Kopieren einer SharePoint\-Lösungs\-Datei an, die von einem SharePoint\-Projekt in Visual Studio auf einen lokalen Host erstellt wird.  In einer bereitgestellten Projektmappe können Sie die Bereitstellungsschritte, wie Wiederverwenden des Internetinformationsdienst \(iis\)\- Pools konfigurieren und die Projektmappe nach Bereitstellung ermöglichen, z. B.  So stellen, verwenden Sie den Befehl **Bereitstellen** im Menü **Erstellen**.  Weitere Informationen finden Sie unter [Gewusst wie: Bearbeiten einer SharePoint-Bereitstellungskonfiguration](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) und [Gewusst wie: Bereitstellen und Veröffentlichen einer SharePoint-Lösung auf einer lokalen SharePoint-Website](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).  
  
 *Veröffentlichung* ist das Hochladen einer Sandbox SharePoint\-Lösungs\-Datei eine Remoteanwendung zu SharePoint\-Website an; das heißt, eine Website auf einem anderen System.  Veröffentlicht ist, Sie können eine SharePoint\-Sandkastenlösungsdatei zu einer lokalen SharePoint\-Website veröffentlichen auch, aber unabhängig davon, ob die Website, die lokal oder remote ist, können Sie den Bereitstellungsschritt nicht konfigurieren.  
  
 *Upgrade* verweist das Aktualisieren eines vorhandenen der lokal oder remote veröffentlichten SharePoint\-Lösung an.  Nachdem Änderungen der SharePoint\-Lösung in Visual Studio vorgenommen sind, ändern Sie die Paketdatei der Projektmappe veröffentlichen, die Projektmappe neu und aktualisiert dann die Projektmappe, nachdem sie erfolgreich erneut veröffentlicht.  Wenn Sie eine veröffentlichte Projektmappe lokal erneut veröffentlichen, können Sie die vorhandene Projektmappendatei überschreiben.  
  
## Bereitstellen von Paketen  
 Sie können die Paketdateien auf dem Entwicklungscomputer für den SharePoint\-Server für Tests und Debugging bereitstellen.  Außerdem können Sie eine Paketdatei erstellen, die Sie auf einem anderen Computer installieren können, indem Sie das Optionsfeld **Im Dateisystem veröffentlichen** im Dialogfeld **Veröffentlichen** auswählen.  Das Paket wird dem angegebenen lokalen Pfad erstellt und kopiert.  Wenn Sie eine SharePoint\-Lösung auf dem lokalen Server bereitzustellen, verwenden Sie den Befehl **Bereitstellen** im Menü **Erstellen**.  Weitere Informationen finden Sie unter [Gewusst wie: Bereitstellen und Veröffentlichen einer SharePoint-Lösung auf einer lokalen SharePoint-Website](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).  
  
 Informationen zum Bereitstellen einer Listendefinition, zum Hinzufügen eines Ereignisempfängers und zum Verwenden des Funktions\-Designers und des Paket\-Designers finden Sie unter [Exemplarische Vorgehensweise: Bereitstellen einer Aufgabenlistendefinition für Projekte](../sharepoint/walkthrough-deploying-a-project-task-list-definition.md).  
  
## Anpassen des Bereitstellungsvorgangs  
 In der folgenden Tabelle werden die zwei Bereitstellungskonfigurationen gezeigt, die Sie beim Debuggen und Bereitstellen einer SharePoint\-Lösung verwenden können.  
  
|Bereitstellungskonfiguration|**Beschreibung**|  
|----------------------------------|----------------------|  
|Default|Die Standardbereitstellungskonfiguration.  Die folgenden Bereitstellungsschritte werden ausgeführt:<br /><br /> 1.  Befehl der Ausführung vor der Bereitstellung.<br />2.  Wiederverwenden des IIS\-Anwendungspools.<br />3.  Zurücknehmen der Lösung.<br />4.  Hinzufügen der Lösung.<br />5.  Aktivieren von Funktionen.<br />6.  Ausführen des Befehls nach der Bereitstellung.<br /><br /> Wenn ein Paket deinstalliert wird, werden die folgenden Rücknahmeschritte ausgeführt.<br /><br /> 1.  Wiederverwenden des IIS\-Anwendungspools.<br />2.  Zurücknehmen der Lösung.|  
|Keine Aktivierung|Bei dieser Bereitstellungskonfiguration werden die gleichen Schritte wie bei der Standardkonfiguration ausgeführt, aber der Aktivierungsschritt wird übersprungen.|  
  
 Sie können eigene Bereitstellungskonfigurationen erstellen, um einen einzelnen Schritt auszuführen oder die Reihenfolge der Schritte im Bereitstellungsprozess zu ändern.  Weitere Informationen finden Sie unter [Gewusst wie: Bearbeiten einer SharePoint-Bereitstellungskonfiguration](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).  
  
 Sie können auch Befehle hinzufügen, die vor und nach der Bereitstellung ausgeführt werden sollen.  Weitere Informationen finden Sie unter [Gewusst wie: Festlegen von SharePoint-Bereitstellungsbefehlen](../sharepoint/how-to-set-sharepoint-deployment-commands.md).  
  
## Veröffentlichungs\-Pakete auf einem Remotewebserver oder auf einem lokalen Server  
 Um eine Sandbox SharePoint\-Lösung auf einem Remoteserver, in der Menüleiste zu veröffentlichen, wählen Sie, **Veröffentlichen**, und klicken Sie im Dialogfeld **Veröffentlichen**, wählen Sie das Optionsfeld **In SharePoint veröffentlichenErstellen** aus und die URL des Remoteservers, wie https:\/\/someremoteserver.sharepoint.microsoftonline.com bereitstellen.  
  
 Wenn Sie eine SharePoint\-Lösung auf einem lokalen Server, im Dialogfeld **Veröffentlichen** zu veröffentlichen, wählen Sie das Optionsfeld **Im Dateisystem veröffentlichen** und ein Pfad des lokalen Systems bereitstellen.  
  
 Nachdem eine Projektmappe erfolgreich zu SharePoint veröffentlichen, wird die Projektmappe im **Lösungskatalog**, in dem Sie sie aktivieren können.  Weitere Informationen finden Sie unter [Gewusst wie: Bereitstellen, Veröffentlichen und Aktualisieren von SharePoint-Lösungen auf einem Remoteserver](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).  
  
### Aktualisieren von veröffentlichten Paketen  
 Wenn Sie Änderungen an SharePoint vornehmen zu einem in Visual Studio, nachdem es veröffentlicht ist, muss das Verzeichnis publish Paket aktualisiert werden, um die Änderungen einzubinden.  Um erfolgreich zu aktualisieren, muss ein Paket einen eindeutigen Namen haben.  Wenn ein Paket mit dem gleichen Namen auf der SharePoint\-Website gefunden \- die auftreten können, wenn Sie eine vorhandene Anwendung aktualisieren \- einen Fehler werden Sie zum Dateinamenkonflikt und können Sie das Paket umbenennen.  Nachdem es erneut veröffentlicht wurde wird das neue Paket auf der SharePoint\-Website und kann aktualisiert werden.  Ermöglicht aktualisierte Paketupdates die Projektmappe, indem Daten aus älteren Paket verwenden, und dann die Projektmappe in SharePoint.  Weitere Informationen finden Sie unter [Gewusst wie: Bereitstellen, Veröffentlichen und Aktualisieren von SharePoint-Lösungen auf einem Remoteserver](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).  
  
## Siehe auch  
 [Verpacken und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  
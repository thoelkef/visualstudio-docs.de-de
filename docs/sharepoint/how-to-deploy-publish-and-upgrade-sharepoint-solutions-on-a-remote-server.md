---
title: "Vorgehensweise: bereitstellen, veröffentlichen und Aktualisieren von SharePoint-Lösungen auf einem Remoteserver | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- remote deployment [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, remote deployment
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
ms.assetid: d9c67fae-d097-4e26-a2b9-0f72ff800987
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 519f40017fff5dd3241f4563c5a85d0d0d15c01b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server"></a>Gewusst wie: Bereitstellen, Veröffentlichen und Aktualisieren von SharePoint-Lösungen auf einem Remoteserver
  Zusätzlich zur Bereitstellung von SharePoint-Lösungen mit dem lokalen System aus, können Sie die SharePoint-sandkastenlösungen an Remotestandorten oder lokale SharePoint-Websites veröffentlichen. Die publishing Remoteprozess die WSP-Datei auf dem SharePoint-Server kopiert werden, installiert die Lösung, und dann können Sie die Projektmappe zu aktivieren. Sie können auch eine Remoteinstallation der SharePoint-Lösung aktualisieren, nachdem Änderungen vorgenommen wurden.  
  
## <a name="to-publish-a-sandboxed-sharepoint-solution-to-a-remote-sharepoint-server"></a>So veröffentlichen Sie eine Sandbox-SharePoint-Lösung auf einem remote-SharePoint-server  
  
1.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für den Sandkasten SharePoint-Projekt, die Sie veröffentlichen, und wählen Sie dann möchten **veröffentlichen**.  
  
2.  In der **veröffentlichen** Dialogfeld Wählen Sie die **in SharePoint-Website veröffentlichen** Optionsfeld aus, und geben Sie dann eine URL für eine online veröffentlichen, wie im folgenden Beispiel: **https:// mytestsite.SharePoint.microsoftonline.com**.  
  
3.  Wählen Sie die **öffnen Sie die Seite für Solution Gallery nach dem Veröffentlichen im Browser** Optionsfeldes zum Anzeigen der Liste der Lösungen in der **Solution Gallery** Seite nach der Veröffentlichung.  
  
4.  Wählen Sie die **veröffentlichen** Schaltfläche.  
  
5.  Melden Sie sich an den Remoteserver ist eine Benutzerauthentifizierung erforderlich.  
  
     Die publishing Status wird angezeigt, in der Visual Studio **Ausgabe** Fenster. Wenn der Vorgang abgeschlossen ist, wird die Projektmappendatei (.wsp) auf dem SharePoint-Remoteserver installiert. Allerdings muss weiterhin aktiviert werden, bevor sie in SharePoint verwendet werden kann.  
  
6.  Auf der **Solution Gallery** Seite, wählen Sie die SharePoint-Anwendung aus, und wählen Sie dann im Menüband die **aktivieren** Schaltfläche.  
  
7.  In der **Lösung aktivieren** auswählen (Dialogfeld), auf dem Menüband der **aktivieren** erneut.  
  
     Die **Status** Spalte auf die **Solution Gallery** Seite gibt an, dass die Anwendung aktiv ist.  
  
## <a name="to-upgrade-a-sandboxed-sharepoint-solution-on-a-remote-sharepoint-server"></a>So aktualisieren Sie eine Sandbox-SharePoint-Lösung auf einem remote-SharePoint-server  
 Wenn eine Sandbox-SharePoint-Lösung auf einem Remoteserver bereits veröffentlicht wurde, die folgende Schritte können Sie es zu aktualisieren, nachdem Sie Änderungen an der Anwendung vornehmen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
1.  Benennen Sie die SharePoint-Paket in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Klicken Sie hierzu in **Projektmappen-Explorer** öffnen Sie das Paket. Er wird in der **Paket-Explorer**.  
  
2.  In **Paket-Explorer**in der **Namen** Feld, ändern Sie den Paketnamen in einen eindeutigen Namen.  
  
3.  Speichern Sie das Projekt.  
  
4.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für das Projekt, und wählen Sie dann **veröffentlichen**.  
  
5.  In der **veröffentlichen** Dialogfeld Wählen Sie die **in SharePoint-Website veröffentlichen** Optionsfeld aus, und klicken Sie dann, wenn die URL für den Remoteserver, in dem die Projektmappe gespeichert ist, nicht vorhanden ist, geben Sie ihn.  
  
6.  Wählen Sie die **öffnen Sie die Seite für Solution Gallery nach dem Veröffentlichen im Browser** Optionsfeldes zum Anzeigen der Liste der Lösungen in der **Solution Gallery** Seite nach der Veröffentlichung.  
  
7.  Wählen Sie die **veröffentlichen** Schaltfläche.  
  
8.  Melden Sie sich an den Remoteserver ist eine Benutzerauthentifizierung erforderlich.  
  
     Wenn Sie mit dem Remoteserver zuletzt angemeldet, möglicherweise Authentifizierung nicht erforderlich.  
  
     Wenn auf dem SharePoint-Server weiterhin die ältere Version der Anwendung mit dem gleichen Namen vorhanden ist, erhalten Sie einen Fehler, den ein Paket mit dem gleichen Namen bereits auf dem SharePoint-Server vorhanden ist. Sie müssen das Paket in einen eindeutigen Namen vor der Veröffentlichung umbenennen.  
  
9. Wählen Sie die neue Anwendung in SharePoint, und wählen Sie dann im Menüband die **Upgrade** Schaltfläche.  
  
10. In der **Lösung aktualisieren** auswählen (Dialogfeld), auf dem Menüband der **Upgrade** erneut. Die **Status** Spalte auf die **Solution Gallery** Seite sollte jetzt anzugeben, dass die Anwendung aktiv ist.  
  
     Die alte Version der Lösung wird deaktiviert, die neue Version der Lösung mit Daten aus der alten Projektmappe verwaltet aktualisiert wird und die neue Projektmappe in SharePoint aktiviert ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Bereitstellen und veröffentlichen Sie eine SharePoint-Lösung in einer lokalen SharePoint-Website](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)   
 [Erstellen von SharePoint-Lösungspaketen](../sharepoint/creating-sharepoint-solution-packages.md)   
 [Vorgehensweise: Anpassen eines SharePoint-Lösungspakets](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)   
 [Vorgehensweise: Hinzufügen und Entfernen von Funktionen und Elementen in einem Paket mit dem Paket-Designer](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)  
  
  
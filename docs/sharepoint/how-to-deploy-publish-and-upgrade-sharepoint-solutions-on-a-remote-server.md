---
title: 'Vorgehensweise: Bereitstellen, veröffentlichen und Aktualisieren von SharePoint-Projektmappen auf einem Remoteserver | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- remote deployment [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, remote deployment
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1473d1c9ea9d876eb539e9672c1675ce06d9762d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53835671"
---
# <a name="how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server"></a>Vorgehensweise: Bereitstellen, veröffentlichen und Aktualisieren von SharePoint-Projektmappen auf einem Remoteserver
  Zusätzlich zur Bereitstellung von SharePoint-Lösungen auf dem lokalen System aus, können Sie die SharePoint-sandkastenlösungen Remotestandorten oder lokale SharePoint-Websites veröffentlichen. Die remote veröffentlichen Prozess Kopien der *.wsp* Datei mit dem SharePoint-Server installiert die Lösung und anschließend können Sie die Lösung zu aktivieren. Sie können auch eine Remoteinstallation der SharePoint-Lösung aktualisieren, nachdem Änderungen vorgenommen werden.  
  
## <a name="to-publish-a-sandboxed-sharepoint-solution-to-a-remote-sharepoint-server"></a>Zum Veröffentlichen einer SharePoint-Sandbox-Lösung auf einem remote-SharePoint-server  
  
1.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für das Sandbox SharePoint-Projekt, das Sie veröffentlichen möchten, und wählen Sie dann **veröffentlichen**.  
  
2.  In der **veröffentlichen** Dialogfeld auf die **in SharePoint-Website veröffentlichen** Optionsfeld aus, und geben Sie dann eine URL für eine online veröffentlichen, z. B.: `https://mytestsite.sharepoint.microsoftonline.com`.  
  
3.  Wählen Sie die **lösungskatal im Browser öffnen, nach der Veröffentlichung** Optionsfeld aus, um das Anzeigen der Liste der Lösungen in der **Lösungskatalog** Seite nach der Veröffentlichung.  
  
4.  Wählen Sie die **veröffentlichen** Schaltfläche.  
  
5.  Melden Sie sich an den Remoteserver ist eine Benutzerauthentifizierung erforderlich.  
  
     Der Veröffentlichungsstatus angezeigt wird angezeigt, in der Visual Studio **Ausgabe** Fenster. Wenn der Vorgang abgeschlossen wird, wird die Projektmappe (*.wsp*) Datei auf dem SharePoint-Remoteserver installiert ist. Es muss jedoch weiterhin aktiviert werden, bevor sie in SharePoint verwendet werden kann.  
  
6.  Auf der **Lösungskatalog** Seite, wählen Sie die SharePoint-Anwendung aus, und wählen Sie dann im Menüband der **aktivieren** Schaltfläche.  
  
7.  In der **Lösung aktivieren** wählen Sie im Dialogfeld auf der Multifunktionsleiste die **aktivieren** erneut.  
  
     Die **Status** Spalte auf die **Lösungskatalog** Seite gibt an, dass die Anwendung aktiv ist.  
  
## <a name="to-upgrade-a-sandboxed-sharepoint-solution-on-a-remote-sharepoint-server"></a>Aktualisieren eine SharePoint-sandkastenlösung auf einem remote-SharePoint-server  
 Wenn eine SharePoint-Sandbox-Lösung auf einem Remoteserver bereits veröffentlicht wurde, wird der folgende Prozess können Sie zum Aktualisieren nach dem vornehmen von Änderungen an die Anwendung in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
1.  Benennen Sie das SharePoint-Paket im [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Klicken Sie hierzu in **Projektmappen-Explorer** öffnen Sie das Paket. Er wird in der **Paket-Explorer**.  
  
2.  In **Paket-Explorer**in die **Namen** ändern den Paketnamen in einen eindeutigen Namen.  
  
3.  Speichern Sie das Projekt.  
  
4.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für das Projekt, und wählen Sie dann **veröffentlichen**.  
  
5.  In der **veröffentlichen** Dialogfeld auf die **in SharePoint-Website veröffentlichen** Optionsfeld aus, und klicken Sie dann, wenn die URL für den Remoteserver, in dem die Lösung gespeichert ist, nicht vorhanden ist, geben Sie ihn.  
  
6.  Wählen Sie die **lösungskatal im Browser öffnen, nach der Veröffentlichung** Optionsfeld aus, um das Anzeigen der Liste der Lösungen in der **Lösungskatalog** Seite nach der Veröffentlichung.  
  
7.  Wählen Sie die **veröffentlichen** Schaltfläche.  
  
8.  Melden Sie sich an den Remoteserver ist eine Benutzerauthentifizierung erforderlich.  
  
     Wenn Sie mit dem Remoteserver zuletzt angemeldet, möglicherweise Authentifizierung nicht erforderlich.  
  
     Wenn auf dem SharePoint-Server weiterhin die ältere Version der Anwendung, die dem gleichen Namen vorhanden ist, erhalten Sie einen Fehler, den ein Paket mit dem gleichen Namen bereits auf dem SharePoint-Server vorhanden ist. Sie müssen das Paket in einen eindeutigen Namen vor der Veröffentlichung umbenennen.  
  
9. Wählen Sie die neue Anwendung in SharePoint, und wählen Sie dann im Menüband der **Upgrade** Schaltfläche.  
  
10. In der **Lösung aktualisieren** wählen Sie im Dialogfeld auf der Multifunktionsleiste die **Upgrade** erneut. Die **Status** Spalte auf die **Lösungskatalog** Seite sollte jetzt anzugeben, dass die Anwendung aktiv ist.  
  
     Die alte Version der Lösung wird deaktiviert, die neue Version der Lösung mit Daten, die von der alten Lösung verwaltet aktualisiert wird und die neue Lösung in SharePoint aktiviert ist.  
  
## <a name="see-also"></a>Siehe auch
 [Vorgehensweise: Bereitstellen und Veröffentlichen einer SharePoint-Lösung auf einer lokalen SharePoint-Website](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)   
 [Erstellen von SharePoint-Lösungspakete](../sharepoint/creating-sharepoint-solution-packages.md)   
 [Vorgehensweise: Anpassen eines SharePoint-Lösungspakets](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)   
 [Vorgehensweise: Hinzufügen und Entfernen von Funktionen und Elementen in einem Paket mithilfe des Paket-Designers](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)  

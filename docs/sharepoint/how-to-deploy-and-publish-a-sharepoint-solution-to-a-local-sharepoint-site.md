---
title: 'Vorgehensweise: Bereitstellen und Veröffentlichen einer SharePoint-Lösung auf einer lokalen SharePoint-Website | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 9537b3eef0d5da445d9456b414c89bbaac08ae87
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62813971"
---
# <a name="how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site"></a>Vorgehensweise: Bereitstellen und Veröffentlichen einer SharePoint-Lösung auf einer lokalen SharePoint-Website
  Bereitstellen oder Veröffentlichen von SharePoint-Lösungen in einer lokalen SharePoint-Server auf Ihrem Entwicklungscomputer. Die Bereitstellung Prozess Kopien der *.wsp* Datei mit dem SharePoint-Server wird die Lösung installiert und aktiviert die Funktionen. Die Veröffentlichung verarbeiten nur Kopien der *.wsp* Datei auf dem SharePoint-Server und installiert es. Sie müssen manuell aktivieren, um in SharePoint zu aktivieren.

## <a name="to-deploy-a-sharepoint-solution-to-the-local-sharepoint-server"></a>Bereitstellen eine SharePoint-Lösung auf dem lokalen SharePoint-server

1. In **Projektmappen-Explorer**, wählen Sie das Projekt, das Sie bereitstellen möchten.

2. Wählen Sie auf der Menüleiste **erstellen**, **Projektmappe bereitstellen**.

     Die *.wsp* Datei erstellt und auf dem lokalen SharePoint-Server installiert ist. Darüber hinaus werden die Funktionen aktiviert.

## <a name="to-publish-a-sharepoint-solution-to-a-local-sharepoint-server"></a>Zum Veröffentlichen von einer SharePoint-Lösung in einer lokalen SharePoint-server

1. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für das SharePoint-Projekt, das Sie veröffentlichen möchten und wählen Sie dann **veröffentlichen**.

2. In der **veröffentlichen** Dialogfeld auf die **im Dateisystem veröffentlichen** Optionsfeld aus.

3. In der **Zielspeicherort** im Textfeld Geben Sie einen lokalen Pfad, und wählen Sie dann die **veröffentlichen** Schaltfläche.

     Der Veröffentlichungsstatus angezeigt wird angezeigt, in der Visual Studio **Ausgabe** Fenster. Wenn der Vorgang abgeschlossen wird, wird die Projektmappe (*.wsp*)-Datei wird auf dem lokalen SharePoint-Server installiert. Allerdings müssen sie immer noch aktiviert werden, die in SharePoint verwendet werden. Wenn die Datei bereits vorhanden ist, wird ein Fehler tritt auf, und fragt, ob die vorhandene Datei überschrieben werden soll. Informationen zum Aktualisieren des Pakets, finden Sie im Abschnitt zum Aktualisieren von remote-Paketen in [Vorgehensweise: Bereitstellen, veröffentlichen und Aktualisieren von SharePoint-Projektmappen auf einem Remoteserver](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).

## <a name="see-also"></a>Siehe auch
- [Vorgehensweise: Bereitstellen, veröffentlichen und Aktualisieren von SharePoint-Projektmappen auf einem Remoteserver](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)
- [Erstellen von SharePoint-Lösungspakete](../sharepoint/creating-sharepoint-solution-packages.md)
- [Vorgehensweise: Anpassen eines SharePoint-Lösungspakets](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Vorgehensweise: Hinzufügen und Entfernen von Funktionen und Elementen in einem Paket mithilfe des Paket-Designers](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)

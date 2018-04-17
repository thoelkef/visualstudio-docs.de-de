---
title: 'Vorgehensweise: Bereitstellen und veröffentlichen Sie eine SharePoint-Lösung in einer lokalen SharePoint-Website | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5c4f7e347f9cea3a73ab5326b42720a1b2c33529
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site"></a>Gewusst wie: Bereitstellen und Veröffentlichen einer SharePoint-Lösung auf einer lokalen SharePoint-Website
  Sie können bereitstellen oder Veröffentlichen von SharePoint-Lösungen auf einer lokalen SharePoint-Server auf dem Entwicklungscomputer. Der Bereitstellungsprozess die WSP-Datei auf dem SharePoint-Server kopiert werden, wird die Lösung installiert und aktiviert die Funktionen. Während der Veröffentlichung wird nur die WSP-Datei auf dem SharePoint-Server kopiert und installiert es. Sie müssen manuell aktivieren, damit es in SharePoint werden kann.  
  
## <a name="to-deploy-a-sharepoint-solution-to-the-local-sharepoint-server"></a>Zum Bereitstellen von einer SharePoint-Lösung auf dem lokalen SharePoint-server  
  
1.  In **Projektmappen-Explorer**, wählen Sie das Projekt, das Sie bereitstellen möchten.  
  
2.  Wählen Sie in der Menüleiste **erstellen**, **Projektmappe bereitstellen**.  
  
     Die WSP-Datei erstellt und auf dem lokalen SharePoint-Server installiert. Darüber hinaus werden die Funktionen aktiviert.  
  
## <a name="to-publish-a-sharepoint-solution-to-a-local-sharepoint-server"></a>So veröffentlichen Sie eine SharePoint-Lösung auf einer lokalen SharePoint-server  
  
1.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für das SharePoint-Projekt, das Sie veröffentlichen möchten und wählen Sie dann **veröffentlichen**.  
  
2.  In der **veröffentlichen** Dialogfeld Wählen Sie die **Veröffentlichen im Dateisystem** Optionsfeld.  
  
3.  In der **Zielspeicherort** Textfeld, geben Sie einen lokalen Pfad, und wählen Sie dann die **veröffentlichen** Schaltfläche.  
  
     Die publishing Status wird angezeigt, in der Visual Studio **Ausgabe** Fenster. Wenn der Vorgang abgeschlossen ist, wird die Projektmappendatei (.wsp) auf dem lokalen SharePoint-Server installiert. Allerdings müssen sie immer noch aktiviert werden, die in SharePoint verwendet werden. Wenn die Projektmappendatei bereits vorhanden ist, ein Fehler tritt auf, und Sie werden gefragt, ob die vorhandene Datei überschrieben werden soll. Informationen zum Aktualisieren des Pakets, finden Sie im Abschnitt zum Aktualisieren von remotepakete in [Vorgehensweise: bereitstellen, veröffentlichen und Aktualisieren von SharePoint-Lösungen auf einem Remoteserver](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: bereitstellen, veröffentlichen und Aktualisieren von SharePoint-Lösungen auf einem Remoteserver](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)   
 [Erstellen von SharePoint-Lösungspaketen](../sharepoint/creating-sharepoint-solution-packages.md)   
 [Vorgehensweise: Anpassen eines SharePoint-Lösungspakets](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)   
 [Vorgehensweise: Hinzufügen und Entfernen von Funktionen und Elementen in einem Paket mit dem Paket-Designer](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)  
  
  
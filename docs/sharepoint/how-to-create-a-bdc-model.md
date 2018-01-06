---
title: 'Vorgehensweise: Erstellen eines BDC-Modells | Microsoft Docs'
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
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
ms.assetid: e8b888d4-a531-4d13-9ebf-efbbd33eebc6
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: fb9cab573243882fb0bd410d69941b01ae290994
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-bdc-model"></a>Gewusst wie: Erstellen eines BDC-Modells
  Sie können ein BDC (Business Data Connectivity)-Modell erstellen, indem Sie die Vorlage für diesen Vorlagentyp verwenden und dann das Modell zu einem SharePoint-Projekt hinzufügen. Weitere Informationen finden Sie unter [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md). Weitere Informationen zum Entwerfen des Modells finden Sie unter [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-create-a-bdc-project"></a>So erstellen Sie ein BDC-Projekt  
  
1.  Wählen Sie in der Menüleiste **Datei**, **Neu**, **Projekt**aus.  
  
    > [!NOTE]  
    >  Wenn die IDE für die Verwendung von Visual Basic-entwicklungseinstellungen festgelegt ist, wählen Sie **Datei**, **neues Projekt**.  
  
     Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
2.  Unter einem **Visual Basic** oder **Visual C#-**, wählen Sie **Office/SharePoint**, **SharePoint-Lösungen**.  
  
3.  In der **Vorlagen** Bereich, wählen Sie die **SharePoint 2013 – leeres Projekt** -Element aus, und wählen Sie dann die **OK** Schaltfläche.  
  
     Die **Assistent zum Anpassen von SharePoint** wird geöffnet.  
  
4.  Auf der **Geben Sie die Website und die Sicherheit für das Debuggen** Seite, geben Sie die URL der SharePoint-Website auf dem lokalen Computer, wählen Sie die **als farmlösung bereitstellen** Optionsfeld aus, und wählen Sie dann die **Fertig stellen** Schaltfläche.  
  
     Sie werden das Modell auf der von Ihnen angegebenen SharePoint-Website testen.  
  
    > [!IMPORTANT]  
    >  Sie müssen das Projekt als Farmlösung bereitstellen, da BDC-Modelle ausschließlich Farmlösungen unterstützen.  
  
     Ein leeres SharePoint-Projekt wurde erstellt.  
  
5.  Wählen Sie in der Menüleiste **Projekt**, **neues Element hinzufügen**.  
  
6.  In der **neues Element hinzufügen** Dialogfeld Wählen Sie die **Office/SharePoint** Knoten.  
  
7.  Wählen Sie in der Liste der SharePoint-Vorlagen **Business Data Connectivity-Modell (nur Farmlösung)**.  
  
8.  In der **Namen** Feld Geben Sie einen Namen für das BDC-Modell, und wählen Sie dann die **hinzufügen** Schaltfläche.  
  
     Ein **Business Data Connectivity-Modell** Element wird dem Projekt hinzugefügt. Standardmäßig wird das Modell im BDC-Designer angezeigt. Weitere Informationen finden Sie unter [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Vorgehensweise: hinzufügen eine vorhandene BDC-Modelldatei zu einem SharePoint-Projekt](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [Vorgehensweise: Verwenden Sie eine Ressourcendatei lokalisierten Namen, Eigenschaften und Berechtigungen angeben.](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [Vorgehensweise: Einfügen einer benutzerdefinierten Assembly in eine BDC-Funktion](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [Integrieren von Geschäftsdaten in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  
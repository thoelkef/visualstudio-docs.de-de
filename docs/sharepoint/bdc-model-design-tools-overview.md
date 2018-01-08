---
title: "BDC-Modell-Designtools (Übersicht) | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.BDC.Method_Details
- VS.SharePointTools.BDC.Explorer
- VS.SharePointTools.BDC.Diagram
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], visual tools
- Business Data Connectivity service [SharePoint development in Visual Studio], visual tools
- Business Data Connectivity service [SharePoint development in Visual Studio], BDC Explorer
- BDC [SharePoint development in Visual Studio], method details
- Business Data Connectivity service [SharePoint development in Visual Studio], designer
- Business Data Connectivity service [SharePoint development in Visual Studio], method details
- BDC [SharePoint development in Visual Studio], BDC Explorer
- BDC [SharePoint development in Visual Studio], designer
ms.assetid: dbd7b746-9e93-4ed4-a546-4a6f17a4725f
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 4572671971c6cf812c31286fba09bddb65080681
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="bdc-model-design-tools-overview"></a>Übersicht über Entwurfstools für BDC-Modelle
  Sie können einem Business Data Connectivity (BDC)-Modell entwerfen, mit dem BDC-Designer, der **BDC-Methodendetails** Fenster, und die **BDC-Explorer**.  
  
 Die **BDC-Explorer** ermöglicht es Ihnen, das Modell durchsuchen, suchen das Modell und Typdeskriptoren zu definieren.  
  
## <a name="bdc-designer"></a>BDC-Designer  
 BDC-Designer können Sie die Entitäten im Modell zu definieren und visuell ihrer Beziehungen untereinander anordnen. Verwenden Sie den BDC-Designer die folgenden Aufgaben ausgeführt:  
  
-   Fügen Sie dem Modell Entitäten hinzu.  
  
-   Entitäten aus dem Modell entfernt.  
  
-   Definieren Sie Beziehungen zwischen Entitäten.  
  
 Um den BDC-Designer zu öffnen, doppelklicken Sie auf die Modelldatei im Projekt, oder öffnen Sie das Kontextmenü für die Berichtsmodelldatei, und wählen Sie dann **öffnen**. Hinzufügen einer Entität für das Modell durch Ziehen oder Kopieren einer **Entität** aus der **Toolbox** in den Designer. Um eine Zuordnung zwischen zwei Entitäten zu erstellen, wählen Sie die **Zuordnung** steuern, der **Toolbox**, wählen Sie die erste Entität, und wählen Sie dann die zweite Entität.  
  
## <a name="bdc-method-details-window"></a>Fenster "Klassendetails" der BDC-Methode  
 Verwenden der **BDC-Methodendetails** Fenster definieren die Parameter, Instanzen und Filterdeskriptoren einer Methode.  
  
 Sie können schnell generieren Finder, spezifischer Finder Ersteller, Updater und Deleter-Methoden in der **BDC-Methodendetails** Fenster. Wenn Sie diese Methoden generieren, fügt Visual Studio Metadaten, z. B. Parameter, Instanzen und Typdeskriptoren, an die Methode an. Sie können diese Metadaten zur Erfüllung von Ihr konkretes Szenario ändern.  
  
 So öffnen die **BDC-Methodendetails** Fenster, in der Menüleiste auswählen **Ansicht**, **Weitere Fenster**, **BDC-Methodendetails**.  
  
 Anzeigen von Methoden in der **BDC-Methodendetails** Fenster, wählen Sie die Entität im BDC-Designer. Die Methoden der ausgewählten Entität angezeigt, der **BDC-Methodendetails** Fenster. Wenn Sie keine Entität im BDC-Designer die **BDC-Methodendetails** Fenster werden keine Informationen angezeigt.  
  
 Erweitern oder Reduzieren von Knoten in der **BDC-Methodendetails** Fenster zum Definieren von Parametern, Instanzen und Filterdeskriptoren. Verwenden der **BDC-Explorer** Typdeskriptoren zu definieren.  
  
## <a name="bdc-explorer"></a>BDC-Explorer  
 Die **BDC-Explorer** zeigt die Elemente, die das Modell bilden. So öffnen die **BDC-Explorer**, wählen Sie in der Menüleiste **Ansicht**, **Weitere Fenster**, **BDC-Explorer**. Um das Modell zu durchsuchen, erweitern Sie im Knoten der **BDC-Explorer**. Jeder Knoten stellt ein Element im XML-Datei des Modells.  
  
 Auswählen von Knoten in der **BDC-Explorer**, die Eigenschaften der einzelnen Knoten, die Sie auswählen, werden in der **Eigenschaften** Fenster. Viele dieser Eigenschaften entsprechen den Attributen in der Modelldatei. Sie können das Modell durchsuchen, indem Sie mithilfe des Suchfelds am oberen Rand der **BDC-Explorer**.  
  
> [!NOTE]  
>  Die **BDC-Explorer** zeigt keine Bezeichner, benutzerdefinierten Eigenschaften, lokalisierte Zeichenfolgen, Zuordnungsgruppen, Aktionen, Filterdeskriptoren, Zugriffssteuerungslisten Aktion und die Standardwerte für Parameter.  
  
### <a name="defining-type-descriptors"></a>Definieren von Typdeskriptoren  
 Verwenden der **BDC-Explorer** Typdeskriptoren zu definieren. BDC-Explorer können Sie definieren einen Typdeskriptor einmal, und klicken Sie dann wiederzuverwenden, Typdeskriptor an anderer Stelle in Ihrem Modell. Zu diesem Zweck einen Typdeskriptor kopieren und fügen Sie ihn auf einem Parameter oder Typdeskriptor.  
  
> [!NOTE]  
>  Änderungen an einer ursprünglichen Typdeskriptor wirken sich nicht auf die Kopien von diesem Typdeskriptor aus.  
  
 Weitere Informationen finden Sie unter [Vorgehensweise: Definieren des Typdeskriptors eines Parameters](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Erstellen eines BDC-Modells](../sharepoint/how-to-create-a-bdc-model.md)   
 [Vorgehensweise: hinzufügen eine Entität zu einem Modell](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Vorgehensweise: hinzufügen eine Finder-Methode](../sharepoint/how-to-add-a-finder-method.md)   
 [Vorgehensweise: hinzufügen eine bestimmten Finder-Methode](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Vorgehensweise: hinzufügen eine Creator-Methode](../sharepoint/how-to-add-a-creator-method.md)   
 [Vorgehensweise: Hinzufügen einer Deleter-Methode](../sharepoint/how-to-add-a-deleter-method.md)   
 [Vorgehensweise: hinzufügen eine Updater-Methode](../sharepoint/how-to-add-an-updater-method.md)   
 [Erstellen einer Assoziation zwischen Entitäten](../sharepoint/creating-an-association-between-entities.md)   
 [Exemplarische Vorgehensweise: Erstellen einer externen Liste in SharePoint mithilfe von Geschäftsdaten](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)   
 [Integrieren von Geschäftsdaten in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)   
 [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  
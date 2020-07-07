---
title: 'Vorgehensweise: Hinzufügen einer Ressourcen Datei | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- resource files [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, resource files
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 657eb473adcff40a62d2fc9b09518ebe8135eeb4
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015174"
---
# <a name="how-to-add-a-resource-file"></a>Vorgehensweise: Hinzufügen einer Ressourcen Datei
  Die Befehle zum Hinzufügen von Ressourcen Dateien finden Sie im Kontextmenü des Projektmappenknotens und der Funktions Knoten in Projektmappen-Explorer. Weitere Informationen finden Sie unter [Lokalisieren von SharePoint-Lösungen](../sharepoint/localizing-sharepoint-solutions.md).

### <a name="to-add-a-global-resource-file-to-a-sharepoint-solution"></a>So fügen Sie einer SharePoint-Lösung eine globale Ressourcen Datei hinzu

1. Öffnen Sie in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] eine SharePoint-Lösung.

2. Wählen Sie in **Projektmappen-Explorer**einen SharePoint-Projekt Knoten aus, und klicken Sie dann in der Menüleiste auf **Projekt**  >  **Neues Element hinzufügen**.

3. Wählen Sie im Dialogfeld **Neues Element hinzufügen** die Vorlage **Global Resources File** aus, und klicken Sie dann auf die Schaltfläche **Hinzufügen** .

   > [!NOTE]
   > Die Projekt Element Vorlage "Global Resources file" wird nur angezeigt, wenn ein SharePoint-Projekt Element ausgewählt wird.

4. Wählen Sie im Dialogfeld **Ressource hinzufügen** eine Kultur für die Ressourcen Datei aus, z. b. Englisch (USA).

    In diesem Schritt wird der Projekt Mappe eine globale Ressourcen Datei im Format Resource_x_ hinzugefügt **.** <em>Kultur</em><strong>.</strong> RESX, z. b. *"Resource1. en-US. resx*.

5. Wenn der **Ressourcen-Editor** in geöffnet [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] wird, fügen Sie der Ressourcen Datei Ressourcen hinzu.

### <a name="to-add-a-feature-resource-file-to-a-sharepoint-feature"></a>So fügen Sie einer SharePoint-Funktion eine featureressourcendatei hinzu

1. Wenn die SharePoint-Lösung nicht bereits in geöffnet ist [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , öffnen Sie die Projekt Mappe.

2. Öffnen Sie in **Projektmappen-Explorer**das Kontextmenü für den Namen eines Features unter dem Knoten **Features** , und wählen Sie dann **Funktions Ressource hinzufügen**aus.

     In diesem Schritt wird dem Feature eine Ressourcen Datei im Format " _resourceFileName_" hinzugefügt **.** _Culture_**. resx**, z. b. *Feature1. en-US. resx*.

3. Wenn der **Ressourcen-Editor** in geöffnet [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] wird, fügen Sie der Ressourcen Datei Ressourcen hinzu.

## <a name="see-also"></a>Weitere Informationen
- [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)

---
title: Erweitern von SharePoint-Projekten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 56e714f910a2421a909cba6714e65d21b66991ce
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49835838"
---
# <a name="extend-sharepoint-projects"></a>Erweitern von SharePoint-Projekte
  Erstellen Sie eine projekterweiterung aus, wenn die Project-Level-Funktionen von SharePoint-Projekte angepasst werden soll. Beispielsweise können Sie benutzerdefinierte Eigenschaften hinzufügen oder reagieren auf Ereignisse auf Projektebene, die ausgelöst werden, wenn der Benutzer eine SharePoint-Lösung in Visual Studio entwickelt.  
  
## <a name="create-project-extensions"></a>Erstellen von Project-Erweiterungen
 Um ein Projektelement erweitern möchten, erstellen Sie eine Visual Studio-Erweiterungsassembly, implementiert die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> Schnittstelle. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen einer SharePoint-projekterweiterung](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
 Wenn Sie eine projekterweiterung erstellen, können Sie auch die folgende Funktionen für die SharePoint-Projekte hinzufügen:  
  
- Hinzufügen eines Kontextmenüelements an. Das Menüelement angezeigt wird, wenn Sie das Kontextmenü für eine SharePoint-Projektknoten im Öffnen **Projektmappen-Explorer** mit der rechten Maustaste des Knotens, oder Sie ihn auswählen, und wählen Sie dann die **UMSCHALT** +  **F10** Schlüssel. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen ein Kontextmenüelements zu SharePoint-Projekten](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md).  
  
- Fügen Sie eine benutzerdefinierte Eigenschaft hinzu. Die Eigenschaft wird in der **Eigenschaften** Fenster bei der Auswahl einer SharePoint-Projekt in **Projektmappen-Explorer**. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen einer Eigenschaft zu SharePoint-Projekte](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  
  
  Eine exemplarische Vorgehensweise, die veranschaulicht, wie erstellen, bereitstellen und Testen Sie eine projekterweiterung finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer SharePoint-projekterweiterung](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md).  
  
## <a name="understand-the-relationship-between-project-extensions-and-project-instances"></a>Verstehen Sie die Beziehung zwischen projekterweiterungen und Instanzen von project
 Bei der Erstellung einer projekterweiterung lädt die Erweiterung wird in der jede Art von SharePoint-Projekt geöffnet [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] enthält mehrere SharePoint-Projektvorlagen, z. B. Ereignisempfänger, Inhaltstypen und Listendefinitionen. Es ist jedoch nur eine Art von SharePoint-Projekt. Die Projekttypen, die in angezeigt werden. die **neues Projekt** im Dialogfeld werden nur die Vorlagen, die eine oder mehrere SharePoint-Projektelemente bündeln. Da nur eine SharePoint-Projekt-Typ vorhanden ist, gelten Erweiterungen, die für ein Projekt erstellt wurde, für alle SharePoint-Projekte. Erstellen nicht möglich ist, z. B. eine Erweiterung, die nur für gilt eine **Inhaltstyp** Projekt.  
  
 Um ein bestimmtes Projekt-Instanz zuzugreifen, behandeln Sie eines der der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> Ereignisse der *Anwendbarkeitsprüfungen* Parameter in der Implementierung von der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> Methode. Um zu bestimmen, wenn eine Lösung ein SharePoint-Projekt hinzugefügt wird, z. B. Behandeln der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> Ereignis. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen einer SharePoint-projekterweiterung](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
## <a name="see-also"></a>Siehe auch
 [Gewusst wie: Erstellen einer SharePoint-projekterweiterung](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [Gewusst wie: Hinzufügen ein Kontextmenüelements zu SharePoint-Projekten](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [Gewusst wie: Hinzufügen einer Eigenschaft zu SharePoint-Projekte](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Exemplarische Vorgehensweise: Erstellen einer SharePoint-projekterweiterung](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)   
 [Definieren von benutzerdefinierten SharePoint-Projektelementtypen](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Erweitern von SharePoint-Projektelemente](../sharepoint/extending-sharepoint-project-items.md)   
 [Erweitern von SharePoint-Packen und-bereitstellen](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Erweitern von SharePoint-Projektsystem](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  

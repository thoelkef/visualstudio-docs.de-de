---
title: Erweitern von SharePoint-Projekten | Microsoft Docs
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
ms.openlocfilehash: ab99253efbef61a3a041f261e44e8944bc7d6024
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2018
ms.locfileid: "34764152"
---
# <a name="extend-sharepoint-projects"></a>Erweitern der SharePoint-Projekte
  Erstellen Sie eine projekterweiterung, wenn Sie auf Projektebene Funktionen von SharePoint-Projekten anpassen möchten. Beispielsweise können Sie benutzerdefinierte Eigenschaften hinzufügen oder reagieren auf Projektebene-Ereignisse, die ausgelöst werden, wenn der Benutzer eine SharePoint-Lösung in Visual Studio entwickelt.  
  
## <a name="create-project-extensions"></a>Erstellen von Project-Erweiterungen
 Um ein Projektelement zu erweitern, erstellen Sie eine Assembly der Visual Studio-Erweiterung, die implementiert die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> Schnittstelle. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen einer SharePoint-Projekterweiterung](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
 Wenn Sie eine projekterweiterung erstellen, können Sie auch die folgende Funktionalität für die SharePoint-Projekte hinzufügen:  
  
-   Hinzufügen eines Kontextmenüelements an. Das Menüelement wird angezeigt, wenn Sie das Kontextmenü für einen SharePoint-Projektknoten öffnen **Projektmappen-Explorer** durch Rechtsklick auf den Knoten oder es auswählen und dann die **UMSCHALT** +  **F10** Schlüssel. Weitere Informationen finden Sie unter [wie: Hinzufügen eines Kontextmenüelements zu SharePoint-Projekten](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md).  
  
-   Fügen Sie eine benutzerdefinierte Eigenschaft hinzu. Die Eigenschaft wird in der **Eigenschaften** Fenster bei der Auswahl von einem SharePoint-Projekt in **Projektmappen-Explorer**. Weitere Informationen finden Sie unter [wie: Hinzufügen einer Eigenschaft zu SharePoint-Projekte](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  
  
 Eine exemplarische Vorgehensweise, die veranschaulicht, wie erstellen, bereitstellen und Testen einer projekterweiterung, finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer SharePoint-Projekterweiterung](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md).  
  
## <a name="understand-the-relationship-between-project-extensions-and-project-instances"></a>Verstehen Sie die Beziehung zwischen Project-Erweiterungen und Instanzen von project
 Bei der Erstellung einer-projekterweiterung die Erweiterung laden, wenn jede Art von SharePoint-Projekt, in geöffnet wird [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] enthält mehrere SharePoint-Projektvorlagen, z. B. Listendefinitionen, Inhaltstypen und Ereignisempfänger. Es ist jedoch nur eine Art von SharePoint-Projekt. Die Projekttypen, die in der **neues Projekt** im Dialogfeld werden nur die Vorlagen, die eine oder mehrere SharePoint-Projektelemente zusammenfassen. Da nur ein Typ von SharePoint-Projekt vorhanden ist, gelten Erweiterungen, die für ein Projekt erstellt für alle SharePoint-Projekte. Erstellen nicht möglich ist, z. B. eine Erweiterung, die nur gilt eine **Inhaltstyp** Projekt.  
  
 Um eine bestimmte Projektinstanz zuzugreifen, behandeln Sie eines der der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> Ereignisse der *ProjectService* Parameter in der Implementierung von der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> Methode. Um zu bestimmen, wenn ein SharePoint-Projekt zu einer Projektmappe hinzugefügt wird, z. B. Behandeln der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> Ereignis. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen einer SharePoint-Projekterweiterung](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
## <a name="see-also"></a>Siehe auch
 [Vorgehensweise: Erstellen einer SharePoint-Projekterweiterung](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [Vorgehensweise: Hinzufügen ein Kontextmenüelements zu SharePoint-Projekten](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [Vorgehensweise: Hinzufügen einer Eigenschaft zu SharePoint-Projekte](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Exemplarische Vorgehensweise: Erstellen einer SharePoint-Projekterweiterung](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)   
 [Definieren von benutzerdefinierten SharePoint-Projektelementtypen](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Erweitern von SharePoint-Projektelementen](../sharepoint/extending-sharepoint-project-items.md)   
 [Erweitern von SharePoint-Packen und-bereitstellen](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Erweitern des SharePoint-Projektsystems](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  

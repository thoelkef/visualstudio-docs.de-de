---
title: "Vorgehensweise: Hinzufügen ein Kontextmenüelements zu SharePoint-Projekten | Microsoft Docs"
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
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: c8cf3a3705fd389f16ac02d5739eeb754df99ac9
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>Gewusst wie: Hinzufügen eines Kontextmenüelements zu SharePoint-Projekten
  Sie können jedem SharePoint-Projekt ein Kontextmenüelement hinzufügen. Das Menüelement wird angezeigt, wenn ein Benutzer einen Projektknoten klickt **Projektmappen-Explorer**.  
  
 Die folgenden Schritte wird davon ausgegangen, dass Sie bereits eine projekterweiterung erstellt haben. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen einer SharePoint-Projekterweiterung](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
### <a name="to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>Hinzufügen ein Kontextmenüelements zu SharePoint-Projekte  
  
1.  In der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> Methode Ihrer <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> -Implementierung, Handle der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> -Ereignis für die *ProjectService* Parameter.  
  
2.  Im Ereignishandler für das <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> Ereignis, fügen Sie einen neuen <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> -Objekt an die <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.ActionMenuItems%2A> oder <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.AddMenuItems%2A> Auflistung von Parameters für die Ereignisargumente.  
  
3.  In der <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> -Ereignishandler für das neue <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> Objekt, führen Sie die Aufgaben klickt ein Benutzer das Kontextmenüelement ausgeführt werden soll.  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel veranschaulicht das Hinzufügen ein Kontextmenüelements zu SharePoint-Projekt-Knoten in **Projektmappen-Explorer**. Wenn der Benutzer mit der rechten Maustaste eines Projektknoten aus und klickt auf die **Schreiben der Nachricht in Fenster "Ausgabe"** Menüelement, Visual Studio zeigt eine Meldung in die **Ausgabe** Fenster. Dieses Beispiel verwendet die SharePoint-Projektdienst, die Meldung angezeigt. Weitere Informationen finden Sie unter [Verwenden des SharePoint-Projektdiensts](../sharepoint/using-the-sharepoint-project-service.md).  
  
 [!code-csharp[SPExtensibility.ProjectExtension.Menu#1](../sharepoint/codesnippet/CSharp/projectmenu/extension/projectitemextensionmenu.cs#1)]
 [!code-vb[SPExtensibility.ProjectExtension.Menu#1](../sharepoint/codesnippet/VisualBasic/projectmenu/extension/projectitemextensionmenu.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilieren des Codes  
 Dieses Beispiel benötigen Sie ein Klassenbibliotheksprojekt mit Verweisen auf die folgenden Assemblys:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Bereitstellen der Erweiterung  
 Zum Bereitstellen der Erweiterung erstellen Sie eine [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] -Erweiterung (VSIX) Verpacken, für die Assembly und alle anderen Dateien, die Sie mit der Erweiterung verteilen möchten. Weitere Informationen finden Sie unter [Bereitstellen von Erweiterungen für SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern von SharePoint-Projekten](../sharepoint/extending-sharepoint-projects.md)   
 [Vorgehensweise: Erstellen einer SharePoint-Projekterweiterung](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [Vorgehensweise: Hinzufügen einer Eigenschaft zu SharePoint-Projekten](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)  
  
  
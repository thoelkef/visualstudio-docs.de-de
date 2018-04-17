---
title: 'Vorgehensweise: Hinzufügen ein Kontextmenüelements zu einer SharePoint-Projektelementerweiterung | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b2ac26672e7df8cc01fbca862df5867787e5283c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension"></a>Gewusst wie: Hinzufügen eines Kontextmenüelements zu einer SharePoint-Projektelementerweiterung
  Sie können einer vorhandenen SharePoint-Projektelement ein Kontextmenüelement hinzufügen, mithilfe einer projektelementerweiterung. Das Menüelement wird angezeigt, wenn ein Benutzer das Projektelement in klickt **Projektmappen-Explorer**.  
  
 Die folgenden Schritte wird davon ausgegangen, dass Sie eine projektelementerweiterung bereits erstellt haben. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen einer SharePoint-Projektelementerweiterung](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
### <a name="to-add-a-shortcut-menu-item-in-a-project-item-extension"></a>Hinzufügen ein Kontextmenüelements in eine projektelementerweiterung  
  
1.  In der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> Methode Ihrer <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> -Implementierung, Handle der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> -Ereignis für die *ProjectItemType* Parameter.  
  
2.  Im Ereignishandler für das <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> Ereignis, fügen Sie einen neuen <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> -Objekt an die <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> oder <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> Auflistung von Parameters für die Ereignisargumente.  
  
3.  In der <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> -Ereignishandler für das neue <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> Objekt, führen Sie die Aufgaben klickt ein Benutzer das Kontextmenüelement ausgeführt werden soll.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht, wie das Ereignisempfänger-Projektelement ein Kontextmenüelement hinzugefügt. Wenn der Benutzer mit der rechten Maustaste des Projektelements in **Projektmappen-Explorer** und klickt auf die **Schreiben der Nachricht in Fenster "Ausgabe"** Menüelement, Visual Studio zeigt eine Meldung in die **Ausgabe**Fenster.  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#1](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemextensionmenu.vb#1)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#1](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemextensionmenu.cs#1)]  
  
 In diesem Beispiel verwendet die SharePoint-Projektdienst zum Schreiben der Nachricht an die **Ausgabe** Fenster. Weitere Informationen finden Sie unter [Verwenden des SharePoint-Projektdiensts](../sharepoint/using-the-sharepoint-project-service.md).  
  
## <a name="compiling-the-code"></a>Kompilieren des Codes  
 Dieses Beispiel benötigen Sie ein Klassenbibliotheksprojekt mit Verweisen auf die folgenden Assemblys:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Bereitstellen der Erweiterung  
 Zum Bereitstellen der Erweiterung erstellen Sie eine [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] -Erweiterung (VSIX) Verpacken, für die Assembly und alle anderen Dateien, die Sie mit der Erweiterung verteilen möchten. Weitere Informationen finden Sie unter [Bereitstellen von Erweiterungen für SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: erstellen eine SharePoint-Projektelementerweiterung](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [Vorgehensweise: Hinzufügen einer Eigenschaft zu einer SharePoint-Projektelementerweiterung](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)   
 [Erweitern von SharePoint-Projektelementen](../sharepoint/extending-sharepoint-project-items.md)   
 [Exemplarische Vorgehensweise: Erweitern eines SharePoint-Projektelementtyps](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
  
---
title: 'Vorgehensweise: Hinzufügen ein Kontextmenüelements zu einer benutzerdefinierten SharePoint-Projektelementtyp | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2bbd0e4ab34b20be3be9a3adaa0b43f436727c2c
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767701"
---
# <a name="how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type"></a>Vorgehensweise: Hinzufügen ein Kontextmenüelements zu einem benutzerdefinierten SharePoint-Projektelementtyp
  Wenn Sie einen benutzerdefinierten SharePoint-Projektelementtyp definieren, können Sie das Projektelement ein Kontextmenüelement hinzufügen. Das Menüelement wird angezeigt, wenn ein Benutzer das Projektelement in klickt **Projektmappen-Explorer**.  
  
 Die folgenden Schritte wird davon ausgegangen, dass Sie eigene SharePoint-Projektelementtyp bereits definiert haben. Weitere Informationen finden Sie unter [wie: Definieren Sie einen SharePoint-Projektelementtyp](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
### <a name="to-add-a-shortcut-menu-item-to-a-custom-project-item-type"></a>Hinzufügen ein Kontextmenüelements zu einem benutzerdefinierten Projektelementtyp  
  
1.  In der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> Methode Ihrer <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> -Implementierung, Handle der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> -Ereignis für die *ProjectItemTypeDefinition* Parameter.  
  
2.  Im Ereignishandler für das <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> Ereignis, fügen Sie einen neuen <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> -Objekt an die <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> oder <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> Auflistung von Parameters für die Ereignisargumente.  
  
3.  In der <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> -Ereignishandler für das neue <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> Objekt, führen Sie die Aufgaben aus, wenn ein Benutzer das Kontextmenüelement auswählt ausgeführt werden soll.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht, wie eine benutzerdefinierte Projektelementtyp ein Kontextmenüelement hinzugefügt. Wenn der Benutzer im Kontextmenü aus dem Projektelement im öffnet **Projektmappen-Explorer** und wählt die **Schreiben der Nachricht in Fenster "Ausgabe"** Menüelement, Visual Studio zeigt eine Meldung in die **Ausgabe**  Fenster.  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypemenu.cs#4)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypemenu.vb#4)]  
  
 In diesem Beispiel verwendet die SharePoint-Projektdienst zum Schreiben der Nachricht an die **Ausgabe** Fenster. Weitere Informationen finden Sie unter [Verwenden des SharePoint-Projektdiensts](../sharepoint/using-the-sharepoint-project-service.md).  
  
## <a name="compiling-the-code"></a>Kompilieren des Codes  
 Dieses Beispiel benötigen Sie ein Klassenbibliotheksprojekt mit Verweisen auf die folgenden Assemblys:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-project-item"></a>Bereitstellen des Projektelements  
 Um Ihr Projektelement anderen Entwicklern zu ermöglichen, erstellen Sie eine Projektvorlage oder eine Projektelementvorlage aus. Weitere Informationen finden Sie unter [Erstellen von Elementvorlagen und Projektvorlagen für SharePoint-Projektelemente](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Erstellen Sie zum Bereitstellen des Projektelements ein [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Erweiterung (VSIX) Verpacken, für die Assembly, die Vorlage und alle anderen Dateien, die Sie mit dem Projektelement verteilen möchten. Weitere Informationen finden Sie unter [Bereitstellen von Erweiterungen für SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Siehe auch
 [Vorgehensweise: Definieren Sie einen SharePoint-Projektelementtyp](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [Vorgehensweise: Hinzufügen einer Eigenschaft zu einem benutzerdefinierten SharePoint-Projektelementtyp](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [Definieren von benutzerdefinierten SharePoint-Projektelementtypen](../sharepoint/defining-custom-sharepoint-project-item-types.md)  
  
 
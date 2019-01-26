---
title: 'Vorgehensweise: Hinzufügen ein Kontextmenüelements zu einer benutzerdefinierten SharePoint-Projektelementtyp | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8cde43b5e04b870ec4264d28ee6a33b56d5571d0
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54873326"
---
# <a name="how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type"></a>Vorgehensweise: Hinzufügen eines Kontextmenüelements zu einer benutzerdefinierten SharePoint-Projektelementtyp
  Wenn Sie einen benutzerdefinierten SharePoint-Projektelementtyp definieren, können Sie ein Kontextmenüelement hinzufügen, auf das Projektelement. Das Menüelement, das angezeigt wird, wenn ein Benutzer mit das Projektelement im klickt **Projektmappen-Explorer**.  
  
 Die folgenden Schritte wird davon ausgegangen, dass Sie bereits Ihre eigenen SharePoint-Projektelementtyp definiert haben. Weitere Informationen finden Sie unter [Vorgehensweise: Definieren Sie einen SharePoint-Projektelementtyp](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
### <a name="to-add-a-shortcut-menu-item-to-a-custom-project-item-type"></a>Hinzufügen ein Kontextmenüelements zu einer benutzerdefinierten Projektelementtyp  
  
1.  In der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> -Methode der Ihre <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> -Implementierung, das Handle der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> Ereignis die *ProjectItemTypeDefinition* Parameter.  
  
2.  Im Ereignishandler für die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> -Ereignis, fügen Sie einen neuen <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> -Objekt an die <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> oder <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> Auflistung von Parameters für Ereignisargumente.  
  
3.  In der <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> -Ereignishandler für das neue <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> Objekt, führen Sie die Aufgaben ausgeführt werden, wenn ein Benutzer das Kontextmenüelement werden soll.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht, wie Sie einen benutzerdefinierten Projektelementtyp Kontextmenüelement hinzufügen. Wenn der Benutzer öffnet Sie im Kontextmenü den Befehl aus dem Projektelement im **Projektmappen-Explorer** und wählt die **Schreiben der Nachricht in Fenster "Ausgabe"** Menüelement, Visual Studio zeigt eine Meldung in die **Ausgabe**  Fenster.  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypemenu.cs#4)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypemenu.vb#4)]  
  
 Dieses Beispiel verwendet die SharePoint-Projektdiensts zum Schreiben der Nachricht, die **Ausgabe** Fenster. Weitere Informationen finden Sie unter [verwenden SharePoint-Projektdiensts](../sharepoint/using-the-sharepoint-project-service.md).  
  
## <a name="compile-the-code"></a>Kompilieren des Codes  
 Dieses Beispiel erfordert ein Klassenbibliotheksprojekt mit Verweisen auf die folgenden Assemblys:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-project-item"></a>Bereitstellen des Projektelements  
 Um Ihr Projektelement anderen Entwicklern zu ermöglichen, erstellen Sie eine Projektvorlage oder eine Projektelementvorlage. Weitere Informationen finden Sie unter [Erstellen von Vorlagen und Projektvorlagen für SharePoint-Projektelemente](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Erstellen Sie zum Bereitstellen des Projektelements eine [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] -Erweiterung (VSIX) Verpacken, für die Assembly, die Vorlage und alle anderen Dateien, die Sie mit dem Projektelement verteilen möchten. Weitere Informationen finden Sie unter [Bereitstellen von Erweiterungen für SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Siehe auch
 [Vorgehensweise: Definieren Sie einen SharePoint-Projektelementtyp](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [Vorgehensweise: Hinzufügen einer Eigenschaft zu einer benutzerdefinierten SharePoint-Projektelementtyp](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [Definieren von benutzerdefinierten SharePoint-Projektelementtypen](../sharepoint/defining-custom-sharepoint-project-item-types.md)  

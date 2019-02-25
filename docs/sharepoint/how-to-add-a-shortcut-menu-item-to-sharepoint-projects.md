---
title: 'Vorgehensweise: Hinzufügen ein Kontextmenüelements zu SharePoint-Projekten | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: aaeb40e97309a06dfe0f4c0e14a7d032edd563ec
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56645250"
---
# <a name="how-to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>Vorgehensweise: Hinzufügen eines Kontextmenüelements zu SharePoint-Projekten
  Sie können ein Kontextmenüelements zu einem SharePoint-Projekt hinzufügen. Das Menüelement, das angezeigt wird, wenn ein Benutzer einen Projektknoten klickt **Projektmappen-Explorer**.

 Die folgenden Schritte wird davon ausgegangen, dass Sie bereits eine projekterweiterung erstellt haben. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen einer SharePoint-projekterweiterung](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

### <a name="to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>Hinzufügen ein Kontextmenüelements zu SharePoint-Projekten

1.  In der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> -Methode der Ihre <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> -Implementierung, das Handle der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> Ereignis die *Anwendbarkeitsprüfungen* Parameter.

2.  Im Ereignishandler für die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> -Ereignis, fügen Sie einen neuen <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> -Objekt an die <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.ActionMenuItems%2A> oder <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.AddMenuItems%2A> Auflistung von Parameters für Ereignisargumente.

3.  In der <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> -Ereignishandler für das neue <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> Objekt, führen Sie die Aufgaben ausgeführt werden, wenn ein Benutzer über das Kontextmenüelement klickt werden soll.

## <a name="example"></a>Beispiel
 Im folgenden Codebeispiel wird veranschaulicht, wie zum Hinzufügen eines Kontextmenüelements zu SharePoint-Projektknoten im **Projektmappen-Explorer**. Wenn der Benutzer mit der rechten Maustaste eines Projektknoten aus und klickt auf die **Schreiben der Nachricht in Fenster "Ausgabe"** Menüelement, Visual Studio zeigt eine Meldung in die **Ausgabe** Fenster. Dieses Beispiel verwendet die SharePoint-Projektdiensts Nachricht anzeigen. Weitere Informationen finden Sie unter [verwenden SharePoint-Projektdiensts](../sharepoint/using-the-sharepoint-project-service.md).

 [!code-csharp[SPExtensibility.ProjectExtension.Menu#1](../sharepoint/codesnippet/CSharp/projectmenu/extension/projectitemextensionmenu.cs#1)]
 [!code-vb[SPExtensibility.ProjectExtension.Menu#1](../sharepoint/codesnippet/VisualBasic/projectmenu/extension/projectitemextensionmenu.vb#1)]

## <a name="compile-the-code"></a>Kompilieren des Codes
 Dieses Beispiel erfordert ein Klassenbibliotheksprojekt mit Verweisen auf die folgenden Assemblys:

-   Microsoft.VisualStudio.SharePoint
-
-   System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Bereitstellen der Erweiterung
 Erstellen Sie zum Bereitstellen der Erweiterungs eine [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] -Erweiterung (VSIX) Verpacken, für die Assembly und alle anderen Dateien, die Sie mit der Erweiterung verteilen möchten. Weitere Informationen finden Sie unter [Bereitstellen von Erweiterungen für SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Siehe auch
- [Erweitern von SharePoint-Projekte](../sharepoint/extending-sharepoint-projects.md)
- [Vorgehensweise: Erstellen einer SharePoint-projekterweiterung](../sharepoint/how-to-create-a-sharepoint-project-extension.md)
- [Vorgehensweise: Hinzufügen einer Eigenschaft zu SharePoint-Projekte](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)

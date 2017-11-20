---
title: 'Vorgehensweise: erstellen eine SharePoint-Projektelementerweiterung | Microsoft Docs'
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
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
ms.assetid: 163738b9-e25a-49c9-8f33-4b57a2da6b07
caps.latest.revision: "31"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c8e9faaf0b38623347c2b6e8ff7351f625416e82
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-a-sharepoint-project-item-extension"></a>Gewusst wie: Erstellen einer SharePoint-Projektelementerweiterung
  Erstellen Sie eine projektelementerweiterung, wenn Sie möchten, Hinzufügen von Funktionen zu einer SharePoint-Projektelement, die in Visual Studio bereits installiert ist. Weitere Informationen finden Sie unter [Erweitern von SharePoint-Projektelemente](../sharepoint/extending-sharepoint-project-items.md).  
  
### <a name="to-create-a-project-item-extension"></a>So erstellen eine projektelementerweiterung  
  
1.  Erstellen Sie ein Klassenbibliotheksprojekt.  
  
2.  Fügen Sie Verweise auf die folgenden Assemblys hinzu:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  Erstellen Sie eine Klasse, die die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>-Schnittstelle implementiert.  
  
4.  Fügen Sie der Klasse die folgenden Attribute hinzu:  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>. Mit diesem Attribut können Sie Visual Studio erkennt und lädt die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> Implementierung. Übergeben Sie die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> Typ an den Attributkonstruktor.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. In einer projektelementerweiterung bezeichnet dieses Attribut das Projektelement, die, das Sie erweitern möchten. Übergeben Sie die ID des Projektelements an den Attributkonstruktor. Eine Liste der IDs von die Projektelemente, die in Visual Studio enthalten sind, finden Sie unter [Erweitern von SharePoint-Projektelemente](../sharepoint/extending-sharepoint-project-items.md).  
  
5.  In der Implementierung von der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> Methode verwenden, Mitglied der *ProjectItemType* Parameter, um das Verhalten der Erweiterung zu definieren. Dieser Parameter ist ein <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> -Objekt, das Zugriff auf die in definierten Ereignisse ermöglicht die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> und <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents> Schnittstellen. Zugriff auf eine bestimmte Instanz der dem Projektelementtyp Sie erweitern behandeln <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> Ereignisse, z. B. <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> und <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized>.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht, wie eine einfache Erweiterung für das Projektelement Ereignisempfänger zu erstellen. Jedes Mal der Benutzer ein SharePoint-Projekt ein Projektelement Ereignisempfänger hinzugefügt, dieser Erweiterung schreibt eine Meldung an die **Ausgabe** Fenster und **Fehlerliste** Fenster.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#1](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemextension.cs#1)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#1](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemextension.vb#1)]  
  
 In diesem Beispiel verwendet die SharePoint-Projektdienst zum Schreiben der Nachricht an die **Ausgabe** Fenster und **Fehlerliste** Fenster. Weitere Informationen finden Sie unter [Verwenden des SharePoint-Projektdiensts](../sharepoint/using-the-sharepoint-project-service.md).  
  
## <a name="compiling-the-code"></a>Kompilieren des Codes  
 Dieses Beispiel erfordert Verweise auf die folgenden Assemblys:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Bereitstellen der Erweiterung  
 Zum Bereitstellen der Erweiterung erstellen Sie eine [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] -Erweiterung (VSIX) Verpacken, für die Assembly und alle anderen Dateien, die Sie mit der Erweiterung verteilen möchten. Weitere Informationen finden Sie unter [Bereitstellen von Erweiterungen für SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern von SharePoint-Projektelementen](../sharepoint/extending-sharepoint-project-items.md)   
 [Exemplarische Vorgehensweise: Erweitern eines SharePoint-Projektelementtyps](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
  
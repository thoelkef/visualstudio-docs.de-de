---
title: 'Vorgehensweise: Definieren Sie einen SharePoint-Projektelementtyp | Microsoft-Dokumentation'
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
ms.openlocfilehash: bfb04256a1bb8aacb062f30839566b75b599a3a3
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54872026"
---
# <a name="how-to-define-a-sharepoint-project-item-type"></a>Vorgehensweise: Definieren Sie einen SharePoint-Projektelementtyp
  Definieren Sie einen Projektelementtyp aus, wenn Sie ein benutzerdefiniertes SharePoint-Projektelement erstellen möchten. Weitere Informationen finden Sie unter [definieren benutzerdefinierte SharePoint-Projektelementtypen](../sharepoint/defining-custom-sharepoint-project-item-types.md).  
  
### <a name="to-define-a-project-item-type"></a>Um einen Projektelementtyp definieren  
  
1.  Erstellen Sie ein Klassenbibliotheksprojekt.  
  
2.  Fügen Sie Verweise auf die folgenden Assemblys hinzu:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  Erstellen Sie eine Klasse, die die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>-Schnittstelle implementiert.  
  
4.  Fügen Sie die folgenden Attribute zur Klasse hinzu:  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>. Mit diesem Attribut können Sie Visual Studio zum Ermitteln und Laden Ihre <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> Implementierung. Übergeben Sie die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> Typ an den Attributkonstruktor.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. In einem Projektelement-Typdefinition gibt dieses Attribut den Zeichenfolgenbezeichner für das neue Projektelement. Es wird empfohlen, dass Sie das Format verwenden *Firmenname*. *Name des Features* zu gewährleisten, dass alle Projektelemente einen eindeutigen Namen haben.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute>. Dieses Attribut gibt an, das für dieses Projektelement in anzuzeigende Symbol **Projektmappen-Explorer**. Dieses Attribut ist optional. Wenn Sie sie nicht auf die Klasse anwenden, zeigt Visual Studio ein Standardsymbol für das Projektelement. Wenn Sie dieses Attribut festgelegt haben, übergeben Sie den vollqualifizierten Namen eines Symbols oder eine Bitmap, in der Assembly eingebettet ist.  
  
5.  In der Implementierung von der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> Methode verwenden, Mitglied der *ProjectItemTypeDefinition* Parameter, um das Verhalten des Projektelementtyps zu definieren. Dieser Parameter ist ein <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> -Objekt, das Zugriff auf die in definierten Ereignisse ermöglicht die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> und <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents> Schnittstellen. Für den Zugriff auf eine bestimmte Instanz des Projektelementtyps, behandeln <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> Ereignisse, z. B. <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> und <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized>.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht, wie Sie einen einfachen Projektelementtyp definieren. Dieser Projektelementtyp schreibt eine Meldung für die **Ausgabe** Fenster und **Fehlerliste** Fenster, wenn ein Benutzer ein Projektelement dieses Typs zu einem Projekt hinzufügt.  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#2](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemtype.vb#2)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#2](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemtype.cs#2)]  
  
 Dieses Beispiel verwendet die SharePoint-Projektdiensts zum Schreiben der Nachricht, die **Ausgabe** Fenster und **Fehlerliste** Fenster. Weitere Informationen finden Sie unter [verwenden SharePoint-Projektdiensts](../sharepoint/using-the-sharepoint-project-service.md).  
  
## <a name="compile-the-code"></a>Kompilieren des Codes  
 Dieses Beispiel erfordert Verweise auf die folgenden Assemblys:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-project-item"></a>Bereitstellen des Projektelements  
 Um Ihr Projektelement anderen Entwicklern zu ermöglichen, erstellen Sie eine Projektvorlage oder eine Projektelementvorlage. Weitere Informationen finden Sie unter [Erstellen von Vorlagen und Projektvorlagen für SharePoint-Projektelemente](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Erstellen Sie zum Bereitstellen des Projektelements eine [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] -Erweiterung (VSIX) Verpacken, für die Assembly, die Vorlage und alle anderen Dateien, die Sie mit dem Projektelement verteilen möchten. Weitere Informationen finden Sie unter [Bereitstellen von Erweiterungen für die SharePoint-tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Siehe auch
 [Definieren von benutzerdefinierten SharePoint-Projektelementtypen](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Erstellen von Elementvorlagen und Projektvorlagen für SharePoint-Projektelemente](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Exemplarische Vorgehensweise: Erstellen eines Projektelements benutzerdefinierte Aktion mit einer Elementvorlage, Teil 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Exemplarische Vorgehensweise: Erstellen eines Projektelements Spalte mit einer Projektvorlage, Teil 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [Vorgehensweise: Hinzufügen einer Eigenschaft zu einer benutzerdefinierten SharePoint-Projektelementtyp](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [Vorgehensweise: Hinzufügen eines Kontextmenüelements zu einer benutzerdefinierten SharePoint-Projektelementtyp](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)  

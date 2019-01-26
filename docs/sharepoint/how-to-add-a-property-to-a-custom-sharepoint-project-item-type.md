---
title: 'Vorgehensweise: Hinzufügen einer Eigenschaft zu einem benutzerdefinierten SharePoint-Projektelementtyp | Microsoft-Dokumentation'
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
ms.openlocfilehash: ca3bfbf6ecd773f0a7c3147a44eb02a5c260764b
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54872793"
---
# <a name="how-to-add-a-property-to-a-custom-sharepoint-project-item-type"></a>Vorgehensweise: Hinzufügen einer Eigenschaft zu einer benutzerdefinierten SharePoint-Projektelementtyp
  Wenn Sie einen benutzerdefinierten SharePoint-Projektelementtyp definieren, können Sie eine Eigenschaft auf das Projektelement hinzufügen. Die Eigenschaft wird in der **Eigenschaften** anzeigen, wenn das Projektelement in ausgewählt ist **Projektmappen-Explorer**.  
  
 Die folgenden Schritte wird davon ausgegangen, dass Sie bereits Ihre eigenen SharePoint-Projektelementtyp definiert haben. Weitere Informationen finden Sie unter [Vorgehensweise: Definieren Sie einen SharePoint-Projektelementtyp](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
### <a name="to-add-a-property-to-a-definition-of-a-project-item-type"></a>Eine Definition der einen Projektelementtyp eine Eigenschaft hinzu  
  
1.  Definieren Sie eine Klasse mit einer öffentlichen Eigenschaft, die die Eigenschaft darstellt, die Sie die benutzerdefinierten Projektelementtyp hinzufügen. Wenn Sie mehrere Eigenschaften um einen benutzerdefinierten Projektelementtyp hinzufügen möchten, können Sie alle Eigenschaften in der gleichen Klasse oder in unterschiedlichen Klassen definieren.  
  
2.  In der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> -Methode der Ihre <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> -Implementierung, das Handle der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> Ereignis die *ProjectItemTypeDefinition* Parameter.  
  
3.  Im Ereignishandler für die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> -Ereignis, fügen Sie eine Instanz dieser Klasse über benutzerdefinierte Eigenschaften der <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> Auflistung von Parameters für Ereignisargumente.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht, wie zum Hinzufügen einer Eigenschaft mit dem Namen **Beispieleigenschaft** an einen benutzerdefinierten Projektelementtyp.  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#11](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#11)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#11](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#11)]  
  
### <a name="understand-the-code"></a>Verstehen des Codes  
 Um sicherzustellen, dass auf die gleiche Instanz von der `CustomProperties` Klasse wird jedes Mal verwendet die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> Ereignis eintritt, im Codebeispiel wird gespeichert, das Eigenschaftenobjekt, das die <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> Eigenschaft Zeitspanne Element das erste Projekt dieses Ereignis tritt auf. Der Code ruft dieses Objekt ab, wenn dieses Ereignis erneut auftritt. Weitere Informationen zur Verwendung der <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> Eigenschaft zum Speichern von Daten mit Projektelementen finden Sie unter [Erweiterungen Zuordnen von benutzerdefinierte Daten mit SharePoint-tools](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
 Beibehalten von Änderungen an den Wert der Eigenschaft der **festgelegt** -Accessor für `ExampleProperty` speichert den neuen Wert, der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> Eigenschaft der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> -Objekt, das die Eigenschaft zugeordnet ist. Weitere Informationen zur Verwendung der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> Eigenschaft zum Speichern von Daten mit-Projektelemente, finden Sie unter [Speichern von Daten in Erweiterungen des SharePoint-Projektsystem](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
### <a name="specify-the-behavior-of-custom-properties"></a>Geben Sie das Verhalten von benutzerdefinierten Eigenschaften  
 Sie können definieren, wie eine benutzerdefinierte Eigenschaft angezeigt werden und verhält sich die **Eigenschaften** Fenster durch Anwenden von Attributen aus dem <xref:System.ComponentModel> Namespace auf die Eigenschaftsdefinition. Die folgenden Attribute sind in vielen Szenarien nützlich:  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>: Gibt den Namen der Eigenschaft, die in angezeigt wird der **Eigenschaften** Fenster.  
  
-   <xref:System.ComponentModel.DescriptionAttribute>: Gibt die Beschreibungszeichenfolge an, die angezeigt wird am unteren Rand der **Eigenschaften** anzeigen, wenn die Eigenschaft aktiviert ist.  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>: Gibt den Standardwert der Eigenschaft an.  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>: Gibt an, eine benutzerdefinierte Konvertierung zwischen der Zeichenfolge, die in angezeigt wird der **Eigenschaften** Fenster und einen nicht-zeichenfolgeneigenschafts-Wert.  
  
-   <xref:System.ComponentModel.EditorAttribute>: Gibt einen benutzerdefinierten Editor zum Ändern der Eigenschaft an.  
  
## <a name="compile-the-code"></a>Kompilieren des Codes  
 Diese Codebeispiele erfordern ein Klassenbibliotheksprojekt mit Verweisen auf die folgenden Assemblys:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-project-item"></a>Bereitstellen des Projektelements  
 Um Ihr Projektelement anderen Entwicklern zu ermöglichen, erstellen Sie eine Projektvorlage oder eine Projektelementvorlage. Weitere Informationen finden Sie unter [Erstellen von Vorlagen und Projektvorlagen für SharePoint-Projektelemente](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Erstellen Sie zum Bereitstellen des Projektelements eine [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] -Erweiterung (VSIX) Verpacken, für die Assembly, die Vorlage und alle anderen Dateien, die Sie mit dem Projektelement verteilen möchten. Weitere Informationen finden Sie unter [Bereitstellen von Erweiterungen für SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Siehe auch
 [Vorgehensweise: Definieren Sie einen SharePoint-Projektelementtyp](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [Vorgehensweise: Hinzufügen eines Kontextmenüelements zu einer benutzerdefinierten SharePoint-Projektelementtyp](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)   
 [Definieren von benutzerdefinierten SharePoint-Projektelementtypen](../sharepoint/defining-custom-sharepoint-project-item-types.md)  

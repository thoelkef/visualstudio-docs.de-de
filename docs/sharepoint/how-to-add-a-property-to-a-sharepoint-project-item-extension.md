---
title: 'Vorgehensweise: Hinzufügen einer Eigenschaft zu einer SharePoint-Projektelementerweiterung | Microsoft Docs'
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
ms.openlocfilehash: 50cbb0eb3a9c0c24abaa3734b7fa9cbd01e839b7
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2018
ms.locfileid: "34766726"
---
# <a name="how-to-add-a-property-to-a-sharepoint-project-item-extension"></a>Vorgehensweise: Hinzufügen einer Eigenschaft zu einer SharePoint-projektelementerweiterung
  Sie können eine projektelementerweiterung verwenden, hinzufügen eine Eigenschaft zu SharePoint-Projektelements, die in Visual Studio bereits installiert ist. Die Eigenschaft wird in der **Eigenschaften** Fenster, wenn das Projektelement in ausgewählt ist **Projektmappen-Explorer**.  
  
 Die folgenden Schritte wird davon ausgegangen, dass Sie eine projektelementerweiterung bereits erstellt haben. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen einer SharePoint-Projektelementerweiterung](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
### <a name="to-add-a-property-to-a-project-item-extension"></a>Hinzufügen eine Eigenschaft zu einer projektelementerweiterung  
  
1.  Definieren Sie eine Klasse mit einer öffentlichen Eigenschaft, die die Eigenschaft darstellt, die Sie einen Projektelementtyp hinzufügen. Wenn Sie einen Projektelementtyp mehrere Eigenschaften hinzufügen möchten, können Sie alle Eigenschaften in der gleichen Klasse oder in unterschiedlichen Klassen definieren.  
  
2.  In der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> Methode Ihrer <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> -Implementierung, Handle der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> -Ereignis für die *ProjectItemType* Parameter.  
  
3.  In den Ereignishandler für das <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> Ereignis, fügen Sie eine Instanz dieser Eigenschaftenklasse der <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> Auflistung von Parameters für die Ereignisargumente.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht, wie eine Eigenschaft mit dem Namen hinzugefügt **Beispieleigenschaft** dem Ereignisempfänger-Projektelement.  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemextensionproperty.cs#8)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemextensionproperty.vb#8)]  
  
### <a name="understanding-the-code"></a>Grundlegendes zum code  
 Um sicherzustellen, dass die gleiche Instanz von der `CustomProperties` Klasse wird jedes Mal verwendet die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> Ereignis tritt auf, die im Codebeispiel des Eigenschaften-Objekts, das die <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> Eigenschaft Zeitspanne Element der ersten Projekt dieses Ereignis tritt auf. Der Code ruft dieses Objekt ab, wenn dieses Ereignis erneut auftritt. Weitere Informationen zum Verwenden der <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> Eigenschaft zuordnen von Daten mit Projektelementen finden Sie unter [Zuordnen von benutzerdefinierten Daten zu SharePoint-Tools-Erweiterungen](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
 Damit Änderungen an den Eigenschaftswert beibehalten der **festgelegt** -Accessor für `ExampleProperty` speichert den neuen Wert, der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> Eigenschaft von der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> -Objekt, das die Eigenschaft zugeordnet ist. Weitere Informationen zum Verwenden der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> Eigenschaft zum Speichern von Daten mit Projektelementen finden Sie unter [speichern Daten in Erweiterungen des SharePoint-Projektsystem](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
### <a name="specifying-the-behavior-of-custom-properties"></a>Angeben des Verhaltens der benutzerdefinierten Eigenschaften  
 Sie können definieren, wie eine benutzerdefinierte Eigenschaft wird angezeigt und verhält sich in der **Eigenschaften** Fenster durch Anwenden von Attributen aus der <xref:System.ComponentModel> Namespace auf die Eigenschaftsdefinition. Die folgenden Attribute sind in vielen Szenarien nützlich:  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>: Gibt den Namen der Eigenschaft, die in der **Eigenschaften** Fenster.  
  
-   <xref:System.ComponentModel.DescriptionAttribute>: Gibt die Beschreibungszeichenfolge an, die angezeigt wird unten auf der die **Eigenschaften** Fenster, wenn die Eigenschaft ausgewählt ist.  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>: Gibt den Standardwert der Eigenschaft.  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>: Gibt eine benutzerdefinierte Konvertierung zwischen der Zeichenfolge, die in angezeigt wird der **Eigenschaften** Fenster und einen nicht-zeichenfolgeneigenschafts-Wert.  
  
-   <xref:System.ComponentModel.EditorAttribute>: Gibt einen benutzerdefinierten Editor zum Ändern der Eigenschaft an.  
  
## <a name="compiling-the-code"></a>Kompilieren des Codes  
 Diese Beispiele erfordern ein Klassenbibliotheksprojekt mit Verweisen auf die folgenden Assemblys:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Bereitstellen der Erweiterung  
 Zum Bereitstellen der Erweiterung erstellen Sie eine [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] -Erweiterung (VSIX) Verpacken, für die Assembly und alle anderen Dateien, die Sie mit der Erweiterung verteilen möchten. Weitere Informationen finden Sie unter [Bereitstellen von Erweiterungen für SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Siehe auch
 [Vorgehensweise: erstellen eine SharePoint-Projektelementerweiterung](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [Vorgehensweise: Hinzufügen ein Kontextmenüelements zu einer SharePoint-Projektelementerweiterung](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)   
 [Erweitern von SharePoint-Projektelementen](../sharepoint/extending-sharepoint-project-items.md)   
 [Exemplarische Vorgehensweise: Erweitern eines SharePoint-Projektelementtyps](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
  

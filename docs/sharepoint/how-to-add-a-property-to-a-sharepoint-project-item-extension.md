---
title: 'Vorgehensweise: Hinzufügen einer Eigenschaft zu einer SharePoint-Projektelementerweiterung | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6dc2c0588fa3078a805f9804263afcf521ae72ed
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56644428"
---
# <a name="how-to-add-a-property-to-a-sharepoint-project-item-extension"></a>Vorgehensweise: Hinzufügen einer Eigenschaft zu einer SharePoint-projektelementerweiterung
  Sie können eine projektelementerweiterung verwenden, zum Hinzufügen einer Eigenschaft zu SharePoint-Projektelements, das in Visual Studio bereits installiert ist. Die Eigenschaft wird in der **Eigenschaften** anzeigen, wenn das Projektelement in ausgewählt ist **Projektmappen-Explorer**.

 Die folgenden Schritte wird davon ausgegangen, dass Sie eine projektelementerweiterung bereits erstellt haben. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen eine SharePoint-Projektelementerweiterung](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

### <a name="to-add-a-property-to-a-project-item-extension"></a>Zum Hinzufügen einer Eigenschaft zu einer projektelementerweiterung

1.  Definieren Sie eine Klasse mit einer öffentlichen Eigenschaft, die die Eigenschaft darstellt, die Sie einen Projektelementtyp hinzufügen. Wenn Sie mehrere Eigenschaften eines Projektelementtyps hinzufügen möchten, können Sie alle Eigenschaften in der gleichen Klasse oder in unterschiedlichen Klassen definieren.

2.  In der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> -Methode der Ihre <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> -Implementierung, das Handle der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> Ereignis die *ProjectItemType* Parameter.

3.  Im Ereignishandler für die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> -Ereignis, fügen Sie eine Instanz dieser Eigenschaftenklasse der <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> Auflistung von Parameters für Ereignisargumente.

## <a name="example"></a>Beispiel
 Im folgenden Codebeispiel wird veranschaulicht, wie zum Hinzufügen einer Eigenschaft mit dem Namen **Beispieleigenschaft** auf das Projektelement-Ereignisempfänger verwenden.

 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemextensionproperty.cs#8)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemextensionproperty.vb#8)]

### <a name="understand-the-code"></a>Verstehen des Codes
 Um sicherzustellen, dass auf die gleiche Instanz von der `CustomProperties` Klasse wird verwendet, jedes Mal die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> Ereignis auftritt, die im Codebeispiel wird das Eigenschaftenobjekt in die <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> Eigenschaft Zeitspanne Element das erste Projekt dieses Ereignis tritt auf. Der Code ruft dieses Objekt ab, wenn dieses Ereignis erneut auftritt. Weitere Informationen zur Verwendung der <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> -Eigenschaft zum Zuordnen von Daten zu Projektelemente, finden Sie unter [Erweiterungen Zuordnen von benutzerdefinierte Daten mit SharePoint-tools](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

 Beibehalten von Änderungen an den Wert der Eigenschaft der **festgelegt** -Accessor für `ExampleProperty` speichert den neuen Wert, der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> Eigenschaft der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> -Objekt, das die Eigenschaft zugeordnet ist. Weitere Informationen zur Verwendung der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> Eigenschaft zum Speichern von Daten mit-Projektelemente, finden Sie unter [Speichern von Daten in Erweiterungen des SharePoint-Projektsystem](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

### <a name="specify-the-behavior-of-custom-properties"></a>Geben Sie das Verhalten von benutzerdefinierten Eigenschaften
 Sie können definieren, wie eine benutzerdefinierte Eigenschaft angezeigt werden und verhält sich die **Eigenschaften** Fenster durch Anwenden von Attributen aus dem <xref:System.ComponentModel> Namespace auf die Eigenschaftsdefinition. Die folgenden Attribute sind in vielen Szenarien nützlich:

-   <xref:System.ComponentModel.DisplayNameAttribute>: Gibt den Namen der Eigenschaft, die in angezeigt wird der **Eigenschaften** Fenster.

-   <xref:System.ComponentModel.DescriptionAttribute>: Gibt die Beschreibungszeichenfolge an, die angezeigt wird am unteren Rand der **Eigenschaften** anzeigen, wenn die Eigenschaft aktiviert ist.

-   <xref:System.ComponentModel.DefaultValueAttribute>: Gibt den Standardwert der Eigenschaft an.

-   <xref:System.ComponentModel.TypeConverterAttribute>: Gibt an, eine benutzerdefinierte Konvertierung zwischen der Zeichenfolge, die in angezeigt wird der **Eigenschaften** Fenster und einen nicht-zeichenfolgeneigenschafts-Wert.

-   <xref:System.ComponentModel.EditorAttribute>: Gibt einen benutzerdefinierten Editor zum Ändern der Eigenschaft an.

## <a name="compile-the-code"></a>Kompilieren des Codes
 Diese Beispiele erfordern ein Klassenbibliotheksprojekt mit Verweisen auf die folgenden Assemblys:

-   Microsoft.VisualStudio.SharePoint

-   System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Bereitstellen der Erweiterung
 Erstellen Sie zum Bereitstellen der Erweiterungs eine [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] -Erweiterung (VSIX) Verpacken, für die Assembly und alle anderen Dateien, die Sie mit der Erweiterung verteilen möchten. Weitere Informationen finden Sie unter [Bereitstellen von Erweiterungen für SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Siehe auch
- [Vorgehensweise: Erstellen einer SharePoint-projektelementerweiterung](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)
- [Vorgehensweise: Hinzufügen eines Kontextmenüelements zu einer SharePoint-projektelementerweiterung](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)
- [Erweitern von SharePoint-Projektelemente](../sharepoint/extending-sharepoint-project-items.md)
- [Exemplarische Vorgehensweise: Erweitern eines SharePoint-Projektelementtyps](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)

---
title: 'Vorgehensweise: Hinzufügen einer Eigenschaft zu SharePoint-Projekte | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fe3b94d7f2072565b2adc2ab7c3c9825ca21ad57
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-a-property-to-sharepoint-projects"></a>Gewusst wie: Hinzufügen einer Eigenschaft zu SharePoint-Projekten
  Sie können eine projekterweiterung verwenden, zum Hinzufügen einer Eigenschaft zu einem SharePoint-Projekt. Die Eigenschaft wird in der **Eigenschaften** Fenster beim Erstellen des Projekts ausgewählt ist, in **Projektmappen-Explorer**.  
  
 Die folgenden Schritte wird davon ausgegangen, dass Sie bereits eine projekterweiterung erstellt haben. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen einer SharePoint-Projekterweiterung](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
### <a name="to-add-a-property-to-a-sharepoint-project"></a>Hinzufügen eine Eigenschaft zu einem SharePoint-Projekt  
  
1.  Definieren Sie eine Klasse mit einer öffentlichen Eigenschaft, die die Eigenschaft darstellt, die Sie für SharePoint-Projekte hinzufügen. Wenn Sie mehrere Eigenschaften hinzufügen möchten, können Sie alle Eigenschaften in der gleichen Klasse oder in unterschiedlichen Klassen definieren.  
  
2.  In der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> Methode Ihrer <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> -Implementierung, Handle der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> -Ereignis für die *ProjectService* Parameter.  
  
3.  In den Ereignishandler für das <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> Ereignis, fügen Sie eine Instanz dieser Eigenschaftenklasse der <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectPropertiesRequestedEventArgs.PropertySources%2A> Auflistung von Parameters für die Ereignisargumente.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht, wie zwei Eigenschaften für SharePoint-Projekte hinzufügen. Eine Eigenschaft weiterhin besteht, die Daten in der Projektdatei des Benutzers Option (die. csproj.user-Datei oder. vbproj.user-Datei). Die Eigenschaft speichert die Daten in der Projektdatei (CSPROJ oder VBPROJ-Datei).  
  
 [!code-vb[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#1)]
 [!code-csharp[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#1)]  
  
### <a name="understanding-the-code"></a>Grundlegendes zum Code  
 Um sicherzustellen, dass die gleiche Instanz von der `CustomProjectProperties` Klasse wird jedes Mal verwendet die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> Ereignis tritt auf, die im Codebeispiel des Eigenschaften-Objekts, das die <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> Eigenschaft, der das Projekt das erste Mal dieses Ereignis tritt auf. Der Code ruft dieses Objekt ab, wenn dieses Ereignis erneut auftritt. Weitere Informationen zum Verwenden der <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> Eigenschaft zuordnen von Daten mit Projekten finden Sie unter [Zuordnen von benutzerdefinierten Daten zu SharePoint-Tools-Erweiterungen](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
 Beibehalten der Änderungen von Eigenschaftswerten, die **festgelegt** Accessoren für die Eigenschaften verwenden Sie die folgenden APIs:  
  
-   `CustomUserFileProperty` verwendet die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> Eigenschaft, um den Wert in der Benutzerdatei Option Projekt speichern.  
  
-   `CustomProjectFileProperty` verwendet die <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> Methode, um seinen Wert in der Projektdatei zu speichern.  
  
 Weitere Informationen zum Beibehalten von Daten in diesen Dateien finden Sie unter [speichern Daten in Erweiterungen des SharePoint-Projektsystem](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
### <a name="specifying-the-behavior-of-custom-properties"></a>Angeben des Verhaltens der benutzerdefinierten Eigenschaften  
 Sie können definieren, wie eine benutzerdefinierte Eigenschaft wird angezeigt und verhält sich in der **Eigenschaften** Fenster durch Anwenden von Attributen aus der <xref:System.ComponentModel> Namespace auf die Eigenschaftsdefinition. Die folgenden Attribute sind in vielen Szenarien nützlich:  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>: Gibt den Namen der Eigenschaft, die in der **Eigenschaften** Fenster.  
  
-   <xref:System.ComponentModel.DescriptionAttribute>: Gibt die Beschreibungszeichenfolge an, die angezeigt wird unten auf der die **Eigenschaften** Fenster, wenn die Eigenschaft ausgewählt ist.  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>: Gibt den Standardwert der Eigenschaft.  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>: Gibt eine benutzerdefinierte Konvertierung zwischen der Zeichenfolge, die in angezeigt wird der **Eigenschaften** Fenster und einen nicht-zeichenfolgeneigenschafts-Wert.  
  
-   <xref:System.ComponentModel.EditorAttribute>: Gibt einen benutzerdefinierten Editor zum Ändern der Eigenschaft an.  
  
## <a name="compiling-the-code"></a>Kompilieren des Codes  
 Dieses Beispiel erfordert Verweise auf die folgenden Assemblys:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.Shell  
  
-   Microsoft.VisualStudio.Shell.Interop  
  
-   Microsoft.VisualStudio.Shell.Interop.8.0  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Bereitstellen der Erweiterung  
 Zum Bereitstellen der Erweiterung erstellen Sie eine [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] -Erweiterung (VSIX) Verpacken, für die Assembly und alle anderen Dateien, die Sie mit der Erweiterung verteilen möchten. Weitere Informationen finden Sie unter [Bereitstellen von Erweiterungen für SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern von SharePoint-Projekten](../sharepoint/extending-sharepoint-projects.md)   
 [Vorgehensweise: Erstellen einer SharePoint-Projekterweiterung](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [Vorgehensweise: Hinzufügen ein Kontextmenüelements zu SharePoint-Projekten](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [Erweitern des SharePoint-Projektsystems](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  
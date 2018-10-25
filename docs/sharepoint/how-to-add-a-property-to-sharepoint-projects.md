---
title: 'Vorgehensweise: Hinzufügen einer Eigenschaft zu SharePoint-Projekte | Microsoft-Dokumentation'
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
ms.openlocfilehash: c956da1df5507d2efecb3ff72f034d54fb377eb5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49898409"
---
# <a name="how-to-add-a-property-to-sharepoint-projects"></a>Gewusst wie: Hinzufügen einer Eigenschaft zu SharePoint-Projekte
  Sie können eine projekterweiterung verwenden, zum Hinzufügen einer Eigenschaft zu einem SharePoint-Projekt. Die Eigenschaft wird in der **Eigenschaften** Wartungszeitfensters, in das Projekt ausgewählt ist, im **Projektmappen-Explorer**.  
  
 Die folgenden Schritte wird davon ausgegangen, dass Sie bereits eine projekterweiterung erstellt haben. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen einer SharePoint-projekterweiterung](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
### <a name="to-add-a-property-to-a-sharepoint-project"></a>Eine Eigenschaft zu einer SharePoint-Projekt hinzufügen  
  
1.  Definieren Sie eine Klasse mit einer öffentlichen Eigenschaft, die die Eigenschaft darstellt, die Sie für SharePoint-Projekte hinzufügen. Wenn Sie mehrere Eigenschaften hinzufügen möchten, können Sie alle Eigenschaften in der gleichen Klasse oder in unterschiedlichen Klassen definieren.  
  
2.  In der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> -Methode der Ihre <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> -Implementierung, das Handle der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> Ereignis die *Anwendbarkeitsprüfungen* Parameter.  
  
3.  Im Ereignishandler für die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> -Ereignis, fügen Sie eine Instanz dieser Eigenschaftenklasse der <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectPropertiesRequestedEventArgs.PropertySources%2A> Auflistung von Parameters für Ereignisargumente.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht, wie zwei Eigenschaften für SharePoint-Projekte hinzugefügt. Eine Eigenschaft behalten deren Daten in der Benutzeroptionsdatei (die *. csproj.user* Datei oder *. vbproj.user* Datei). Die andere Eigenschaft behalten deren Daten in der Projektdatei (*csproj* Datei oder *vbproj* Datei).  
  
 [!code-vb[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#1)]
 [!code-csharp[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#1)]  
  
### <a name="understand-the-code"></a>Verstehen des Codes  
 Um sicherzustellen, dass auf die gleiche Instanz von der `CustomProjectProperties` Klasse wird verwendet, jedes Mal die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> Ereignis auftritt, die im Codebeispiel wird das Eigenschaftenobjekt in der <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> Eigenschaft, der das Projekt das erste Mal dieses Ereignis tritt auf. Der Code ruft dieses Objekt ab, wenn dieses Ereignis erneut auftritt. Weitere Informationen zur Verwendung der <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> -Eigenschaft zum Zuordnen von Daten zu Projekten finden Sie unter [Erweiterungen Zuordnen von benutzerdefinierte Daten mit SharePoint-tools](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
 Beibehalten von Änderungen an die Werte, die **festgelegt** Accessoren für Eigenschaften verwenden Sie die folgenden APIs:  
  
- `CustomUserFileProperty` verwendet die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> Eigenschaft, um den Wert in der Benutzeroptionsdatei zu speichern.  
  
- `CustomProjectFileProperty` verwendet die <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> Methode, um den Wert in der Projektdatei zu speichern.  
  
  Weitere Informationen zum Beibehalten von Daten in diesen Dateien finden Sie unter [Speichern von Daten in Erweiterungen des SharePoint-Projektsystem](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
### <a name="specify-the-behavior-of-custom-properties"></a>Geben Sie das Verhalten von benutzerdefinierten Eigenschaften  
 Sie können definieren, wie eine benutzerdefinierte Eigenschaft angezeigt werden und verhält sich die **Eigenschaften** Fenster durch Anwenden von Attributen aus dem <xref:System.ComponentModel> Namespace auf die Eigenschaftsdefinition. Die folgenden Attribute sind in vielen Szenarien nützlich:  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>: Gibt an, den Namen der Eigenschaft, die in angezeigt wird der **Eigenschaften** Fenster.  
  
-   <xref:System.ComponentModel.DescriptionAttribute>: Gibt an, die Description-Zeichenfolge, die angezeigt wird am unteren Rand der **Eigenschaften** anzeigen, wenn die Eigenschaft aktiviert ist.  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>: Gibt an, der Standardwert der Eigenschaft.  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>: Gibt an, eine benutzerdefinierte Konvertierung zwischen der Zeichenfolge, die in angezeigt wird der **Eigenschaften** Fenster und einen nicht-zeichenfolgeneigenschafts-Wert.  
  
-   <xref:System.ComponentModel.EditorAttribute>: Gibt einen benutzerdefinierten Editor zum Ändern der Eigenschaft.  
  
## <a name="compile-the-code"></a>Kompilieren des Codes  
 Dieses Beispiel erfordert Verweise auf die folgenden Assemblys:  
  
-   Microsoft.VisualStudio.SharePoint
-    
-   Microsoft.VisualStudio.Shell
-     
-   Microsoft.VisualStudio.Shell.Interop
-     
-   Microsoft.VisualStudio.Shell.Interop.8.0
-     
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-extension"></a>Bereitstellen der Erweiterung  
 Erstellen Sie zum Bereitstellen der Erweiterungs eine [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] -Erweiterung (VSIX) Verpacken, für die Assembly und alle anderen Dateien, die Sie mit der Erweiterung verteilen möchten. Weitere Informationen finden Sie unter [Bereitstellen von Erweiterungen für SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Siehe auch
 [Erweitern von SharePoint-Projekte](../sharepoint/extending-sharepoint-projects.md)   
 [Gewusst wie: Erstellen einer SharePoint-projekterweiterung](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [Gewusst wie: Hinzufügen ein Kontextmenüelements zu SharePoint-Projekten](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [Erweitern von SharePoint-Projektsystem](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  

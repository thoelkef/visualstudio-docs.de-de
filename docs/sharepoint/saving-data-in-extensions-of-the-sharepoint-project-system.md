---
title: Speichern von Daten in Erweiterungen des SharePoint-Projektsystems | Microsoft Docs
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SharePoint project items, saving string data
- project items [SharePoint development in Visual Studio], saving string data
- projects [SharePoint development in Visual Studio], saving string data
- SharePoint projects, saving string data
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 56cdfb95de6f0e5f8644ea3c73daacbf90e33a97
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="saving-data-in-extensions-of-the-sharepoint-project-system"></a>Speichern von Daten in Erweiterungen des SharePoint-Projektsystems
  Wenn Sie die SharePoint-Projektsystem erweitern, können Sie Zeichenfolgendaten speichern, die erhalten bleibt, nachdem eine SharePoint-Projekt geschlossen wird. Die Daten sind in der Regel mit einem bestimmten Projektelement oder das Projekt selbst zugeordnet.  
  
 Wenn Sie über Daten, die nicht persistent speichern müssen verfügen, können Sie die Daten hinzufügen, auf ein beliebiges Objekt in der SharePoint-Tools-Objektmodell, die implementiert die <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> Schnittstelle. Weitere Informationen finden Sie unter [Zuordnen von benutzerdefinierten Daten zu SharePoint-Tools-Erweiterungen](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
## <a name="saving-data-that-is-associated-with-a-project-item"></a>Speichern von Daten, die zugeordnet ist ein Projektelement  
 Bei Daten, die einem bestimmten SharePoint-Projektelement, z. B. den Wert einer Eigenschaft zugeordnet ist, die Sie in der ein Projektelement hinzufügen können Sie die Daten in der SPDATA-Datei für das Projektelement speichern. Verwenden Sie hierzu die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> Eigenschaft ein <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> Objekt. Daten, die Sie, um diese Eigenschaft hinzufügen werden gespeichert, der **ExtensionData** -Element in der SPDATA-Datei für das Projektelement. Weitere Informationen finden Sie unter [ExtensionData-Element](../sharepoint/extensiondata-element.md).  
  
 Im folgenden Codebeispiel wird veranschaulicht, wie die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> Eigenschaft, um den Wert des eine Zeichenfolgeneigenschaft zu speichern, die in einem benutzerdefinierten SharePoint-Projektelementtyp definiert ist. Dieses Beispiel im Kontext eines umfangreicheren Beispiels finden Sie unter [wie: Hinzufügen einer Eigenschaft zu einem benutzerdefinierten SharePoint-Projektelementtyp](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#14)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#14)]  
  
## <a name="saving-data-that-is-associated-with-a-project"></a>Speichern von Daten, die zugeordnet ist ein Projekt  
 Bei auf Projektebene-Daten, z. B. den Wert einer Eigenschaft, die Sie für SharePoint-Projekte hinzufügen können Sie die Daten in der Projektdatei (CSPROJ-Datei oder VBPROJ-Datei) oder die Projektdatei des Benutzers Option speichern (die. csproj.user-Datei oder. vbproj.user-Datei). Die Datei, der Sie zum Speichern der Daten in auswählen, hängt davon ab, wie Sie die Daten verwendet werden sollen:  
  
-   Wenn Sie möchten die Daten zur Verfügung stehen alle Entwickler, die das SharePoint-Projekt zu öffnen, speichern Sie die Daten in die Projektdatei. Diese Datei wird in Steuerelement Quelldatenbanken, immer eingecheckt, damit die Daten in dieser Datei an andere Entwickler verfügbar ist, die das Projekt auscheckt.  
  
-   Wenn Sie möchten die Daten nur für den aktuellen-Entwickler verfügbar ist, hat der SharePoint-Projekt in Visual Studio öffnen, speichern Sie die Daten in die Projektdatei des Benutzers Option. Diese Datei ist nicht in der Regel Steuerelement Quelldatenbanken, eingecheckt, damit die Daten in dieser Datei nicht an andere Entwickler verfügbar ist, die das Projekt auscheckt.  
  
### <a name="saving-data-to-the-project-file"></a>Speichern von Daten in der Projektdatei  
 Zum Speichern von Daten in der Projektdatei Konvertieren einer <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> -Objekt an eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> -Objekts und anschließendes Verwenden der <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> Methode. Im folgenden Codebeispiel wird veranschaulicht, wie diese Methode verwendet, um den Wert einer Projekteigenschaft in der Projektdatei zu speichern. Dieses Beispiel im Kontext einer größeren Codebeispiel finden Sie unter [wie: Hinzufügen einer Eigenschaft zu SharePoint-Projekte](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  
  
 [!code-vb[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#3)]
 [!code-csharp[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#3)]  
  
 Weitere Informationen zum Konvertieren von <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> Objekten in andere Typen in der Visual Studio-Automatisierungsobjektmodell oder-Integrationsobjektmodell finden Sie unter [Konvertieren zwischen SharePoint-Projektsystemtypen und anderen Visual Studio-Projekttypen ](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).  
  
### <a name="saving-data-to-the-project-user-option-file"></a>Speichern von Daten in der Projektdatei des Benutzers Option  
 Verwenden Sie zum Speichern von Daten in der Projektdatei des Benutzers Option die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> Eigenschaft ein <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> Objekt. Im folgenden Codebeispiel wird veranschaulicht, wie diese Eigenschaft verwendet, um den Wert einer Projekteigenschaft in der Benutzerdatei Option Projekt zu speichern. Dieses Beispiel im Kontext einer größeren Codebeispiel finden Sie unter [wie: Hinzufügen einer Eigenschaft zu SharePoint-Projekte](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  
  
 [!code-vb[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#2)]
 [!code-csharp[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#2)]  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern des SharePoint-Projektsystems](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Zuordnen von benutzerdefinierten Daten zu SharePoint-Tools-Erweiterungen](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)   
 [Konvertieren zwischen SharePoint-Projektsystemtypen und anderen Visual Studio-Projekttypen](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)  
  
  
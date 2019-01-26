---
title: Speichern von Daten in Erweiterungen des SharePoint-Projektsystems | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: conceptual
helpviewer_keywords:
- SharePoint project items, saving string data
- project items [SharePoint development in Visual Studio], saving string data
- projects [SharePoint development in Visual Studio], saving string data
- SharePoint projects, saving string data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 373f031795238c599d15eec92f1730289662c3a0
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54866541"
---
# <a name="save-data-in-extensions-of-the-sharepoint-project-system"></a>Speichern von Daten in Erweiterungen des SharePoint-Projektsystem
  Wenn Sie SharePoint-Projektsystem erweitern, können Sie Zeichenfolgedaten speichern, die erhalten bleibt, nachdem ein SharePoint-Projekt geschlossen wird. Die Daten sind in der Regel mit einem bestimmten Projekt-Element oder das Projekt selbst zugeordnet.  
  
 Wenn Sie über Daten, die nicht beibehalten werden muss verfügen, können Sie die Daten hinzufügen, auf ein beliebiges Objekt in der SharePoint-Tools-Objektmodell, die implementiert die <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> Schnittstelle. Weitere Informationen finden Sie unter [Erweiterungen Zuordnen von benutzerdefinierte Daten mit SharePoint-tools](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
## <a name="save-data-that-is-associated-with-a-project-item"></a>Speichern von Daten, die mit einem Projektelement verknüpft ist
 Wenn Sie über Daten verfügen, die einer bestimmten SharePoint-Projektelement, z. B. den Wert einer Eigenschaft zugeordnet ist, die Sie auf ein Projektelement hinzufügen können, speichern Sie die Daten, die *SPDATA* -Datei für das Projektelement. Verwenden Sie hierzu die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> Eigenschaft ein <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> Objekt. Daten, die Sie, um diese Eigenschaft hinzufügen werden gespeichert, der **ExtensionData** Element in der *SPDATA* -Datei für das Projektelement. Weitere Informationen finden Sie unter [ExtensionData-Element](../sharepoint/extensiondata-element.md).  
  
 Im folgenden Codebeispiel wird veranschaulicht, wie Sie mit der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> Eigenschaft, um den Wert einer Zeichenfolgeneigenschaft zu speichern, die in einer benutzerdefinierten SharePoint-Projektelementtyp definiert ist. Dieses Beispiel im Kontext eines größeren Beispiels, finden Sie unter [Vorgehensweise: Hinzufügen einer Eigenschaft zu einer benutzerdefinierten SharePoint-Projektelementtyp](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#14)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#14)]  
  
## <a name="save-data-that-is-associated-with-a-project"></a>Speichern von Daten, die einem Projekt zugeordnet ist.
 Bei Daten auf Projektebene, z. B. den Wert einer Eigenschaft, die Sie für SharePoint-Projekte, hinzufügen, können Sie die Daten in der Projektdatei speichern (die *csproj* Datei oder *vbproj* Datei) oder die Option für Projekt Datei (die *. csproj.user* Datei oder *. vbproj.user* Datei). Die Datei zum Speichern der Daten im gewählten hängt davon ab, wie Sie die Daten verwendet werden sollen:  
  
-   Wenn Sie möchten die Daten für alle Entwickler verfügbar sein, die die SharePoint-Projekt öffnen, können Sie die Daten in der Projektdatei gespeichert. Diese Datei wird immer auf Quelldatenbanken-Steuerelement, eingecheckt, damit die Daten in dieser Datei für andere Entwickler verfügbar ist, die das Projekt auschecken.  
  
-   Wenn Sie möchten die Daten nur für Entwickler verfügbar sein sollen, wer das SharePoint-Projekt in Visual Studio geöffnet haben, können speichern Sie die Daten in der Benutzeroptionsdatei. Diese Datei ist nicht in der Regel auf Quelldatenbanken-Steuerelement, eingecheckt, damit die Daten in dieser Datei nicht an andere Entwickler verfügbar ist, die das Projekt auschecken.  
  
### <a name="save-data-to-the-project-file"></a>Speichern Sie Daten in der Projektdatei
 Um Daten in der Projektdatei speichern möchten, konvertieren eine <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> -Objekt an eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> Objekt aus, und verwenden Sie dann die <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> Methode. Im folgenden Codebeispiel wird veranschaulicht, wie Sie mithilfe dieser Methode den Wert einer Projekteigenschaft in der Projektdatei speichern. Dieses Beispiel im Kontext eines größeren Beispiels, finden Sie unter [Vorgehensweise: Hinzufügen einer Eigenschaft zu SharePoint-Projekte](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  
  
 [!code-vb[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#3)]
 [!code-csharp[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#3)]  
  
 Weitere Informationen zum Konvertieren von <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> Objekte für andere Typen in der Visual Studio-Automatisierungsobjektmodell oder-Integrationsobjektmodell [Konvertieren zwischen SharePoint-Projektsystemtypen und anderen Visual Studio-Projekttypen](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).  
  
### <a name="save-data-to-the-project-user-option-file"></a>Speichern Sie Daten in der Benutzeroptionsdatei.
 Verwenden, um Daten in der Benutzeroptionsdatei zu speichern, die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> Eigenschaft eine <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> Objekt. Im folgenden Codebeispiel wird veranschaulicht, wie Sie diese Eigenschaft verwenden, um den Wert einer Projekteigenschaft in der Benutzeroptionsdatei speichern. Dieses Beispiel im Kontext eines größeren Beispiels, finden Sie unter [Vorgehensweise: Hinzufügen einer Eigenschaft zu SharePoint-Projekte](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  
  
 [!code-vb[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#2)]
 [!code-csharp[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#2)]  
  
## <a name="see-also"></a>Siehe auch
 [Erweitern von SharePoint-Projektsystem](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Zuordnen von benutzerdefinierten Daten zu SharePoint-Tools-Erweiterungen](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)   
 [Konvertieren Sie zwischen SharePoint-Projektsystemtypen und anderen Visual Studio-Projekttypen](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)  

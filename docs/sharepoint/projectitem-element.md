---
title: ProjectItem-Element | Microsoft Docs
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
helpviewer_keywords: ProjectItem element
ms.assetid: df588235-12a1-4798-bc56-ef81843de17f
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e8a9f1ac258f6501aedb2fd89ce21514d785b25f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="projectitem-element"></a>ProjectItem-Element
  Stellt ein SharePoint-Projektelement dar. Dies ist das erforderliche Stammelement der SPDATA-Datei.  
  
## <a name="syntax"></a>Syntax  
  
```  
<ProjectItem DefaultFile = "File that opens in the editor when you open the project item"  
    FeatureReceiverClass = "Class that implements a feature receiver for the project item"  
    FeatureReceiverAssembly = "Assembly that defines a feature receiver for the project item"  
    SupportedTrustLevels = "Trust levels that the project item supports"  
    SupportedDeploymentScopes = "Deployment scopes that the project item supports"  
    Type="Identifier for the project item">  
  <Files>...</Files>  
  <ProjectItemFolder>...</ProjectItemFolder>  
  <SafeControls>...</SafeControls>  
  <FeatureProperties>...</FeatureProperties>  
  <ExtensionData>...</ExtensionData>  
</ProjectItem>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|**DefaultFile**|Optionale **xs: String** Attribut.<br /><br /> Der relative Pfad, einschließlich des Dateinamens, der Datei, die in der Visual Studio-Editor wird, beim Öffnen der SharePoint-Projektelement in geöffnet **Projektmappen-Explorer**. Der Pfad ist relativ aus dem Ordner, der die SPDATA-Datei enthält.|  
|**FeatureReceiverClass**|Optionale **xs: String** Attribut.<br /><br /> Der vollqualifizierte Name einer Klasse der Funktion Empfänger für diese SharePoint-Projektelement. Weitere Informationen zum Feature Empfänger finden Sie unter [Bereitstellen von Pack- und Bereitstellungsinformationen in Projektelementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|  
|**FeatureReceiverAssembly**|Optionale **xs: String** Attribut.<br /><br /> Gibt den vollqualifizierten Namen einer Assembly, die einen Funktionsempfänger für diese SharePoint-Projektelements definiert. Weitere Informationen zum Feature Empfänger finden Sie unter [Bereitstellen von Pack- und Bereitstellungsinformationen in Projektelementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md). Weitere Informationen zu vollqualifizierten Assemblynamen finden Sie unter [Assemblynamen](/dotnet/framework/app-domains/assembly-names).|  
|**SupportedTrustLevels**|Optionale **xs: String** Attribut.<br /><br /> Gibt die Vertrauensebenen, die diese SharePoint-Projektelement unterstützt. Dieser Wert kann eine der folgenden Zeichenfolgen: Sandkasten, FullTrust oder alle. Der Wert All Sandkasten und FullTrust gibt.<br /><br /> In einem benutzerdefinierten SharePoint-Projektelementtyp, der Wert dieses Attributs entspricht dem Wert, den Sie zum Zuweisen der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> Eigenschaft in der Implementierung von der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> Methode. Wenn Sie einen anderen Wert für dieses Attribut angeben, überschreibt Visual Studio den Wert so, dass die gleiche Vertrauensebene angegeben wird, die Sie, in angeben der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> Eigenschaft.|  
|**SupportedDeploymentScopes**|Optionale **xs: String** Attribut.<br /><br /> Gibt die Bereitstellungsbereiche, die diese SharePoint-Projektelement unterstützt. Dieser Wert ist eine durch Trennzeichen getrennte Zeichenfolge, die besteht aus einem oder mehreren der folgenden Zeichenfolgen: Farm, Website, Web, WebApplication oder Paket. Z. B. "Web Site".<br /><br /> In einem benutzerdefinierten SharePoint-Projektelementtyp, der Wert dieses Attributs entspricht dem Wert, den Sie zum Zuweisen der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> Eigenschaft in der Implementierung von der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> Methode. Wenn Sie einen anderen Wert für dieses Attribut angeben, überschreibt Visual Studio den Wert so, dass die gleiche Vertrauensebene angegeben wird, die Sie, in angeben der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> Eigenschaft.|  
|**Typ**|Erforderliche **xs: String** Attribut.<br /><br /> Der Bezeichner für die SharePoint-Projektelement. In einem benutzerdefinierten SharePoint-Projektelementtyp der Bezeichner ist die Zeichenfolge, die Sie zum Übergeben der <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. Weitere Informationen finden Sie unter [wie: Definieren Sie einen SharePoint-Projektelementtyp](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).<br /><br /> Eine Liste der Bezeichner für den integrierten SharePoint-Projektelemente, die mit Visual Studio enthalten, finden Sie unter [Erweitern von SharePoint-Projektelemente](../sharepoint/extending-sharepoint-project-items.md).|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|Optionales Element.<br /><br /> Stellt eine Auflistung benutzerdefinierter Datenelemente, die SharePoint-Projektelements zugeordnet sind.<br /><br /> Sie können nur eine einschließen **ExtensionData** Element.|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Optionales Element.<br /><br /> Stellt eine Auflistung von Eigenschaftswerten, die in eine Funktion eingeschlossen werden, wenn er für SharePoint bereitgestellt wird.<br /><br /> Sie können nur eine einschließen **FeatureProperties** Element.|  
|[Dateien](../sharepoint/files-element.md)|Optionale **FileCollectionType** Element.<br /><br /> Gibt die Dateien, die mit der SharePoint-Projektelement, z. B. featuredateien-Element und die Ausgabe der abhängigen nicht-SharePoint-Projekten bereitgestellt.<br /><br /> Müssen Sie auch entweder ein **Dateien** oder ein **ProjectItemFolder** -Element, aber nicht beides.|  
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|Optionale **ProjectItemFolderType** Element.<br /><br /> Stellt einen zugeordneten Ordner dar.<br /><br /> Müssen Sie auch entweder ein **Dateien** oder ein **ProjectItemFolder** -Element, aber nicht beides.|  
|["SafeControls"](../sharepoint/safecontrols-element.md)|Optionales Element.<br /><br /> Stellt eine Auflistung von ASPX-Steuerelementen und Webparts, die als sichere für alle Benutzer Zugriff auf alle ASPX-Seite auf der SharePoint-Website festgelegt werden.<br /><br /> Sie können nur eine einschließen **"SafeControls"** Element.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
 Keine  
  
## <a name="element-information"></a>Elementinformationen  
  
|||  
|-|-|  
|**Namespace**|http://Schemas.Microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**Schemaname**|SharePoint-Projektelementschema|  
|**Validierungsdatei**|"ProjectItemModelSchema.xsd" benannt|  
|**Kann leer sein**|Nein|  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz zum SharePoint-Projektelementschema](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  
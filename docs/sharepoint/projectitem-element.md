---
title: "ProjectItem Element | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "ProjectItem element"
ms.assetid: df588235-12a1-4798-bc56-ef81843de17f
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# ProjectItem Element
  Stellt ein SharePoint\-Projektelement dar.  Dies ist das erforderliche Stammelement der SPDATA\-Datei.  
  
## Syntax  
  
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
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|**DefaultFile**|Optionales **xs:string**\-Attribut.<br /><br /> Der relative Pfad, einschließlich des Dateinamens, der Datei, die im Visual Studio\-Editor geöffnet wird, wenn Sie das SharePoint\-Projektelement im **Projektmappen\-Explorer** öffnen.  Der Pfad ist relativ von dem Ordner, der die SPDATA\-Datei enthält.|  
|**FeatureReceiverClass**|Optionales **xs:string**\-Attribut.<br /><br /> Der vollqualifizierte Namen einer Funktionsempfängerklasse für dieses SharePoint\-Projektelement.  Weitere Informationen zu Funktionsempfängern finden Sie unter [Bereitstellen von Pack- und Bereitstellungsinformationen in Projektelementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|  
|**FeatureReceiverAssembly**|Optionales **xs:string**\-Attribut.<br /><br /> Gibt den vollqualifizierten Namen einer Assembly an, die einen Funktionsempfänger für dieses SharePoint\-Projektelement definiert.  Weitere Informationen zu Funktionsempfängern finden Sie unter [Bereitstellen von Pack- und Bereitstellungsinformationen in Projektelementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  Weitere Informationen zu vollqualifizierten Assemblynamen finden Sie unter [Assemblynamen](../Topic/Assembly%20Names.md).|  
|**SupportedTrustLevels**|Optionales **xs:string**\-Attribut.<br /><br /> Gibt die Vertrauensebenen an, die das SharePoint\-Projektelement unterstützt.  Dieser Wert kann eine der folgenden Zeichenfolgen sein: Sandkasten, FullTrust oder Alle:  Der Wert "All" gibt sowohl Sandkasten als auch FullTrust an.<br /><br /> In einem benutzerdefinierten SharePoint\-Projektelementtyp entspricht der Wert dieses Attributs dem Wert, der der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A>\-Eigenschaft in Ihrer Implementierung der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>\-Methode zugeordnet ist.  Wenn Sie einen anderen Wert für dieses Attribut angeben, überschreibt Visual Studio den Wert, damit die gleiche Vertrauensebene angegeben wird, die Sie in der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A>\-Eigenschaft angeben.|  
|**SupportedDeploymentScopes**|Optionales **xs:string**\-Attribut.<br /><br /> Gibt die Bereitstellungsbereiche an, die dieses SharePoint\-Projektelement unterstützt.  Dieser Wert ist eine durch Trennzeichen getrennte Zeichenfolge, die aus mindestens einer der folgenden Zeichenfolgen besteht: Farm, Website, Web, WebApplication oder Paket.  Beispiel: "Web, Site".<br /><br /> In einem benutzerdefinierten SharePoint\-Projektelementtyp entspricht der Wert dieses Attributs dem Wert, der der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A>\-Eigenschaft in Ihrer Implementierung der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>\-Methode zugeordnet ist.  Wenn Sie einen anderen Wert für dieses Attribut angeben, überschreibt Visual Studio den Wert, damit die gleiche Vertrauensebene angegeben wird, die Sie in der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A>\-Eigenschaft angeben.|  
|**Type**|Erforderliches **xs:string**\-Attribut.<br /><br /> Der Bezeichner für das SharePoint\-Projektelement.  In einem benutzerdefinierten SharePoint\-Projektelementtyp ist der Bezeichner die Zeichenfolge, die an <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> weitergegeben wird.  Weitere Informationen finden Sie unter [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).<br /><br /> Eine Liste der Bezeichner für die integrierten SharePoint\-Projektelemente in Visual Studio finden Sie unter [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md).|  
  
### Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|Optionales Element.<br /><br /> Stellt eine Auflistung benutzerdefinierter Datenelemente dar, die dem SharePoint\-Projektelement zugeordnet sind.<br /><br /> Sie können nur ein **ExtensionData**\-Element einschließen.|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Optionales Element.<br /><br /> Stellt eine Auflistung von Eigenschaftswerten dar, die beim Bereitstellen für SharePoint in einer Funktion enthalten sind.<br /><br /> Sie können nur ein **FeatureProperties**\-Element einschließen.|  
|[Dateien](../sharepoint/files-element.md)|Optionales **FileCollectionType**\-Element.<br /><br /> Gibt die Dateien an, die zusammen mit dem SharePoint\-Projektelement bereitgestellt werden sollen \(beispielsweise Funktionselementdateien und die Ausgabe von abhängigen Nicht\-SharePoint\-Projekten\).<br /><br /> Sie müssen entweder ein **Files**\-Element oder ein **ProjectItemFolder**\-Element einschließen, jedoch nicht beide Elemente.|  
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|Optionales **ProjectItemFolderType**\-Element.<br /><br /> Stellt einen zugeordneten Ordner dar.<br /><br /> Sie müssen entweder ein **Files**\-Element oder ein **ProjectItemFolder**\-Element einschließen, jedoch nicht beide Elemente.|  
|[SafeControls](../sharepoint/safecontrols-element.md)|Optionales Element.<br /><br /> Stellt eine Auflistung von ASPX\-Steuerelementen oder \-Webparts dar, die als sicher festgelegt sind, um allen Benutzern auf der SharePoint\-Website den Zugriff auf jede ASPX\-Seite zu ermöglichen.<br /><br /> Sie können nur ein **SafeControls**\-Element einschließen.|  
  
### Übergeordnete Elemente  
 Keine.  
  
## Elementinformationen  
  
|||  
|-|-|  
|**Namespace**|http:\/\/schemas.microsoft.com\/VisualStudio\/2010\/SharePointTools\/SharePointProjectItemModel|  
|**Schemaname**|SharePoint\-Projektelementschema|  
|**Validierungsdatei**|ProjectItemModelSchema.xsd|  
|**Kann leer sein.**|Nein|  
  
## Siehe auch  
 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  
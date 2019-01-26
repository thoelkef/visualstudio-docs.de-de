---
title: ProjectItem-Element | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItem element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2d2736dbcde8708589b4918979acacfdafa34cc4
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54864280"
---
# <a name="projectitem-element"></a>ProjectItem-Element
  Stellt ein SharePoint-Projektelement dar. Dieses Element die Erforderliches Stammelement von der *SPDATA* Datei.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
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
|**DefaultFile**|Optionale **Xs: String** Attribut.<br /><br /> Der relative Pfad, einschließlich des Dateinamens, der Datei, die in Visual Studio-Editor wird geöffnet, wenn Sie in der SharePoint-Projektelement öffnen **Projektmappen-Explorer**. Der Pfad ist relativ aus dem Ordner mit den *SPDATA* Datei.|  
|**FeatureReceiverClass**|Optionale **xs: String** Attribut.<br /><br /> Der vollqualifizierte Name von einer Featureempfängerklasse für diese SharePoint-Projektelement. Weitere Informationen zu Feature-Empfängern, finden Sie unter [Angaben zu packen und-Bereitstellen in Projektelementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|  
|**FeatureReceiverAssembly**|Optionale **xs: String** Attribut.<br /><br /> Gibt den vollqualifizierten Namen einer Assembly, die einen Funktionsempfänger für diese SharePoint-Projektelements definiert. Weitere Informationen zu Feature-Empfängern, finden Sie unter [Angaben zu packen und-Bereitstellen in Projektelementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md). Weitere Informationen zu den vollqualifizierten Assemblynamen verwenden zu müssen, finden Sie unter [Assemblynamen](/dotnet/framework/app-domains/assembly-names).|  
|**SupportedTrustLevels**|Optionale **xs: String** Attribut.<br /><br /> Gibt an, die Vertrauensebenen, die dieses SharePoint-Projektelement unterstützt. Dieser Wert kann eine der folgenden Zeichenfolgen sein: Sandkasten, FullTrust, oder alle. Der Wert All gibt sowohl die Sandkasten als auch die FullTrust.<br /><br /> In einer benutzerdefinierten SharePoint-Projektelementtyp, der Wert dieses Attributs entspricht dem Wert, den Sie zum Zuweisen der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> Eigenschaft in der Implementierung von der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> Methode. Wenn Sie einen anderen Wert für dieses Attribut angeben, Visual Studio überschreibt den Wert so, dass es sich um dieselbe Vertrauensebene, die Sie angeben angibt, in der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> Eigenschaft.|  
|**SupportedDeploymentScopes**|Optionale **xs: String** Attribut.<br /><br /> Gibt die Bereitstellungsbereiche an, denen dieses SharePoint-Projektelement unterstützt. Dieser Wert ist eine durch Trennzeichen getrennte Zeichenfolge, die eine oder mehrere der folgenden Zeichenfolgen besteht: Farm, Website, Web, WebApplication oder Pakets. Beispiel: `Web, Site`<br /><br /> In einer benutzerdefinierten SharePoint-Projektelementtyp, der Wert dieses Attributs entspricht dem Wert, den Sie zum Zuweisen der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> Eigenschaft in der Implementierung von der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> Methode. Wenn Sie einen anderen Wert für dieses Attribut angeben, Visual Studio überschreibt den Wert so, dass es sich um dieselbe Vertrauensebene, die Sie angeben angibt, in der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> Eigenschaft.|  
|**Type**|Erforderliche **xs: String** Attribut.<br /><br /> Der Bezeichner für die SharePoint-Projektelement. In einer benutzerdefinierten SharePoint-Projektelementtyp, der Bezeichner ist die Zeichenfolge, die Sie übergeben die <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. Weitere Informationen finden Sie unter [Vorgehensweise: Definieren Sie einen SharePoint-Projektelementtyp](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).<br /><br /> Eine Liste der Bezeichner für den integrierten SharePoint-Projektelemente, die in Visual Studio enthalten, finden Sie unter [Erweitern von SharePoint-Projektelemente](../sharepoint/extending-sharepoint-project-items.md).|  
  
### <a name="child-elements"></a>Untergeordnete Elemente
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|Optionales Element.<br /><br /> Stellt eine Auflistung von benutzerdefinierten Daten-Elementen, die die SharePoint-Projektelement zugeordnet sind.<br /><br /> Sie können nur eine einschließen **ExtensionData** Element.|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Optionales Element.<br /><br /> Stellt eine Auflistung von Eigenschaftswerten, die mit einer Funktion enthalten sind, wenn sie in SharePoint bereitgestellt wird.<br /><br /> Sie können nur eine einschließen **FeatureProperties** Element.|  
|[Dateien](../sharepoint/files-element.md)|Optionale **FileCollectionType** Element.<br /><br /> Gibt die Dateien, die mit der SharePoint-Projektelement, z. B. von featureelementen und die Ausgabe der abhängigen nicht-SharePoint-Projekten bereitgestellt.<br /><br /> Einschließen einer **Dateien** oder **ProjectItemFolder** -Element, aber nicht beides.|  
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|Optionale **ProjectItemFolderType** Element.<br /><br /> Stellt einen zugeordneten Ordner an.<br /><br /> Einschließen einer **Dateien** oder **ProjectItemFolder** -Element, aber nicht beides.|  
|[SafeControls](../sharepoint/safecontrols-element.md)|Optionales Element.<br /><br /> Stellt eine Auflistung von ASPX-Steuerelementen und Webparts, die als sicher für alle Benutzer Zugriff auf jede ASPX-Seite auf die SharePoint-Website festgelegt werden.<br /><br /> Sie können nur eine einschließen **SafeControls** Element.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente
 Keine  
  
## <a name="element-information"></a>Elementinformationen
  
|||  
|-|-|  
|**Namespace**|http<nolink>://schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|  
|**Name des Schemas**|SharePoint-Projektelementschema|  
|**Validierungsdatei**|ProjectItemModelSchema.xsd|  
|**Kann leer sein.**|Nein|  
  
## <a name="see-also"></a>Siehe auch
[SharePoint Project Item Schema rseference](../sharepoint/sharepoint-project-item-schema-reference.md)  

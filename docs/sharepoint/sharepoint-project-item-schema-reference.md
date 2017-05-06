---
title: "SharePoint Project Item Schema Reference"
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
  - "FeatureProperty element"
  - "SafeControls element"
  - "SafeControl element"
  - ".spdata files"
  - "ExtensionData element"
  - "FeatureProperties element"
  - "ProjectOutputFile element"
  - "Files element"
  - "ProjectItemFolder element"
  - "ProjectItemFile element"
  - "ExtensionDataItem element"
  - "ProjectItem element"
ms.assetid: 12b63cbc-bf94-4175-bfa8-2117943d00d1
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# SharePoint Project Item Schema Reference
  Anhand des SharePoint\-Projektelementschemas wird von Visual Studio der Inhalt von SPDATA\-Dateien überprüft.  SPDATA\-Dateien dienen zum Angeben des Inhalts und des Verhaltens eines SharePoint\-Projektelements.  Weitere Informationen zum Inhalt der SharePoint\-Projektelemente finden Sie unter [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Das SharePoint\-Projektelementschema ist mit "ProjectItemModelSchema.xsd" benannt und standardmäßig unter "%Programme \(x86\)%\\Microsoft Visual Studio 11.0\\Xml\\Schemas" installiert.  
  
 Das Stammelement ist das [ProjectItem](../sharepoint/projectitem-element.md)\-Element.  In der folgenden Tabelle werden alle durch das Schema definierten Elemente beschrieben:  
  
|Element|Description|  
|-------------|-----------------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|Stellt eine Auflistung benutzerdefinierter Datenelemente dar, die dem SharePoint\-Projektelement zugeordnet sind.|  
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|Stellt ein benutzerdefiniertes Datenelement \(im Schlüssel\-Wert\-Format\) dar, das dem SharePoint\-Projektelement zugeordnet ist.  Sowohl der Schlüssel als auch der Wert muss eine Zeichenfolge sein.|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Stellt eine Auflistung von Eigenschaftswerten dar, die beim Bereitstellen für SharePoint in einer Funktion enthalten sind.  Nach dem Bereitstellen einer Funktion können Sie im Code auf die Eigenschaftswerte zugreifen.|  
|[FeatureProperty](../sharepoint/featureproperty-element.md)|Stellt eine benutzerdefinierte Eigenschaft dar, die in eine Funktion eingeschlossen wird, wenn diese für SharePoint bereitgestellt wird.  Nach dem Bereitstellen einer Funktion können Sie im Code auf die Eigenschaft zugreifen.|  
|[Dateien](../sharepoint/files-element.md)|Gibt die Dateien an, die zusammen mit dem SharePoint\-Projektelement bereitgestellt werden sollen \(beispielsweise eine Feature\-Elementdatei oder die Ausgabe eines Projekts\).|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Stellt ein SharePoint\-Projektelement dar.|  
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|Stellt eine SharePoint\-Datei \(beispielsweise eine Feature\-Elementdatei\) dar, die im Projektelement enthalten sein soll, wenn dieses für SharePoint bereitgestellt wird.|  
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|Stellt einen zugeordneten Ordner dar.|  
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|Stellt die Ausgabe eines Projekts dar, die im Projektelement enthalten sein soll, wenn es in SharePoint bereitgestellt wird.|  
|[SafeControl](../sharepoint/safecontrol-element.md)|Stellt ein ASPX\-Steuerelement oder \-Webpart dar, das als sicher festgelegt ist, um allen Benutzern auf der SharePoint\-Website den Zugriff auf jede ASPX\-Seite zu ermöglichen.|  
|[SafeControls](../sharepoint/safecontrols-element.md)|Stellt eine Auflistung von ASPX\-Steuerelementen oder \-Webparts dar, die als sicher festgelegt sind, um allen Benutzern auf der SharePoint\-Website den Zugriff auf jede ASPX\-Seite zu ermöglichen.|  
  
## Siehe auch  
 [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)  
  
  
---
title: SharePoint-Projektelementschema | Microsoft Docs
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
helpviewer_keywords:
- FeatureProperty element
- SafeControls element
- SafeControl element
- .spdata files
- ExtensionData element
- FeatureProperties element
- ProjectOutputFile element
- Files element
- ProjectItemFolder element
- ProjectItemFile element
- ExtensionDataItem element
- ProjectItem element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 99a2471919483f02a9f58a35ad164527a12a39c5
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="sharepoint-project-item-schema-reference"></a>Referenz zum SharePoint-Projektelementschema
  Visual Studio verwendet die SharePoint-Projektelementschema auf um den Inhalt von SPDATA-Dateien zu überprüfen. SPDATA-Datei gibt den Inhalt und das Verhalten von einer SharePoint-Projektelement. Weitere Informationen zum Inhalt der SharePoint-Projektelemente, finden Sie unter [Erstellen von Elementvorlagen und Projektvorlagen für SharePoint-Projektelemente](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Die SharePoint-Projektelementschema ist mit dem Namen "ProjectItemModelSchema.xsd" benannt und standardmäßig im %Programme (x86)%\Microsoft Visual Studio 11.0\Xml\Schemas.  
  
 Das Stammelement ist das [ProjectItem](../sharepoint/projectitem-element.md) Element. Die folgende Tabelle beschreibt alle vom Schema definierten Elemente.  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|Stellt eine Auflistung benutzerdefinierter Datenelemente, die SharePoint-Projektelements zugeordnet sind.|  
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|Stellt ein Element von benutzerdefinierten Daten, die die SharePoint-Projektelement im Schlüssel/Wert-Format zugeordnet ist. Sowohl der Schlüssel und Wert müssen Zeichenfolgen sein.|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Stellt eine Auflistung von Eigenschaftswerten, die in eine Funktion eingeschlossen werden, wenn er für SharePoint bereitgestellt wird. Nachdem eine Funktion bereitgestellt wird, können Sie die Eigenschaftswerte in Ihrem Code zugreifen.|  
|[FeatureProperty](../sharepoint/featureproperty-element.md)|Stellt eine benutzerdefinierte Eigenschaft, die in eine Funktion eingeschlossen wird, wenn er für SharePoint bereitgestellt wird. Nachdem eine Funktion bereitgestellt wird, können Sie die Eigenschaft im Code zugreifen.|  
|[Dateien](../sharepoint/files-element.md)|Gibt die Dateien, die mit der SharePoint-Projektelement, z. B. eine Featuredatei für das Element oder die Ausgabe eines Projekts bereitgestellt.|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Stellt ein SharePoint-Projektelement dar.|  
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|Stellt eine SharePoint-Datei, z. B. Elementdatei Feature, das Projektelement enthalten sein soll, wenn er für SharePoint bereitgestellt wird.|  
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|Stellt einen zugeordneten Ordner dar.|  
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|Stellt die Ausgabe eines Projekts mit dem Projektelement eingeschlossen werden soll, wenn er für SharePoint bereitgestellt wird.|  
|[SafeControl](../sharepoint/safecontrol-element.md)|Stellt eine ASPX-Steuerelement oder ein Webpart, das als sichere für alle Benutzer Zugriff auf alle ASPX-Seite auf der SharePoint-Website festgelegt ist.|  
|["SafeControls"](../sharepoint/safecontrols-element.md)|Stellt eine Auflistung von ASPX-Steuerelementen und Webparts, die als sichere für alle Benutzer Zugriff auf alle ASPX-Seite auf der SharePoint-Website festgelegt werden.|  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Elementvorlagen und Projektvorlagen für SharePoint-Projektelemente](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)  
  
  
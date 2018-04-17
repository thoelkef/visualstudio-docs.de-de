---
title: SharePoint-Projektelementschema | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9b039b1cf31a04a24819b03114c661a3ab1b108a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
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
  
  
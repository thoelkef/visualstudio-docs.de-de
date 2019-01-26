---
title: SharePoint-Projektelementschema | Microsoft-Dokumentation
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c261115b21d1067b7494d09ad8031b3f4dc5a8c5
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54864916"
---
# <a name="sharepoint-project-item-schema-reference"></a>SharePoint-Projektelementschema
  Visual Studio verwendet die SharePoint-Projektelementschema So überprüfen den Inhalt der *SPDATA* Dateien. Ein *SPDATA* Datei gibt den Inhalt und Verhalten des SharePoint-Projektelements. Weitere Informationen zum Inhalt der SharePoint-Projektelemente, finden Sie unter [Erstellen von Vorlagen und Projektvorlagen für SharePoint-Projektelemente](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Die SharePoint-Projektelementschema heißt "ProjectItemModelSchema.xsd" benannt und ist standardmäßig installiert, in %Programme (x86)%\Microsoft Visual Studio 11.0\Xml\Schemas.  
  
 Das Stammelement der [ProjectItem](../sharepoint/projectitem-element.md) Element. Die folgende Tabelle beschreibt alle vom Schema definierten Elemente.  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|Stellt eine Auflistung von benutzerdefinierten Daten-Elementen, die die SharePoint-Projektelement zugeordnet sind.|  
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|Stellt ein Element von benutzerdefinierten Daten, die im Schlüssel/Wert-Format der SharePoint-Projektelement zugeordnet ist. Sowohl der Schlüssel und Wert müssen Zeichenfolgen sein.|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Stellt eine Auflistung von Eigenschaftswerten, die mit einer Funktion enthalten sind, wenn sie in SharePoint bereitgestellt wird. Nachdem eine Funktion bereitgestellt wird, können Sie die Eigenschaftswerte in Ihrem Code zugreifen.|  
|[FeatureProperty](../sharepoint/featureproperty-element.md)|Stellt eine benutzerdefinierte Eigenschaft, die mit einer Funktion enthalten ist, wenn sie in SharePoint bereitgestellt wird. Nachdem eine Funktion bereitgestellt wird, können Sie die Eigenschaft in Ihrem Code zugreifen.|  
|[Dateien](../sharepoint/files-element.md)|Gibt die Dateien, die mit der SharePoint-Projektelement, z. B. eine Featuredatei für das Element oder die Ausgabe eines Projekts bereitgestellt.|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Stellt ein SharePoint-Projektelement dar.|  
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|Stellt eine SharePoint-Datei, z. B. Feature-Element-Datei, um mit dem Projektelement enthalten, wenn sie in SharePoint bereitgestellt wird.|  
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|Stellt einen zugeordneten Ordner an.|  
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|Zeigt die Ausgabe eines Projekts mit dem Projektelement eingeschlossen werden soll, wenn sie in SharePoint bereitgestellt wird.|  
|[SafeControl](../sharepoint/safecontrol-element.md)|Stellt eine ASPX-Steuerelement oder ein Webpart, das als für alle Benutzer Zugriff auf jede ASPX-Seite auf die SharePoint-Website festgelegt ist.|  
|[SafeControls](../sharepoint/safecontrols-element.md)|Stellt eine Auflistung von ASPX-Steuerelementen und Webparts, die als sicher für alle Benutzer Zugriff auf jede ASPX-Seite auf die SharePoint-Website festgelegt werden.|  
  
## <a name="see-also"></a>Siehe auch
 [Erstellen von Elementvorlagen und Projektvorlagen für SharePoint-Projektelemente](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)  

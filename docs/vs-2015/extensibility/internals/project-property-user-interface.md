---
title: Benutzeroberfläche für die Eigenschaft Project | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e295bff2f8398765f90c3fd537ca4f546208ce4b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51768294"
---
# <a name="project-property-user-interface"></a>Benutzeroberfläche für Projekteigenschaften
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Einem Projektuntertyp kann mithilfe der Elemente im Projekt **Eigenschaftenseiten** (Dialogfeld), wie sie mit dem Basisprojekt, bereitgestellt werden ausblenden oder schreibgeschützte Steuerelemente und machen komplette Seiten angegeben, oder die ProjektuntertypspezifischeSeitenhinzufügen**Eigenschaftenseiten** Dialogfeld.  
  
## <a name="extending-the-project-property-dialog-box"></a>Erweitern Sie den Projekt-Eigenschaft (Dialogfeld)  
 Einem Projektuntertyp Automatisierungsextender und Konfiguration Durchsuchen von Projektobjekten implementiert werden. Implementieren Sie diese Extender die <xref:EnvDTE.IFilterProperties> Schnittstelle die bestimmte Eigenschaften ausgeblendet oder schreibgeschützt. Die **Eigenschaftenseiten** Dialogfeld des Basisprojekts, implementiert das Basisprojekt, berücksichtigt die Filterung durch den Automatisierungsextender ausgeführt.  
  
 Der Prozess der Erweiterung eine **Projekteigenschaft** Dialogfeld wird unten beschrieben:  
  
- Das Basisprojekt ruft der Extender aus den Projektuntertyp ab, durch die Implementierung der <xref:EnvDTE80.IInternalExtenderProvider> Schnittstelle. Das Durchsuchen, Projekt-Automatisierung und Projekt durchsuchen Konfigurationsobjekte des Basisprojekts alle implementieren diese Schnittstelle.  
  
- Die Implementierung der <xref:EnvDTE80.IInternalExtenderProvider> für dem Suchobjekt des Projekts und das Automation-Projektobjekt an Delegieren der <xref:EnvDTE80.IInternalExtenderProvider> Implementierung des Sammlers Untertyp Projekt (d. h. sie `QueryInterface` für <xref:EnvDTE80.IInternalExtenderProvider> auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Project-Objekt).  
  
- Die Basis projektkonfigurationssuchobjekt implementiert auch <xref:EnvDTE80.IInternalExtenderProvider> , direkt in den Automatisierungsextender aus dem Projektuntertyp-Konfigurationsobjekt zu verknüpfen. Die Implementierung delegiert an die <xref:EnvDTE80.IInternalExtenderProvider> Schnittstelle, die vom Projekt Untertyp Aggregator implementiert.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>, implementiert das projektkonfigurationssuchobjekt, gibt die <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Objekt.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>, auch durch das projektkonfigurationssuchobjekt, gibt implementiert die <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> Objekt.  
  
- Einem Projektuntertyp kann die entsprechenden CATIDs für die verschiedenen erweiterbare Objekte des Basisprojekts zur Laufzeit bestimmen, indem Sie die folgenden abrufen <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> Werte:  
  
  -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
  -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
  -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
  Um die CATIDs für den Projektumfang zu bestimmen, ruft die oben aufgeführten Eigenschaften für der Projektuntertyp ab <xref:Microsoft.VisualStudio.VSConstants.VSITEMID> aus der `VSITEMID``typedef`. Einem Projektuntertyp sollten auch zu bestimmen, welche **Eigenschaftenseiten** dialogfeldseiten werden angezeigt, für das Projekt, sowohl die abhängig von der Konfiguration als auch die Konfiguration unabhängig. Einige Projektuntertypen können müssen, entfernen die integrierte Seiten und Hinzufügen von Projekt Untertyp bestimmte Seiten. Damit können dies, die Aufrufe der verwaltete Client-Projekt die <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> Methode für die folgenden Eigenschaften:  
  
- `VSHPROPID_PropertyPagesCLSIDList` – eine durch Semikolons getrennte Liste von CLSIDs der konfigurationsunabhängigen Eigenschaftenseiten.  
  
- `VSHPROPID_CfgPropertyPagesCLSIDList —` eine durch Semikolons getrennte Liste von CLSIDs der konfigurationsabhängigen Eigenschaftenseiten.  
  
  Da das Projekt Untertyp Aggregate der <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Objekt ist, können sie die Definition dieser Eigenschaften zu bestimmen, welche überschreiben **Eigenschaftenseiten** Dialogfelder angezeigt werden. Der Projektuntertyp kann diese Eigenschaften aus dem inneren Basisprojekt abzurufen, und klicken Sie dann hinzufügen oder Entfernen von CLSIDs nach Bedarf.  
  
  Neue Eigenschaftenseiten, die von einem Projektuntertyp hinzugefügt, werden von der Implementierung des Projekts eine projektkonfigurationssuchobjekt übergeben. Diese projektkonfigurationssuchobjekt unterstützt Automatisierungsextender. Weitere Informationen zu AutomationExtenders, finden Sie unter [implementieren und Verwenden von Automatisierungsextendern](http://msdn.microsoft.com/library/0d5c218c-f412-4b28-ab0c-33a611f62356). Die Eigenschaftenseiten implementiert durch den Aufruf der Projekt-Untertyp <xref:EnvDTE.Project.Extender%2A> eigene projektkonfigurationssuchobjekt Untertyp abgerufen, die dem Suchobjekt der Konfiguration des Basisprojekts erweitert.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:EnvDTE.IFilterProperties>   
 [Property Pages Dialog Box](http://msdn.microsoft.com/en-us/4a3d34ac-ed03-45e8-ae60-a0e1aad300e4)


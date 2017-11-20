---
title: "Benutzeroberfläche für die Eigenschaft Projekt | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 36d8f6afebf09d4efd176ba204dcc6f485a56124
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="project-property-user-interface"></a>Benutzeroberfläche von Project-Eigenschaft
Ein Projektuntertyp mithilfe der Elemente im Projekt **Eigenschaftenseiten** (Dialogfeld), wie sie mit der Basis-Projekt bereitgestellt werden ausblenden stellen schreibgeschützte Steuerelemente und die komplette Seiten angegeben oder die ProjektUntertyp-spezifischeSeitenhinzufügen**Eigenschaftenseiten** (Dialogfeld).  
  
## <a name="extending-the-project-property-dialog-box"></a>Erweitern Sie den Projekt-Eigenschaft (Dialogfeld)  
 Ein Projektuntertyp implementiert Automatisierungsextender und Projekt-Konfigurationsobjekte durchsuchen. Diese Extender implementieren die <xref:EnvDTE.IFilterProperties> Schnittstelle, um bestimmte Eigenschaften ausgeblendet oder schreibgeschützt machen. Die **Eigenschaftenseiten** Dialogfeld des Basis-Projekts von der Basisprojekt implementiert wird berücksichtigt, die Filterung von der Automatisierungsextender ausgeführt.  
  
 Bei der Erweiterung einer **Projekteigenschaft** Dialogfeld wird im folgenden erläutert:  
  
-   Das Basisprojekt ruft Extender aus den Untertyp des Projekts ab, durch die Implementierung der <xref:EnvDTE80.IInternalExtenderProvider> Schnittstelle. Implementieren diese Schnittstelle, die zum Durchsuchen, Projekt-Automatisierung und Projekt Konfigurationsobjekte zum Durchsuchen des Basis-Projekts alle.  
  
-   Die Implementierung der <xref:EnvDTE80.IInternalExtenderProvider> für das Projektobjekt durchsuchen und das Projektobjekt für die Automatisierung zum Delegieren der <xref:EnvDTE80.IInternalExtenderProvider> Implementierung des Projekts Untertyp Aggregator (d. h. sie `QueryInterface` für <xref:EnvDTE80.IInternalExtenderProvider> auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Projektobjekt).  
  
-   Implementiert das Basisprojekt durchsuchen Konfigurationsobjekt auch <xref:EnvDTE80.IInternalExtenderProvider> , direkt in den Automatisierungsextender aus dem Projekt Untertyp Configuration-Objekt von Netzwerkdaten. Ihre Implementierung delegiert an die <xref:EnvDTE80.IInternalExtenderProvider> Schnittstelle, die vom Projekt Untertyp Aggregator implementiert.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>, durch die Konfiguration durchsuchen Projektobjekt, gibt implementiert die <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Objekt.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>, auch vom Projekt Konfiguration durchsuchen Objekt implementiert, gibt die <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> Objekt.  
  
-   Ein Projektuntertyp kann die entsprechenden CATIDs für die verschiedenen erweiterbare Objekte des Basis-Projekts zur Laufzeit bestimmen, indem Folgendes abrufen <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> Werte:  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
 Zum Bestimmen der CATIDs für des Projektumfangs ruft Untertyp des Projekts ab, die oben aufgeführten Eigenschaften für <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT> aus der `VSITEMID``typedef`. Ein Projektuntertyp sollten auch zu bestimmen, welche **Eigenschaftenseiten** dialogfeldseiten für das Projekt angezeigt, sind abhängig von der Konfiguration und Konfiguration unabhängig. Einige Projekt Untertypen müssen möglicherweise integrierte Seiten zu entfernen und Projekt Untertyp bestimmte Seiten hinzufügen. Damit dies als verwalteter Client Projekt Aufrufe können die <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> Methode für die folgenden Eigenschaften:  
  
-   `VSHPROPID_PropertyPagesCLSIDList`– eine durch Semikolons getrennte Liste von CLSIDs konfigurationsunabhängige Eigenschaftenseiten.  
  
-   `VSHPROPID_CfgPropertyPagesCLSIDList —`eine durch Semikolons getrennte Liste von CLSIDs konfigurationsabhängigen Eigenschaftenseiten.  
  
 Da das Projekt Untertyp Aggregate der <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> -Objekt, kann die Definition dieser Eigenschaften zu bestimmen, welche überschreiben **Eigenschaftenseiten** Dialogfelder angezeigt werden. Untertyp des Projekts kann diese Eigenschaften aus dem inneren Basis Projekt abzurufen, und klicken Sie dann hinzufügen oder Entfernen von CLSIDs nach Bedarf.  
  
 Neue Eigenschaftenseiten, die durch einen Projektuntertyp hinzugefügt werden von der Implementierung Basisprojekt ein Projekt zum Durchsuchen Konfigurationsobjekt übergeben. Dieses Projekt durchsuchen Konfigurationsobjekt unterstützt Automatisierungsextender. Weitere Informationen zu AutomationExtenders, finden Sie unter [implementieren und Verwenden von Automatisierungsextender](http://msdn.microsoft.com/Library/0d5c218c-f412-4b28-ab0c-33a611f62356). Die Eigenschaftenseiten, die durch den Aufruf des Project-Untertyp implementiert <xref:EnvDTE.Project.Extender%2A> ihre eigenen Projekt Untertyp durchsuchen Konfigurationsobjekt abgerufen, die das Konfigurationsobjekt zum Durchsuchen des Basis-Projekts erweitert.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:EnvDTE.IFilterProperties>   
 [Dialogfeld Eigenschaftenseiten](http://msdn.microsoft.com/en-us/4a3d34ac-ed03-45e8-ae60-a0e1aad300e4)
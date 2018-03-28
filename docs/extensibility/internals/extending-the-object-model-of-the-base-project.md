---
title: Erweitern das Objektmodell der Basisprojekt | Microsoft Docs
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
caps.latest.revision: ''
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: a0fdda35744aaddf8789818afd1f938897470147
ms.sourcegitcommit: 768118d470da9c7164d2f23ca918dfe26a4be72f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/28/2018
---
# <a name="extending-the-object-model-of-the-base-project"></a>Erweitern Sie das Objektmodell des Basis-Projekts

Ein Projektuntertyp verlängert die Automatisierungsobjektmodell des Basis-Projekts in den folgenden Stellen:

-   Project.Extender ("\<ProjectSubtypeName >") – Dies ermöglicht einen Projektuntertyp auf ein Objekt mit benutzerdefinierten Methoden aus bieten die <xref:EnvDTE.Project>. Ein Projektuntertyp können Automatisierungsextender verfügbar machen die `Project` Objekt. Die <xref:EnvDTE80.IInternalExtenderProvider> Schnittstelle implementiert wird, auf dem Hauptprojekt Untertyp Aggregator bieten das Objekt für die `VSHPROPID_ExtObjectCATID` aus <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> (entspricht einer `itemid` Wert [VSITEMID. Root-](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)) CATID.

-   ProjectItem.Extender("\<ProjectSubtypeName>") - This allows a project subtype to offer an object with custom methods from a particular <xref:EnvDTE.ProjectItem> object within the project. Ein Projektuntertyp können Automatisierungsextender, dieses Objekt verfügbar gemacht wird. Die <xref:EnvDTE80.IInternalExtenderProvider> Schnittstelle implementiert wird, auf dem Hauptprojekt Untertyp Aggregator muss das Objekt für bieten die `VSHPROPID_ExtObjectCATID` aus <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (entspricht einem gewünschten <xref:Microsoft.VisualStudio.VSConstants.VSITEMID>) CATID.

-   Project.Properties - dieser Auflistung zeigt die konfigurationsunabhängigen Eigenschaften der `Project` Objekt. Weitere Informationen zu Projekteigenschaften, finden Sie unter <xref:EnvDTE.Project.Properties%2A>. Ein Projektuntertyp können Automatisierungsextender, seine Eigenschaften, die dieser Sammlung hinzufügen. Die <xref:EnvDTE80.IInternalExtenderProvider> Schnittstelle implementiert wird, auf dem Hauptprojekt Untertyp Aggregator muss das Objekt für bieten die `VSHPROPID_BrowseObjectCATID` aus VSHPROPID2 (entspricht einer `itemid` Wert [VSITEMID. Root-](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>), aus <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>) CATID.

-   Configuration.Properties - diese Auflistung macht die konfigurationsabhängigen Eigenschaften des Projekts für eine bestimmte Konfiguration (z. B. "Debug"). Weitere Informationen finden Sie unter <xref:EnvDTE.Configuration>. Ein Projektuntertyp können Automatisierungsextender, seine Eigenschaften, die dieser Sammlung hinzufügen. Die <xref:EnvDTE80.IInternalExtenderProvider> Schnittstelle implementiert wird, auf dem Hauptprojekt Untertyp Aggregator bietet das Objekt für die CATID `VSHPROPID_CfgBrowseObjectCATID` (entspricht einer `itemid` Wert [VSITEMID. Root-](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)). Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>Schnittstelle wird verwendet, um ein Konfigurationsobjekt durchsuchen voneinander zu unterscheiden.

## <a name="see-also"></a>Siehe auch

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>
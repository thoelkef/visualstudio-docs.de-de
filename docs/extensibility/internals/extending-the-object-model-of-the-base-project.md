---
title: Erweitern des Objektmodells des Basisprojekts | Microsoft-Dokumentation
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0a297d8d70db2254e5c6ea2f64f3ab4cbadc3936
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2018
ms.locfileid: "39497206"
---
# <a name="extend-the-object-model-of-the-base-project"></a>Erweitern Sie das Objektmodell des Basisprojekts

Einem Projektuntertyp kann das Automatisierungsobjektmodell des Basisprojekts in den folgenden Orten erweitern:

-   Project.Extender ("\<ProjectSubtypeName >"): Dies ermöglicht einem Projektuntertyp bieten ein Objekt mit benutzerdefinierten Methoden aus der <xref:EnvDTE.Project> Objekt. Einem Projektuntertyp kann Automatisierungsextender verwenden, um verfügbar zu machen die `Project` Objekt. Die <xref:EnvDTE80.IInternalExtenderProvider> Schnittstelle, die auf dem Hauptprojekt Untertyp Aggregator implementiert, sollte das Objekt für bieten die `VSHPROPID_ExtObjectCATID` aus <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> (entspricht einer `itemid` Wert [VSITEMID. Root](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)) CATID.

-   ProjectItem.Extender ("\<ProjectSubtypeName >"): Dies ermöglicht einem Projektuntertyp, ein Objekt mit benutzerdefinierten Methoden anzubieten, aus einer bestimmten <xref:EnvDTE.ProjectItem> Objekt innerhalb des Projekts. Automatisierungsextender können einem Projektuntertyp dieses Objekt verfügbar gemacht wird. Die <xref:EnvDTE80.IInternalExtenderProvider> auf dem Hauptprojekt Untertyp Aggregator implementierte Schnittstelle muss das Objekt für bieten die `VSHPROPID_ExtObjectCATID` aus <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (für eine gewünschte <xref:Microsoft.VisualStudio.VSConstants.VSITEMID>) CATID.

-   Project.Properties: Diese Auflistung macht die konfigurationsunabhängigen Eigenschaften der `Project` Objekt. Weitere Informationen zu `Project` Eigenschaften finden Sie <xref:EnvDTE.Project.Properties%2A>. Einem Projektuntertyp kann Automatisierungsextender verwenden, um seine Eigenschaften, die dieser Sammlung hinzuzufügen. Die <xref:EnvDTE80.IInternalExtenderProvider> auf dem Hauptprojekt Untertyp Aggregator implementierte Schnittstelle muss das Objekt für bieten die `VSHPROPID_BrowseObjectCATID` aus VSHPROPID2 (entspricht einer `itemid` Wert [VSITEMID. Root](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>), von <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>) CATID.

-   Configuration.Properties: Diese Auflistung macht die konfigurationsabhängigen Eigenschaften des Projekts für eine bestimmte Konfiguration (beispielsweise "Debug"). Weitere Informationen finden Sie unter <xref:EnvDTE.Configuration>. Einem Projektuntertyp kann Automatisierungsextender verwenden, um seine Eigenschaften, die dieser Sammlung hinzuzufügen. Die <xref:EnvDTE80.IInternalExtenderProvider> Schnittstelle implementiert wird, auf dem Hauptprojekt Untertyp Aggregator bietet das Objekt für die CATID `VSHPROPID_CfgBrowseObjectCATID` (entspricht einer `itemid` Wert [VSITEMID. Root](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)). Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>Schnittstelle wird verwendet, um ein Konfigurationsobjekt durchsuchen voneinander zu unterscheiden.

## <a name="see-also"></a>Siehe auch

<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>
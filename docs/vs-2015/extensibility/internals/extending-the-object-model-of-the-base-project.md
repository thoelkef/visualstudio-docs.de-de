---
title: Erweitern des Objektmodells des Basisprojekts | Microsoft-Dokumentation
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
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: db8ec193b49b7b72e922d2e4f715061d78be37ad
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51783278"
---
# <a name="extending-the-object-model-of-the-base-project"></a>Erweitern des Objektmodells des Basisprojekts
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Einem Projektuntertyp kann das Automatisierungsobjektmodell des Basisprojekts in den folgenden Orten erweitern:  
  
-   Project.Extender ("\<ProjectSubtypeName >") – Dies ermöglicht einem Projektuntertyp bieten ein Objekt mit benutzerdefinierten Methoden aus der <xref:EnvDTE.Project>. Einem Projektuntertyp kann Automatisierungsextender verwenden, um verfügbar zu machen die `Project` Objekt. Die <xref:EnvDTE80.IInternalExtenderProvider>Schnittstelle, die auf dem Hauptprojekt Untertyp Aggregator implementiert, sollte das Objekt für bieten die `VSHPROPID_ExtObjectCATID` aus <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> (entspricht einer `itemid` Wert VSITEMID_ROOT aus `VSITEMID`) CATID.  
  
-   ProjectItem.Extender ("\<ProjectSubtypeName >") – Dies ermöglicht einem Projektuntertyp, ein Objekt mit benutzerdefinierten Methoden anzubieten, aus einer bestimmten <xref:EnvDTE.ProjectItem> Objekt innerhalb des Projekts. Automatisierungsextender können einem Projektuntertyp dieses Objekt verfügbar gemacht wird. Die <xref:EnvDTE80.IInternalExtenderProvider> auf dem Hauptprojekt Untertyp Aggregator implementierte Schnittstelle muss das Objekt für bieten die `VSHPROPID_ExtObjectCATID` aus <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (für eine gewünschte `VSITEMID`) CATID.  
  
-   Project.Properties: Diese Auflistung macht unabhängige Eigenschaften für die die `Project` Objekt. Weitere Informationen zu Projekteigenschaften finden Sie unter <xref:EnvDTE.Project.Properties%2A>. Einem Projektuntertyp kann Automatisierungsextender verwenden, um seine Eigenschaften, die dieser Sammlung hinzuzufügen. Die <xref:EnvDTE80.IInternalExtenderProvider> auf dem Hauptprojekt Untertyp Aggregator implementierte Schnittstelle muss das Objekt für bieten die `VSHPROPID_BrowseObjectCATID` aus VSHPROPID2 (entspricht einer `itemid` Wert VSITEMID_ROOT aus <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>) CATID.  
  
-   Configuration.Properties – macht dieser Auflistung die abhängigen Eigenschaften der Konfiguration des Projekts für eine bestimmte Konfiguration (beispielsweise "Debug"). Weitere Informationen finden Sie unter <xref:EnvDTE.Configuration>. Einem Projektuntertyp kann Automatisierungsextender verwenden, um seine Eigenschaften, die dieser Sammlung hinzuzufügen. Die <xref:EnvDTE80.IInternalExtenderProvider> Schnittstelle implementiert wird, auf dem Hauptprojekt Untertyp Aggregator bietet das Objekt für die CATID `VSHPROPID_CfgBrowseObjectCATID` (entspricht einer `itemid` Wert <xref:Microsoft.VisualStudio.VSConstants.VSITEMID>). Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>Schnittstelle wird verwendet, um ein Konfigurationsobjekt durchsuchen voneinander zu unterscheiden.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>


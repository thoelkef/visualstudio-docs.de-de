---
title: Erweitern des Objektmodells des Basisprojekts | Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 33186cd477ade7f562f6191393dabe8e94f4f194
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708398"
---
# <a name="extend-the-object-model-of-the-base-project"></a>Erweitern des Objektmodells des Basisprojekts

Ein Projektuntertyp kann das Automatisierungsobjektmodell des Basisprojekts an den folgenden Stellen erweitern:

- Project.Extender("\<ProjectSubtypeName>"): Dadurch kann ein Projektuntertyp ein <xref:EnvDTE.Project> Objekt mit benutzerdefinierten Methoden aus dem Objekt anbieten. Ein Projektuntertyp kann Automation Extender `Project` verwenden, um das Objekt verfügbar zu machen. Die <xref:EnvDTE80.IInternalExtenderProvider> schnittstelle, die auf dem Hauptprojekt-Subtype-Aggregator implementiert ist, sollte sein Objekt für das `VSHPROPID_ExtObjectCATID` von <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> (entsprechend einem `itemid` Wert von [VSITEMID) anbieten. Root](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID.

- ProjectItem.Extender("\<ProjectSubtypeName>"): Dadurch kann ein Projektuntertyp ein Objekt <xref:EnvDTE.ProjectItem> mit benutzerdefinierten Methoden aus einem bestimmten Objekt innerhalb des Projekts anbieten. Ein Projektuntertyp kann Automatisierungs-Extender verwenden, um dieses Objekt verfügbar zu machen. Die <xref:EnvDTE80.IInternalExtenderProvider> Schnittstelle, die auf dem Hauptprojekt-Subtype-Aggregator <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> implementiert ist, <xref:Microsoft.VisualStudio.VSConstants.VSITEMID>muss sein Objekt für die `VSHPROPID_ExtObjectCATID` von (entsprechend einer gewünschten) CATID anbieten.

- Project.Properties: Diese Auflistung macht die konfigurationsunabhängigen `Project` Eigenschaften des Objekts verfügbar. Weitere Informationen zu `Project`-Eigenschaften finden Sie unter <xref:EnvDTE.Project.Properties%2A>. Ein Projektuntertyp kann Automation Extender verwenden, um seine Eigenschaften zu dieser Auflistung hinzuzufügen. Die <xref:EnvDTE80.IInternalExtenderProvider> Schnittstelle, die auf dem Hauptprojekt-Subtype-Aggregator implementiert ist, muss sein Objekt für das `VSHPROPID_BrowseObjectCATID` von <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (entsprechend einem `itemid` Wert von [VSITEMID) anbieten. Root](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID.

- Configuration.Properties: Diese Auflistung macht die konfigurationsabhängigen Eigenschaften des Projekts für eine bestimmte Konfiguration verfügbar (z. B. Debug). Weitere Informationen finden Sie unter <xref:EnvDTE.Configuration>. Ein Projektuntertyp kann Automation Extender verwenden, um seine Eigenschaften zu dieser Auflistung hinzuzufügen. Die <xref:EnvDTE80.IInternalExtenderProvider> schnittstelle, die auf dem Hauptprojekt-Subtype-Aggregator implementiert ist, bietet ihr Objekt für die CATID `VSHPROPID_CfgBrowseObjectCATID` (entsprechend einem `itemid` Wert von [VSITEMID). Root](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)). Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject> Schnittstelle wird verwendet, um ein Konfigurationssuchobjekt von einem anderen zu unterscheiden.

## <a name="see-also"></a>Weitere Informationen

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>

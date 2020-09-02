---
title: Erweitern des Objektmodells des Basis Projekts | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7723881bce81824b66a936793175077a0ec67666
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187168"
---
# <a name="extending-the-object-model-of-the-base-project"></a>Erweitern des Objektmodells des Basisprojekts
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Mit einem Projekt Untertyp kann das Automatisierungs Objektmodell des Basis Projekts an den folgenden Stellen erweitert werden:  
  
- Project. Extender (" \<ProjectSubtypeName> ") – Dies ermöglicht einem Projekt Untertyp das anbieten eines Objekts mit benutzerdefinierten Methoden aus <xref:EnvDTE.Project> . Ein Projekt Untertyp kann Automatisierungs Erweiterungen verwenden, um das Objekt verfügbar zu machen `Project` . Die- <xref:EnvDTE80.IInternalExtenderProvider> Schnittstelle, die auf dem Hauptprojekt-Untertyp Aggregator implementiert ist, sollte das-Objekt für den `VSHPROPID_ExtObjectCATID` von <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> (entsprechend dem `itemid` Wert VSITEMID_ROOT, von `VSITEMID` ) CATID anbieten.  
  
- ProjectItem. Extender (" \<ProjectSubtypeName> ") – Dies ermöglicht einem Projekt Untertyp das anbieten eines Objekts mit benutzerdefinierten Methoden aus einem bestimmten <xref:EnvDTE.ProjectItem> Objekt innerhalb des Projekts. Ein Projekt Untertyp kann Automatisierungs Erweiterungen verwenden, um dieses Objekt verfügbar zu machen. Die- <xref:EnvDTE80.IInternalExtenderProvider> Schnittstelle, die auf dem Hauptprojekt-Untertyp Aggregator implementiert ist, muss das-Objekt für den `VSHPROPID_ExtObjectCATID` von <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (entsprechend einer gewünschten `VSITEMID` ) CATID anbieten.  
  
- Project. Properties – diese Sammlung macht die Konfigurations unabhängigen Eigenschaften des `Project` Objekts verfügbar. Weitere Informationen zu Projekteigenschaften finden Sie unter <xref:EnvDTE.Project.Properties%2A> . Ein Projekt Untertyp kann mithilfe von Automatisierungsextendern seine Eigenschaften zu dieser Auflistung hinzufügen. Die- <xref:EnvDTE80.IInternalExtenderProvider> Schnittstelle, die auf dem Hauptprojekt-Untertyp Aggregator implementiert ist, muss das-Objekt für den `VSHPROPID_BrowseObjectCATID` from VSHPROPID2 (entsprechend dem `itemid` Wert VSITEMID_ROOT, von <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> ) CATID anbieten.  
  
- Configuration. Properties – diese Sammlung macht die Konfigurations abhängigen Eigenschaften des Projekts für eine bestimmte Konfiguration verfügbar (z. b. Debug). Weitere Informationen finden Sie unter <xref:EnvDTE.Configuration>. Ein Projekt Untertyp kann mithilfe von Automatisierungsextendern seine Eigenschaften zu dieser Auflistung hinzufügen. Die- <xref:EnvDTE80.IInternalExtenderProvider> Schnittstelle, die auf dem Hauptprojekt-Untertyp Aggregator implementiert ist, stellt das-Objekt für die CATID `VSHPROPID_CfgBrowseObjectCATID` (entsprechend dem- `itemid` Wert) zur Auswahl <xref:Microsoft.VisualStudio.VSConstants.VSITEMID> . Die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject> Schnittstelle wird verwendet, um ein Konfigurations Such Objekt von einem anderen zu unterscheiden.  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>

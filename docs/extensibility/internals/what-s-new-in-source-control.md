---
title: Was&#39;s in Quellcodeverwaltung | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio SDK], source control
- source control [Visual Studio SDK], what's new
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b46730ab1acac6605af2e1ff1c418dbe8c886406
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31137767"
---
# <a name="what39s-new-in-source-control"></a>Was&#39;s in Datenquellen-Steuerelements
In [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Sie können eine hochgradig Source Control-Lösung bereitstellen, indem ein Datenquellen-Steuerelement VSPackage implementieren. Dieser Abschnitt beschreibt die Funktionen des Datenquellen-Steuerelements VSPackages und bietet eine Übersicht über die Schritte für die Implementierung.  
  
## <a name="the-source-control-vspackage"></a>Das Source Control VSPackage  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] unterstützt zwei Arten von Datenquellen-Steuerelement-Lösungen. In allen Versionen von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], Sie können weiterhin integrieren, Datenquellen-Steuerelement-Plug-in-API-basierte-Plug-in. Sie können auch eine VSPackage für die Datenquellen-Steuerelements die bietet eine umfassende Integration erstellen [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Pfad für die Datenquellen-Steuerelement-Lösungen, die ein hohes Maß an Komplexität und Autonomie erfordern geeignet ist.  
  
 Eine VSPackage kann nahezu jede Art von Funktionen zum Hinzufügen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Ein Datenquellen-Steuerelement VSPackage bietet eine umfassende Quelle Steuerelement für [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], über die Benutzeroberfläche für den Benutzer auf die Back-End-Kommunikation mit dem Quellcodeverwaltungssystem dargestellt.  
  
 Implementieren ein VSPackage des Datenquellen-Steuerelement erfordert eine Strategie für die "" alle "oder" nichts ". Der Ersteller des ein Datenquellen-Steuerelement VSPackage muss eine beträchtliche Menge an Aufwand bei der Implementierung einer Reihe von Datenquellen-Steuerelement-Schnittstellen und neue Elemente der Benutzeroberfläche (Dialogfelder, Menüs und Symbolleisten), um die gesamte Quellcodeverwaltungsfunktion abzudecken sowie Schnittstellen investieren müssen. erforderlich für jedes Paket erfolgreich integriert [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Die folgenden Schritte bieten einen allgemeinen Überblick darüber, was benötigt wird, um ein Source Control-Paket zu implementieren. Weitere Informationen finden Sie unter [Erstellen eines Source Control VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md).  
  
1.  Erstellen eines VSPackages, das einen privaten quellcodeverwaltungsdienst proffers an.  
  
2.  Implementieren von Schnittstellen in der Quelle Steuerelement-bezogene Dienste, die von angeboten werden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (z. B. die <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> Schnittstelle).  
  
3.  Registrieren Sie die quellcodeverwaltung VSPackage ein.  
  
4.  Alle Datenquellen-Steuerelement-Benutzeroberfläche, z. B. Menüelemente, Dialogfelder, Symbolleisten und Kontextmenüs zu implementieren.  
  
5.  Alle Datenquellen-Steuerelement-bezogene Ereignisse werden der quellcodeverwaltung VSackage übergeben, wenn er aktiv ist und von Ihrem VSPackage behandelt werden muss.  
  
6.  Die quellcodeverwaltung VSPackage muss auf Ereignisse, z. B. die implementierende lauschen, die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> sowie Ereignisse nachverfolgen Projekt Dokument (TPD)-Schnittstelle (wie von implementiert die <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> Schnittstelle) und erforderliche Maßnahmen.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [Übersicht](../../extensibility/internals/source-control-integration-overview.md)   
 [Erstellen eines Quellcodeverwaltungs-VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)
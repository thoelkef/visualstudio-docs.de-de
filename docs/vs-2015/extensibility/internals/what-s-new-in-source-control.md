---
title: Neuigkeiten in der Quellcodeverwaltung
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio SDK], source control
- source control [Visual Studio SDK], what's new
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 31b55c57f47f25814eff24f13bcf91408468d0f4
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60087309"
---
# <a name="what39s-new-in-source-control-in-visual-studio-2015"></a>Was&#39;Neues in der Quellcodeverwaltung in Visual Studio 2015

[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] können Sie eine vollständig integriert Source-Control-Lösung bereitstellen, durch die Implementierung eines Quellcodeverwaltungs-VSPackage. Dieser Abschnitt beschreibt die Funktionen der quellcodeverwaltung VSPackages und bietet eine Übersicht über die Schritte für die Implementierung.  
  
## <a name="the-source-control-vspackage"></a>Der Quellcodeverwaltungs-VSPackage  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] unterstützt zwei Arten von Quellcode-Kontrollmechanismen. In allen Versionen von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], Sie können weiterhin integrieren, eine Source-Control-Plug-in-API-basierte-Plug-in. Sie können auch eine VSPackage für die quellcodeverwaltung bietet eine umfassende-Integration erstellen [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] Pfad für die Quellcode-Kontrollmechanismen, die ein hohes Maß an Komplexität und Autonomie erfordern geeignet ist.  
  
 Eine VSPackage kann nahezu jede Art von Funktionalität hinzufügen [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Ein Quellcodeverwaltungs-VSPackage bietet vollständige Quellcodeverwaltungsfeature für [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], über die Benutzeroberfläche, die dem Benutzer auf die Back-End-Kommunikation mit dem Quellcodeverwaltungssystem angezeigt.  
  
 Implementierung eines Quellcodeverwaltungs-VSPackage ist eine Strategie für die "Alles oder nichts" erforderlich. Der Ersteller eines Quellcodeverwaltungs-VSPackage muss sehr viel Aufwand bei der Implementierung einer Reihe von Steuerelement-Schnittstellen und neue Benutzeroberflächenelemente (Dialogfelder, Menüs und Symbolleisten) die gesamte Quelle Listensteuerelement-Funktionalität abgedeckt und Schnittstellen investieren. der hinzugefügten Pakete erforderlich werden, um die erfolgreiche Integration in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 Die folgenden Schritte bieten einen allgemeinen Überblick darüber, was benötigt wird, um ein Quellcodeverwaltungspaket zu implementieren. Weitere Informationen finden Sie unter [Erstellen eines Quellcodeverwaltungs-VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md).  
  
1. Erstellen Sie eine VSPackage, das einen privaten quellcodeverwaltungsdienst anbietet.  
  
2. Implementieren von Schnittstellen in Quelle Steuerelement-bezogenen Diensten, die durch, die angeboten werden [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (z. B. die <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> Schnittstelle).  
  
3. Registrieren Sie Ihre quellcodeverwaltung VSPackage ein.  
  
4. Implementieren Sie alle Datenquellen-Steuerelement-Benutzeroberfläche, auch werden, Menüelemente, Dialogfelder, Symbolleisten und Kontextmenüs.  
  
5. Alle Datenquellen-Steuerelement-bezogene Ereignisse werden der quellcodeverwaltung VSackage übergeben, wenn er aktiv ist, und vom VSPackage behandelt werden muss.  
  
6. Ihre quellcodeverwaltung VSPackage muss auf Ereignisse, z. B. die implementierende lauschen, die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> sowie die Ereignisse des Track-Project-Dokument (TPD)-Schnittstelle (entsprechend der Implementierung durch die <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> Schnittstelle) und erforderliche Maßnahmen.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [Übersicht](../../extensibility/internals/source-control-integration-overview.md)   
 [Erstellen eines Quellcodeverwaltungs-VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)

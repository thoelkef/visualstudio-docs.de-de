---
title: VSPackage-Struktur (Quellcodeverwaltungs-VSPackage) | Microsoft-Dokumentation
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
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
caps.latest.revision: 27
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6eaad545d1c1b3fe96ecbad3a88cc7636b777a54
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51737979"
---
# <a name="vspackage-structure-source-control-vspackage"></a>VSPackage-Struktur (Quellcodeverwaltungs-VSPackage)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Das Source-Steuerelement-Paket-SDK bietet Richtlinien zum Erstellen von einer VSPackages, das Zulassen einer Quelle Steuerelement Implementierer Quellcodeverwaltungsfunktionen mit seinem Integrieren der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Umgebung. Ein VSPackage ist eine COM-Komponente, die in der Regel bei Bedarf durch Laden der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integrierte Entwicklungsumgebung (IDE) auf Grundlage der Dienste, die vom Paket in seine Registrierungseinträge vorgenommen angekündigt werden. Jedes VSPackage implementieren muss die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>. Eine VSPackage in der Regel nutzt Dienste, die von der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE und einige eigene-Dienste anbietet.  
  
 Eine VSPackage deklariert seine Menüelemente und richtet einen Standardzustand des Elements über der VSCT-Datei ein. Die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE werden die Menüelemente in diesem Zustand angezeigt, bis das VSPackage geladen wird. Anschließend kann die VSPackage Implementierung von der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> aufgerufen, um aktivieren oder Deaktivieren von Menüelementen.  
  
## <a name="source-control-package-characteristics"></a>Source-Paket Eigenschaften  
 Ein Datenquellen-Steuerelement, das VSPackage ist umfassend in integriert [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 Die VSPackage-Semantik gehören:  
  
- Schnittstelle, die aufgrund ihrer Zugehörigkeit zu einem VSPackage implementiert werden (die `IVsPackage` Schnittstelle)  
  
- Benutzeroberfläche-Implementierung (VSCT-Datei und die Implementierung der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle)  
  
- Registrierung von VSPackages mit [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
  Das Quellcodeverwaltungs-VSPackage muss die Kommunikation mit diesen anderen [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Entitäten:  
  
- Projekte  
  
- Editoren  
  
- Projektmappen  
  
- Windows  
  
- Die aktive Dokumenttabelle  
  
### <a name="visual-studio-environment-services-that-may-be-consumed"></a>Visual Studio-Umgebung-Dienste, die genutzt werden kann  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 SVsRegisterScciProvider-Dienst  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>  
  
### <a name="vsip-interfaces-implemented-and-called"></a>VSIP-Schnittstellen implementiert und wird aufgerufen  
 Ein Quellcodeverwaltungspaket ist ein VSPackage und aus diesem Grund können sie direkt mit anderen VSPackages, die mit registriert sind interagieren [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Um die gesamte Bandbreite der quellcodeverwaltung zu gewährleisten, kann ein Datenquellen-Steuerelement Projekte oder die Shell bereitgestellten Schnittstellen für VSPackage behandeln.  
  
 In jedem Projekt [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] müssen implementieren die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> als ein Projekt in erkannt werden die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE. Diese Schnittstelle ist jedoch nicht spezialisiert genug für die quellcodeverwaltung. Projekte, die als quellcodeverwaltung werden steuern, implementieren die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>. Diese Schnittstelle wird durch das Quellcodeverwaltungs-VSPackage verwendet, zum Abfragen von ein Projekt für deren Inhalte und Symbole und Bindungsinformationen (die erforderlichen Informationen zum Herstellen einer Verbindung zwischen den Serverstandort und den Speicherort eines Projekts, die unter Bereitstellen Datenquellen-Steuerelement).  
  
 Das Datenquellen-Steuerelement, das VSPackage implementiert die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, wodurch wiederum ermöglicht Projekten, registrieren sich für die quellcodeverwaltung und deren Status Symbole abrufen.  
  
 Eine vollständige Liste der Schnittstellen, die ein Quellcodeverwaltungs-VSPackage berücksichtigen müssen, finden Sie unter [Verwandte Dienste und Schnittstellen](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Entwurfselemente](../../extensibility/internals/source-control-vspackage-design-elements.md)   
 [Verwandte Dienste und Schnittstellen](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)


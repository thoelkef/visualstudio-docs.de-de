---
title: VSPackage-Struktur (Quelle Steuerelement VSPackage) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
caps.latest.revision: "26"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 168aa0f7b93d20afaa30924dc17f05e0cac465bb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="vspackage-structure-source-control-vspackage"></a>VSPackage-Struktur (Quelle Steuerelement VSPackage)
Das Source Control Paket-SDK bietet Richtlinien zum Erstellen eines VSPackages, ermöglichen eine Quelle Steuerelement Implementierer sein eigenes Quellcodeverwaltungsfunktion mit Integration der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Umgebung. Ein VSPackage ist eine COM-Komponente, die in der Regel bei Bedarf durch geladen wird die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung (IDE) auf Grundlage der Dienste, die vom Paket in die Registrierungseinträge angekündigt werden. Jedes VSPackage implementieren muss die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>. Eine VSPackage in der Regel-Diensten nutzt die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE und proffers einige Dienste selbst.  
  
 Eine VSPackage die Menüelemente deklariert und richtet Standardstatus Element über die VSCT-Datei ein. Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zeigt IDE Menüelemente in diesem Zustand, bis das VSPackage geladen wurde. Anschließend kann die VSPackage Implementierung der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode wird aufgerufen, um zu aktivieren oder Deaktivieren von Menüelementen.  
  
## <a name="source-control-package-characteristics"></a>Datenquellen-Steuerelement Paketmerkmale  
 Ein VSPackage ist tief in integriert Quellcodeverwaltungs [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Die VSPackage-Semantik gehören:  
  
-   Schnittstelle, die implementiert werden, durch ein VSPackage wird (die `IVsPackage` Schnittstelle)  
  
-   Implementierung von UI-Befehl (VSCT-Datei und die Implementierung der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle)  
  
-   Registrierung des VSPackage mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Die Datenquellen-Steuerelements VSPackage muss kommunizieren mit diesen anderen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Entitäten:  
  
-   Projekte  
  
-   Editoren  
  
-   Projektmappen  
  
-   Windows  
  
-   Die Dokumenttabelle der ausgeführten  
  
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
 Ein Steuerelement Source-Paket ist ein VSPackage und aus diesem Grund können Sie sich direkt mit anderen VSPackages, die registriert werden interagieren [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Um die volle Bandbreite der Quellcodeverwaltungsfunktion zu gewährleisten, kann ein Datenquellen-Steuerelement von Projekten oder in der Befehlsshell bereitgestellten Schnittstellen VSPackage behandeln.  
  
 Jedes Projekt in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] implementieren müssen die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> als in-Projekt erkannt werden die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Diese Schnittstelle ist jedoch nicht speziell hoch genug für die Datenquellen-Steuerelements. Projekte, die unter der Quelle werden erwartet werden steuern, implementieren die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>. Diese Schnittstelle wird durch die quellcodeverwaltung VSPackage verwendet, um ein Projekt für ihre Inhalte abzufragen und um die Authentifizierungsfunktionalität bereitzustellen, Symbole und Bindungsinformationen (die benötigten Informationen zum Herstellen einer Verbindungs zwischen den Standort des Servers und eines Projekts, die unter dem Speicherort des Datenträgers Datenquellen-Steuerelement).  
  
 Die Datenquellen-Steuerelements, das VSPackage implementiert die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, wodurch wiederum Projekte, registrieren sich für die quellcodeverwaltung und ihren Status Symbole abzurufen.  
  
 Eine vollständige Liste der Schnittstellen, die ein Datenquellen-Steuerelement VSPackage berücksichtigen müssen, finden Sie unter [verknüpften Diensten und Schnittstellen](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Entwurfselemente](../../extensibility/internals/source-control-vspackage-design-elements.md)   
 [Verknüpfte Dienste und Schnittstellen](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)
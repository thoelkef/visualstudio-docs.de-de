---
title: "VSPackage-Struktur (Source Control VSPackage) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPackages, Struktur"
  - "Quellcode-Verwaltungspaketen VSPackage (Übersicht)"
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
caps.latest.revision: 26
caps.handback.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
---
# VSPackage-Struktur (Source Control VSPackage)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Der Source Control Paket SDK bietet Richtlinien für das Erstellen eines VSPackages ermöglichen eine Quelle Steuerelement Ausführender Quellcodeverwaltungsfunktionen mit seinem Integrieren der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Umgebung. Ein VSPackage ist eine COM\-Komponente, die in der Regel bei Bedarf durch Laden der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung \(IDE\) auf Grundlage der Dienste, die vom Paket in den Registrierungseinträgen angekündigt werden. Jede VSPackage implementieren muss die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>. Ein VSPackage i. d. r. angebotenen Dienste nutzt die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE und einige Dienste über eigene proffers.  
  
 Ein VSPackage deklariert seine Menüelemente und richtet den Standardzustand der Artikel über die VSCT\-Datei. Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zeigt IDE Menüelemente in diesem Zustand, bis das VSPackage geladen wird. Anschließend kann das VSPackage\-Implementierung von der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode wird aufgerufen, um zu aktivieren oder Deaktivieren von Menüelementen.  
  
## Source Control Package\-Eigenschaften  
 Ein Datenquellen\-Steuerelement, das VSPackage ist tief in integriert [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Die Semantik des VSPackage enthalten:  
  
-   Schnittstelle, die aufgrund ihrer Zugehörigkeit zu einem VSPackage implementiert werden \(die `IVsPackage` Schnittstelle\)  
  
-   Implementierung von UI\-Befehl \(VSCT\-Datei und die Implementierung der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle\)  
  
-   Registrierung des VSPackage mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Das Datenquellen\-Steuerelement VSPackage muss kommunizieren mit diesen anderen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Entitäten:  
  
-   Projekte  
  
-   Editoren  
  
-   Projektmappen  
  
-   Windows  
  
-   Der Dokumenttabelle der aktiven  
  
### Visual Studio\-Umgebung\-Dienste, die verwendet werden können  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 SVsRegisterScciProvider\-Dienst  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>  
  
### VSIP\-Schnittstellen implementiert und aufgerufen  
 Quellcodeverwaltungs\-Paket ist ein VSPackage, und daher können sie direkt mit anderen VSPackages, die bei registriert sind interagieren [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Um die volle Bandbreite der Quellcodeverwaltungsfunktionen bereitzustellen, kann ein Datenquellen\-Steuerelement VSPackage\-Projekten oder in der Befehlsshell bereitgestellten Schnittstellen behandeln.  
  
 Jedes Projekt in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] implementieren muss die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> als ein Projekt erkannt werden die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Diese Schnittstelle ist jedoch nicht speziell für Datenquellen\-Steuerelement ausreichend. Projekte, die unter Quelle werden steuern, implementieren die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>. Diese Schnittstelle wird von der Datenquelle VSPackage verwendet, ein Projekt für den Inhalt Abfragen und zur Verfügung stellt, Symbole und Bindungsinformationen \(die Informationen zum Herstellen einer Verbindungs zwischen den Serverstandort und den Speicherort ein Projekt, das Datenquellen\-Steuerelement ist erforderlich\).  
  
 Das Datenquellen\-Steuerelement, das VSPackage implementiert die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, wodurch wiederum Projekte, registrieren sich für Datenquellen\-Steuerelement und deren Status Symbole abzurufen.  
  
 Eine vollständige Liste der Schnittstellen, die ein Datenquellen\-Steuerelement VSPackage berücksichtigen müssen, finden Sie unter [\-Bezogenen Diensten und Schnittstellen](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md).  
  
## Siehe auch  
 [Design\-Elemente](../../extensibility/internals/source-control-vspackage-design-elements.md)   
 [\-Bezogenen Diensten und Schnittstellen](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)
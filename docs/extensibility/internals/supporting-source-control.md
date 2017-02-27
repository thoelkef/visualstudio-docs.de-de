---
title: "Unterst&#252;tzung von Datenquellen-Steuerelement | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Source Control [Visual Studio SDK], Unterstützung"
ms.assetid: 567acde3-354e-4f39-8d99-0ef86c103396
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# Unterst&#252;tzung von Datenquellen-Steuerelement
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Auscheckvorgänge unterstützt[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , Einchecken und andere Quellcodeverwaltungsvorgänge für das Projekt bzw. den Editor.  Als Quellcodeverwaltung client ist [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entworfen, um mit einem Paket Quellcodeverwaltung, z. B. [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]zu interagieren, das das Archivieren bereitstellt, Versionsverwaltung und Sicherheitsschnittstellen für einen dynamisch definierten Satz von Dateien.  
  
## In diesem Abschnitt  
 [Modell für Source Control\-Pakete](../../extensibility/internals/model-for-source-control-packages.md)  
 Beschreibt die Schnittstellen, die einen Projekttyp implementieren muss, um die Quellcodeverwaltung zu unterstützen.  
  
 [Designentscheidungen](../../extensibility/internals/source-control-design-decisions.md)  
 Stellt Informationen bereit, deren Antworten ändern, wie Sie einen Projekttyp implementieren.  
  
 [Ausführliche Informationen zur Konfiguration](../../extensibility/internals/source-control-configuration-details.md)  
 Beschreibt, wie Änderungen der Quellcodeverwaltung unterliegen, unterstützt die Implementierung eines Projekttyps.  
  
 [Weitere Richtlinien für Projekte und Editoren](../../extensibility/internals/additional-source-control-guidelines-for-projects-and-editors.md)  
 Erörtert Methoden für Projekttypen und Editoren.  
  
 [Laufzeit\-Details](../../extensibility/internals/source-control-runtime-details.md)  
 Beschreibt, wie ein Projekt registriert, wenn ein Benutzer einem Quellcodeverwaltungssystem sie hinzugefügt werden.  
  
## Referenz  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>  
 Teilt dem Paket oder Umgebungs\- Quellcodeverwaltung an, dass eine Datei im Begriff ist, im Speicher geändert oder gespeichert werden.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>  
 Ermöglicht Projekte und Hierarchien, deren Schnittmenge mit Quellcodeverwaltung zu registrieren und Quellcodeverwaltung Informationen über den Status zu erhalten.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>  
 Wird in einem Projektsystem, um die Quellcodeverwaltung für Projektdateien und Projektelemente bereitzustellen.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>  
 Wird von Projekten, die Umgebung abzufragen, damit die Berechtigung hinzufügen, entfernen oder benennen Sie eine Datei oder ein Verzeichnis in einer Projektmappe.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>  
 Benachrichtigt Clients über Änderungen, die an den Projektdateien oder Verzeichnissen vorgenommen wurden.  
  
## Verwandte Abschnitte  
 [Projekttypen](../../extensibility/internals/project-types.md)  
 Bietet eine Übersicht über Projekte als die Grundbausteine der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung \(IDE\).  Links zu weiteren Themen bereitgestellt, in denen das Projekt steuer und Kompilieren von Code verdeutlichen.
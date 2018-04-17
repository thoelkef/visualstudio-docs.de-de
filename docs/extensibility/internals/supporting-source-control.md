---
title: Datenquellen-Steuerelements unterstützen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], supporting
ms.assetid: 567acde3-354e-4f39-8d99-0ef86c103396
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9ae3590a5d02c2b3f1d4b67f724d0177f671f7d2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="supporting-source-control"></a>Unterstützung von Datenquellen-Steuerelements
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Auschecken von Dateien, Check-ins und andere Quellcodeverwaltungsvorgänge für das Projekt oder die-Editor unterstützt. Als einem Quellcodeverwaltungsclient [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dient für die Interaktion mit einem Steuerelement-Quellpaket [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], Archivierung, versionsverwaltung und Steuerung Einrichtungen für eine dynamisch definierte Gruppe von Dateien bietet.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Modell für Quellcodeverwaltungspakete](../../extensibility/internals/model-for-source-control-packages.md)  
 Beschreibt die Schnittstellen, die ein Projekttyp implementieren muss zur Unterstützung des Datenquellen-Steuerelements.  
  
 [Entwurfsentscheidungen](../../extensibility/internals/source-control-design-decisions.md)  
 Stellt Fragen, deren Antworten zu ändern, wie Sie einen Projekttyp implementieren.  
  
 [Konfigurationsdetails](../../extensibility/internals/source-control-configuration-details.md)  
 Beschreibt, wie Datenquellen-Steuerelements unterstützen die Implementierung des Project-Typs ändert.  
  
 [Zusätzliche Richtlinien für Projekte und Editoren](../../extensibility/internals/additional-source-control-guidelines-for-projects-and-editors.md)  
 Beschreibt bewährte Methoden für Projekttypen und Editoren.  
  
 [Common Language Runtime-Details](../../extensibility/internals/source-control-runtime-details.md)  
 Beschreibt, wie ein Projekt zu registrieren, wenn ein Benutzer auf einem Quellcodeverwaltungssystem hinzufügt.  
  
## <a name="reference"></a>Referenz  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>  
 Gibt an, für die Umgebung oder Ihre Source Control-Paket, die eine Datei im Arbeitsspeicher geändert oder gespeichert werden.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>  
 Können Projekte und-Hierarchien an, registrieren sich mit der quellcodeverwaltung und Abrufen von Informationen zum Status des Datenquellen-Steuerelement.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>  
 Implementiert ein Projektsystem Projektdateien und Projektelemente Datenquellen-Steuerelements bereit.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>  
 Von Projekten verwendet zum Abfragen der Umgebung für die Berechtigung zum Hinzufügen, entfernen oder Umbenennen einer Datei oder eines Verzeichnisses in einer Projektmappe.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>  
 Benachrichtigt Clients, der Project-Dateien oder Verzeichnisse vorgenommenen Änderungen.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Projekttypen](../../extensibility/internals/project-types.md)  
 Bietet eine Übersicht über Projekte als die Grundbausteine der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung (IDE). Links werden zu weiteren Themen bereitgestellt, die erläutern, wie Projekte steuern, erstellen und Kompilieren von Code.
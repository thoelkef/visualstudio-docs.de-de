---
title: Unterstützung des Datenquellen-Steuerelement | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], supporting
ms.assetid: 567acde3-354e-4f39-8d99-0ef86c103396
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d1166197a5c79dcb0d1ddf4018227914346a6172
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58957470"
---
# <a name="supporting-source-control"></a>Unterstützen der Quellcodeverwaltung
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] unterstützt die Datei auschecken, Eincheckvorgänge und andere Quellcodeverwaltungsvorgänge für Ihr Projekt oder den Editor. Als ein Quellcode-Verwaltungsclient [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] dient zur Interaktion mit einem Quellcodeverwaltungspaket [!INCLUDE[vsvss](../../includes/vsvss-md.md)], die bereitstellt, Archivierung, versionsverwaltung und Kontrolle-Funktionen für eine dynamisch definierte Gruppe von Dateien.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Modell für Quellcodeverwaltungspakete](../../extensibility/internals/model-for-source-control-packages.md)  
 Beschreibt die Schnittstellen, die ein Projekttyp implementieren muss zur Unterstützung des Datenquellen-Steuerelement.  
  
 [Entwurfsentscheidungen](../../extensibility/internals/source-control-design-decisions.md)  
 Stellt Fragen, deren Antworten zu ändern, wie Sie einen Projekttyp implementieren.  
  
 [Konfigurationsdetails](../../extensibility/internals/source-control-configuration-details.md)  
 Beschreibt, wie das Datenquellen-Steuerelement unterstützt die Implementierung eines Projekttyps ändert.  
  
 [Zusätzliche Richtlinien für Projekte und Editoren](../../extensibility/internals/additional-source-control-guidelines-for-projects-and-editors.md)  
 Beschreibt bewährte Methoden für Projekttypen und Editoren.  
  
 [Runtime-Details](../../extensibility/internals/source-control-runtime-details.md)  
 Beschreibt, wie ein Projekt zu registrieren, wenn ein Benutzer ein Quellcodeverwaltungssystem hinzugefügt.  
  
## <a name="reference"></a>Referenz  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>  
 Gibt an, dem umgebungs-oder Quellcodeverwaltungspaket, die eine Datei im Arbeitsspeicher geändert oder gespeichert werden.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>  
 Können Projekte und Hierarchien, registrieren sich mit der quellcodeverwaltung und Abrufen von Informationen zu den Status der quellcodeverwaltung.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>  
 In einem Projektsystem, geben Sie die quellcodeverwaltung für Projektdateien und Projektelemente implementiert.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>  
 Von Projekten verwendet, um die Umgebung für die Berechtigung zum Hinzufügen, entfernen oder Umbenennen einer Datei oder eines Verzeichnisses in einer Projektmappe abzufragen.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>  
 Benachrichtigt Clients über Änderungen, die an Projektdateien oder-Verzeichnissen vorgenommen wurden.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Projekttypen](../../extensibility/internals/project-types.md)  
 Bietet eine Übersicht über Projekte als die grundlegenden Bausteine von der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integrierte Entwicklungsumgebung (IDE). Links werden zu weiteren Themen bereitgestellt, die erläutern, wie Projekte zu erstellen und Kompilieren von Code steuern.

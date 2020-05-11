---
title: Unterstützung der Quellcodeverwaltung | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], supporting
ms.assetid: 567acde3-354e-4f39-8d99-0ef86c103396
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 84de3120783528d209b1475477aee5087edac42b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704730"
---
# <a name="supporting-source-control"></a>Unterstützen der Quellcodeverwaltung
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]unterstützt Dateiauschecken, Eincheckvorgänge und andere Quellcodeverwaltungsvorgänge für Ihr Projekt oder Ihren Editor. Als Quellcodeverwaltungsclient [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ist die Interaktion mit einem Quellcodeverwaltungspaket konzipiert, z. [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]B. , das Archivierungs-, Versionsverwaltungs- und Steuerungsfunktionen für einen dynamisch definierten Satz von Dateien bereitstellt.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Modell für Quellcodeverwaltungspakete](../../extensibility/internals/model-for-source-control-packages.md)

 Beschreibt die Schnittstellen, die ein Projekttyp implementieren muss, um die Quellcodeverwaltung zu unterstützen.

- [Designentscheidungen](../../extensibility/internals/source-control-design-decisions.md)

 Stellt Fragen bereit, deren Antworten die Implementierung eines Projekttyps ändern.

- [Konfigurationsdetails](../../extensibility/internals/source-control-configuration-details.md)

 Beschreibt, wie die Unterstützung der Quellcodeverwaltung die Implementierung eines Projekttyps ändert.

- [Zusätzliche Richtlinien für Projekte und Editoren](../../extensibility/internals/additional-source-control-guidelines-for-projects-and-editors.md)

 Erläutert bewährte Methoden für Projekttypen und Editoren.

- [Runtime-Details](../../extensibility/internals/source-control-runtime-details.md)

 Beschreibt, wie ein Projekt registriert wird, wenn ein Benutzer es einem Quellcodeverwaltungssystem hinzufügt.

## <a name="reference"></a>Referenz
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>Gibt der Umgebung oder dem Quellcodeverwaltungspaket an, dass eine Datei im Arbeitsspeicher geändert oder gespeichert werden soll.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>Ermöglicht Es Projekten und Hierarchien, sich selbst bei der Quellcodeverwaltung zu registrieren und Informationen zum Quellcodeverwaltungsstatus zu erhalten.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>In einem Projektsystem implementiert, um die Quellcodeverwaltung für Projektdateien und Projektelemente bereitzustellen.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>Wird von Projekten verwendet, um die Umgebung nach Berechtigungen zum Hinzufügen, Entfernen oder Umbenennen einer Datei oder eines Verzeichnisses in einer Projektmappe abzufragen.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>Benachrichtigt Clients über Änderungen, die an Projektdateien oder Verzeichnissen vorgenommen wurden.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Projekttypen](../../extensibility/internals/project-types.md)

 Bietet einen Überblick über Projekte als [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] grundlegende Bausteine der integrierten Entwicklungsumgebung (IDE). Es werden Links zu weiteren Themen bereitgestellt, in denen erläutert wird, wie Projekte das Erstellen und Kompilieren von Code steuern.

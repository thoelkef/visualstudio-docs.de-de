---
title: Übersicht über Lösungen
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, about solutions
ms.assetid: 3b21e3a1-170a-4485-941e-6b04b7b27886
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 767db749d953855cd5c6f81f356a195c830aa838
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705301"
---
# <a name="solutions-overview"></a>Übersicht über Lösungen

Eine Projektmappe ist eine Gruppierung eines oder mehrerer Projekte, die zusammenarbeiten, um eine Anwendung zu erstellen. Die Projekt- und Statusinformationen zur Projektmappe werden in zwei verschiedenen Projektmappendateien gespeichert. Die [Lösungsdatei (.sln)](solution-dot-sln-file.md) ist textbasiert und kann unter Quellcodeverwaltung platziert und von Benutzern gemeinsam genutzt werden. Die [Lösungsbenutzeroption (.suo)](solution-user-options-dot-suo-file.md) Datei ist binär. Daher kann die .suo-Datei nicht unter Quellcodeverwaltung gestellt werden und enthält benutzerspezifische Informationen.

Jedes VSPackage kann in beide Lösungsdateien schreiben. Aufgrund der Art der Dateien gibt es zwei verschiedene Schnittstellen implementiert, um sie zu schreiben. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> Schnittstelle schreibt Textinformationen in die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> .sln-Datei und die Schnittstelle schreibt binäre Streams in die .suo-Datei.

> [!NOTE]
> Ein Projekt muss nicht explizit einen Eintrag für sich selbst in die Projektmappendatei schreiben. die Umgebung verarbeitet dies für das Projekt. Daher müssen Sie Ihr VSPackage nicht auf diese Weise registrieren, es sei denn, Sie möchten der Lösungsdatei zusätzliche Inhalte speziell hinzufügen.

Jede VSPackage-unterstützende Lösungpersistenz <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> verwendet drei Schnittstellen, die Schnittstelle, die von `IVsPersistSolutionProps` der `IVsPersistSolutionOpts`Umgebung implementiert und vom VSPackage aufgerufen wird, und und , die beide vom VSPackage implementiert werden. Die `IVsPersistSolutionOpts` Schnittstelle muss nur implementiert werden, wenn private Informationen vom VSPackage in die .suo-Datei geschrieben werden sollen.

Wenn eine Lösung geöffnet wird, findet der folgende Prozess statt.

1. Die Umgebung liest die Lösung.

2. Wenn die Umgebung `CLSID`eine findet, lädt sie das entsprechende VSPackage.

3. Wenn ein VSPackage geladen wird, ruft `QueryInterface` die Umgebung die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> Schnittstelle für die Schnittstelle auf, die das VSPackage benötigt.

   - Beim Lesen aus einer .sln-Datei ruft `QueryInterface` die Umgebung `IVsPersistSolutionProps`nach .

   - Beim Lesen aus einer .suo-Datei ruft `QueryInterface` die Umgebung `IVsPersistSolutionOpts`nach .

   Spezifische Informationen zur Verwendung dieser Dateien finden Sie in [Solution (. Sln) Datei-](../../extensibility/internals/solution-dot-sln-file.md) und [Lösungsbenutzeroptionen (. Suo) Datei](../../extensibility/internals/solution-user-options-dot-suo-file.md).

> [!NOTE]
> Wenn Sie eine neue Projektmappenkonfiguration erstellen möchten, die aus den Konfigurationen von zwei Projekten besteht und ein Drittel vom Build ausschließt, müssen Sie die Benutzeroberfläche oder Automatisierung von Eigenschaftenseiten verwenden. Sie können die Lösungsbuild-Manager-Konfigurationen und deren Eigenschaften nicht direkt `SolutionBuild` ändern, aber Sie können den Lösungsbuild-Manager mithilfe der Klasse von DTE im Automatisierungsmodell bearbeiten. Weitere Informationen zum Konfigurieren von Lösungen finden Sie unter [Lösungskonfiguration](../../extensibility/internals/solution-configuration.md).

## <a name="see-also"></a>Weitere Informationen

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>

---
title: Projekt "sonstige Dateien" | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- files, adding existing files to solutions
- Miscellaneous Files project
- Solution Items folder
- files, opening with Miscellaneous Files project
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c46126507ef9bb293bd0fa6771f53343ad6206f7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726678"
---
# <a name="miscellaneous-files-project"></a>Verschiedene Projektdateien
Wenn ein Benutzer Projekt Elemente öffnet, weist die IDE dem Projekt "sonstige Dateien" alle Elemente zu, die keine Mitglieder einer Projekt Mappe sind.

 Projekte spielen eine bedeutende Rolle beim bestimmen, welcher Editor verwendet wird, wenn ein Benutzer ein Projekt Element öffnet. Ein Projekt kann so entworfen werden, dass bestimmte Dateien mit einem projektspezifischen Editor oder einem Standard Editor geöffnet werden.

 Für einen projektspezifischen Editor ist es in der Regel erforderlich, dass der Benutzer über besondere Kenntnisse verfügt oder besondere Schnittstellen aus dem Projekt verwendet. Weitere Informationen finden Sie unter Gewusst [wie: Öffnen von projektspezifischen Editoren](../../extensibility/how-to-open-project-specific-editors.md).

 Mit einem Standard-Editor kann eine beliebige Datei einer bestimmten Erweiterung in jedem Projekt geöffnet werden. Der Benutzer kann einige Standard-Editoren, z. b. den [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Text-Editor, für Projekte anpassen, behält aber weiterhin sein öffentliches Zeichen bei. Standard-Editoren werden mithilfe der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>-Methode erstellt.

 Wenn kein Projekt in der Projekt Mappe antwortet, dass ein Projekt Element geöffnet werden kann, stellt die IDE ein spezielles Projekt namens "sonstige Dateien" bereit, mit dem eine beliebige Datei geöffnet wird.

 Dieses spezielle Projekt ermöglicht das Öffnen einer Datei außerhalb des Kontexts eines Projekts. Während der Verarbeitung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A>-Methode antwortet das Projekt "sonstige Dateien" immer mit einer sehr niedrigen Priorität. Aus diesem Grund ergibt das Projekt "sonstige Dateien" immer alle Projekte mit höherer Priorität, die Dateien öffnen können.

 Das Projekt "sonstige Dateien" erfordert nicht, dass der Benutzer es explizit mit dem Dialogfeld " **Neues Projekt** " erstellt. Außerdem verwaltet das Projekt "sonstige Dateien" eine Liste von Projekt Membern nicht dauerhaft. Es wird ein optionales Feature verwendet, um eine Liste der zuletzt verwendeten Dateien für jeden Benutzer aufzuzeichnen.

## <a name="see-also"></a>Siehe auch
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>
- <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>
- [Gewusst wie: Öffnen von projektspezifischen Editoren](../../extensibility/how-to-open-project-specific-editors.md)
- [Gewusst wie: Öffnen von Standard-Editoren](../../extensibility/how-to-open-standard-editors.md)
- [Hinzufügen von Projekt- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Hinzufügen von Projekt- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md)
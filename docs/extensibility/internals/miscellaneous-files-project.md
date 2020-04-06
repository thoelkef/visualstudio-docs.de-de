---
title: Projekt für verschiedene Dateien | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- files, adding existing files to solutions
- Miscellaneous Files project
- Solution Items folder
- files, opening with Miscellaneous Files project
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 95cc1312fb7b381e1e20df834698480295fadcc8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707100"
---
# <a name="miscellaneous-files-project"></a>Verschiedene Projektdateien
Wenn ein Benutzer Projektelemente öffnet, weist die IDE dem Projekt Verschiedene Dateien alle Elemente zu, die nicht Mitglieder von Projekten in einer Projektmappe sind.

 Projekte spielen eine wichtige Rolle bei der Bestimmung, welcher Editor verwendet wird, wenn ein Benutzer ein Projektelement öffnet. Ein Projekt kann entworfen werden, um bestimmte Dateien mithilfe eines projektspezifischen Editors oder eines Standardeditors zu öffnen.

 Ein projektspezifischer Editor erfordert in der Regel, dass der Benutzer über spezielle Kenntnisse verfügt oder spezielle Schnittstellen aus dem Projekt verwendet. Weitere Informationen finden Sie unter [Gewusst wie: Öffnen von projektspezifischen Editoren](../../extensibility/how-to-open-project-specific-editors.md).

 Ein Standardeditor kann jede Datei einer bestimmten Erweiterung in jedem Projekt öffnen. Der Benutzer kann einige Standardeditoren, z. B. den [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Texteditor, für Projekte anpassen, aber dennoch ihren öffentlichen Charakter beibehalten. Standard-Editoren werden <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> mit der Methode erstellt.

 Wenn kein Projekt in der Projektmappe darauf reagiert, dass ein Projektelement geöffnet werden kann, stellt die IDE ein spezielles Projekt namens "Verschiedene Dateien" bereit, das eine beliebige Datei öffnet.

 Dieses spezielle Projekt sieht das Öffnen einer Datei außerhalb des Kontexts eines Projekts vor. Während der Verarbeitung <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> der Methode reagiert das Projekt Verschiedene Dateien immer mit sehr geringer Priorität. Daher gibt das Projekt Verschiedene Dateien immer jedem Projekt mit höherer Priorität nach, das Dateien öffnen kann.

 Das Projekt Verschiedene Dateien erfordert nicht, dass der Benutzer es explizit mit dem Dialogfeld **Neues Projekt** erstellt. Außerdem verwaltet das Projekt Verschiedene Dateien keine Liste von Projektmitgliedern dauerhaft. Es verwendet eine optionale Funktion, um eine Liste der zuletzt verwendeten Dateien für jeden Benutzer aufzuzeichnen.

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>
- <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>
- [Gewusst wie: Öffnen von projektspezifischen Editoren](../../extensibility/how-to-open-project-specific-editors.md)
- [Gewusst wie: Öffnen von Standard-Editoren](../../extensibility/how-to-open-standard-editors.md)
- [Hinzufügen von Projekt- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Hinzufügen von Projekt- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md)

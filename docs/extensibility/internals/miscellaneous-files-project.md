---
title: Projekt "Sonstige Dateien" | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- files, adding existing files to solutions
- Miscellaneous Files project
- Solution Items folder
- files, opening with Miscellaneous Files project
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3a1d0530d6a7a759bfab557be1a3d80fcfc9df78
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56630820"
---
# <a name="miscellaneous-files-project"></a>Verschiedene Projektdateien
Wenn ein Benutzer die Projektelemente geöffnet wird, weist die IDE alle Elemente, die keine Projekte in einer Projektmappe gehören, auf das Projekt verschiedene Dateien.

 Projekte spielen eine bedeutende Rolle beim bestimmen, welcher Editor verwendet wird, wenn ein Benutzer ein Projektelement geöffnet wird. Ein Projekt kann entworfen werden, um bestimmte Dateien über einen projektspezifischen Editor oder einem standard-Editor zu öffnen.

 Ein projektspezifischer Editor erfordert in der Regel an, dass der Benutzer verfügen über spezielle Kenntnisse oder spezielle Schnittstellen aus dem Projekt. Weitere Informationen finden Sie unter [Vorgehensweise: Öffnen von projektspezifischen Editoren](../../extensibility/how-to-open-project-specific-editors.md).

 Ein standard-Editor, kann in jedem Projekt eine Datei eine bestimmte Erweiterung öffnen. Benutzer kann einige standard-Editoren, anpassen, wie z. B. die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Text-Editor für Projekte, behalten aber immer noch ihre öffentlichen Zeichen. Standard-Editoren werden erstellt, mit der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> Methode.

 Wenn kein Projekt in der Projektmappe antwortet, dass ein Projektelement geöffnet werden kann, bietet die IDE ein bestimmtes Projekt aufgerufen, das Projekt verschiedene Dateien, das eine beliebige Datei geöffnet wird.

 Dieses spezielle Projekt bietet zum Öffnen einer Datei außerhalb des Kontexts eines Projekts. Bei der Verarbeitung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> -Methode, mit sehr niedriger Priorität immer das Projekt verschiedene Dateien antwortet. Aus diesem Grund Projekt verschiedene Dateien immer führt zu höherer Priorität Projekte, die Dateien öffnen können.

 Das Projekt verschiedene Dateien nicht, dass der Benutzer explizit erstellen sie mit der **neues Projekt** Dialogfeld. Darüber hinaus verwaltet das Projekt verschiedene Dateien nicht dauerhaft eine Liste von Projektmitgliedern. Ein optionales Feature verwendet, um eine Liste der zuletzt verwendeten Dateien für jeden Benutzer aufgezeichnet.

## <a name="see-also"></a>Siehe auch
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>
- <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>
- [Vorgehensweise: Öffnen von projektspezifischen Editoren](../../extensibility/how-to-open-project-specific-editors.md)
- [Vorgehensweise: Open-Standard-Editoren](../../extensibility/how-to-open-standard-editors.md)
- [Hinzufügen von Projekt- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Hinzufügen von Projekt- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md)
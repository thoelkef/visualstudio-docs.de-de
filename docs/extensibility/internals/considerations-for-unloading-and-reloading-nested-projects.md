---
title: Überlegungen zum Entladen und Neuladen von geschachtelten Projekten | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: db5af7d761df39e2a0fee29f27e3f34526f07a7e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53870939"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>Überlegungen zu entladen und Neuladen von geschachtelten Projekten

Wenn Sie geschachtelte Projekttypen implementieren, müssen Sie zusätzliche Schritte ausführen, wenn Sie entladen und Laden Sie die Projekte erneut. Sie müssen ordnungsgemäß auslösen, um Listener zu Projektmappenereignissen ordnungsgemäß zu benachrichtigen, die `OnBeforeUnloadProject` und `OnAfterLoadProject` Ereignisse.

Ein Grund zum Auslösen dieser Ereignisse ist für die quellcodeverwaltung (SCC). Sie möchten nicht SCC aus, um die Elemente vom Server zu löschen und dann hinzufügen, als *neue* liegt eine `Get` Vorgang aus SCC. In diesem Fall würde eine neue Datei aus SCC geladen werden. Sie müssten entladen und laden alle Dateien aus, für den Fall, dass sie unterschiedlich sind.

Source Code Control ruft `ReloadItem`. Implementieren der <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> Schnittstelle aufrufen, `OnBeforeUnloadProject` und `OnAfterLoadProject` löschen Sie das Projekt, und erstellen Sie ihn erneut. Wenn Sie auf diese Weise die Schnittstelle implementieren, wird die SCC darüber informiert, dass das Projekt wurde vorübergehend gelöscht und erneut hinzugefügt. Aus diesem Grund nicht SCC auf das Projekt arbeiten, als ob das Projekt wurde *tatsächlich* gelöscht und erneut hinzugefügt.

## <a name="reload-projects"></a>Laden von Projekten

Um das erneute Laden von geschachtelten Projekten unterstützen, implementieren Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> Methode. In der Implementierung von `ReloadItem`, Sie schließen die geschachtelte Projekte, und dann neu erstellen.

In der Regel ein Projekt erneut geladen wird, die IDE löst, wenn die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> Ereignisse. Für geschachtelte Projekte, die gelöscht und neu geladen werden, initiiert das übergeordnete Projekt jedoch den Prozess, der nicht in der IDE. Da das übergeordnete Projekt keine Projektmappenereignisse auslösen, und die IDE verfügt über keine Informationen zur Initialisierung des Prozesses, werden nicht die Ereignisse ausgelöst.

Dieser Prozess, die Aufrufe der übergeordneten Projekt zu behandeln `QueryInterface` auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> Schnittstelle. `IVsFireSolutionEvents` verfügt über Funktionen, die die IDE zum Auslösen von Teilen der `OnBeforeUnloadProject` Ereignis, das geschachtelte Projekt entladen, und erhöhen Sie dann die `OnAfterLoadProject` Ereignis, um das gleiche Projekt erneut laden.

## <a name="see-also"></a>Siehe auch

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- [Schachteln von Projekten](../../extensibility/internals/nesting-projects.md)
---
title: Überlegungen für das entladen und erneutes Laden geschachtelt Projekte | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
caps.latest.revision: ''
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: bfe39e82a9f15825a5328fe1950347add9d182bb
ms.sourcegitcommit: 67374acb6d24019a434d96bf705efdab99d335ee
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>Überlegungen zum Entladen und erneutes Laden geschachtelten Projekte

Wenn Sie geschachtelte Projekttypen implementieren, müssen Sie zusätzliche Schritte ausführen, wenn entladen und laden die Projekte. Sie müssen ordnungsgemäß auslösen, um Listener zur Lösung Ereignisse korrekt zu benachrichtigen, die `OnBeforeUnloadProject` und `OnAfterLoadProject` Ereignisse.

Ein Grund für das Auslösen dieser Ereignisse ist für die quellcodeverwaltung (SCC). Sollen SCC löschen die Elemente auf dem Server, und fügen Sie ihn dann wieder als *neue* ist ein `Get` Vorgang von SCC. In diesem Fall würde eine neue Datei außerhalb des gültigen SCC geladen werden. Sie müssen dann entladen und laden alle Dateien aus, für den Fall, dass sie verschiedene sind.

Source Code Control Aufrufe `ReloadItem`. Implementieren der <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> Schnittstelle aufrufen `OnBeforeUnloadProject` und `OnAfterLoadProject` löschen Sie das Projekt und erstellen Sie ihn erneut. Wenn Sie auf diese Weise die Schnittstelle implementieren, wird die SCC darüber informiert, dass das Projekt wurde vorübergehend gelöscht und erneut hinzugefügt. Aus diesem Grund nicht SCC für das Projekt arbeiten, als wäre das Projekt *tatsächlich* gelöscht und erneut hinzugefügt.

## <a name="reloading-projects"></a>Erneutes Laden von Projekten

Zum erneuten Laden des geschachtelten Projekte zu unterstützen, implementieren Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> Methode. In der Implementierung von `ReloadItem`, die geschachtelte Projekte schließen und dann neu erstellen.

In der Regel, wenn ein Projekt geladen wird, die IDE löst die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> Ereignisse. Allerdings startet übergeordneten Projekts für geschachtelte Projekte, die gelöscht und erneut geladen werden, der werden nicht in der IDE an. Die Ereignisse werden nicht ausgelöst, da übergeordneten Projekts keine Lösung Ereignisse auslösen und die IDE keine Informationen zur Initialisierung des Prozesses hat.

Dieser Prozess, die Aufrufe der übergeordneten Projekt behandelt `QueryInterface` auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> Schnittstelle. `IVsFireSolutionEvents` verfügt über Funktionen, die von der IDE zum Auslösen von Teilen der `OnBeforeUnloadProject` Ereignis, um das Entladen des geschachtelten Projekts, und erhöhen Sie dann die `OnAfterLoadProject` Ereignis, um das gleiche Projekt erneut laden.

## <a name="see-also"></a>Siehe auch

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- [Schachteln von Projekten](../../extensibility/internals/nesting-projects.md)
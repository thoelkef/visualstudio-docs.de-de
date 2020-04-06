---
title: Überlegungen zum Entladen und Nachladen verschachtelter Projekte | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2ab705953eea1fcac99883bb4f88c0e95eced108
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709290"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>Überlegungen zum Entladen und Nachladen verschachtelter Projekte

Wenn Sie verschachtelte Projekttypen implementieren, müssen Sie beim Entladen und Erneutladen der Projekte zusätzliche Schritte ausführen. Um Listener korrekt an Lösungsereignissen zu `OnBeforeUnloadProject` benachrichtigen, müssen Sie die und die Ereignisse `OnAfterLoadProject` korrekt anheben.

Ein Grund, diese Ereignisse zu erhöhen, ist die Quellcodeverwaltung (Source Code Control, SCC). Sie möchten nicht, dass SCC die Elemente vom Server *new* löscht und sie `Get` dann als neu hinzufügt, wenn es einen Vorgang von SCC gibt. In diesem Fall würde eine neue Datei aus SCC geladen werden. Sie müssten alle Dateien entladen und neu laden, falls sie unterschiedlich sind.

Quellcodeverwaltungsaufrufe `ReloadItem`. Implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> Sie die `OnBeforeUnloadProject` `OnAfterLoadProject` Schnittstelle, um das Projekt aufzurufen und zu löschen und neu zu erstellen. Wenn Sie die Schnittstelle auf diese Weise implementieren, wird SCC darüber informiert, dass das Projekt vorübergehend gelöscht und erneut hinzugefügt wurde. Daher arbeitet SCC nicht mit dem Projekt, als ob das Projekt *tatsächlich* gelöscht und neu hinzugefügt wurde.

## <a name="reload-projects"></a>Neuladen von Projekten

Um das erneute Laden verschachtelter <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> Projekte zu unterstützen, implementieren Sie die Methode. In der `ReloadItem`Implementierung von schließen Sie die verschachtelten Projekte und erstellen sie dann neu.

Wenn ein Projekt neu geladen wird, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> löst die IDE in der Regel die und-Ereignisse aus. Bei geschachtelten Projekten, die gelöscht und neu geladen werden, initiiert das übergeordnete Projekt jedoch den Prozess, nicht die IDE. Da das übergeordnete Projekt keine Lösungsereignisse auslöst und die IDE keine Informationen über die Initialisierung des Prozesses enthält, werden die Ereignisse nicht ausgelöst.

Um diesen Prozess zu verarbeiten, `QueryInterface` <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> ruft das übergeordnete Projekt die Schnittstelle auf. `IVsFireSolutionEvents`hat Funktionen, die die `OnBeforeUnloadProject` IDE anweisen, das Ereignis zum Entladen `OnAfterLoadProject` des verschachtelten Projekts zu erhöhen und dann das Ereignis zum erneuten Laden desselben Projekts zu erhöhen.

## <a name="see-also"></a>Weitere Informationen

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- [Nest-Projekte](../../extensibility/internals/nesting-projects.md)

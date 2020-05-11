---
title: Befehlsroutingalgorithmus | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing
ms.assetid: 998b616b-bd08-45cb-845f-808efb8c33bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af8d3e53e09214ce36a80ca18856085dfb2bb746
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709540"
---
# <a name="command-routing-algorithm"></a>Befehlsroutingalgorithmus
In Visual Studio werden Befehle von einer Reihe verschiedener Komponenten verarbeitet. Befehle werden vom innersten Kontext, der auf der aktuellen Auswahl basiert, an den äußersten Kontext (auch als globaler Kontext bezeichnet) weitergeleitet. Weitere Informationen finden Sie unter [Befehlsverfügbarkeit](../../extensibility/internals/command-availability.md).

## <a name="order-of-command-resolution"></a>Reihenfolge der Befehlsauflösung
 Befehle werden durch die folgenden Befehlsebenen übergeben:

1. Add-Ins: Die Umgebung bietet den Befehl zuerst allen vorhandenen Add-Ins an.

2. Prioritätsbefehle: Diese Befehle <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget>werden mithilfe von registriert. Sie werden für jeden Befehl in Visual Studio aufgerufen und in der Reihenfolge aufgerufen, in der sie registriert wurden.

3. Kontextmenübefehle: Ein Befehl in einem Kontextmenü wird zuerst dem Befehlsziel angeboten, das dem Kontextmenü zur Verfügung gestellt wird, und danach dem typischen Routing.

4. Toolbar -Befehlsziele festlegen: Diese Befehlsziele werden beim Aufrufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A>von registriert. Der `pCmdTarget` Parameter `null`kann . Wenn dies `null`nicht der Fall ist, wird dieses Befehlsziel verwendet, um alle Befehle auf der Symbolleiste zu aktualisieren, die Sie einrichten. Wenn die Shell die Symbolleiste einrichtet, übergibt `pCmdTarget` sie den Fensterrahmen als den, sodass alle Aktualisierungen der Befehle auf der Symbolleiste durch den Fensterrahmen fließen, auch wenn er nicht im Fokus ist.

5. Toolfenster: Toolfenster, die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> in der Regel <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> die Schnittstelle implementieren, sollten auch die Schnittstelle implementieren, damit Visual Studio das Befehlsziel abrufen kann, wenn das Toolfenster das aktive Fenster ist. Wenn das Toolfenster mit Fokus jedoch das **Projektfenster** ist, wird <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> der Befehl an die Schnittstelle weitergeleitet, die das gemeinsame übergeordnete Element der ausgewählten Elemente ist. Wenn sich diese Auswahl über mehrere Projekte erstreckt, wird der Befehl an die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> Hierarchie weitergeleitet. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Schnittstelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> enthält <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> die und Methoden, die analog <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> zu den entsprechenden Befehlen auf der Schnittstelle sind.

6. Dokumentfenster: Wenn für `RouteToDocs` den Befehl das Flag in der *.vsct-Datei* festgelegt ist, sucht Visual Studio <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> nach einem Befehlsziel für das <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> Dokumentansichtsobjekt, das entweder eine Instanz einer Schnittstelle oder eine Instanz eines Dokumentobjekts (in der Regel eine Schnittstelle oder eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> Schnittstelle) ist. Wenn das Dokumentansichtsobjekt den Befehl nicht unterstützt, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> leitet Visual Studio den Befehl an die zurückgegebene Schnittstelle weiter. (Dies ist eine optionale Schnittstelle für Dokumentdatenobjekte.)

7. Aktuelle Hierarchie: Die aktuelle Hierarchie kann das Projekt sein, das das aktive Dokumentfenster besitzt, oder die Hierarchie, die im **Projektmappen-Explorer**ausgewählt ist. Visual Studio sucht <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> nach der Schnittstelle, die in der aktuellen oder aktiven Hierarchie implementiert ist. Die Hierarchie sollte Befehle unterstützen, die gültig sind, wenn die Hierarchie aktiv ist, auch wenn ein Dokumentfenster eines Projektelements den Fokus hat. Befehle, die nur gelten, wenn **der Projektmappen-Explorer** den Fokus hat, müssen jedoch mithilfe der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Schnittstelle und ihrer <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> Methoden unterstützt werden.

     **Ausschneiden**, **Kopieren**, **Einfügen**, **Löschen**, **Umbenennen**, **Enter**und **DoubleClick** Befehle erfordern eine spezielle Handhabung. Informationen zum **Behandeln** von Befehlen löschen und **Entfernen** in Hierarchien finden Sie in der <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler> Schnittstelle.

8. Global: Wenn ein Befehl nicht von den zuvor genannten Kontexten verarbeitet wurde, versucht Visual Studio, ihn <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> an das VSPackage weiterzuleiten, das einen Befehl besitzt, der die Schnittstelle implementiert. Wenn das VSPackage noch nicht geladen wurde, wird es <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> nicht geladen, wenn Visual Studio die Methode aufruft. Das VSPackage wird nur <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> geladen, wenn die Methode aufgerufen wird.

## <a name="see-also"></a>Weitere Informationen
- [Befehlsentwurf](../../extensibility/internals/command-design.md)

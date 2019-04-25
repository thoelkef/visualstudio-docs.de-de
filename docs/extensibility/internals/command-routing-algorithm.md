---
title: Befehl Routingalgorithmus | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing
ms.assetid: 998b616b-bd08-45cb-845f-808efb8c33bc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 591a5bdbeaa8724eb51d5755066b382c08740bf9
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60102944"
---
# <a name="command-routing-algorithm"></a>Algorithmus für das Befehlsrouting
In Visual Studio werden die Befehle durch eine Reihe von verschiedenen Komponenten behandelt. Befehle werden aus dem innersten Kontext, die für die aktuelle Auswahl basiert, an der äußerste Kontext angegeben (auch bekannt als "global") weitergeleitet. Weitere Informationen finden Sie unter [Befehl Verfügbarkeit](../../extensibility/internals/command-availability.md).

## <a name="order-of-command-resolution"></a>Reihenfolge der Auflösung des Befehls
 Befehle werden durch die folgenden Ebenen der Befehlskontext übergeben:

1. -Add-ins: Die Umgebung bietet zuerst den Befehl zum alle-add-ins, die vorhanden sind.

2. Priorität-Befehle: Diese Befehle werden registriert, indem Sie mithilfe von <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget>. Sie werden für jeden Befehl in Visual Studio aufgerufen, und Sie werden aufgerufen, in der Reihenfolge, in der sie registriert wurden.

3. Kontextmenübefehle: Ein Befehl befindet sich in einem Kontextmenü wird zuerst auf das Ziel des Befehls angeboten, die dem Kontextmenü Menüelemente hinzu, und klicken Sie anschließend in der typischen routing bereitgestellt wird.

4. Symbolleiste festlegen Befehlsziele: Dieser Befehlsziele registriert sind, beim Aufrufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A>. Die `pCmdTarget` -Parameters auch `null`. Ist dies nicht `null`, und klicken Sie dann das Ziel dieses Befehls verwendet wird, aktualisieren Sie alle Befehle, befindet sich auf der Symbolleiste, die Sie einrichten. Wenn die Shell ist eine Symbolleiste, und dann den Fensterrahmen als übergibt die `pCmdTarget` so, dass alle Updates auf die Befehle in der Flow Symbolleiste über dem Fensterrahmen, auch wenn es ist nicht im Fokus.

5. Toolfenster: Toolfenster, die in der Regel implementieren die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> Schnittstelle, sollten auch implementieren die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle, damit Visual Studio das Ziel des Befehls abrufen können, wenn das Toolfenster das aktive Fenster ist. Wenn jedoch im Toolfenster, das hat den Fokus ist die **Projekt** Fenster, und klicken Sie dann auf den Befehl geleitet wird die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Schnittstelle, die das gemeinsame übergeordnete Element der ausgewählten Elemente ist. Diese Auswahl umfasst die mehrere Projekte, wird der Befehl weitergeleitet, auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> Hierarchie. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Schnittstelle enthält die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> Methoden, die analog zu der entsprechenden Befehle auf den <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle.

6. Dokumentfenster: Wenn der Befehl hat die `RouteToDocs` Flag festgelegt wird, die *VSCT* -Datei, Visual Studio sucht ein Befehlsziel für das dokumentenansichtsobjekt, der entweder eine Instanz von einer <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> -Schnittstelle oder eine Instanz eines Dokuments-Objekts ( in der Regel eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> Schnittstelle oder ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> Schnittstelle). Wenn das dokumentenansichtsobjekt den Befehl nicht unterstützt, leitet Visual Studio den Befehl aus, um die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> -Schnittstelle, die zurückgegeben wird. (Dies ist eine optionale Schnittstelle für dokumentdatenobjekten.)

7. Aktuelle Hierarchie: Die aktuelle Hierarchie kann das Projekt, das der Besitzer ist das aktive Fenster oder der Hierarchie, die ausgewählt wird sein **Projektmappen-Explorer**. Visual Studio sucht nach dem <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> -Schnittstelle, die für die aktuelle oder aktive-Hierarchie implementiert wird. Befehle, die gültig sind, wenn die Hierarchie aktiv ist, auch wenn ein Dokumentfenster eines Projektelements den Fokus besitzt, sollte von der Hierarchie unterstützt werden. Jedoch Befehle, gelten nur, wenn **Projektmappen-Explorer** hat den Fokus muss unterstützt werden, mithilfe der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Schnittstelle und die zugehörige <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> Methoden.

     **Ausschneiden**, **Kopie**, **einfügen**, **löschen**, **umbenennen**, **geben**, und **DoubleClick** Befehle erfordern eine besondere Behandlung. Informationen zum Umgang mit **löschen** und **entfernen** Befehle in Hierarchien finden Sie unter den <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler> Schnittstelle.

8. Global: Wenn ein Befehl nicht von den zuvor erwähnten Kontexten behandelt wurde, versucht Visual Studio, um die Weiterleitung an das VSPackage, das einen Befehl besitzt, die implementiert die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle. Wenn das VSPackage nicht bereits geladen wurde, wird Sie nicht geladen, wenn Visual Studio ruft die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode. Das VSPackage geladen wird nur dann, wenn die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> Methode wird aufgerufen.

## <a name="see-also"></a>Siehe auch
- [Befehlsentwurf](../../extensibility/internals/command-design.md)
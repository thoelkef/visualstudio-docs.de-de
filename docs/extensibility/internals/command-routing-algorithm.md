---
title: Befehl Routingalgorithmus | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing
ms.assetid: 998b616b-bd08-45cb-845f-808efb8c33bc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: aba7ddcdda4dd4eabbb9266e0fa89c916bb028f6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131493"
---
# <a name="command-routing-algorithm"></a>Befehl-Routing-Algorithmus
In Visual Studio werden die Befehle durch eine Reihe von anderen Komponenten verarbeitet. Befehle werden aus dem innersten Kontext, die auf die aktuelle Auswahl basiert, an der äußerste Kontext angegeben (auch bekannt als global) weitergeleitet. Weitere Informationen finden Sie unter [Verfügbarkeit](../../extensibility/internals/command-availability.md).  
  
## <a name="order-of-command-resolution"></a>Auflösungsreihenfolge von Befehl  
 Befehle werden über die folgenden Ebenen Befehlskontext übergeben:  
  
1.  -Add-ins: Die Umgebung bietet zuerst den Befehl aus, um alle Add-Ins, die vorhanden sind.  
  
2.  Priorität-Befehle: mit diesen Befehlen werden mit registriert <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget>. Sie werden für jeden der Befehle in Visual Studio aufgerufen und aufgerufen werden, in der Reihenfolge, in der sie registriert wurden.  
  
3.  Kontextmenübefehle: ein Befehl befindet sich auf ein Kontextmenü wird zuerst bereitgestellt, um das Befehlsziel, die dem Kontextmenü Menüelemente hinzu, und klicken Sie danach auf die typischen routing bereitgestellt wird.  
  
4.  Symbolleiste festlegen Befehlsziele: Diese Befehlsziele registriert sind, beim Aufrufen von <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A>. Die `pCmdTarget` Parameter möglich `null`. Ist er nicht `null`, und klicken Sie dann diese Befehlsziel verwendet wird, aktualisieren Sie alle Befehle befindet sich auf der Symbolleiste, die Sie einrichten. Wenn die Shell ist das Einrichten der Symbolleiste angezeigt wird, übergibt des Fensterrahmens als die `pCmdTarget` , damit alle Updates auf die Befehle auf der Symbolleiste des Datenflusses dem Fensterrahmen, selbst wenn es ist nicht im Fokus.  
  
5.  Toolfenster: Toolfenster, die in der Regel implementieren die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> -Schnittstelle, die auch implementieren, sollten die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle, damit Visual Studio das Befehlsziel abrufen können, wenn das Toolfenster das aktive Fenster ist. Wenn allerdings im Toolfenster befindet, die Fokus ist die **Projekt** Fenster, und klicken Sie dann auf den Befehl weitergeleitet wird, um die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Schnittstelle, die die gemeinsamen übergeordneten Element der ausgewählten Elemente ist. Wenn dieser Auswahl mehrere Projekte erstreckt, wird der Befehl weitergeleitet, um die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> Hierarchie. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Schnittstelle enthält die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> Methoden, die analog zu den entsprechenden Befehlen auf die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle.  
  
6.  Dokumentfenster: Wenn der Befehl das RouteToDocs-Kennzeichen, die in einer VSCT-Datei festgelegt ist, Visual Studio sucht nach ein Befehlsziel auf des dokumentansichtsobjekts, der entweder eine Instanz von einer <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> Schnittstelle oder eine Instanz ein Document-Objekt (i. d. r. eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>Schnittstelle oder eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> Schnittstelle). Wenn das Ansichtsobjekt Dokument den Befehl nicht unterstützt wird, leitet Visual Studio den Befehl aus, um die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> -Schnittstelle, die zurückgegeben wird. (Dies ist eine optionale Schnittstelle für Data-Dokumentobjekte.)  
  
7.  Aktuelle Hierarchie: die aktuelle Hierarchie kann das Projekt, das aktive Fenster oder der Hierarchie, die ausgewählt wurde der Besitzer ist **Projektmappen-Explorer**. Visual Studio sucht nach der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle, die für die aktuelle oder aktive-Hierarchie implementiert wird. Die Hierarchie muss es sich um Befehle unterstützen, die gültig sind, wenn die Hierarchie aktiv ist, auch wenn ein Dokumentfenster, der ein Projektelement den Fokus besitzt. Allerdings Befehle, gelten nur, wenn **Projektmappen-Explorer** hat Fokus unterstützt werden muss, mithilfe der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Schnittstelle und die zugehörige <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>Methoden.  
  
     **Ausschneiden**, **Kopie**, **einfügen**, **löschen**, **umbenennen**, **geben**, und **DoubleClick** Befehle erfordern eine besondere Behandlung. Informationen zum Umgang mit **löschen** und **entfernen** Befehle in Hierarchien finden Sie unter der <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler> Schnittstelle.  
  
8.  Global: Wenn ein Befehl nicht durch die oben erwähnten Kontexte verarbeitet wurde, Visual Studio versucht, Weiterleitung an das VSPackage, das einen Befehl besitzt, die implementiert die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle. Wenn das VSPackage nicht bereits geladen wurde, wird Sie nicht geladen, wenn Visual Studio aufgerufen werden, die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode. Das VSPackage erfolgt nur, wenn die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> -Methode aufgerufen wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Befehlsentwurf](../../extensibility/internals/command-design.md)
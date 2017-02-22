---
title: "Befehl-Routing-Algorithmus | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Befehle, routing"
  - "Befehlsrouting"
ms.assetid: 998b616b-bd08-45cb-845f-808efb8c33bc
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# Befehl-Routing-Algorithmus
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

In Visual Studio werden die Befehle von einer Reihe von verschiedenen Komponenten behandelt. Befehle werden aus dem innersten Kontext, die auf die aktuelle Auswahl basiert, an der äußerste Kontext angegeben \(auch bekannt als global\) weitergeleitet. Weitere Informationen finden Sie unter [Verfügbarkeit](../../extensibility/internals/command-availability.md).  
  
## Reihenfolge der Befehl Auflösung  
 Befehle werden durch die folgenden Ebenen der Befehlskontext übergeben:  
  
1.  \-Add\-ins: Die Umgebung bietet zuerst den Befehl, um alle Add\-Ins, die vorhanden sind.  
  
2.  Priorität Befehle: Diese Befehle sind mit registriert <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget>. Sie werden für jeden Befehl in Visual Studio aufgerufen und heißen in der Reihenfolge, in der sie registriert wurden.  
  
3.  Kontextmenübefehle: ein Befehl im Kontextmenü wird zunächst bereitgestellt, um das Ziel des Befehls, um das Kontextmenü, und klicken Sie danach die typische routing bereitgestellt wird.  
  
4.  Symbolleiste Befehlsziele festgelegt: Diese Befehlsziele registriert sind, beim Aufruf von <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A>. Die `pCmdTarget` Parameter `null`. Ist dies nicht `null`, und klicken Sie dann diese Befehlsziel verwendet wird, aktualisieren Sie alle Befehle befindet sich auf der Symbolleiste, die Sie einrichten. Wenn die Shell ist das Einrichten der Symbolleiste, übergibt des Fensterrahmens als die `pCmdTarget` damit auch alle Updates mit den Befehlen auf der Symbolleiste des Datenflusses Fensterrahmen, wird er nicht den Fokus.  
  
5.  Toolfenster: Toolfenster, die in der Regel Implementieren der <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> Benutzeroberfläche, muss ebenfalls implementiert die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> \-Schnittstelle, damit Visual Studio das Ziel des Befehls abrufen können, wenn das Toolfenster das aktive Fenster ist. Das Toolfenster, bei dem Fokus ist jedoch die **Projekt** Fenster, und klicken Sie dann auf den Befehl weitergeleitet wird, um die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Schnittstelle, die die gemeinsamen übergeordneten Element der ausgewählten Elemente ist. Diese Auswahl mehrerer Projekte umfasst, wird der Befehl weitergeleitet, auf der <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> Hierarchie. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Schnittstelle enthält die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> Methoden, die für die entsprechenden Befehle auf analoge sind die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle.  
  
6.  Dokumentfenster: Wenn der Befehl das RouteToDocs\-Flag in der VSCT\-Datei festgelegt wurde, Visual Studio sucht nach als Befehlsziel auf das Document\-Objekt anzeigen, der entweder eine Instanz von einer <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> Schnittstelle oder eine Instanz von ein Document\-Objekt \(i. d. r. eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> Schnittstelle oder eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> Schnittstelle\). Wenn das Ansichtsobjekt Dokument mit dem Befehl nicht unterstützt, leitet Visual Studio den Befehl aus, um die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> \-Schnittstelle, die zurückgegeben wird. \(Dies ist eine optionale Schnittstelle für Datenobjekte Dokument.\)  
  
7.  Aktuelle Hierarchie: die aktuelle Hierarchie kann das Projekt, das Besitzer das aktive Fenster bzw. der Hierarchie, die ausgewählt wird **Projektmappen\-Explorer**. Visual Studio sucht die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> \-Schnittstelle, die für die aktuelle oder aktive Hierarchie implementiert wird. Die Hierarchie sollte Befehle unterstützen, die gültig sind, wenn die Hierarchie aktiv ist, selbst wenn ein Dokumentfenster eines Projektelements den Fokus besitzt. Allerdings Befehle, gelten nur, wenn **Projektmappen\-Explorer** hat Fokus muss unterstützt werden, mithilfe der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Schnittstelle und deren <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>Methoden.  
  
     **Ausschneiden**, **Kopie**, **Einfügen**, **Löschen**, **Umbenennen**, **EINGABETASTE**, und **DoubleClick** Befehle erfordern eine besondere Behandlung. Weitere Informationen zum Behandeln von **Löschen** und **Entfernen** Befehle in Hierarchien finden Sie unter der <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler> Schnittstelle.  
  
8.  Global: Wenn ein Befehl nicht von den zuvor erwähnten Kontexten behandelt wurde, Visual Studio versucht zum Weiterleiten an das VSPackage mit einem Befehl, in denen implementiert die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle. Wenn das VSPackage nicht bereits geladen wurde, wird Sie nicht geladen, wenn Visual Studio aufgerufen werden, die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode. Das VSPackage erfolgt nur, wenn die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> Methode wird aufgerufen.  
  
## Siehe auch  
 [Befehl Design](../../extensibility/internals/command-design.md)
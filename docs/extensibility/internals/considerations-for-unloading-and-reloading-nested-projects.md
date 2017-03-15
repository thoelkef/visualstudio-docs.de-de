---
title: "Hinweise f&#252;r entfernen und erneutes Laden geschachtelten Projekte | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "geschachtelte Projekte entladen und neu laden"
  - "Projekte [Visual Studio SDK], geschachtelt, entladen und neu laden"
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Hinweise f&#252;r entfernen und erneutes Laden geschachtelten Projekte
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Bei geschachtelten Projekttypen implementieren, müssen Sie zusätzliche Schritte ausführen, wenn Sie die Projekte entladen und erneut geladen werden.  Um Projektmappen Listener Ereignisse korrekt zu benachrichtigen, müssen Sie die `OnBeforeUnloadProject` und `OnAfterLoadProject` ordnungsgemäß Ereignisse auslösen.  
  
 Ein Grund, den Sie diese Ereignisse auslösen müssen auf diese Weise, dass Sie Quellcodeverwaltung \(SCC\) die Elemente aus den Server nicht löschen und anschließend wieder hinzufügen möchten, ein neues als bei einem `Get` Ausführung von SCC vorhanden ist.  In diesem Fall würde eine neue Datei aus SCC out geladen, und Sie müssen alle Dateien entladen und neu laden, falls sie ungleich sind.  SCC ruft `ReloadItem`an.  Die Implementierung dieses Aufrufs wird das Projekt erneut zu löschen und neu zu erstellen, indem `IVsFireSolutionEvents` implementiert, um `OnBeforeUnloadProject` und `OnAfterLoadProject`aufzurufen.  Wenn Sie diese Implementierung ausführen, ist das SCC informiert, dass das Projekt vorübergehend gelöscht und erneut hinzugefügt wurde.  Daher können die SCC nicht mit dem Projekt ausführen, als ob das Projekt tatsächlich vom Server gelöscht wurde und erneut hinzugefügt.  
  
## Projekte erneut geladen werden  
 Um das erneute Laden von geschachtelten Projekte zu unterstützen, implementieren Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A>\-Methode.  In der Implementierung von `ReloadItem`, schließen Sie die geschachtelten Projekte erstellen und sie anschließend neu.  
  
 In der Regel wird ausgelöst, wenn ein Projekt erneut geladen wird, löst die IDE das <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> und die `M:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject(Microsoft.VisualStudio.Shell.Interop.IVsHierarchy,Microsoft.VisualStudio.Shell.Interop.IVsHierarchy)` von Ereignissen aus.  Für geschachtelte Projekte, die gelöscht und erneut geladen werden, den Prozess initiiert das übergeordnete Projekt, nicht die IDE.  Da das übergeordnete Projekt nicht Ereignisse auslöst und Projektmappen der IDE keine Informationen über die Initialisierung des Prozesses verfügt, werden die Ereignisse nicht ausgelöst.  
  
 Um diesen Prozess zu behandeln, ruft das übergeordnete Projekt `QueryInterface` auf der <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents>\-Schnittstelle aus der <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution>\-Schnittstelle an.  `IVsFireSolutionEvents` verfügt über Funktionen, die von der IDE anweisen, das `OnBeforeUnloadProject`\-Ereignis auszulösen, um das geschachtelte Projekt zu entladen, und anschließend wird das `OnAfterLoadProject`\-Ereignis aus, um das gleiche Projekt erneut zu laden.  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 [Die Schachtelung von Projekten](../../extensibility/internals/nesting-projects.md)
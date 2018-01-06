---
title: "Überlegungen für das entladen und erneutes Laden geschachtelt Projekte | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fd45ebf8be2732cded5c84f18338f104b76840cf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>Überlegungen zum Entladen und erneutes Laden geschachtelten Projekte
Wenn Sie geschachtelte Projekttypen implementieren, müssen Sie zusätzliche Schritte ausführen, wenn entladen und laden die Projekte. Sie müssen ordnungsgemäß auslösen, um Listener zur Lösung Ereignisse korrekt zu benachrichtigen, die `OnBeforeUnloadProject` und `OnAfterLoadProject` Ereignisse.  
  
 Ein Grund, Sie müssen diese Ereignisse auf diese Weise ausgelöst wird, dass Quellcodeverwaltungssystem (SCC unerwünschte), löschen die Elemente auf dem Server und dann wieder als ein neues Element hinzufügen, ist es eine `Get` Vorgang aus der Quellcodeverwaltung. In diesem Fall wird eine neue Datei außerhalb des gültigen SCC geladen werden, und Sie entladen und laden alle Dateien aus, für den Fall, dass sie sich unterscheiden müssen. SCC Aufrufe `ReloadItem`. Die Implementierung dieses Aufrufs ist, löschen Sie das Projekt und erneut erstellen Sie es erneut durch die Implementierung `IVsFireSolutionEvents` Aufrufen `OnBeforeUnloadProject` und `OnAfterLoadProject`. Beim Ausführen dieser Implementierung ist SCC informiert, dass das Projekt wurde vorübergehend gelöscht und erneut hinzugefügt. Aus diesem Grund kann SCC nicht auf das Projekt ausgeführt werden, als ob das Projekt tatsächlich vom Server gelöscht, und klicken Sie dann erneut hinzugefügt wurde.  
  
## <a name="reloading-projects"></a>Erneutes Laden von Projekten  
 Zum erneuten Laden des geschachtelten Projekte zu unterstützen, implementieren Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> Methode. In der Implementierung von `ReloadItem`, die geschachtelte Projekte schließen und dann neu erstellen.  
  
 In der Regel, wenn ein Projekt geladen wird, die IDE löst die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> und `M:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject(Microsoft.VisualStudio.Shell.Interop.IVsHierarchy,Microsoft.VisualStudio.Shell.Interop.IVsHierarchy)` Ereignisse. Allerdings startet übergeordneten Projekts für geschachtelte Projekte, die gelöscht und erneut geladen werden, der werden nicht in der IDE an. Da übergeordneten Projekts keine Projektmappenereignisse löst und die IDE keine Informationen zur Initialisierung des Prozesses hat, werden Ereignisse nicht ausgelöst.  
  
 Behandeln Sie dabei, die Aufrufe der übergeordneten Projekt `QueryInterface` auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> Schnittstelle deaktiviert die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> Schnittstelle. `IVsFireSolutionEvents`verfügt über Funktionen, die von der IDE zum Auslösen von Teilen der `OnBeforeUnloadProject` Ereignis, um das Entladen des geschachtelten Projekts, und erhöhen Sie dann die `OnAfterLoadProject` Ereignis, um das gleiche Projekt erneut laden.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 [Schachteln von Projekten](../../extensibility/internals/nesting-projects.md)
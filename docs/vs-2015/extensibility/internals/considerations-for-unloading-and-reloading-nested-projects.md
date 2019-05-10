---
title: Überlegungen zum Entladen und Neuladen von geschachtelten Projekten | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 65145530c8cd6b68b82391a09b395bb8c9a61117
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58961928"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>Überlegungen für das Entladen und Neuladen von geschachtelten Projekten
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wenn Sie geschachtelte Projekttypen implementieren, müssen Sie zusätzliche Schritte ausführen, wenn Sie entladen und Laden Sie die Projekte erneut. Sie müssen ordnungsgemäß auslösen, um Listener zu Projektmappenereignissen ordnungsgemäß zu benachrichtigen, die `OnBeforeUnloadProject` und `OnAfterLoadProject` Ereignisse.  
  
 Ein Grund, Sie müssen diese Ereignisse auf diese Weise ausgelöst wird, dass Sie die quellcodeverwaltung (SCC), löschen die Elemente auf dem Server, und klicken Sie dann als ein neues Element hinzufügen, wenn Sie vorhanden ist, nicht wünschen eine `Get` Vorgang aus SCC. In diesem Fall wird eine neue Datei aus SCC geladen werden, und Sie entladen und laden alle Dateien aus, für den Fall, dass sich die Werte unterscheiden müssen. SCC-Aufrufe `ReloadItem`. Die Implementierung von diesem Aufruf wird auf das Projekt zu löschen und erneut durch die Implementierung neu erstellen `IVsFireSolutionEvents` aufzurufende `OnBeforeUnloadProject` und `OnAfterLoadProject`. Beim Ausführen dieser Implementierung wird die SCC darüber informiert, dass das Projekt wurde vorübergehend gelöscht und erneut hinzugefügt. Aus diesem Grund kann die SCC nicht auf das Projekt ausgeführt werden, als ob das Projekt tatsächlich vom Server gelöscht wurde, und klicken Sie dann erneut hinzugefügt werden.  
  
## <a name="reloading-projects"></a>Erneutes Laden von Projekten  
 Um das erneute Laden von geschachtelten Projekten unterstützen, implementieren Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> Methode. In der Implementierung von `ReloadItem`, Sie schließen die geschachtelte Projekte, und dann neu erstellen.  
  
 In der Regel ein Projekt erneut geladen wird, die IDE löst, wenn die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> und `M:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject(Microsoft.VisualStudio.Shell.Interop.IVsHierarchy,Microsoft.VisualStudio.Shell.Interop.IVsHierarchy)` Ereignisse. Für geschachtelte Projekte, die gelöscht und neu geladen werden, initiiert das übergeordnete Projekt jedoch den Prozess, der nicht in der IDE. Da das übergeordnete Projekt keine Projektmappenereignisse löst, und die IDE verfügt über keine Informationen zur Initialisierung des Prozesses, werden die Ereignisse nicht ausgelöst.  
  
 Dieser Prozess, die Aufrufe der übergeordneten Projekt zu behandeln `QueryInterface` auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> Schnittstelle aus der <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> Schnittstelle. `IVsFireSolutionEvents` verfügt über Funktionen, die die IDE zum Auslösen von Teilen der `OnBeforeUnloadProject` Ereignis, das geschachtelte Projekt entladen, und erhöhen Sie dann die `OnAfterLoadProject` Ereignis, um das gleiche Projekt erneut laden.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 [Schachteln von Projekten](../../extensibility/internals/nesting-projects.md)

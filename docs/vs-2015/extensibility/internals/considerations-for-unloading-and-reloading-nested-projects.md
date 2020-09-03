---
title: Überlegungen zum Entladen und erneuten Laden von in einem Projekt Vorgängen | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197011"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>Überlegungen für das Entladen und Neuladen von geschachtelten Projekten
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Beim Implementieren von Typen mit einem anderen Typ müssen Sie beim Entladen und erneuten Laden der Projekte zusätzliche Schritte ausführen. Damit Listener korrekt an projektmappenereignisse benachrichtigt werden, müssen Sie die Ereignisse und ordnungsgemäß ausgeben `OnBeforeUnloadProject` `OnAfterLoadProject` .  
  
 Ein Grund, warum Sie diese Ereignisse auf diese Weise erhöhen müssen, besteht darin, dass Sie nicht möchten, dass die Quell Code Verwaltung (SCC) die Elemente vom Server löscht und Sie dann wieder als etwas neues hinzufügt, wenn ein- `Get` Vorgang von SCC vorliegt. In diesem Fall wird eine neue Datei aus SCC geladen, und Sie müssen alle Dateien entladen und erneut laden, falls Sie sich unterscheiden. SCC-Aufrufe `ReloadItem` . Die Implementierung dieses Aufrufens besteht darin, das Projekt zu löschen und neu zu erstellen, indem Sie implementieren `IVsFireSolutionEvents` , um und aufzurufen `OnBeforeUnloadProject` `OnAfterLoadProject` . Wenn Sie diese Implementierung durchführen, wird der SCC informiert, dass das Projekt vorübergehend gelöscht und erneut hinzugefügt wurde. Daher funktioniert SCC nicht mit dem Projekt, als ob das Projekt tatsächlich vom Server gelöscht und dann erneut hinzugefügt wurde.  
  
## <a name="reloading-projects"></a>Erneutes Laden von Projekten  
 Um das erneute Laden von in-Projekten zu unterstützen, implementieren Sie die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> Methode. In ihrer Implementierung von `ReloadItem` Schließen Sie die in der Liste der Projekte, und erstellen Sie Sie neu.  
  
 In der Regel löst die IDE das <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> -Ereignis und das-Ereignis aus, wenn ein Projekt erneut geladen wird `M:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject(Microsoft.VisualStudio.Shell.Interop.IVsHierarchy,Microsoft.VisualStudio.Shell.Interop.IVsHierarchy)` . Bei der Löschung und erneuten Laden von zu erstellenden und erneuten geladenen Projekten initiiert das übergeordnete Projekt jedoch den Prozess und nicht die IDE. Da das übergeordnete Projekt keine projektmappenereignisse aufhebt und die IDE keine Informationen über die Initialisierung des Prozesses hat, werden die Ereignisse nicht ausgelöst.  
  
 Um diesen Prozess zu verarbeiten, ruft das übergeordnete Projekt die `QueryInterface` <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> Schnittstelle aus der <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> Schnittstelle auf. `IVsFireSolutionEvents` verfügt über Funktionen, die die IDE anweisen, das- `OnBeforeUnloadProject` Ereignis zum Entladen des-Projekts aufzurichten, und dann das- `OnAfterLoadProject` Ereignis zum erneuten Laden desselben Projekts aufzurichten.  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 [Schachteln von Projekten](../../extensibility/internals/nesting-projects.md)

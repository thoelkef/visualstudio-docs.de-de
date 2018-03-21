---
title: Verwalten von Projekt laden in einer Projektmappe | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 2dbbb8ddcf574f2e3db81ce63db257e21ff88839
ms.sourcegitcommit: a80e7ef2f0a0f6d906a44f4d696aeb208bc1ad70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2018
---
# <a name="managing-project-loading-in-a-solution"></a>Verwalten von Projekt laden in einer Projektmappe
Visual Studio-Projektmappen können eine große Anzahl von Projekten enthalten. Das Standardverhalten für Visual Studio wird beim Laden aller Projekte in einer Projektmappe zum Zeitpunkt der Projektmappe geöffnet ist und nicht auf ermöglicht dem Benutzer die Projekte zugreifen, bis alle von ihnen geladen wurden. Wenn die während des Ladevorgangs Projekt mehr als zwei Minuten dauert, wird eine Statusanzeige angezeigt, die Anzahl der geladenen Projekte und die Gesamtzahl der Projekte. Der Benutzer kann Projekte entladen, während in einer Projektmappe mit mehreren Projekten arbeiten, aber diese Prozedur umfasst einige Nachteile: die entladen Projekte werden nicht als Teil eines Befehls für die Projektmappe neu erstellen erstellt, und IntelliSense Beschreibungen von Typen und Member von "geschlossen" Projekte werden nicht angezeigt.  
  
 Entwickler können Lösung Ladezeiten reduzieren und Projekt loading-Verhaltens durch das Erstellen einer Lösung Last Manager verwalten. Die Lösung des Managers kann stellen Sie sicher, dass Projekte vor dem Starten eines Builds im Hintergrund geladen werden, verzögert, im Hintergrund geladen, bis andere Vorgänge im Hintergrund abgeschlossen sind, und andere Verwaltungsaufgaben Projekt laden.  
  
## <a name="creating-a-solution-load-manager"></a>Erstellen einer Lösung Last-Managers  
 Entwickler eine Lösung Last-Manager erstellen können durch die Implementierung <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> und der Beratung von Visual Studio der Projektmappe Load-Manager aktiv ist.  
  
#### <a name="activating-a-solution-load-manager"></a>Einen Lösung Load-Manager aktivieren  
 Visual Studio bietet nur eine Projektmappe des Managers zu einem bestimmten Zeitpunkt auf, sodass Sie Visual Studio informieren müssen, wenn Sie Ihre Projektmappe Last aktivieren möchten Manager. Wenn später auf ein zweite Lösung Load-Manager aktiviert ist, wird Ihre Lösung Load-Manager getrennt.  
  
 Benötigen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> service, und legen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> Eigenschaft:  
  
```csharp  
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;  
object objLoadMgr = this;   //the class that implements IVsSolutionManager  
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);  
```  
  
 Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> Methode wird aufgerufen, wenn Visual Studio geschlossen wird oder ein anderes Paket von Aufrufen als die aktive Projektmappe des Managers übernommen wurde <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> mit der <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> Eigenschaft.  
  
#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Strategien für verschiedene Arten von Projektmappen Load-manager  
 Unterschiedlich, abhängig von den Arten von Projektmappen, die sie zum Verwalten von vorgesehen sind, können Sie Projektmappen Load-Manager implementieren.  
  
 Wenn der Projektmappen-Load-Manager zum Verwalten von Projektmappen, die in der Regel laden gedacht ist, kann es als Teil eines VSPackage implementiert werden. Das Paket sollte auf Autoload festgelegt werden, durch Hinzufügen der <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> für das VSPackage, mit dem Wert <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>. Die Lösung des Managers kann dann in aktiviert werden die <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> Methode.  
  
> [!NOTE]
>  Weitere Informationen zu Automatisches Laden von Paketen finden Sie unter [Laden von VSPackages](../extensibility/loading-vspackages.md).  
  
 Da Visual Studio nur den letzten Projektmappe laden Manager aktiviert werden, erkennt, sollte die allgemeine Lösung Load-Manager immer erkennen, ob es ein vorhandenen Load-Manager vor dem Aktivieren selbst ist. GetProperty() im Projektmappen-Dienst für die beim Aufrufen <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> gibt `null`, es ist kein aktive Projektmappe Load-Manager. Wenn es nicht null zurückgibt, überprüfen Sie, ob das Objekt identisch mit der Lösung des Managers ist.  
  
 Wenn die Lösung des Managers nur einige Arten von Projektmappen verwaltet werden sollen, kann das VSPackage Lösung laden Ereignisse abonnieren (durch Aufrufen von <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>), und verwenden Sie den Ereignishandler für <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> So aktivieren Sie die Lösung des Managers.  
  
 Wenn die Lösung des Managers dafür vorgesehen ist, um nur bestimmte Lösungen zu verwalten, kann Aktivierungsinformationen im Rahmen der Projektmappendatei beibehalten werden, durch den Aufruf <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> für den Abschnitt vor der Lösung.  
  
 Spezifische Lösung Load-Manager sollten deaktivieren, selbst in den <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> -Ereignishandler in der Reihenfolge nicht mit anderen Lösung Load-Managern in Konflikt stehen.  
  
 Wenn Sie einen Projektmappe laden Manager benötigen, nur um globale laden Projekteigenschaften (z. B. Eigenschaften, die auf einer Seite "Optionen" festgelegt) beizubehalten, die Lösung des Managers in aktiviert werden kann die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> Ereignishandler, d. h. die Einstellung in den Projektmappeneigenschaften beibehalten Deaktivieren Sie die Lösung des Managers.  
  
## <a name="handling-solution-load-events"></a>Behandlung von Ereignissen für Projektmappe laden  
 Rufen Sie zum Abonnieren der Lösung ladeereignissen <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> bei Sie Ihrer Projektmappe Load-Manager aktivieren. Wenn Sie implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>, Sie können reagieren auf Ereignisse, die auf anderen Projekt laden Eigenschaften beziehen.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: Dieses Ereignis wird ausgelöst, bevor eine Projektmappe geöffnet ist.
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: Dieses Ereignis wird ausgelöst, nachdem die Projektmappe vollständig geladen ist, aber vor dem Hintergrund Projekt laden wird erneut gestartet.
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: Dieses Ereignis wird ausgelöst, nachdem eine Projektmappe anfänglich wurden vollständig geladen ist, und zwar unabhängig davon, ob ein Lösung Load-Manager vorhanden ist. Es wird auch ausgelöst, nachdem der Hintergrund laden oder bei Bedarf geladen werden, wenn die Projektmappe vollständig geladen wird. Zur gleichen Zeit <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> erneut aktiviert wird.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: Dieses Ereignis wird ausgelöst, bevor Sie das Laden eines Projekts (oder Projekten). Um sicherzustellen, dass andere Hintergrundprozesse im abgeschlossen werden, bevor die Projekte geladen werden, legen Sie `pfShouldDelayLoadToNextIdle` auf **"true"**.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: Dieses Ereignis wird ausgelöst, wenn ein Batch von Projekten gerade geladen werden. Wenn `fIsBackgroundIdleBatch` ist "true", die Projekte sind im Hintergrund; geladen werden, wenn `fIsBackgroundIdleBatch` "false", die Projekte werden geladen synchron als Ergebnis einer Anforderung des Benutzers, z. B. wenn der Benutzer eine ausstehende Projekt im Projektmappen-Explorer erweitert wird. Sie können dieses Ereignis, um teure Arbeit zu erledigen, die andernfalls benötigen würden, erfolgen behandeln <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: Dieses Ereignis wird ausgelöst, nachdem ein Batch von Projekten geladen wurde.  
  
## <a name="detecting-and-managing-solution-and-project-loading"></a>Erkennen und Verwalten von Projektmappen und Projekt laden  
 Aufrufen, um den Status Laden von Projekten und Projektmappen zu erkennen, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> mit den folgenden Werten:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` gibt `true` , wenn die Projektmappe und alle darin enthaltenen Projekte geladen wurde, andernfalls werden `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` gibt `true` , wenn ein Batch von Projekten andernfalls derzeit im Hintergrund geladen wird `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` gibt `true` Wenn ein Batch von Projekten derzeit synchron als Ergebnis eines Befehls Benutzer oder andere explizite laden, andernfalls geladen wird `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>: `var` gibt `true` , wenn die Projektmappe aktuell, andernfalls geschlossen wird `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>: `var` gibt `true` Wenn Öffnen einer Projektmappe derzeit, andernfalls wird `false`.  
  
 Sie können auch sicherstellen, dass Projekte und Projektmappen geladen werden, durch den Aufruf einer der folgenden Methoden:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: das Aufrufen dieser Methode erzwingt, dass die Projekte in einer Projektmappe geladen, bevor die Methode zurückgegeben.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: das Aufrufen dieser Methode erzwingt, dass die Projekte in `guidProject` geladen, bevor die Methode zurückgegeben.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: das Aufrufen dieser Methode erzwingt, dass das Projekt im `guidProjectID` geladen, bevor die Methode zurückgegeben.  

---
title: Verwalten von Projekt laden in einer Projektmappe | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a2be2c75704646bab50f89377d960d44f6fa14f1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="managing-project-loading-in-a-solution"></a>Verwalten von Projekt laden in einer Projektmappe
Visual Studio-Projektmappen können eine große Anzahl von Projekten enthalten. Das Standardverhalten für Visual Studio wird beim Laden aller Projekte in einer Projektmappe zum Zeitpunkt der Projektmappe geöffnet ist und nicht auf ermöglicht dem Benutzer die Projekte zugreifen, bis alle von ihnen geladen wurden. Wenn die während des Ladevorgangs Projekt mehr als zwei Minuten dauert, wird eine Statusanzeige angezeigt, die Anzahl der geladenen Projekte und die Gesamtzahl der Projekte. Der Benutzer kann Projekte entladen, während in einer Projektmappe mit mehreren Projekten arbeiten, aber diese Prozedur umfasst einige Nachteile: die entladen Projekte werden nicht als Teil eines Befehls für die Projektmappe neu erstellen erstellt, und IntelliSense Beschreibungen von Typen und Member von "geschlossen" Projekte werden nicht angezeigt.  
  
 Entwickler können Lösung Ladezeiten reduzieren und Projekt loading-Verhaltens durch das Erstellen einer Lösung Last Manager verwalten. Die Lösung des Managers anderen Projekt laden Prioritäten für bestimmte Projekte oder Projekttypen festgelegt, stellen Sie sicher, dass Projekte vor dem Starten eines Builds im Hintergrund geladen werden, verzögert werden im Hintergrund geladen, bis andere Vorgänge im Hintergrund abgeschlossen sind und ausführen andere Verwaltungsaufgaben für den Projekt laden.  
  
## <a name="project-loading-priorities"></a>Projekt Laden von Prioritäten  
 Visual Studio definiert vier verschiedene laden Projektprioritäten:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>(Standard): Wenn eine Projektmappe geöffnet ist, werden Projekte asynchron geladen. Wenn die Priorität auf eine entladene Projekt festgelegt ist, nachdem die Projektmappe bereits geöffnet ist, wird das Projekt am nächsten Leerlauf geladen werden.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: Wenn eine Projektmappe geöffnet ist, werden Projekte im Hintergrund, sodass der Benutzer auf die Projekte zugreifen, da sie ohne zu warten, bis alle Projekte geladen werden erneut geladen werden geladen.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: Projekte werden geladen, wenn darauf zugegriffen wird. Ein Projekt erfolgt, wenn der Benutzer den Projektknoten im Projektmappen-Explorer erweitert wird, wenn eine Datei, die dem Projekt gehören geöffnet wird, wenn die Projektmappe geöffnet wird, weil es in der Liste der geöffneten Dokument (persistent in der Projektmappen-Benutzeroptionendatei) ist, oder wenn ein anderes Projekt d. h. setzt auf das Projekt geladen wird. Diese Art von Projekt wird nicht automatisch geladen, bevor ein Buildprozess gestartet; der Projektmappen-Load-Manager ist dafür verantwortlich, dass die notwendigen Projekte geladen werden. Diese Projekte sollte auch vor dem Starten einer Suchen/Ersetzen in Dateien in der gesamten Projektmappe geladen werden.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: Projekte werden nicht geladen, wenn der Benutzer explizit anfordert. Dies ist der Fall, wenn Sie Projekte explizit entladen werden.  
  
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
  
#### <a name="implementing-ivssolutionloadmanager"></a>Implementieren von IVsSolutionLoadManager  
 Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnBeforeOpenProject%2A> Methode wird aufgerufen, während der Prozess des Öffnens der Projektmappe. Um diese Methode implementieren, verwenden Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManagerSupport> Dienst für die Load-Priorität für den Typ des Projekts festgelegt. Sie verwalten möchten. Der folgende Code legt beispielsweise C#-Projekttypen im Hintergrund geladen:  
  
```csharp  
Guid guidCSProjectType = new Guid("{FAE04EC0-301F-11d3-BF4B-00C04F79EFBC}");  
pSLMgrSupport.SetProjectLoadPriority(guidProjectID, (uint)_VSProjectLoadPriority.PLP_BackgroundLoad);  
```  
  
 Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> Methode wird aufgerufen, wenn Visual Studio geschlossen wird oder ein anderes Paket von Aufrufen als die aktive Projektmappe des Managers übernommen wurde <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> mit der <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> Eigenschaft.  
  
#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Strategien für verschiedene Arten von Projektmappen Load-manager  
 Unterschiedlich, abhängig von den Arten von Projektmappen, die sie zum Verwalten von vorgesehen sind, können Sie Projektmappen Load-Manager implementieren.  
  
 Wenn der Projektmappen-Load-Manager zum Verwalten von Projektmappen, die in der Regel laden gedacht ist, kann es als Teil eines VSPackage implementiert werden. Das Paket sollte auf Autoload festgelegt werden, durch Hinzufügen der <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> für das VSPackage, mit dem Wert <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>. Die Lösung des Managers kann dann in aktiviert werden die <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> Methode.  
  
> [!NOTE]
>  Weitere Informationen zu Automatisches Laden von Paketen finden Sie unter [Laden von VSPackages](../extensibility/loading-vspackages.md).  
  
 Da Visual Studio nur den letzten Projektmappe laden Manager aktiviert werden, erkennt, sollte die allgemeine Lösung Load-Manager immer erkennen, ob es ein vorhandenen Load-Manager vor dem Aktivieren selbst ist. GetProperty() im Projektmappen-Dienst für die beim Aufrufen <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> gibt `null`, es ist kein aktive Projektmappe Load-Manager. Wenn es nicht null zurückgibt, überprüfen Sie, ob das Objekt identisch mit der Lösung des Managers ist.  
  
 Wenn die Lösung des Managers nur einige Arten von Projektmappen verwaltet werden sollen, kann das VSPackage Lösung laden Ereignisse abonnieren (durch Aufrufen von <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>), und verwenden Sie den Ereignishandler für <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> So aktivieren Sie die Lösung des Managers.  
  
 Wenn die Lösung des Managers dafür vorgesehen ist, um nur bestimmte Lösungen zu verwalten, kann die Aktivierungsinformationen im Rahmen der Projektmappendatei beibehalten werden. Zu diesem Zweck rufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> für den Abschnitt vor der Lösung.  
  
 Spezifische Lösung Load-Manager sollten deaktivieren, selbst in den <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> -Ereignishandler in der Reihenfolge nicht mit anderen Lösung Load-Managern in Konflikt stehen.  
  
 Wenn Sie einen Projektmappe laden Manager benötigen, nur um globale laden Projektprioritäten (z. B. Eigenschaften, die auf einer Seite "Optionen" festgelegt) beizubehalten, die Lösung des Managers in aktiviert werden kann die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> Ereignishandler, d. h. die Einstellung in den Projektmappeneigenschaften beibehalten Deaktivieren Sie die Lösung des Managers.  
  
## <a name="handling-solution-load-events"></a>Behandlung von Ereignissen für Projektmappe laden  
 Rufen Sie zum Abonnieren der Lösung ladeereignissen <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> bei Sie Ihrer Projektmappe Load-Manager aktivieren. Wenn Sie implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>, Sie können reagieren auf Ereignisse, die auf anderen Projekt laden Prioritäten beziehen.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: Wird ausgelöst, bevor eine Projektmappe geöffnet ist. Sie können es verwenden, um das Projekt, laden die Priorität für die Projekte in der Projektmappe zu ändern.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: Dieses Ereignis wird ausgelöst, nachdem die Projektmappe vollständig geladen, aber vor dem Hintergrund Projekt laden erneut beginnt. Z. B. ein Benutzer kann auf ein Projekt, dessen Priorität laden LoadIfNeeded ist, zugegriffen haben oder die Lösung des Managers möglicherweise eine Projekt laden Priorität zu BackgroundLoad, d. h. einen Hintergrund laden dieses Projekts starten würden geändert haben.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: Dieses Ereignis wird ausgelöst, nachdem eine Projektmappe anfänglich wurden vollständig geladen ist, und zwar unabhängig davon, ob ein Lösung Load-Manager vorhanden ist. Es wird auch ausgelöst, nachdem der Hintergrund laden oder bei Bedarf geladen werden, wenn die Projektmappe vollständig geladen wird. Zur gleichen Zeit <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> erneut aktiviert wird.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: Dies ist vor dem Laden eines Projekts (oder Projekte) ausgelöst. Um sicherzustellen, dass andere Hintergrundprozesse im abgeschlossen werden, bevor die Projekte geladen werden, legen Sie `pfShouldDelayLoadToNextIdle` auf **"true"**.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: Wird ausgelöst, wenn ein Batch von Projekten wird geladen werden soll. Wenn `fIsBackgroundIdleBatch` ist "true", die Projekte sind im Hintergrund; geladen werden, wenn `fIsBackgroundIdleBatch` "false", die Projekte werden geladen synchron als Ergebnis einer Anforderung des Benutzers, z. B. wenn der Benutzer eine ausstehende Projekt im Projektmappen-Explorer erweitert wird. Implementieren Sie diese Option, um teure Arbeit zu erledigen, die andernfalls benötigen würden, erfolgen <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: Dieses Ereignis wird ausgelöst, nachdem ein Batch von Projekten geladen wurde.  
  
## <a name="detecting-and-managing-solution-and-project-loading"></a>Erkennen und Verwalten von Projektmappen und Projekt laden  
 Aufrufen, um den Status Laden von Projekten und Projektmappen zu erkennen, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> mit den folgenden Werten:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` gibt `true` , wenn die Projektmappe und alle darin enthaltenen Projekte geladen wurde, andernfalls werden `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` gibt `true` , wenn ein Batch von Projekten werden gerade andernfalls im Hintergrund geladen `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` gibt `true` , wenn ein Batch von Projekten werden gerade geladen synchron als Ergebnis eines Befehls Benutzer oder andere explizite laden, andernfalls `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>: `var` gibt `true` , wenn die Projektmappe aktuell, andernfalls geschlossen wird `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>: `var` gibt `true` Wenn Öffnen einer Projektmappe derzeit, andernfalls wird `false`.  
  
 Sie können auch sicherstellen, dass Projekte und Projektmappen geladen werden (unabhängig davon, was die Auslastung Projektprioritäten sind) durch Aufrufen einer der folgenden Methoden:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: das Aufrufen dieser Methode erzwingt, dass die Projekte in einer Projektmappe geladen, bevor die Methode zurückgegeben.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: das Aufrufen dieser Methode erzwingt, dass die Projekte in `guidProject` geladen, bevor die Methode zurückgegeben.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: das Aufrufen dieser Methode erzwingt, dass das Projekt im `guidProjectID` geladen, bevor die Methode zurückgegeben.  
  
> [!NOTE]
>  sein. Standardmäßig nur die Projekte, die der Anforderung haben laden und Hintergrund laden Prioritäten werden geladen, aber wenn die <xref:Microsoft.VisualStudio.Shell.Interop.__VSBSLFLAGS> Flag wird an die Methode übergeben, werden alle Projekte außer diejenigen, die markiert sind, um explizit laden geladen.
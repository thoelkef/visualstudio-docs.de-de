---
title: "Verwalten von Projekt laden in einer Projektmappe | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Lösungen, Verwalten von Projekt laden"
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Verwalten von Projekt laden in einer Projektmappe
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio\-Projektmappen können es sich um eine große Anzahl von Projekten enthalten. Das Standardverhalten von Visual Studio wird auf alle Projekte in einer Projektmappe gleichzeitig zu laden, wenn die Projektmappe geöffnet wird und nicht auf dem Benutzer ermöglichen, die Projekte zugreifen können, bis alle abgeschlossen sind. Wenn der Prozess des Ladens Projekt mehr als zwei Minuten zuletzt wird, wird eine Statusanzeige angezeigt, die Anzahl der geladenen Projekte und die Gesamtzahl der Projekte. Der Benutzer kann Projekte entladen, während Sie in einer Projektmappe mit mehreren Projekten arbeiten, aber diese Prozedur umfasst einige Nachteile: entladen Projekte sind nicht als Teil eines Befehls für die Projektmappe neu erstellt, und IntelliSense\-Beschreibungen der Typen und Member der abgeschlossenen Projekten werden nicht angezeigt.  
  
 Entwickler können Ladezeiten Lösung verringern und Projekt Ladeverhaltens durch Erstellen einer Lösung Last Manager verwalten. Der Lösung Manager kann anderen Projekt laden Prioritäten für bestimmte Projekte oder Projekttypen festlegen, stellen Sie sicher, dass Projekte vor dem Erstellen eines Builds Hintergrund geladen werden, verzögert Hintergrund geladen, bis andere Tasks im Hintergrund abgeschlossen sind, und andere Projekt laden Verwaltungsaufgaben ausführen.  
  
## Projekt Laden von Prioritäten  
 Visual Studio definiert vier Prioritäten von anderen Projekt laden:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority> \(Standard\): Wenn eine Projektmappe geöffnet ist, werden Projekte asynchron geladen. Wenn dieser Priorität auf eine entladene Projekt festgelegt wird, nachdem die Projektmappe bereits geöffnet ist, wird das Projekt am nächsten im Leerlauf geladen werden.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: Wenn eine Projektmappe geöffnet wird, werden Projekte im Hintergrund, sodass der Benutzer auf die Projekte zugreifen, ohne zu warten, bis alle Projekte geladen werden geladen werden geladen.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: Projekte werden geladen, wenn darauf zugegriffen wird. Ein Projekt zugegriffen wird, wenn der Benutzer den Projektknoten im Projektmappen\-Explorer erweitert, wenn eine Datei, die für das Projekt geöffnet wird, wenn die Projektmappe geöffnet wird, da sie in der Liste der geöffneten Dokument \(persistent in der Projektmappe Benutzeroptionendatei\) ist, oder wenn ein anderes Projekt ist, die geladen wird eine Abhängigkeit auf das Projekt hat. Diese Art von Projekt wird nicht automatisch geladen, bevor ein Buildprozess gestartet; der Solution Manager ist dafür verantwortlich, dass alle notwendigen Projekte geladen werden. Diese Projekte sollten auch vor dem Starten einer suchen und Ersetzen in Dateien in der gesamten Projektmappe geladen werden.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: Projekte werden nicht geladen, wenn der Benutzer explizit anfordert. Dies ist der Fall, wenn Projekte explizit entladen werden.  
  
## Erstellen eine Lösung Last\-manager  
 Entwickler können ein Laden der Projektmappe Manager durch Implementieren von <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> und der Beratung von Visual Studio, dass der Lösung Manager aktiv ist.  
  
#### Einen Lösung Load\-Manager aktivieren  
 Visual Studio können nur eine Lösung des Managers zu einem Zeitpunkt auf, daher Sie Visual Studio mitteilen müssen, wenn Sie Ihre Projektmappe Last aktivieren möchten Manager. Wenn eine zweite Lösung des Managers später aktiviert ist, wird Ihre Lösung Load\-Manager getrennt.  
  
 Sie benötigen die <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> Dienst, und stellen die <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> Eigenschaft:  
  
```c#  
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution; object objLoadMgr = this;   //the class that implements IVsSolutionManager pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);  
```  
  
#### Implementieren von IVsSolutionLoadManager  
 Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnBeforeOpenProject%2A> Methode wird aufgerufen, bei der die Projektmappe öffnen. Um diese Methode zu implementieren, verwenden Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManagerSupport> Dienst zum Festlegen der Load\-Priorität für den Typ des Projekts, Sie verwalten möchten. Im folgende Code wird z. B. C\#\-Projekttypen im Hintergrund geladen:  
  
```c#  
Guid guidCSProjectType = new Guid("{FAE04EC0-301F-11d3-BF4B-00C04F79EFBC}"); pSLMgrSupport.SetProjectLoadPriority(guidProjectID, (uint)_VSProjectLoadPriority.PLP_BackgroundLoad);  
```  
  
 Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> Methode wird aufgerufen, wenn die Visual Studio heruntergefahren wird oder wenn ein anderes Paket durch Aufrufen von als der aktuellen Projektmappe Manager übernommen wurde <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> mit der <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> Eigenschaft.  
  
#### Strategien für verschiedene Arten von Projektmappen lädt\-manager  
 Unterschiedlich, abhängig von den Typen von Projektmappen, die sie zum Verwalten von vorgesehen sind, können Sie Projektmappen Load\-Manager implementieren.  
  
 Wenn der Manager Lösung zum Verwalten von Projektmappen, die in der Regel laden gedacht ist, kann es als Teil eines VSPackage implementiert werden. Das Paket muss auf Autoload festgelegt werden, durch Hinzufügen der <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> auf das VSPackage mit einem Wert von <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>. Der Lösung Manager kann dann aktiviert werden, der <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> Methode.  
  
> [!NOTE]
>  Weitere Informationen zu es Paketen finden Sie unter [Laden von VSPackages](../extensibility/loading-vspackages.md).  
  
 Da Visual Studio nur den letzten Projektmappe laden Manager aktiviert werden erkennt, sollte allgemeine Lösung Load\-Manager immer erkannt werden, ob vor dem Aktivieren der selbst ein vorhandenen Auslastungstest\-Manager ist. Wenn GetProperty\(\) für den Dienst Lösung Aufrufen <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> gibt `null`, keine Lösung für die aktive Load\-Manager vorhanden ist. Wenn es nicht null zurückgibt, überprüfen Sie, ob das Objekt identisch mit der Lösung des Managers.  
  
 Wenn der Manager Lösung nur einige Arten von Lösung verwalten soll, kann das VSPackage Lösung laden Ereignisse abonnieren \(durch Aufrufen von <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>\), und verwenden Sie den Ereignishandler für <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> den Lösung Manager aktivieren.  
  
 Wenn der Manager Lösung gedacht ist, um nur bestimmte Lösungen zu verwalten, kann die Aktivierungsinformationen als Teil der Projektmappendatei beibehalten werden. Hierzu rufen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> für den Abschnitt vor der Lösung.  
  
 Spezifische Lösung Load\-Manager sollten deaktivieren, sich selbst in der <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> \-Ereignishandler in der Reihenfolge nicht mit anderen Lösung Load\-Managern in Konflikt stehen.  
  
 Wenn Sie eine Lösung des\-Managers benötigen, nur um globale Load Projektprioritäten \(z. B. Eigenschaften, die auf eine Optionsseite festgelegt\) beizubehalten, in den Projektmappe Manager aktiviert werden kann der <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> \-Ereignishandler die Einstellung in den Projektmappeneigenschaften, speichern und dann den Projektmappe Manager deaktivieren.  
  
## Behandlung von Ereignissen für Projektmappe laden  
 Rufen Sie zum abonnieren Ereignisse Laden der Projektmappe <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> beim Aktivieren der Lösung des Managers. Wenn Sie implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>, Sie reagieren auf Ereignisse, die auf anderen Projekt laden Prioritäten beziehen.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: Wird ausgelöst, bevor eine Projektmappe geöffnet wird. Sie können es verwenden, so ändern Sie das Projekt, die Priorität für die Projekte in der Projektmappe geladen.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: Wird ausgelöst, nachdem die Projektmappe vollständig geladen ist, aber vor dem Hintergrund Projekt laden erneut beginnt. Z. B. ein Benutzer kann einem Projekt, dessen Priorität Load LoadIfNeeded zugegriffen haben, oder möglicherweise der Lösung Manager eine Projekt laden Priorität geändert, um BackgroundLoad, die einen Hintergrund Laden des Projekts gestartet werden konnte.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: Wird ausgelöst, nachdem eine Projektmappe zunächst vollständig geladen ist, ob ein Projektmappe Load\-Manager vorhanden ist. Es wird auch ausgelöst, nachdem der Hintergrund laden oder bei Bedarf geladen werden, sobald die Lösung vollständig geladen wird. Gleichzeitig <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> wird erneut aktiviert.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: Dies ist vor dem Laden eines Projekts \(oder Projekten\) ausgelöst. Festlegen, um sicherzustellen, dass andere Hintergrundprozesse abgeschlossen sind, bevor die Projekte geladen werden, `pfShouldDelayLoadToNextIdle`**true**.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: Wird ausgelöst, wenn ein Batch von Projekten wird geladen werden soll. Wenn `fIsBackgroundIdleBatch` true ist, die Projekte sind im Hintergrund; geladen werden, wenn `fIsBackgroundIdleBatch` "false", die Projekte werden geladen synchron als Ergebnis einer benutzeranforderung, z. B. wenn der Benutzer eine ausstehende Projekt im Projektmappen\-Explorer erweitert wird. Implementieren Sie diese Option, um Aktionen teuer, die ansonsten in ausgeführt werden müssten <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterOpenProject%2A>.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: Wird ausgelöst, nachdem ein Batch von Projekten geladen wurde.  
  
## Erkennen und Verwalten von Projektmappen und Projekt laden  
 Aufrufen, damit den Status des von Projekten und Projektmappen zu erkennen, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> mit den folgenden Werten:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` gibt `true` wenn die Projektmappe und alle darin enthaltenen Projekte geladen wurde, andernfalls werden `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` gibt `true` wenn ein Batch von Projekten gerade andernfalls im Hintergrund geladen werden `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` gibt `true` wenn ein Batch von Projekten werden gerade geladen synchron als Ergebnis eines Befehls Benutzer oder andere explizite laden, andernfalls `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>: `var` gibt `true` wenn die Projektmappe aktuell, andernfalls geschlossen wird `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>: `var` gibt `true` Wenn Öffnen einer Projektmappe derzeit, andernfalls wird `false`.  
  
 Sie können auch sicherstellen, dass Projekte und Projektmappen geladen werden \(unabhängig davon, was die Auslastung Projektprioritäten sind\) eine der folgenden Methoden aufrufen:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: das Aufrufen dieser Methode erzwingt, dass die Projekte in einer Projektmappe geladen werden, bevor die Methode zurückgegeben.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: das Aufrufen dieser Methode erzwingt, dass die Projekte in `guidProject` geladen, bevor die Methode zurückgegeben.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: das Aufrufen dieser Methode erzwingt, dass das Projekt im `guidProjectID` geladen, bevor die Methode zurückgegeben.  
  
> [!NOTE]
>  . Standardmäßig nur die Projekte, die über den Bedarf laden und Hintergrund laden Prioritäten geladen, aber wenn die <xref:Microsoft.VisualStudio.Shell.Interop.__VSBSLFLAGS> Flag an die Methode übergeben wird, werden alle Projekte geladen, mit Ausnahme derer, die markiert sind, um explizit zu laden.
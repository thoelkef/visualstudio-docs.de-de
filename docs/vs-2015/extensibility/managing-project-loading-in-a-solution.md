---
title: Verwalten des Laden von Projekten in einer Projekt Mappe | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a6598e2f1a178845b3ad2017716576439185379e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840887"
---
# <a name="managing-project-loading-in-a-solution"></a>Verwalten des Ladens von Projekten in einer Projektmappe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio-Projektmappen können eine große Anzahl von Projekten enthalten. Das Standardverhalten von Visual Studio besteht darin, alle Projekte in einer Projekt Mappe zu dem Zeitpunkt zu laden, zu dem die Projekt Mappe geöffnet wird, und nicht, um dem Benutzer den Zugriff auf Projekte zu gestatten, bis alle Elemente vollständig geladen wurden. Wenn der Ladevorgang für das Projekt mehr als zwei Minuten dauert, wird eine Statusanzeige angezeigt, in der die Anzahl der geladenen Projekte und die Gesamtzahl der Projekte angezeigt wird. Der Benutzer kann Projekte bei der Arbeit in einer Projekt Mappe mit mehreren Projekten entladen, aber dieses Verfahren hat einige Nachteile: die entladenen Projekte werden nicht als Teil des Befehls "Rebuild Solution" erstellt, und IntelliSense-Beschreibungen von Typen und Membern geschlossener Projekte werden nicht angezeigt.  
  
 Entwickler können die Ladezeiten von Projektmappen reduzieren und das Ladeverhalten von Projekten verwalten, indem Sie einen Projektmappen- Der projektmappenload-Manager kann verschiedene Projekt Lade Prioritäten für bestimmte Projekte oder Projekttypen festlegen. Stellen Sie sicher, dass Projekte geladen werden, bevor Sie einen Hintergrund Build starten, das Laden von hintergrundgängen verzögern, bis andere Hintergrundaufgaben vollständig sind, und andere Aufgaben zum Laden von Projekten ausführen  
  
## <a name="project-loading-priorities"></a>Projekt Lade Prioritäten  
 Visual Studio definiert vier verschiedene Projekt Lade Prioritäten:  
  
- <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority> (Standard): Wenn eine Projekt Mappe geöffnet wird, werden Projekte asynchron geladen. Wenn diese Priorität für ein entladenes Projekt festgelegt wird, nachdem die Projekt Mappe bereits geöffnet ist, wird das Projekt am nächsten Leerlauf Punkt geladen.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: Wenn eine Projekt Mappe geöffnet wird, werden Projekte im Hintergrund geladen, sodass der Benutzer auf die Projekte zugreifen kann, während Sie geladen werden, ohne zu warten, bis alle Projekte geladen sind.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: Projekte werden geladen, wenn auf Sie zugegriffen wird. Auf ein Projekt wird zugegriffen, wenn der Benutzer den Projekt Knoten im Projektmappen-Explorer erweitert, wenn eine Datei, die zum Projekt gehört, geöffnet wird, wenn die Projekt Mappe geöffnet wird, da Sie sich in der geöffneten Dokument Liste befindet (persistent in der Benutzer Optionsdatei der Projekt Mappe) oder wenn ein anderes Projekt, das geladen wird, eine Abhängigkeit vom Projekt aufweist. Dieser Projekttyp wird vor dem Starten eines Buildprozesses nicht automatisch geladen. der projektmappenload-Manager ist dafür verantwortlich, sicherzustellen, dass alle erforderlichen Projekte geladen werden. Diese Projekte sollten auch geladen werden, bevor eine Suche/Replace in-Dateien für die gesamte Projekt Mappe gestartet wird.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: Projekte können nur geladen werden, wenn der Benutzer Sie explizit anfordert. Dies ist der Fall, wenn Projekte explizit entladen werden.  
  
## <a name="creating-a-solution-load-manager"></a>Erstellen eines projektmappenlade-Managers  
 Entwickler können einen projektmappenload-Manager erstellen, indem Sie Visual Studio implementieren und angleichen, dass der Projektmappen- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> Load Manager aktiv  
  
#### <a name="activating-a-solution-load-manager"></a>Aktivieren eines projektmappenlade-Managers  
 Visual Studio ermöglicht nur einen projektmappenload-Manager zu einem bestimmten Zeitpunkt. Daher müssen Sie Visual Studio anweisen, wenn Sie den Projektmappen-Load Manager aktivieren möchten. Wenn ein zweiter projektmappenload-Manager später aktiviert wird, wird der Projektmappen-Load Manager getrennt.  
  
 Sie müssen den <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> Dienst erhalten und die- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> Eigenschaft festlegen:  
  
```csharp  
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;  
object objLoadMgr = this;   //the class that implements IVsSolutionManager  
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);  
```  
  
#### <a name="implementing-ivssolutionloadmanager"></a>Implementieren von ivssolutionloadmanager  
 Die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnBeforeOpenProject%2A> Methode wird während des Öffnens der Projekt Mappe aufgerufen. Um diese Methode zu implementieren, verwenden Sie den- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManagerSupport> Dienst, um die Last Priorität für den Projekttyp festzulegen, den Sie verwalten möchten. Der folgende Code legt z. b. c#-Projekttypen fest, die im Hintergrund geladen werden sollen:  
  
```csharp  
Guid guidCSProjectType = new Guid("{FAE04EC0-301F-11d3-BF4B-00C04F79EFBC}");  
pSLMgrSupport.SetProjectLoadPriority(guidProjectID, (uint)_VSProjectLoadPriority.PLP_BackgroundLoad);  
```  
  
 Die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> Methode wird entweder aufgerufen, wenn Visual Studio heruntergefahren wird oder wenn ein anderes Paket als aktiver projektmappenload-Manager übernommen wurde, indem <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> mit der-Eigenschaft aufgerufen wird <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> .  
  
#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Strategien für verschiedene Arten von Lösung Load Manager  
 Sie können projektmappenlade-Manager je nach Art der Lösungen, die Sie verwalten möchten, auf unterschiedliche Weise implementieren.  
  
 Wenn der projektmappenload-Manager im Allgemeinen das Laden von Projektmappen verwalten soll, kann er als Teil eines VSPackage implementiert werden. Das Paket sollte auf "AutoLoad" festgelegt werden, indem Sie <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> für das VSPackage mit dem Wert hinzufügen <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid> . Der projektmappenload-Manager kann dann in der-Methode aktiviert werden <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> .  
  
> [!NOTE]
> Weitere Informationen zu automatischen Paketen finden Sie unter Laden von [VSPackages](../extensibility/loading-vspackages.md).  
  
 Da Visual Studio nur den letzten projektmappenload-Manager erkennt, der aktiviert werden soll, sollten allgemeine projektmappenload-Manager immer erkennen, ob ein Lasten-Manager vorhanden ist, bevor Sie sich selbst aktivieren Wenn "GetProperty ()" für den Lösungs Dienst für "Returns" aufgerufen wird <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> `null` , ist kein aktiver projektmappenload-Manager vorhanden. Wenn keine NULL-Werte zurückgegeben werden, überprüfen Sie, ob das Objekt dem projektmappenload-Manager entspricht.  
  
 Wenn der projektmappenload-Manager nur wenige Arten von Projektmappen verwalten soll, kann das VSPackage projektmappenlade-Ereignisse abonnieren (durch Aufrufen von <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> ) und den-Ereignishandler für verwenden, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> um den projektmappenlade-Manager zu aktivieren.  
  
 Wenn der projektmappenload-Manager nur bestimmte Lösungen verwalten soll, können die Aktivierungs Informationen als Teil der Projektmappendatei beibehalten werden. Um dies zu erreichen, müssen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> für den Abschnitt vor der Projekt Mappe aufzurufen.  
  
 Bestimmte projektmappenload-Manager sollten sich selbst im <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> Ereignishandler deaktivieren, damit kein Konflikt mit anderen projektmappenlade-Managern auftritt.  
  
 Wenn Sie einen projektmappenload-Manager benötigen, um globale Projekt Last Prioritäten beizubehalten (z. b. auf einer Options Seite festgelegte Eigenschaften), können Sie den projektmappenload-Manager im <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents2.OnAfterOpenProject%2A> Ereignishandler aktivieren, die Einstellung in den Projektmappeneigenschaften beibehalten und dann den Projektmappen-Lasten-Manager deaktivieren.  
  
## <a name="handling-solution-load-events"></a>Behandeln von projektmappenlade Ereignissen  
 Um Projektmappen-Lade Ereignisse zu abonnieren, wenden Sie an, wenn Sie den Projektmappen- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> Load Manager Wenn Sie implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents> , können Sie auf Ereignisse reagieren, die sich auf verschiedene Projekt Lade Prioritäten beziehen.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: Wird ausgelöst, bevor eine Projekt Mappe geöffnet wird. Sie können es verwenden, um die Projekt Lade Priorität für die Projekte in der Projekt Mappe zu ändern.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: Wird ausgelöst, nachdem die Projekt Mappe vollständig geladen wurde, aber bevor der Ladevorgang für das Projekt erneut beginnt. Ein Benutzer hat z. b. möglicherweise auf ein Projekt zugegriffen, dessen Lade Priorität nicht erforderlich ist, oder der projektmappenload-Manager hat möglicherweise eine Projekt Lade Priorität in backgroundload geändert, wodurch ein Hintergrund Ladevorgang des Projekts gestartet wird.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: Dies wird ausgelöst, nachdem eine Projekt Mappe anfänglich vollständig geladen wurde, unabhängig davon, ob ein projektmappenload-Manager vorhanden ist. Sie wird auch ausgelöst, wenn die Projekt Mappe vollständig geladen wird, nachdem die Projekt Mappe vollständig geladen wurde. Gleichzeitig <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> wird erneut aktiviert.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: Dies wird vor dem Laden eines Projekts (oder Projekten) ausgelöst. Um sicherzustellen, dass andere Hintergrundprozesse abgeschlossen sind, bevor die Projekte geladen werden, legen `pfShouldDelayLoadToNextIdle` Sie auf **true**fest.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: Wird ausgelöst, wenn ein Batch von Projekten geladen wird. Wenn `fIsBackgroundIdleBatch` true ist, werden die Projekte im Hintergrund geladen. Wenn `fIsBackgroundIdleBatch` false ist, werden die Projekte als Ergebnis einer Benutzer Anforderung synchron geladen, z. b. wenn der Benutzer ein ausstehendes Projekt in Projektmappen-Explorer erweitert. Sie können dies implementieren, um aufwändige Aufgaben durchzuführen, die andernfalls in ausgeführt werden müssen <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: Wird ausgelöst, nachdem ein Batch von Projekten geladen wurde.  
  
## <a name="detecting-and-managing-solution-and-project-loading"></a>Erkennen und Verwalten von Projektmappen und Projekten  
 Um den Ladestatus von Projekten und Projektmappen zu ermitteln, müssen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> mit den folgenden Werten aufzurufen:  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` gibt zurück `true` , wenn die Projekt Mappe und alle zugehörigen Projekte geladen werden, andernfalls `false` .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` gibt zurück `true` , wenn ein Batch von Projekten gegenwärtig im Hintergrund geladen wird; andernfalls `false` .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` gibt zurück `true` , wenn ein Batch von Projekten momentan aufgrund eines Benutzer Befehls oder einer anderen expliziten Auslastung synchron geladen wird; andernfalls `false` .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>: `var` gibt zurück `true` , wenn die Projekt Mappe gerade geschlossen wird; andernfalls `false` .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>: `var` gibt zurück `true` , wenn eine Projekt Mappe gerade geöffnet wird; andernfalls `false` .  
  
  Sie können auch sicherstellen, dass Projekte und Projektmappen geladen werden (unabhängig von den Projekt Lade Prioritäten), indem Sie eine der folgenden Methoden aufrufen:  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: durch Aufrufen dieser Methode wird erzwungen, dass die Projekte in einer Projekt Mappe geladen werden, bevor die Methode zurückgibt.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: durch das Aufrufen dieser Methode wird erzwungen, dass die Projekte in `guidProject` geladen werden, bevor die Methode zurückgibt.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: durch das Aufrufen dieser Methode wird erzwungen, dass das Projekt in `guidProjectID` geladen wird, bevor die Methode zurückgibt.  
  
> [!NOTE]
> . Standardmäßig werden nur die Projekte geladen, die die Prioritäten für den Anforderungs Lade-und den Hintergrund Ladevorgang aufweisen. Wenn jedoch das <xref:Microsoft.VisualStudio.Shell.Interop.__VSBSLFLAGS> Flag an die-Methode übermittelt wird, werden alle Projekte mit Ausnahme derjenigen geladen, die zum expliziten Laden markiert sind.

---
title: Verwalten des Ladens von Projekten in einer Projektmappe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 465adc1c7804582767415c3e9e5311c2379c7b8b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49281384"
---
# <a name="managing-project-loading-in-a-solution"></a>Verwalten des Ladens von Projekten in einer Projektmappe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio-Projektmappen können es sich um eine große Anzahl von Projekten enthalten. Das Standardverhalten für Visual Studio ist beim Laden alle Projekte in einer Projektmappe zum Zeitpunkt der Projektmappe geöffnet wird und nicht, damit Benutzer auf keinem der Projekte zugreifen, bis alle abgeschlossen sind. Wenn der Prozess des Ladens von Projekten mit mehr als zwei Minuten dauern wird, wird eine Statusanzeige zeigt die Anzahl der Projekte, die geladen und die Gesamtzahl der Projekte angezeigt. Der Benutzer kann Projekte entladen, während der Arbeit in einer Projektmappe mit mehreren Projekten, aber dieses Verfahren hat einige Nachteile: die entladenen Projekte werden nicht als Teil eines Befehls für die Projektmappe neu erstellen erstellt und IntelliSense-Beschreibungen von Typen und Member von geschlossen Projekte werden nicht angezeigt.  
  
 Entwickler können für geringere Ladezeiten von Projektmappen und das Verhalten von erstellen einen Ladevorgang für Projektmappen Manager Laden des Projekts zu verwalten. Die projektmappenlastmanager können anderen Projekt Laden von Prioritäten für bestimmte Projekte oder Projekttypen festlegen, stellen Sie sicher, dass die Projekte geladen werden, vor dem Starten eines Builds Hintergrund, verzögern Hintergrund zu laden, bis andere Aufgaben im Hintergrund abgeschlossen sind und ausführen andere Verwaltungsaufgaben für den Projekt laden.  
  
## <a name="project-loading-priorities"></a>Das Laden von Prioritäten des Projekts  
 Visual Studio definiert vier Prioritäten von anderen Projekt laden:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority> (Standard): Wenn eine Projektmappe geöffnet ist, werden Projekte asynchron geladen. Wenn die Priorität auf entladenes Projekt festgelegt ist, nachdem die Projektmappe bereits geöffnet ist, wird das Projekt am nächsten im Leerlauf geladen werden.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: Wenn eine Projektmappe geöffnet wird, werden Projekte im Hintergrund, damit der Benutzers auf die Projekte zugreifen, wie sie ohne zu warten, bis alle Projekte geladen werden geladen werden geladen.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: Projekte geladen werden, wenn darauf zugegriffen wird. Ein Projekt erfolgt, wenn der Benutzer den Projektknoten im Projektmappen-Explorer erweitert wird, wenn eine Datei, die zum Projekt gehören geöffnet wird, wenn die Projektmappe wird geöffnet, da sie in der geöffneten Dokumentenliste (persistent in der die projektmappenbenutzer-Optionsdatei) ist, oder wenn ein anderes Projekt d. h. weist eine Abhängigkeit wird auf das Projekt geladen wird. Diese Art Projekt wird nicht automatisch geladen, bevor Sie einen Buildprozess zu starten; der Solution Load Manager ist dafür verantwortlich, sicherzustellen, dass alle notwendigen Projekte geladen werden. Diese Projekte sollten auch vor dem Starten ein Suchen/Ersetzen in Dateien in der gesamten Projektmappe geladen werden.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: Projekte werden nicht geladen, wenn der Benutzer dies explizit fordert. Dies ist der Fall, wenn Sie Projekte explizit entladen werden.  
  
## <a name="creating-a-solution-load-manager"></a>Erstellen einen Ladevorgang für Projektmappen-Managers  
 Entwickler können Laden einer Projektmappe Manager erstellen durch die Implementierung <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> und der Beratung von Visual Studio, dass die projektmappenlastmanager aktiv ist.  
  
#### <a name="activating-a-solution-load-manager"></a>Einen projektmappenlastmanager aktivieren  
 Visual Studio können nur einen projektmappenlastmanager zu einem beliebigen Zeitpunkt auf, daher Sie Visual Studio mitteilen müssen, wenn Sie Ihre Ladevorgang für Projektmappen aktivieren möchten Manager. Wenn ein zweite projektmappenlastmanager später aktiviert ist, werden Ihre projektmappenlastmanager getrennt.  
  
 Erhalten Sie die <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> Dienst, und legen die <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> Eigenschaft:  
  
```csharp  
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;  
object objLoadMgr = this;   //the class that implements IVsSolutionManager  
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);  
```  
  
#### <a name="implementing-ivssolutionloadmanager"></a>Implementieren von IVsSolutionLoadManager  
 Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnBeforeOpenProject%2A> Methode wird aufgerufen, während des Prozesses, der die Projektmappe öffnen. Um diese Methode implementieren, verwenden Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManagerSupport> Dienst für die Load-Priorität für den Typ des Projekts festgelegt, Sie verwalten möchten. Der folgende Code legt z. B. C#-Projekttypen im Hintergrund geladen:  
  
```csharp  
Guid guidCSProjectType = new Guid("{FAE04EC0-301F-11d3-BF4B-00C04F79EFBC}");  
pSLMgrSupport.SetProjectLoadPriority(guidProjectID, (uint)_VSProjectLoadPriority.PLP_BackgroundLoad);  
```  
  
 Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> Methode wird aufgerufen, wenn Visual Studio heruntergefahren wird oder ein anderes Paket als den aktiven projektmappenlademanager Aufrufen über genommen hat <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> mit der <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> Eigenschaft.  
  
#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Strategien für verschiedene Arten von projektmappenlastmanager  
 Sie können die Solution Load Manager unterschiedlich, je nach Art der Lösungen implementieren, die sie verwalten sollen.  
  
 Wenn die projektmappenlastmanager, zum Verwalten von Projektmappen im Allgemeinen werden geladen vorgesehen ist, kann es als Teil eines VSPackage implementiert werden. Das Paket sollte auf Autoload festgelegt werden, durch das Hinzufügen der <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> für das VSPackage, mit dem Wert <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>. Die projektmappenlastmanager kann dann aktiviert werden, der <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> Methode.  
  
> [!NOTE]
>  Weitere Informationen zu Automatisches Laden von Paketen finden Sie unter [Laden von VSPackages](../extensibility/loading-vspackages.md).  
  
 Da Visual Studio nur die letzten projektmappenlastmanager zu aktivierenden erkennt, sollten allgemeine Lösung Load-Manager, ob vor dem Aktivieren der selbst ein vorhandenen Load-Manager ist nicht immer erkennen. Wenn der Aufruf von GetProperty() für den Dienst der Lösung für <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> gibt `null`, es gibt keine aktiven projektmappenlademanager. Wenn es nicht null zurückgibt, überprüfen Sie, ob das Objekt Ihrer projektmappenlastmanager identisch ist.  
  
 Wenn die projektmappenlastmanager vorgesehen ist, um nur einige Arten von Projektmappen zu verwalten, kann das VSPackage projektmappenladeereignisse abonnieren (durch Aufrufen von <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>), und verwenden Sie den Ereignishandler für <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> der projektmappenlastmanager aktivieren.  
  
 Wenn die projektmappenlastmanager vorgesehen ist, können nur bestimmte Lösungen verwalten, kann die Aktivierungsinformationen als Teil der Projektmappendatei gespeichert werden. Zu diesem Zweck rufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> für den Abschnitt vor Ausführung der Projektmappe.  
  
 Spezifische Lösung Load Manager sollte deaktivieren, sich selbst in die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> -Ereignishandler in der Reihenfolge nicht mit anderen Solution Load-Managern in Konflikt stehen.  
  
 Bei Bedarf einen projektmappenlastmanager, nur um globalen projektauflistung ladeprioritäten (z. B. Eigenschaften, die für eine Seite mit Optionen festlegen) beizubehalten, die projektmappenlastmanager in können Sie aktivieren die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents2.OnAfterOpenProject%2A> Ereignishandler, klicken Sie dann die Einstellung in den Projektmappeneigenschaften beibehalten Deaktivieren Sie die projektmappenlademanager.  
  
## <a name="handling-solution-load-events"></a>Behandeln von projektmappenladeereignisse  
 Rufen Sie zum Abonnieren von projektmappenladeereignisse <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> Wenn Sie Ihre projektmappenlastmanager aktivieren. Wenn Sie implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>, Sie können auf Ereignisse im Zusammenhang mit anderen Projekt laden Prioritäten reagieren.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: Dieser Fehler wird ausgelöst, bevor eine Projektmappe geöffnet wird. Sie können es verwenden, so ändern Sie das Projekt, die Priorität für die Projekte in der Projektmappe laden.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: Wird ausgelöst, nachdem die Projektmappe vollständig geladen ist, aber vor dem Hintergrund wird das Laden des Projekts erneut gestartet. Beispielsweise ein Benutzer möglicherweise auf ein Projekt, dessen lastpriorität LoadIfNeeded ist, zugegriffen haben, oder möglicherweise der projektmappenlastmanager eine projektlastpriorität geändert, um BackgroundLoad, die einen Hintergrund laden dieses Projekts gestartet werden konnte.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: Wird ausgelöst, nachdem eine Projektmappe ursprünglich vollständig geladen ist, ob es ein projektmappenlademanager ist. Es wird auch ausgelöst, nachdem der Hintergrund laden oder bei Bedarf geladen werden, wenn die Projektmappe vollständig geladen wird. Zur gleichen Zeit <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> wird erneut aktiviert.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: Wird ausgelöst, bevor Sie das Laden eines Projekts (oder Projekte). Um sicherzustellen, dass andere Hintergrundprozesse abgeschlossen sind, bevor die Projekte geladen werden, legen Sie `pfShouldDelayLoadToNextIdle` zu **"true"**.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: Wird ausgelöst, wenn ein Batch von Projekten wird geladen werden soll. Wenn `fIsBackgroundIdleBatch` ist "true", die Projekte sind im Hintergrund; geladen werden, wenn `fIsBackgroundIdleBatch` ist "false", die Projekte geladen werden sollen synchron aufgrund einer benutzeranforderung, z. B. wenn der Benutzer ein ausstehendes Projekt im Projektmappen-Explorer erweitert wird. Sie können diese Option, um teure Arbeit zu erledigen, die andernfalls ausgeführt werden müssten implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: Wird ausgelöst, nachdem ein Batch von Projekten geladen wurde.  
  
## <a name="detecting-and-managing-solution-and-project-loading"></a>Erkennen und Verwalten von Projektmappen und des Ladens von Projekten  
 Um den Load-Status der Projekte und Projektmappen zu erkennen, rufen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> mit den folgenden Werten:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` gibt `true` , wenn die Projektmappe und alle darin enthaltenen Projekte geladen wurde, andernfalls werden `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` gibt `true` , wenn ein Batch Projekte sind gerade andernfalls im Hintergrund geladen `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` gibt `true` , wenn ein Batch Projekte werden gerade geladen synchron als Ergebnis eines Befehls für die Benutzer oder andere explizite laden, andernfalls `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>: `var` gibt `true` , wenn die Projektmappe gerade geschlossen wird, andernfalls wird `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>: `var` gibt `true` , wenn eine Projektmappe gerade, andernfalls geöffnet wird `false`.  
  
 Sie können auch sicherstellen, dass Projekte und Projektmappen geladen werden (unabhängig davon, was die Auslastung Projektprioritäten sind) durch Aufrufen einer der folgenden Methoden:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: das Aufrufen dieser Methode erzwingt, dass die Projekte in einer Projektmappe geladen werden, bevor die Methode zurückgibt.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: das Aufrufen dieser Methode erzwingt, dass die Projekte in `guidProject` geladen, bevor die Methode zurückgibt.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: das Aufrufen dieser Methode erzwingt, dass das Projekt im `guidProjectID` geladen, bevor die Methode zurückgibt.  
  
> [!NOTE]
>  sein. Standardmäßig nur die Projekte, die die Anforderung geladen und Hintergrund ladeprioritäten geladen sind, aber wenn die <xref:Microsoft.VisualStudio.Shell.Interop.__VSBSLFLAGS> Flag wird an die Methode übergeben, werden alle Projekte geladen werden, außer denjenigen, die markiert sind, um explizit zu laden.


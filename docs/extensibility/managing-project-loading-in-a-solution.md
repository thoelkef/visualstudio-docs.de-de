---
title: Verwalten des Ladens von Projekten in einer Projektmappe | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a80430c4a5dcf5526445275b89fa2da7f02f5529
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340583"
---
# <a name="manage-project-loading-in-a-solution"></a>Verwalten des Ladens von Projekten in einer Projektmappe
Visual Studio-Projektmappen können es sich um eine große Anzahl von Projekten enthalten. Das Standardverhalten für Visual Studio ist beim Laden alle Projekte in einer Projektmappe zum Zeitpunkt der Projektmappe geöffnet wird und nicht, damit Benutzer auf keinem der Projekte zugreifen, bis alle abgeschlossen sind. Wenn der Prozess des Ladens von Projekten mit mehr als zwei Minuten dauern wird, wird eine Statusanzeige zeigt die Anzahl der Projekte, die geladen und die Gesamtzahl der Projekte angezeigt. Der Benutzer kann Projekte entladen, während der Arbeit in einer Projektmappe mit mehreren Projekten, aber dieses Verfahren hat einige Nachteile: die entladenen Projekte werden nicht als Teil eines Befehls für die Projektmappe neu erstellen erstellt und IntelliSense-Beschreibungen von Typen und Member von geschlossen Projekte werden nicht angezeigt.

 Entwickler können für geringere Ladezeiten von Projektmappen und das Verhalten von erstellen einen Ladevorgang für Projektmappen Manager Laden des Projekts zu verwalten. Die projektmappenlastmanager kann stellen Sie sicher, dass die Projekte geladen werden, vor dem Starten eines Builds Hintergrund verzögert Hintergrund zu laden, bis andere Aufgaben im Hintergrund abgeschlossen sind und andere Projekt-Load-Verwaltungsaufgaben ausführen.

## <a name="create-a-solution-load-manager"></a>Erstellen Sie einen Ladevorgang für Projektmappen-manager
 Entwickler können Laden einer Projektmappe Manager erstellen durch die Implementierung <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> und der Beratung von Visual Studio, dass die projektmappenlastmanager aktiv ist.

### <a name="activate-a-solution-load-manager"></a>Einen projektmappenlastmanager aktivieren
 Visual Studio können nur einen projektmappenlastmanager zu einem beliebigen Zeitpunkt auf, daher Sie Visual Studio mitteilen müssen, wenn Sie Ihre Ladevorgang für Projektmappen aktivieren möchten Manager. Wenn ein zweite projektmappenlastmanager später aktiviert ist, werden Ihre projektmappenlastmanager getrennt.

 Erhalten Sie die <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> Dienst, und legen die [__VSPROPID4. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) Eigenschaft:

```csharp
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;
object objLoadMgr = this;   //the class that implements IVsSolutionManager
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);
```

 Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> Methode wird aufgerufen, wenn Visual Studio heruntergefahren wird oder ein anderes Paket als den aktiven projektmappenlademanager Aufrufen über genommen hat <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> mit der [__VSPROPID4. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) Eigenschaft.

#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Strategien für verschiedene Arten von projektmappenlastmanager
 Sie können die Solution Load Manager unterschiedlich, je nach Art der Lösungen implementieren, die sie verwalten sollen.

 Wenn die projektmappenlastmanager, zum Verwalten von Projektmappen im Allgemeinen werden geladen vorgesehen ist, kann es als Teil eines VSPackage implementiert werden. Das Paket sollte auf Autoload festgelegt werden, durch das Hinzufügen der <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> für das VSPackage, mit dem Wert <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>. Die projektmappenlastmanager kann dann aktiviert werden, der <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> Methode.

> [!NOTE]
> Weitere Informationen zu Automatisches Laden von Paketen finden Sie unter [Laden von VSPackages](../extensibility/loading-vspackages.md).

 Da Visual Studio nur die letzten projektmappenlastmanager zu aktivierenden erkennt, sollten allgemeine Lösung Load-Manager, ob vor dem Aktivieren der selbst ein vorhandenen Load-Manager ist nicht immer erkennen. Wenn der Aufruf `GetProperty()` für den Dienst Lösung [__VSPROPID4. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) gibt `null`, es gibt keine aktiven projektmappenlademanager. Wenn es nicht null zurückgibt, überprüfen Sie, ob das Objekt Ihrer projektmappenlastmanager identisch ist.

 Wenn die projektmappenlastmanager vorgesehen ist, um nur einige Arten von Projektmappen zu verwalten, kann das VSPackage projektmappenladeereignisse abonnieren (durch Aufrufen von <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>), und verwenden Sie den Ereignishandler für <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> der projektmappenlastmanager aktivieren.

 Wenn die projektmappenlastmanager vorgesehen ist, können nur bestimmte Lösungen verwalten, kann Aktivierungsinformationen als Teil der Projektmappendatei beibehalten werden, durch den Aufruf <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> für den Abschnitt vor Ausführung der Projektmappe.

 Spezifische Lösung Load Manager sollte deaktivieren, sich selbst in die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> -Ereignishandler in der Reihenfolge nicht mit anderen Solution Load-Managern in Konflikt stehen.

 Bei Bedarf einen projektmappenlastmanager, nur um globalen projektauflistung Load-Eigenschaften (z. B. Eigenschaften, die für eine Seite mit Optionen festlegen) beizubehalten, die projektmappenlastmanager in können Sie aktivieren die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> Ereignishandler, klicken Sie dann die Einstellung in den Projektmappeneigenschaften beibehalten Deaktivieren Sie die projektmappenlademanager.

## <a name="handle-solution-load-events"></a>Behandeln von projektmappenladeereignisse
 Rufen Sie zum Abonnieren von projektmappenladeereignisse <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> Wenn Sie Ihre projektmappenlastmanager aktivieren. Wenn Sie implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>, Sie können auf Ereignisse im Zusammenhang mit anderen Projekt beim Laden der Eigenschaften reagieren.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: Dieses Ereignis wird ausgelöst, bevor eine Projektmappe geöffnet wird.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: Dieses Ereignis wird ausgelöst, nachdem die Projektmappe vollständig geladen ist, aber vor dem Hintergrund wird das Laden des Projekts erneut gestartet.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: Dieses Ereignis wird ausgelöst, nachdem eine Projektmappe ursprünglich vollständig geladen wurde, ob es ein projektmappenlademanager ist. Es wird auch ausgelöst, nachdem der Hintergrund laden oder bei Bedarf geladen werden, wenn die Projektmappe vollständig geladen wird. Zur gleichen Zeit <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> wird erneut aktiviert.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: Dieses Ereignis wird ausgelöst, bevor Sie das Laden eines Projekts (oder Projekte). Um sicherzustellen, dass andere Hintergrundprozesse abgeschlossen sind, bevor die Projekte geladen werden, legen Sie `pfShouldDelayLoadToNextIdle` zu **"true"** .

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: Dieses Ereignis wird ausgelöst, wenn ein Batch Projekte gerade geladen werden. Wenn `fIsBackgroundIdleBatch` ist "true", die Projekte sind im Hintergrund; geladen werden, wenn `fIsBackgroundIdleBatch` ist "false", die Projekte geladen werden sollen synchron aufgrund einer benutzeranforderung, z. B. wenn der Benutzer ein ausstehendes Projekt im Projektmappen-Explorer erweitert wird. Sie können dieses Ereignis, um teure Arbeit zu erledigen, die andernfalls benötigen würden, erfolgen behandeln <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: Dieses Ereignis wird ausgelöst, nachdem ein Batch von Projekten geladen wurde.

## <a name="detect-and-manage-solution-and-project-loading"></a>Erkennen und Verwalten von Projektmappen und des Ladens von Projekten
 Um den Load-Status der Projekte und Projektmappen zu erkennen, rufen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> mit den folgenden Werten:

- [__VSPROPID4. VSPROPID_IsSolutionFullyLoaded](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsSolutionFullyLoaded>): `var` gibt `true` , wenn die Projektmappe und alle darin enthaltenen Projekte geladen wurde, andernfalls werden `false`.

- [__VSPROPID4. VSPROPID_IsInBackgroundIdleLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInBackgroundIdleLoadProjectBatch>): `var` gibt `true` , wenn ein Batch Projekte andernfalls aktuell im Hintergrund geladen wird `false`.

- [__VSPROPID4. VSPROPID_IsInSyncDemandLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInSyncDemandLoadProjectBatch>): `var` gibt `true` , wenn ein Batch Projekte aktuell synchron als Ergebnis eines Befehls für die Benutzer oder andere explizite laden, andernfalls geladen wird `false`.

- [__VSPROPID2. VSPROPID_IsSolutionClosing](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2.VSPROPID_IsSolutionClosing>): `var` gibt `true` , wenn die Projektmappe gerade geschlossen wird, andernfalls wird `false`.

- [__VSPROPID. VSPROPID_IsSolutionOpening](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID.VSPROPID_IsSolutionOpening>): `var` gibt `true` , wenn eine Projektmappe gerade, andernfalls geöffnet wird `false`.

Sie können auch sicherstellen, dass Projekte und Projektmappen geladen werden, indem Sie eine der folgenden Methoden aufrufen:

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: das Aufrufen dieser Methode erzwingt, dass die Projekte in einer Projektmappe geladen werden, bevor die Methode zurückgibt.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: das Aufrufen dieser Methode erzwingt, dass die Projekte in `guidProject` geladen, bevor die Methode zurückgibt.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: das Aufrufen dieser Methode erzwingt, dass das Projekt im `guidProjectID` geladen, bevor die Methode zurückgibt.

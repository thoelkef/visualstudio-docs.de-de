---
title: Verwalten des Ladens von Projekten in einer Projektmappe | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 21cd5e7e557e795db49aea7a14e8e4cc7caa0422
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702731"
---
# <a name="manage-project-loading-in-a-solution"></a>Verwalten des Ladens von Projekten in einer Projektmappe
Visual Studio-Lösungen können eine große Anzahl von Projekten enthalten. Das standardmäßige Visual Studio-Verhalten besteht darin, alle Projekte zum Zeitpunkt des Öffnens der Projektmappe in eine Projektmappe zu laden und dem Benutzer den Zugriff auf die Projekte erst zu gestatten, wenn alle Projekte abgeschlossen sind. Wenn der Prozess des Ladens des Projekts länger als zwei Minuten dauert, wird eine Fortschrittsleiste angezeigt, die die Anzahl der geladenen Projekte und die Gesamtzahl der Projekte anzeigt. Der Benutzer kann Projekte entladen, während er in einer Projektmappe mit mehreren Projekten arbeitet, aber dieses Verfahren hat einige Nachteile: Die entladenen Projekte werden nicht als Teil eines Befehls "Projektmappe neu erstellen" erstellt, und IntelliSense-Beschreibungen von Typen und Mitgliedern geschlossener Projekte werden nicht angezeigt.

 Entwickler können die Ladezeiten von Lösungen reduzieren und das Ladeverhalten von Projekten verwalten, indem sie einen Lösungslast-Manager erstellen. Der Projektmappenlast-Manager kann sicherstellen, dass Projekte geladen werden, bevor ein Hintergrundbuild gestartet wird, das Laden im Hintergrund verzögert, bis andere Hintergrundaufgaben abgeschlossen sind, und andere Aufgaben zur Projektlastverwaltung ausführen.

## <a name="create-a-solution-load-manager"></a>Erstellen eines Lösungslast-Managers
 Entwickler können einen Lösungslastmanager erstellen, indem sie Visual Studio implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> und darauf hinraten, dass der Lösungslast-Manager aktiv ist.

### <a name="activate-a-solution-load-manager"></a>Aktivieren eines Lösungslastmanagers
 Visual Studio lässt nur einen Lösungslast-Manager zu einem bestimmten Zeitpunkt zu, daher müssen Sie Visual Studio informieren, wenn Sie den Lösungslast-Manager aktivieren möchten. Wenn ein zweiter Lösungslastmanager später aktiviert wird, wird die Verbindung zum Lastmanager der Lösung getrennt.

 Sie müssen <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> den Dienst abrufen und die [__VSPROPID4 festlegen. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) Unterkunft:

```csharp
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;
object objLoadMgr = this;   //the class that implements IVsSolutionManager
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);
```

 Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> Methode wird entweder aufgerufen, wenn Visual Studio heruntergefahren wird, oder wenn ein <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> anderes Paket als aktiver Lösungslade-Manager übernommen wurde, indem sie mit dem __VSPROPID4 aufgerufen [wird. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) Eigenschaft.

#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Strategien für verschiedene Arten von Lösungslastmanagern
 Je nach Denkprogrammtypen können Sie Lösungslastmanager auf unterschiedliche Weise implementieren, je nachdem, welche Lösungstypen sie verwalten sollen.

 Wenn der Lösungslastmanager die Projektierung im Allgemeinen verwalten soll, kann er als Teil eines VSPackage implementiert werden. Das Paket sollte auf autoload <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> gesetzt werden, indem das <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>auf dem VSPackage mit dem Wert hinzugefügt wird. Der Lösungslastmanager kann dann <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> in der Methode aktiviert werden.

> [!NOTE]
> Weitere Informationen zum automatischen Laden von Paketen finden Sie unter [Laden von VSPackages](../extensibility/loading-vspackages.md).

 Da Visual Studio nur den zuletzt zu aktivierenden Lösungslastmanager erkennt, sollten allgemeine Lösungslastmanager immer erkennen, ob ein vorhandener Lastmanager vorhanden ist, bevor Sie sich selbst aktivieren. Wenn `GetProperty()` Sie den Lösungsdienst für [__VSPROPID4 aufrufen. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) `null`gibt es keinen aktiven Lösungslast-Manager. Wenn null nicht zurückgegeben wird, überprüfen Sie, ob das Objekt mit dem Lastmanager der Lösung identisch ist.

 Wenn der Lösungslast-Manager nur wenige Lösungstypen verwalten soll, kann das VSPackage Lösungslastereignisse abonnieren (durch Aufrufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>), und den Ereignishandler verwenden, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> um den Lösungslast-Manager zu aktivieren.

 Wenn der Lösungslastmanager nur bestimmte Lösungen verwalten soll, können die Aktivierungsinformationen <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> als Teil der Lösungsdatei beibehalten werden, indem der Abschnitt vor der Lösung aufgerufen wird.

 Bestimmte Lösungslastmanager sollten sich <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> selbst im Ereignishandler deaktivieren, um nicht mit anderen Lösungslastmanagern in Konflikt zu geraten.

 Wenn Sie einen Projektmappen-Last-Manager nur benötigen, um globale Projektlasteigenschaften beizubehalten (z. B. Eigenschaften, die auf einer Optionsseite festgelegt sind), können Sie den Projektmappenlast-Manager im <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> Ereignishandler aktivieren, die Einstellung in den Lösungseigenschaften beibehalten und dann den Projektmappenlast-Manager deaktivieren.

## <a name="handle-solution-load-events"></a>Behandeln von Lösungslastereignissen
 Um Lösungsladeereignisse zu <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> abonnieren, rufen Sie an, wenn Sie den Lastmanager der Lösung aktivieren. Wenn Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>implementieren, können Sie auf Ereignisse reagieren, die sich auf unterschiedliche Projektladeeigenschaften beziehen.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: Dieses Ereignis wird ausgelöst, bevor eine Lösung geöffnet wird.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: Dieses Ereignis wird ausgelöst, nachdem die Projektmappe vollständig geladen wurde, aber bevor das Laden des Hintergrundprojekts erneut beginnt.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: Dieses Ereignis wird ausgelöst, nachdem eine Lösung zunächst vollständig geladen wurde, unabhängig davon, ob ein Lösungslade-Manager vorhanden ist oder nicht. Es wird auch nach Hintergrundlast oder Bedarfslast ausgelöst, wenn die Lösung vollständig geladen wird. Gleichzeitig <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> wird reaktiviert.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: Dieses Ereignis wird vor dem Laden eines Projekts (oder VonProjekten) ausgelöst. Um sicherzustellen, dass andere Hintergrundprozesse abgeschlossen werden, bevor die Projekte geladen werden, legen Sie auf `pfShouldDelayLoadToNextIdle` **true**fest.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: Dieses Ereignis wird ausgelöst, wenn ein Projektstapel geladen werden soll. Wenn `fIsBackgroundIdleBatch` dies zutrifft, sollen die Projekte im Hintergrund geladen werden; Wenn `fIsBackgroundIdleBatch` false ist, werden die Projekte aufgrund einer Benutzeranforderung synchron geladen, z. B. wenn der Benutzer ein ausstehendes Projekt im Projektmappen-Explorer erweitert. Sie können dieses Ereignis verarbeiten, um teure Arbeiten <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>zu erledigen, die andernfalls in ausgeführt werden müssten.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: Dieses Ereignis wird ausgelöst, nachdem ein Projektstapel geladen wurde.

## <a name="detect-and-manage-solution-and-project-loading"></a>Erkennen und Verwalten von Projektmappen und Projektladungen
 Um den Ladezustand von Projekten und <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> Lösungen zu erkennen, rufen Sie die folgenden Werte auf:

- [__VSPROPID4. VSPROPID_IsSolutionFullyLoaded](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsSolutionFullyLoaded>) `var` : `true` gibt zurück, wenn die Projektmappe und alle ihre Projekte andernfalls geladen `false`werden.

- [__VSPROPID4. VSPROPID_IsInBackgroundIdleLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInBackgroundIdleLoadProjectBatch>) `var` : `true` Gibt zurück, wenn derzeit ein Projektstapel `false`im Hintergrund geladen wird, andernfalls .

- [__VSPROPID4. VSPROPID_IsInSyncDemandLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInSyncDemandLoadProjectBatch>) `var` : `true` Gibt zurück, wenn ein Projektbatch derzeit aufgrund eines Benutzerbefehls oder `false`einer anderen expliziten Last synchron geladen wird, andernfalls .

- [__VSPROPID2. VSPROPID_IsSolutionClosing](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2.VSPROPID_IsSolutionClosing>) `var` : `true` kehrt zurück, wenn die `false`Lösung gerade geschlossen wird, andernfalls .

- [__VSPROPID. VSPROPID_IsSolutionOpening](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID.VSPROPID_IsSolutionOpening>) `var` : `true` Gibt zurück, wenn eine `false`Lösung gerade geöffnet wird, andernfalls .

Sie können auch sicherstellen, dass Projekte und Lösungen geladen werden, indem Sie eine der folgenden Methoden aufrufen:

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: Wenn Sie diese Methode aufrufen, werden die Projekte in einer Projektmappe geladen, bevor die Methode zurückgegeben wird.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: Wenn Sie diese `guidProject` Methode aufrufen, werden die Projekte geladen, bevor die Methode zurückgegeben wird.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: Wenn sie diese `guidProjectID` Methode aufruft, wird das Projekt geladen, bevor die Methode zurückgegeben wird.

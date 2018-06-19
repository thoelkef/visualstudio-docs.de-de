---
title: Arbeitsbereich Datei Kontexte in Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 7aaa0e65-f492-49ea-a845-35bd14910ca7
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: cdb013bb10c72041b03fce43e115806ecb3faeac
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31146350"
---
# <a name="workspace-file-contexts"></a>Arbeitsbereich Datei Kontexte

Alle Erkenntnisse [Ordner öffnen](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) Arbeitsbereiche werden von "Datei Kontext Anbieter", implementieren, erzeugt der <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> Schnittstelle. Diese Erweiterungen möglicherweise nach Mustern in Ordnern suchen oder Dateien, Lesen von Dateien von MSBuild und Makefiles, erkennen paketabhängigkeiten usw. zum Sammeln der Einsichten, die sie benötigen, um einen Kontext definieren. Ein Kontext selbst führt keine eingreifen, sondern bietet Daten, denen eine andere Erweiterung klicken Sie dann auf bearbeiten können.

Jede <xref:Microsoft.VisualStudio.Workspace.FileContext> verfügt über eine `Guid` zugeordnet, der den Typ der Daten identifiziert er ausführt. Ein Arbeitsbereich verwendet dieses `Guid` später, um es mit der Erweiterung übereinstimmen, die die Daten durch Nutzen der <xref:Microsoft.VisualStudio.Workspace.FileContext.Context> Eigenschaft. Eine Datei Kontextanbieter mit Metadaten, durch welche Dateikontext identifiziert exportiert `Guid`s können sie Daten für erzeugt.

Sobald definiert, kann ein Kontext eine beliebige Anzahl von Dateien oder Ordner im Arbeitsbereich zugeordnet werden. Bestimmte Dateien oder Ordner kann eine beliebige Anzahl von Kontexten Datei zugeordnet werden. Es ist eine m: n-Beziehung.

Die häufigsten Szenarien für die Datei Kontexte beziehen sich erstellen, Debuggen und Dienste für Sprachen. Weitere Informationen finden Sie unter den anderen Themen im Zusammenhang mit diesen Szenarien.

## <a name="file-context-lifecycle"></a>Datei-Kontext-Lebenszyklus

Lebenszyklen für eine `FileContext` sind nicht deterministisch. Zu jedem Zeitpunkt kann eine Komponente für einen Satz mit Kontexttypen asynchron anfordern. Anbieter, die eine Teilmenge der die Anforderung Kontexttypen unterstützen abgefragt werden. Die `IWorkspace` Instanz fungiert als die mittleren-Man zwischen dem Kunden und Anbieter über das <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> Methode. Consumer können einen Anforderungskontext und führen Sie eine kurzfristige Aktion, die auf Grundlage des Kontexts, während andere möglicherweise einen Anforderungskontext und einen langlebiges Verweis beibehalten. 

Änderungen können auf Dateien auftreten, die dazu führen, einen Kontext dass veraltet. Der Anbieter kann auf ein Ereignis auslösen der `FileContext` Updates Verbraucher darüber informieren. Beispielsweise kann wird ein buildkontext für eine Datei bereitgestellt, aber eine Änderung auf dem Datenträger werden diesem Kontext ungültig, klicken Sie dann die ursprüngliche Producer das Ereignis aufrufen. Verweisen Sie immer noch auf Consumer `FileContext` können dann für einen neuen requery `FileContext`.

>[!NOTE]
>Es gibt keine Pushmodell für Consumer. Consumer nicht neu eines Anbieters benachrichtigt werden `FileContext` nach ihrer Anforderung.

## <a name="expensive-file-context-computations"></a>Teure Datei Kontext Berechnungen

Dateiinhalte vom Datenträger lesen, können speicherintensiv sein, insbesondere, wenn ein Anbieter die Beziehung zwischen Dateien auflösen muss. Z. B. ein Anbieter kann für einige Quelldatei Dateikontext abgefragt werden, aber der Kontext ist abhängig von Metadaten aus einer Projektdatei. Analysieren die Projektdatei oder Evaluieren MSBuild ist kostspielig. Stattdessen kann die Erweiterung exportieren ein `IFileScanner` erstellen `FileDataValue` Daten während der Indizierung Arbeitsbereich. Jetzt Wenn Sie gefragt werden für den Kontext der Datei, die `IFileContextProvider` können für diese indizierte Daten schnell Abfragen. Weitere Informationen zu indizieren, finden Sie unter der [Arbeitsbereich Indizierung](workspace-indexing.md) Thema.

>[!WARNING]
>Seien Sie bei anderen Arten der `FileContext` möglicherweise aufwendig zu berechnen. Einige UI Interaktionen sind synchron, abhängig ist, eine große Anzahl `FileContext` Anforderungen. Beispiele für eine Registerkarte "Editor" öffnen und eine **Projektmappen-Explorer** Kontextmenü. Diese Aktionen stellen viele buildkontext Anforderungen geben.

## <a name="file-context-related-apis"></a>Verknüpfte Datei APIs

- <xref:Microsoft.VisualStudio.Workspace.FileContext> enthält Daten und Metadaten.
- <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> und <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider`1> den Dateikontext zu erstellen.
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextProviderAttribute> exportiert eine Datei Kontextanbieter.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> für Consumer dient zum Abrufen der Datei Kontexten.
- <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes> definiert die Build-Kontexttypen, die belegt Ordner öffnen.

## <a name="file-context-actions"></a>Kontext-Datei-Aktionen

Während einer `FileContext` selbst nur die Daten zu einigen Datei(en) ist ein <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> lässt sich express und wirken sich auf die Daten. `IFileContextAction` ist flexibel in ihre Nutzung. Zwei der am häufigsten vorkommenden Fälle sind erstellen Debuggen und.

## <a name="reporting-progress"></a>Fortschrittsbericht

Die <xref:Microsoft.VisualStudio.Workspace.IFileContextActionBase.ExecuteAsync%2A> -Methode übergeben `IProgress<IFileContextActionProgressUpdate>`, aber das Argument darf nicht als dieses Typs verwendet werden. `IFileContextActionProgressUpdate` ist eine leere Schnittstelle, und das Ergebnis `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` lösen möglicherweise `NotImplementedException`. Stattdessen die `IFileContextAction` muss das Argument in einen anderen Typ nach Bedarf für das Szenario umgewandelt.

Informationen hinsichtlich der Arten von Visual Studio bereitgestellte finden Sie in der Dokumentation des jeweiligen Szenarios.

## <a name="file-context-action-related-apis"></a>Datei Kontext Aktion bezogene APIs

- <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> führt einige Verhalten auf Basis einer `FileContext`.
- <xref:Microsoft.VisualStudio.Workspace.IFileContextActionProvider> erstellt Instanzen von `IFileContextAction`.
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextActionProviderAttribute> den Typ exportiert `IWorkspaceProviderFactory<IFileContextActionProvider>`.

## <a name="file-watching"></a>Dateien überwachen

Ein Arbeitsbereich Lauscht auf dateiänderungsbenachrichtigungen und stellt die <xref:Microsoft.VisualStudio.Workspace.IFileWatcherService> über <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A>. Dateien mit der Einstellung "ExcludedItems" übereinstimmt, gibt keine Benachrichtigungsereignisse Datei zurück. Zur Vereinfachung der Benachrichtigung und doppelte Verringerung wird ein Schwellenwert zwischen Ereignissen verwendet. Sie müssen auf eine Änderung an einer Datei zu reagieren, sollten Sie diesen Dienst abonnieren.

>[!TIP]
>Eines Arbeitsbereichs [Indexdienst](workspace-indexing.md) standardmäßig Ereignisse abonniert. Hinzufügen von Dateien und Änderungen führt dazu, dass relevante `IFileScanner`s Ereignisse für neue Daten für diese Datei aufgerufen werden. Datei löschen entfernt volltextindizierten Daten. Sie müssen nicht abonnieren Ihrer `IFileScanner` an den Dateidienst-Watcher.

## <a name="next-steps"></a>Nächste Schritte

* [Indizierung](workspace-indexing.md) -Arbeitsbereich Indizierung erfasst und behält die Informationen über den Arbeitsbereich ".
* [Arbeitsbereiche](workspaces.md) -Arbeitsbereich Konzepte und einstellungsspeicher überprüfen.

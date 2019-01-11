---
title: Arbeitsbereich dateikontexte in Visual Studio | Microsoft-Dokumentation
ms.date: 02/21/2018
ms.topic: conceptual
ms.assetid: 7aaa0e65-f492-49ea-a845-35bd14910ca7
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 93690eab989cee62d756a774675bf1d46da017fb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53826863"
---
# <a name="workspace-file-contexts"></a>Arbeitsbereich dateikontexte

Alle Einblicke in ["Ordner öffnen"](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) Arbeitsbereiche werden erstellt, von "Kontext dateianbieter", die implementieren die <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> Schnittstelle. Diese Erweiterungen können Suchen Sie nach Mustern in Ordnern oder Dateien, und Lesen von Dateien von MSBuild und Makefiles, erkennen paketabhängigkeiten usw. zum Sammeln der Erkenntnisse zu gewinnen, müssen sie einen Kontext definieren. Ein Kontext selbst führt keine Maßnahmen, sondern bietet Daten, denen eine andere Erweiterung klicken Sie dann auf bearbeiten können.

Jede <xref:Microsoft.VisualStudio.Workspace.FileContext> verfügt über eine `Guid` zugeordnet, der den Typ der Daten bezeichnet. es enthält. Ein Arbeitsbereich verwendet diese `Guid` später, um es mit Erweiterungen übereinstimmen, die Daten durch nutzen, der <xref:Microsoft.VisualStudio.Workspace.FileContext.Context> Eigenschaft. Ein Kontext dateianbieter mit Metadaten, die die Dateikontext identifiziert exportiert wird `Guid`s können sie Daten für erzeugt.

Nachdem definiert, kann ein Kontext eine beliebige Anzahl von Dateien oder Ordner im Arbeitsbereich zugeordnet werden. Eine Datei oder Ordner kann eine beliebige Anzahl von dateikontexte zugeordnet werden. Es ist eine m: n Beziehung.

Die häufigsten Szenarien für dateikontexte beziehen sich auf Build-, Debug- und Sprachdienste. Weitere Informationen finden Sie unter den anderen Themen im Zusammenhang mit diesen Szenarien.

## <a name="file-context-lifecycle"></a>Datei-Kontext-Lebenszyklus

Lebenszyklen für das ein `FileContext` sind nicht deterministisch. Zu jedem Zeitpunkt kann eine Komponente für eine Gruppe von der Kontexttypen asynchron anfordern. Anbieter, die eine Teilmenge von der Kontexttypen Anforderung unterstützen werden abgefragt. Die `IWorkspace` -Instanz fungiert als mittelsmann zwischen dem Consumer und Anbieter über die <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> Methode. Consumer möglicherweise einen Anforderungskontext und führen Sie eine kurzfristige Aktion, die auf Grundlage des Kontexts, während andere möglicherweise eine Anforderungskontext und langlebig verweisen. 

Änderungen können Dateien auftreten, die dazu führen, einen Kontext dass veraltet. Der Anbieter kann ein Ereignis auslösen, auf die `FileContext` Consumer von Updates benachrichtigt. Beispielsweise kann wird ein buildkontext für eine Datei bereitgestellt, aber eine Änderung auf dem Datenträger wird diesem Kontext ungültig, klicken Sie dann der ursprüngliche Producer das Ereignis aufrufen. Verweisen Sie immer noch auf Consumer `FileContext` kann dann für einen neuen requery `FileContext`.

>[!NOTE]
>Es gibt keine Push-Modell für Kunden. Consumer nicht informiert, eines Anbieters für die neue `FileContext` nach ihrer Anforderung.

## <a name="expensive-file-context-computations"></a>Teure Datei Kontext Berechnungen

Lesen von Dateiinhalt vom Datenträger können speicherintensiv sein, insbesondere, wenn ein Anbieter die Beziehung zwischen Dateien auflösen muss. Z. B. ein Anbieter kann für einige der Quelldatei Dateikontext abgefragt werden, aber der Kontext ist abhängig von Metadaten aus einer Projektdatei. Analysieren die Projektdatei oder MSBuild evaluieren ist teuer. Stattdessen kann die Erweiterung Exportieren einer `IFileScanner` erstellen `FileDataValue` Daten während der Indizierung Arbeitsbereich. Jetzt beim dateikontexte, aufgefordert die `IFileContextProvider` können Sie schnell Abfragen für die indizierten Daten. Weitere Informationen zur Indizierung finden Sie unter den [Arbeitsbereich Indizierung](workspace-indexing.md) Thema.

>[!WARNING]
>Achten Sie darauf, dass Sie von anderen Möglichkeiten Ihrer `FileContext` möglicherweise aufwändig zu berechnen. Einige UI-Interaktionen sind synchron und verlassen sich auf eine große Anzahl von `FileContext` Anforderungen. Beispiele hierfür sind eine Registerkarte "Editor" zu öffnen, und Öffnen einer **Projektmappen-Explorer** Kontextmenü. Diese Aktionen stellen viele buildkontext Anforderungen geben.

## <a name="file-context-related-apis"></a>Dateikontext beziehen APIs.

- <xref:Microsoft.VisualStudio.Workspace.FileContext> enthält Daten und Metadaten.
- <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> und <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider`1> den Kontext zu erstellen.
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextProviderAttribute> exportiert eine Datei Kontextanbieter.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> wird für Verbraucher verwendet, um dateikontexte zu erhalten.
- <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes> definiert die Build-Kontexttypen, die belegt "Ordner öffnen".

## <a name="file-context-actions"></a>Datei kontextaktionen

Während einer `FileContext` selbst ist nur Daten über einige Dateien, eine <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> ist eine Möglichkeit, express, und mit diesen Daten. `IFileContextAction` ist die Nutzung flexibel. Zwei der am häufigsten vorkommenden Fälle erstellen-Debuggen und.

## <a name="reporting-progress"></a>Statusmeldung

Die <xref:Microsoft.VisualStudio.Workspace.IFileContextActionBase.ExecuteAsync%2A> -Methode übergeben `IProgress<IFileContextActionProgressUpdate>`, aber das Argument darf nicht als dieses Typs verwendet werden. `IFileContextActionProgressUpdate` ist eine leere Schnittstelle und den Aufruf `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` löst möglicherweise `NotImplementedException`. Stattdessen die `IFileContextAction` muss das Argument in einen anderen Typ je nach Bedarf für das Szenario umgewandelt.

Informationen zu den Arten von Visual Studio bereitgestellt werden finden Sie in das entsprechende Szenario-Dokumentation.

## <a name="file-context-action-related-apis"></a>Dateikontextaktion beziehen APIs.

- <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> führt einige Verhalten basierend auf einer `FileContext`.
- <xref:Microsoft.VisualStudio.Workspace.IFileContextActionProvider> erstellt Instanzen von `IFileContextAction`.
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextActionProviderAttribute> den Typ exportiert `IWorkspaceProviderFactory<IFileContextActionProvider>`.

## <a name="file-watching"></a>Überwachung von Dateien

Ein Arbeitsbereich Lauscht auf dateiänderungsbenachrichtigungen und stellt die <xref:Microsoft.VisualStudio.Workspace.IFileWatcherService> über <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A>. Dateien, die mit der Einstellung "ExcludedItems" übereinstimmt, werden nicht Benachrichtigungsereignisse Datei erstellt. Ein Schwellenwert zwischen Ereignissen dient zur Vereinfachung der Benachrichtigung und doppelte Verringerung. Wenn Sie auf eine dateiänderung reagieren müssen, sollten Sie diesen Dienst abonnieren.

>[!TIP]
>Des Arbeitsbereichs [Indexdienst](workspace-indexing.md) standardmäßig Ereignisse abonniert. Dateihinzufügungen und Änderungen führt dazu, dass relevante `IFileScanner`s-Ereignisse für neue Daten für diese Datei aufgerufen werden. Datei löschen entfernt die indizierte Daten. Sie müssen nicht abonnieren Ihre `IFileScanner` an den Datei-Watcher-Dienst.

## <a name="next-steps"></a>Nächste Schritte

* [Indizierung](workspace-indexing.md) -Indizierung Arbeitsbereich erfasst und Informationen zum Arbeitsbereich beibehalten.
* [Arbeitsbereiche](workspaces.md) -überprüfen Sie die Arbeitsbereich-Konzepte und einstellungsspeicher.

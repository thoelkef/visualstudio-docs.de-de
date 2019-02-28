---
title: Diagnose von Grafiken | Microsoft-Dokumentation
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics
ms.assetid: fa69c550-62a7-41b5-bb1f-7eb04af1a6e8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cbc3edfabe041804a632b919eff4e565be9cc5e3
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56703031"
---
# <a name="visual-studio-graphics-diagnostics"></a>Visual Studio-Grafikdiagnose
Visual Studio*Grafikdiagnose* ist ein Satz von Tools zum Aufzeichnen, und klicken Sie dann Analysieren von Rendering- und Leistungsproblemen in Direct3D-apps. Die Grafikdiagnose kann für Apps verwendet werden, die lokal auf Ihrem Windows-PC, in einem Windows-Geräteemulator oder auf einem Remotecomputer oder-gerät ausgeführt werden.

 Der Grafikdiagnose-Workflow beginnt mit der Erfassung eines Datensatzes zur Verwendung von Direct3D durch Ihre App – live, während der Ausführung –, damit das Verhalten sofort analysiert, freigegeben oder für die spätere Nutzung gespeichert werden kann. Erfassungssitzungen können und verwaltet werden initiiert manuell aus Visual Studio oder mit dem Befehlszeilen-Erfassungstool **dxcap.exe**. Erfassungssitzungen können auch initiiert und programmgesteuert mithilfe der Grafikdiagnose-erfassungs-APIs gesteuert werden.

 Nachdem eine Erfassungssitzung aufgezeichnet wurde, kann der Inhalt der *Visual Studio-Grafikanalyse* zu einem beliebigen Zeitpunkt wiedergegeben werden, wobei die aufgezeichneten Frames durch genau dieselben Ressourcen neu erstellt und die von der App verwendeten Befehle gerendert werden. Anschließend können mit den Tools im Grafikanalyse-Fenster, alle aufgezeichneten Frames im Detail analysiert werden. Diese Tools können verwendet werden, um Direct3D-API-Aufrufe, Ressourcen, Pipelinezustandsobjekte, Pipelinestufen oder sogar den vollständigen Verlauf jedes Pixels in einem erfassten Frame zu untersuchen. Durch die kombinierte Verwendung dieser Tools kann ein Renderingproblem intuitiv untersucht werden, beginnend bei der Anzeige in einem erfassten Frame bis zu den Grundursachen in Quellcode, Shadern oder Grafikressourcen der App.

 Sie können einen erfassten Frame mithilfe des Tools *Frame-Analyse* analysieren, um Leistungsprobleme zu diagnostizieren. Das Tool ermittelt, ob ein Potenzial zur Leistungsoptimierung vorhanden ist, indem es automatisch die Art und Weise ändert, in der die App Direct3D verwendet, und Vergleichstests zu allen Varianten ausführt. In der Vergangenheit haben Sie diese Änderungen möglicherweise manuell vorgenommen und die Ergebnisse gemessen, um herauszufinden, welche Unterschiede auftreten. Mit Frame-Analyse müssen Sie nur noch die Änderungen vornehmen, von denen Sie wissen, dass sie sich auszahlen.

 Grafikdiagnose hilft Ihnen, Aussehen und Funktion einer grafisch aufwendigen Direct3D-App zu optimieren.

 Weiterhin [Übersicht](overview-of-visual-studio-graphics-diagnostics.md) erfahren Sie, was Visual Studio Grafikdiagnose bietet.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Übersicht über die](overview-of-visual-studio-graphics-diagnostics.md) führt die Grafikdiagnose-Workflow und Tools.

 [Erste Schritte](getting-started-with-visual-studio-graphics-diagnostics.md) In diesem Abschnitt erfahren Sie wie Visual Studio-Grafikdiagnose installieren und starten Sie mithilfe der Grafikdiagnose mit der Direct3D-app.

 [Erfassen von Grafikinformationen](capturing-graphics-information.md) um die Grafikdiagnose verwenden, um ein Renderingproblem in Ihrer app zu untersuchen, zeichnen Sie zuerst Informationen darüber, wie die app DirectX verwendet. In der Aufzeichnungssitzung, während der Ihre App normal ausgeführt wird, können Sie die gewünschten Frames *aufzeichnen*, d. h. auswählen. Die Aufzeichnungen enthalten ausführliche Informationen darüber, wie die Frames gerendert werden. Sie können die aufgezeichneten Informationen als Grafikprotokolldokument speichern, um sie später zu untersuchen oder für andere Teammitglieder freizugeben.

 [GPU-Nutzung](gpu-usage.md) zur profilerstellung Ihrer app die Grafikdiagnose verwenden, verwenden Sie das Tool GPU-Nutzung. Die GPU-Auslastung kann zusammen mit anderen Tools zur Profilerstellung, z. B. CPU-Nutzung, verwendet werden, um einen Zusammenhang zwischen CPU- und GPU-Aktivität und daraus resultierenden Leistungsproblemen in Ihrer App herzustellen.

 [Grafikprotokolldokument](graphics-log-document.md) um die Untersuchung eines aufgezeichneten grafikprotokolls zu starten, können Sie die Dokumentfenster "Grafikprotokolle" einen aufgezeichneten Frame ausgewählt haben – oder sogar ein bestimmtes Pixel –, damit Sie untersuchen können, im Detail die *Ereignisse* (die ist die DirectX-API-Aufrufe), die Auswirkung darauf.

 [Frame-Analyse](graphics-frame-analysis.md) Sie Grafikframe-Analyse, nachdem Sie einen Frame ausgewählt haben, um zu untersuchen und optimieren Ihre Renderingleistung verwenden.

 [Ereignisliste](graphics-event-list.md) , nachdem Sie einen Frame ausgewählt haben, verwenden Sie die **Graphics Event List** untersuchen die Ereignisse aus, um zu bestimmen, ob sie mit dem Renderingproblem zusammenhängen.

 [Status](graphics-state.md) das Statusfenster hilft Ihnen der Status der Grafik zu verstehen, die zum Zeitpunkt des aktuellen Ereignisses aktiv ist.

 [Pipelinestufen](graphics-pipeline-stages.md) In die **Grafikpipelinestufen** Fenster, Sie untersuchen, wie das aktuell ausgewählte Ereignis einzelnen Stufen der Grafikpipeline verarbeitet wird, sodass Sie, wo erkennen können das Renderingproblem zuerst wird angezeigt. Die Untersuchung der Pipelinephasen ist besonders hilfreich, wenn ein Objekt aufgrund einer falschen Transformation nicht angezeigt wird, oder wenn eine der Stufen eine Ausgabe erzeugt, die nicht mit der in der nächsten Phase erwarteten Ausgabe übereinstimmt.

 [Aufrufliste](graphics-event-call-stack.md) Sie verwenden die **Aufrufliste des Grafikereignisses** die Aufrufliste des aktuell ausgewählten Ereignisses zu untersuchen, sodass Sie app-Code navigieren können, die mit dem Renderingproblem zusammenhängt.

 [Pixelverlauf](graphics-pixel-history.md) mithilfe der **Grafikpixelverlauf** Fenster zu analysieren, wie das derzeit ausgewählte Pixel von den Ereignissen auswirken, die beeinflusst, Sie können das Ereignis oder eine Kombination von Ereignissen, die dazu führen, bestimmte dass identifizieren Arten von Renderingproblemen. Der Pixelverlauf ist besonders hilfreich, wenn ein Objekt falsch gerendert wird, da entweder die Ausgabe des Pixel-Shaders falsch ist oder falsch mit dem Framepuffer kombiniert wurde. Der Pixelverlauf ist ebenfalls aufschlussreich, wenn ein Objekt gar nicht angezeigt wird, da seine Pixel verworfen wurden, bevor sie den Framepuffer erreicht haben.

 [Objekttabelle](graphics-object-table.md) Sie verwenden die **Grafikobjekttabelle** , überprüfen Sie die Eigenschaften und Inhalte bestimmter Direct3D-Objekte und Ressourcen, die für das aktuell ausgewählte Ereignis in Kraft sind. Die Objekttabelle unterstützt Sie bei der Ermittlung des Grafikgerätekontexts, der während eines Ereignisses aktiv ist, und bei der Untersuchung von Inhalten aus Grafikressourcen, wie Konstantenpuffer, Vertexpuffer und Texturen.

 [HLSL-Debugger](hlsl-shader-debugger.md) um untersuchen, wie der Shader-Code für das aktuell ausgewählte Ereignis grafikpipelinestufe und verhält, verwenden Sie die **HLSL-Debugger** um den Code schrittweise durchlaufen, untersuchen Sie den Inhalt von Variablen, und führen Sie andere typische Debugaufgaben. Mit dem HLSL-Debugger können Sie auch den Compute-Shader-Code unabhängig davon untersuchen, ob die Ergebnisse weiter durch die Grafikpipeline verarbeitet oder nur von der Anwendung eingelesen werden.

 [Befehlszeilen-Erfassungs-Tool](command-line-capture-tool.md) verwenden Sie das Befehlszeilen-erfassungs-Tool, um schnell erfassen und Grafikinformationen ohne Verwendung von Visual Studio oder programmgesteuerter Erfassung wiederzugeben. Insbesondere können Sie das Befehlszeilen-Erfassungstool für die Automatisierung oder in einer Testumgebung verwenden.

 [Beispiele für](graphics-diagnostics-examples.md) mehrere Beispiele veranschaulichen, wie die grafikdiagnosetools gemeinsam zu verwenden, um verschiedene Arten von Renderingprobleme zu diagnostizieren.

## <a name="related-sections"></a>Verwandte Abschnitte

| Titel | Beschreibung |
| - | - |
| [Debugger – Featuretour](/visualstudio/debugger/debugger-feature-tour) | Stellt die Debuggingfunktionen in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vor. |
| [DirectX-Grafiken und -Spiele](http://go.microsoft.com/fwlink/?LinkId=256498) | Enthält Artikel, in denen die DirectX-Grafiktechnologien erläutert werden. |

---
title: Grafik Diagnose | Microsoft-Dokumentation
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
ms.openlocfilehash: e69d88bb5764836d82232cec26606009eaf694d7
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2019
ms.locfileid: "73187738"
---
# <a name="visual-studio-graphics-diagnostics"></a>Visual Studio-Grafikdiagnose
Visual Studio*Grafikdiagnose* ist eine Reihe von Tools zum Aufzeichnen und anschließenden Analysieren von Rendering-und Leistungsproblemen in Direct3D-apps. Die Grafikdiagnose kann für Apps verwendet werden, die lokal auf Ihrem Windows-PC, in einem Windows-Geräteemulator oder auf einem Remotecomputer oder-gerät ausgeführt werden.

 Der Grafikdiagnose-Workflow beginnt mit der Erfassung eines Datensatzes zur Verwendung von Direct3D durch Ihre App – live, während der Ausführung –, damit das Verhalten sofort analysiert, freigegeben oder für die spätere Nutzung gespeichert werden kann. Erfassungs Sitzungen können manuell von Visual Studio oder mit dem Befehlszeilen-Erfassungs Tool **dxcap. exe**initiiert und gesteuert werden. Erfassungs Sitzungen können auch Programm gesteuert mithilfe der Grafikdiagnose Capture-APIs initiiert und gesteuert werden.

 Nachdem eine Erfassungssitzung aufgezeichnet wurde, kann der Inhalt der *Visual Studio-Grafikanalyse* zu einem beliebigen Zeitpunkt wiedergegeben werden, wobei die aufgezeichneten Frames durch genau dieselben Ressourcen neu erstellt und die von der App verwendeten Befehle gerendert werden. Mithilfe der im grafikanalyse Fenster bereitgestellten Tools können alle aufgezeichneten Frames ausführlich analysiert werden. Diese Tools können verwendet werden, um Direct3D-API-Aufrufe, Ressourcen, Pipelinezustandsobjekte, Pipelinestufen oder sogar den vollständigen Verlauf jedes Pixels in einem erfassten Frame zu untersuchen. Durch die kombinierte Verwendung dieser Tools kann ein Renderingproblem intuitiv untersucht werden, beginnend bei der Anzeige in einem erfassten Frame bis zu den Grundursachen in Quellcode, Shadern oder Grafikressourcen der App.

 Sie können einen erfassten Frame mithilfe des Tools *Frame-Analyse* analysieren, um Leistungsprobleme zu diagnostizieren. Das Tool ermittelt, ob ein Potenzial zur Leistungsoptimierung vorhanden ist, indem es automatisch die Art und Weise ändert, in der die App Direct3D verwendet, und Vergleichstests zu allen Varianten ausführt. In der Vergangenheit haben Sie diese Änderungen möglicherweise manuell vorgenommen und die Ergebnisse gemessen, um herauszufinden, welche Unterschiede auftreten. Mit Frame-Analyse müssen Sie nur noch die Änderungen vornehmen, von denen Sie wissen, dass sie sich auszahlen.

 Grafikdiagnose hilft Ihnen, Aussehen und Funktion einer grafisch aufwendigen Direct3D-App zu optimieren.

 Weitere Informationen zu den Funktionen von Visual Studio Grafikdiagnose finden Sie weiter in der [Übersicht](overview-of-visual-studio-graphics-diagnostics.md) .

## <a name="in-this-section"></a>In diesem Abschnitt
 [Übersicht](overview-of-visual-studio-graphics-diagnostics.md) Führt die Grafikdiagnose Workflow und die Tools ein.

 [Einstieg](getting-started-with-visual-studio-graphics-diagnostics.md) In diesem Abschnitt erfahren Sie, wie Sie Visual Studio Grafikdiagnose installieren und Grafikdiagnose mit ihrer Direct3D-App verwenden.

 [Erfassen von Grafik Informationen](capturing-graphics-information.md) Wenn Sie Grafikdiagnose zum Überprüfen eines renderingproblems in Ihrer APP verwenden möchten, zeichnen Sie zuerst Informationen darüber auf, wie DirectX von der APP verwendet wird. In der Aufzeichnungssitzung, während der Ihre App normal ausgeführt wird, können Sie die gewünschten Frames *aufzeichnen*, d. h. auswählen. Die Aufzeichnungen enthalten ausführliche Informationen darüber, wie die Frames gerendert werden. Sie können die aufgezeichneten Informationen als Grafikprotokolldokument speichern, um sie später zu untersuchen oder für andere Teammitglieder freizugeben.

 [GPU-Nutzung](../../profiling/gpu-usage.md) Verwenden Sie das GPU-Nutzungs Tool, um Grafikdiagnose für die Profilerstellung für Ihre APP zu verwenden. Die GPU-Auslastung kann zusammen mit anderen Tools zur Profilerstellung, z. B. CPU-Nutzung, verwendet werden, um einen Zusammenhang zwischen CPU- und GPU-Aktivität und daraus resultierenden Leistungsproblemen in Ihrer App herzustellen.

 [Grafik Protokoll Dokument](graphics-log-document.md) Zum Starten der Untersuchung eines aufgezeichneten Grafik Protokolls verwenden Sie das Dokument Fenster des Grafik Protokolls, um einen aufgezeichneten Frame auszuwählen – oder sogar ein bestimmtes Pixel – damit Sie die *Ereignisse* (d. h. die DirectX-API-Aufrufe), die sich darauf auswirken, ausführlich untersuchen können.

 [Frame-Analyse](graphics-frame-analysis.md) Nachdem Sie einen Frame ausgewählt haben, verwenden Sie Grafikframe-Analyse, um die Renderingleistung zu überprüfen und zu optimieren.

 [Ereignisliste](graphics-event-list.md) Nachdem Sie einen Frame ausgewählt haben, verwenden Sie die **Grafik Ereignisliste** , um die Ereignisse zu untersuchen und zu ermitteln, ob Sie mit dem Renderingproblem verknüpft sind.

 [Status](graphics-state.md) Das Statusfenster hilft Ihnen, den Grafik Zustand zu verstehen, der zum Zeitpunkt des aktuellen Ereignisses aktiv ist.

 [Pipeline Stufen](graphics-pipeline-stages.md) Im Fenster **Grafik Pipeline Stufen** untersuchen Sie, wie das aktuell ausgewählte Ereignis von den einzelnen Stufen der Grafik Pipeline verarbeitet wird, sodass Sie ermitteln können, wo das Renderingproblem zuerst auftritt. Die Untersuchung der Pipelinephasen ist besonders hilfreich, wenn ein Objekt aufgrund einer falschen Transformation nicht angezeigt wird, oder wenn eine der Stufen eine Ausgabe erzeugt, die nicht mit der in der nächsten Phase erwarteten Ausgabe übereinstimmt.

 [Ereignis aufrufsstapel](graphics-event-call-stack.md) Mithilfe der **Aufrufstapel des Grafik Ereignisses** können Sie die aufrufsstapel des aktuell ausgewählten Ereignisses untersuchen, sodass Sie zu app-Code navigieren können, der mit dem Renderingproblem zusammenhängt.

 [Pixel Verlauf](graphics-pixel-history.md) Wenn Sie das Fenster **Grafik Pixel Verlauf** verwenden, um zu analysieren, wie das aktuell ausgewählte Pixel von den Ereignissen betroffen ist, die es beeinflusst haben, können Sie das Ereignis oder die Kombination von Ereignissen ermitteln, die bestimmte Arten von Renderingproblemen auslösen. Der Pixelverlauf ist besonders hilfreich, wenn ein Objekt falsch gerendert wird, da entweder die Ausgabe des Pixel-Shaders falsch ist oder falsch mit dem Framepuffer kombiniert wurde. Der Pixelverlauf ist ebenfalls aufschlussreich, wenn ein Objekt gar nicht angezeigt wird, da seine Pixel verworfen wurden, bevor sie den Framepuffer erreicht haben.

 [Objekttabelle](graphics-object-table.md) Mithilfe der **Grafik Objekttabelle** können Sie die Eigenschaften und den Inhalt spezifischer Direct3D-Objekte und-Ressourcen untersuchen, die für das aktuell ausgewählte Ereignis gelten. Die Objekttabelle unterstützt Sie bei der Ermittlung des Grafikgerätekontexts, der während eines Ereignisses aktiv ist, und bei der Untersuchung von Inhalten aus Grafikressourcen, wie Konstantenpuffer, Vertexpuffer und Texturen.

 [HLSL-Debugger](hlsl-shader-debugger.md) Um zu überprüfen, wie sich der Shader-Code für die aktuell ausgewählte Ereignis-und Grafik Pipeline Phase verhält, verwenden Sie den **HLSL-Debugger** , um den Code schrittweise auszuführen, den Inhalt von Variablen zu überprüfen und andere typische Debuggingaufgaben auszuführen Mit dem HLSL-Debugger können Sie auch den Compute-Shader-Code unabhängig davon untersuchen, ob die Ergebnisse weiter durch die Grafikpipeline verarbeitet oder nur von der Anwendung eingelesen werden.

 [Befehlszeilen-Erfassungs Tool](command-line-capture-tool.md) Verwenden Sie das Befehlszeilen-Erfassungs Tool, um Grafik Informationen schnell zu erfassen und wiederzugeben, ohne Visual Studio oder eine programmgesteuerte Erfassung zu verwenden. Insbesondere können Sie das Befehlszeilen-Erfassungstool für die Automatisierung oder in einer Testumgebung verwenden.

 [Beispiele](graphics-diagnostics-examples.md) In den folgenden Beispielen wird veranschaulicht, wie die Grafikdiagnose Tools zur Diagnose verschiedener Arten von Renderingproblemen verwendet werden.

## <a name="related-sections"></a>Verwandte Abschnitte

| Titel | Beschreibung |
| - | - |
| [Debugger – Featuretour](../debugger-feature-tour.md) | Stellt die Debuggingfunktionen in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vor. |
| [DirectX-Grafiken und -Spiele](/windows/win32/directx) | Enthält Artikel, in denen die DirectX-Grafiktechnologien erläutert werden. |

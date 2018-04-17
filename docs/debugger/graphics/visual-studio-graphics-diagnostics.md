---
title: Visual Studio-Grafikdiagnose | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics
ms.assetid: fa69c550-62a7-41b5-bb1f-7eb04af1a6e8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1974480a2abefaaa38c05f4b1e4588eaddfd480e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="visual-studio-graphics-diagnostics"></a>Visual Studio-Grafikdiagnose
Visual Studio*Grafikdiagnose* ist ein Satz von Tools zum Aufzeichnen und anschließenden Analysieren von Rendering- und Leistungsproblemen in Direct3D-apps. Die Grafikdiagnose kann für Apps verwendet werden, die lokal auf Ihrem Windows-PC, in einem Windows-Geräteemulator oder auf einem Remotecomputer oder-gerät ausgeführt werden.  
  
 Der Grafikdiagnose-Workflow beginnt mit der Erfassung eines Datensatzes zur Verwendung von Direct3D durch Ihre App – live, während der Ausführung –, damit das Verhalten sofort analysiert, freigegeben oder für die spätere Nutzung gespeichert werden kann. Capture-Sitzungen können initiiert und gesteuert, die manuell über Visual Studio oder mit dem Befehlszeilen-Erfassungstool **dxcap.exe**. Erfassungssitzungen können auch programmgesteuert mit Grafikdiagnose-Erfassungs-APIs initiiert und gesteuert werden.  
  
 Nachdem eine erfassungssitzung aufgezeichnet wurde sein Inhalt können wiedergegeben werden von Visual Studio *Grafikanalyse* zu einem beliebigen Zeitpunkt neu erstellen die aufgezeichneten Frames durch genauen dieselben Ressourcen verwenden und das rendering Befehle der app verwendet. Anschließend können mit den Tools im Grafikanalyse-Fenster alle aufgezeichneten Frames im Detail analysiert werden. Diese Tools können verwendet werden, um Direct3D-API-Aufrufe, Ressourcen, Pipelinezustandsobjekte, Pipelinestufen oder sogar den vollständigen Verlauf jedes Pixels in einem erfassten Frame zu untersuchen. Durch die kombinierte Verwendung dieser Tools kann ein Renderingproblem intuitiv untersucht werden, beginnend bei der Anzeige in einem erfassten Frame bis zu den Grundursachen in Quellcode, Shadern oder Grafikressourcen der App.  
  
 Um Leistungsprobleme zu diagnostizieren, ein erfassten Frame analysiert werden kann, mithilfe der *Frame-Analyse* Tool. Das Tool ermittelt, ob ein Potenzial zur Leistungsoptimierung vorhanden ist, indem es automatisch die Art und Weise ändert, in der die App Direct3D verwendet, und Vergleichstests zu allen Varianten ausführt. In der Vergangenheit haben Sie diese Änderungen möglicherweise manuell vorgenommen und die Ergebnisse gemessen, um herauszufinden, welche Unterschiede auftreten. Mit Frame-Analyse müssen Sie nur noch die Änderungen vornehmen, von denen Sie wissen, dass sie sich auszahlen.  
  
 Grafikdiagnose hilft Ihnen, Aussehen und Funktion einer grafisch aufwendigen Direct3D-App zu optimieren.  
  
 Weiterhin [Übersicht](overview-of-visual-studio-graphics-diagnostics.md) Weitere Informationen zu den Visual Studio-Grafikdiagnose bietet.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Übersicht](overview-of-visual-studio-graphics-diagnostics.md)  
 Bietet eine Einführung in den Workflow und die Tools der Grafikdiagnose.  
  
 [Erste Schritte](getting-started-with-visual-studio-graphics-diagnostics.md)  
 In diesem Abschnitt erfahren Sie, wie Sie Visual Studio-Grafikdiagnose installieren und mit der Direct3D-App verwenden.  
  
 [Capturing Graphics Information](capturing-graphics-information.md)  
 Um die Grafikdiagnose zur Untersuchung eines Renderingproblems zu verwenden, zeichnen Sie zuerst Informationen darüber auf, wie die App DirectX verwendet. Während der aufzeichnungssitzung, wie Ihre app normal ausgeführt wird, Sie *erfassen* (d. h. auswählen) die Frames, die Sie interessiert sind. Die Aufzeichnungen enthalten ausführliche Informationen darüber, wie die Frames gerendert werden. Sie können die aufgezeichneten Informationen als Grafikprotokolldokument speichern, um sie später zu untersuchen oder für andere Teammitglieder freizugeben.  
  
 [GPU-Nutzung](gpu-usage.md)  
 Zur Profilerstellung Ihrer App mit der Grafikdiagnose verwenden Sie das GPU-Auslastungstool. Die GPU-Auslastung kann zusammen mit anderen Tools zur Profilerstellung, z. B. CPU-Nutzung, verwendet werden, um einen Zusammenhang zwischen CPU- und GPU-Aktivität und daraus resultierenden Leistungsproblemen in Ihrer App herzustellen.  
  
 [Grafikprotokolldokument](graphics-log-document.md)  
 Um die Prüfung eines aufgezeichneten grafikprotokolls zu starten, verwenden Sie die Grafikprotokoll-Dokumentfenster, um einen aufgezeichneten Frame ausgewählt haben – oder sogar ein bestimmtes Pixel –, damit Sie prüfen können, im Detail der *Ereignisse* (d. h. die DirectX-API-Aufrufe), die sie betreffen .  
  
 [Die Frame-Analyse](graphics-frame-analysis.md)  
 Nach der Auswahl eines Frames verwenden Sie die Grafikframe-Analyse, um Ihre Renderingleistung zu untersuchen und anzupassen.  
  
 [Ereignisliste](graphics-event-list.md)  
 Nachdem Sie einen Frame ausgewählt haben, verwenden Sie die **Grafikereignisliste** untersuchen die Ereignisse, um zu bestimmen, ob mit dem Renderingproblem zusammenhängen.  
  
 [Zustand](graphics-state.md)  
 Das Statusfenster hilft Ihnen, den während des aktuellen Ereignisses aktiven Status der Grafik zu verstehen.  
  
 [Pipelinestufen](graphics-pipeline-stages.md)  
 In der **Grafikpipelinestufen** Fenster Sie untersuchen, wie das aktuell ausgewählte Ereignis jeder Stufe der Grafikpipeline verarbeitet wird, sodass Sie feststellen können, wo das Renderingproblem zuerst angezeigt wird. Die Untersuchung der Pipelinephasen ist besonders hilfreich, wenn ein Objekt aufgrund einer falschen Transformation nicht angezeigt wird, oder wenn eine der Stufen eine Ausgabe erzeugt, die nicht mit der in der nächsten Phase erwarteten Ausgabe übereinstimmt.  
  
 [Ereignisaufrufliste](graphics-event-call-stack.md)  
 Verwenden Sie die **Aufrufliste des Grafikereignisses** die Aufrufliste des aktuell ausgewählten Ereignisses überprüfen, damit Sie app-Code navigieren können, die mit dem Renderingproblem zusammenhängt.  
  
 [Pixelverlauf](graphics-pixel-history.md)  
 Mithilfe der **Grafikpixelverlauf** Fenster zu analysieren, wie das derzeit ausgewählte Pixel von den Ereignissen auswirken, die beeinflusst, bestimmen Sie das Ereignis oder die Kombination von Ereignissen, die bestimmte Arten von Renderingprobleme verursachen. Der Pixelverlauf ist besonders hilfreich, wenn ein Objekt falsch gerendert wird, da entweder die Ausgabe des Pixel-Shaders falsch ist oder falsch mit dem Framepuffer kombiniert wurde. Der Pixelverlauf ist ebenfalls aufschlussreich, wenn ein Objekt gar nicht angezeigt wird, da seine Pixel verworfen wurden, bevor sie den Framepuffer erreicht haben.  
  
 [Objekttabelle](graphics-object-table.md)  
 Verwenden Sie die **Grafikobjekttabelle** untersuchen Sie die Eigenschaften und Inhalte bestimmter Direct3D-Objekte und Ressourcen, die für das aktuell ausgewählte Ereignis in Kraft sind. Die Objekttabelle unterstützt Sie bei der Ermittlung des Grafikgerätekontexts, der während eines Ereignisses aktiv ist, und bei der Untersuchung von Inhalten aus Grafikressourcen, wie Konstantenpuffer, Vertexpuffer und Texturen.  
  
 [HLSL-Debugger](hlsl-shader-debugger.md)  
 Um zu untersuchen, wie der Shader-Code für das aktuell ausgewählte Ereignis-grafikpipelinestufe und verhält, verwenden Sie die **HLSL-Debugger** um den Code schrittweise durchlaufen, untersuchen Sie den Inhalt von Variablen und andere typische Debugaufgaben durchführen. Mit dem HLSL-Debugger können Sie auch den Compute-Shader-Code unabhängig davon untersuchen, ob die Ergebnisse weiter durch die Grafikpipeline verarbeitet oder nur von der Anwendung eingelesen werden.  
  
 [Befehlszeilen-Erfassungstool](command-line-capture-tool.md)  
 Verwenden Sie das Befehlszeilen-Erfassungstool, umGrafikinformationen schnell aufzuzeichnen und ohne Verwendung von Visual Studio oder programmgesteuerter Erfassung wiederzugeben. Insbesondere können Sie das Befehlszeilen-Erfassungstool für die Automatisierung oder in einer Testumgebung verwenden.  
  
 [Beispiele](graphics-diagnostics-examples.md)  
 Hier finden Sie einige Beispiele, die zeigen, wie die Grafikdiagnosetools gemeinsam zur Diagnose unterschiedlicher Renderingprobleme verwendet werden.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[Debugger – Featuretour](../debugging-in-visual-studio.md)|Stellt die Debuggingfunktionen in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vor.|  
|[DirectX-Grafiken und-Spiele](http://go.microsoft.com/fwlink/?LinkId=256498)|Enthält Artikel, in denen die DirectX-Grafiktechnologien erläutert werden.|
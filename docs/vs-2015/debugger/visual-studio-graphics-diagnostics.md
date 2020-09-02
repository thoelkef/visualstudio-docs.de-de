---
title: Visual Studio-Grafikdiagnose | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics
ms.assetid: fa69c550-62a7-41b5-bb1f-7eb04af1a6e8
caps.latest.revision: 42
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ca0a1613f46f8542a3ede4ce2053b3584824590e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75847828"
---
# <a name="visual-studio-graphics-diagnostics"></a>Visual Studio-Grafikdiagnose
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die *Grafikdiagnose* von Visual Studio umfasst eine Reihe von Tools zum Aufzeichnen und anschließenden Analysieren von Rendering- und Leistungsproblemen in Direct3D-Apps. Die Grafikdiagnose kann für Apps verwendet werden, die lokal auf Ihrem Windows-PC, in einem Windows-Geräteemulator oder auf einem Remotecomputer oder-gerät ausgeführt werden.  
  
 Der Grafikdiagnose-Workflow beginnt mit der Erfassung eines Datensatzes zur Verwendung von Direct3D durch Ihre App – live, während der Ausführung –, damit das Verhalten sofort analysiert, freigegeben oder für die spätere Nutzung gespeichert werden kann. Erfassungssitzungen können manuell über Visual Studio oder mit dem Befehlszeilenerfassungstool **dxcap.exe** initiiert und gesteuert werden. Erfassungssitzungen können auch programmgesteuert mit Grafikdiagnose-Erfassungs-APIs initiiert und gesteuert werden.  
  
 Nachdem eine Erfassungssitzung aufgezeichnet wurde, kann der Inhalt der *Visual Studio-Grafikanalyse* zu einem beliebigen Zeitpunkt wiedergegeben werden, wobei die aufgezeichneten Frames durch genau dieselben Ressourcen neu erstellt und die von der App verwendeten Befehle gerendert werden. Anschließend können mit den Tools im Fenster „Grafikanalyse“ alle aufgezeichneten Frames im Detail analysiert werden. Diese Tools können verwendet werden, um Direct3D-API-Aufrufe, Ressourcen, Pipelinezustandsobjekte, Pipelinestufen oder sogar den vollständigen Verlauf jedes Pixels in einem erfassten Frame zu untersuchen. Durch die kombinierte Verwendung dieser Tools kann ein Renderingproblem intuitiv untersucht werden, beginnend bei der Anzeige in einem erfassten Frame bis zu den Grundursachen in Quellcode, Shadern oder Grafikressourcen der App.  
  
 Sie können einen erfassten Frame mithilfe des Tools *Frame-Analyse* analysieren, um Leistungsprobleme zu diagnostizieren. Das Tool ermittelt, ob ein Potenzial zur Leistungsoptimierung vorhanden ist, indem es automatisch die Art und Weise ändert, in der die App Direct3D verwendet, und Vergleichstests zu allen Varianten ausführt. In der Vergangenheit haben Sie diese Änderungen möglicherweise manuell vorgenommen und die Ergebnisse gemessen, um herauszufinden, welche Unterschiede auftreten. Mit Frame-Analyse müssen Sie nur noch die Änderungen vornehmen, von denen Sie wissen, dass sie sich auszahlen.  
  
 Grafikdiagnose hilft Ihnen, Aussehen und Funktion einer grafisch aufwendigen Direct3D-App zu optimieren.  
  
 Mehr über die Möglichkeiten der Visual Studio-Grafikdiagnose erfahren Sie unter [Übersicht über Visual Studio-Grafikdiagnose](../debugger/overview-of-visual-studio-graphics-diagnostics.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Übersicht](../debugger/overview-of-visual-studio-graphics-diagnostics.md)  
 Bietet eine Einführung in den Workflow und die Tools der Grafikdiagnose.  
  
 [Erste Schritte](../debugger/getting-started-with-visual-studio-graphics-diagnostics.md)  
 In diesem Abschnitt erfahren Sie, wie Sie Visual Studio-Grafikdiagnose installieren und mit der Direct3D-App verwenden.  
  
 [Capturing Graphics Information](../debugger/capturing-graphics-information.md)  
 Um die Grafikdiagnose zur Untersuchung eines Renderingproblems zu verwenden, zeichnen Sie zuerst Informationen darüber auf, wie die App DirectX verwendet. In der Aufzeichnungssitzung, während der Ihre App normal ausgeführt wird, können Sie die gewünschten Frames *aufzeichnen*, d. h. auswählen. Die Aufzeichnungen enthalten ausführliche Informationen darüber, wie die Frames gerendert werden. Sie können die aufgezeichneten Informationen als Grafikprotokolldokument speichern, um sie später zu untersuchen oder für andere Teammitglieder freizugeben.  
  
 [GPU-Nutzung](../debugger/gpu-usage.md)  
 Zur Profilerstellung Ihrer App mit der Grafikdiagnose verwenden Sie das GPU-Auslastungstool. Die GPU-Auslastung kann zusammen mit anderen Tools zur Profilerstellung, z. B. CPU-Nutzung, verwendet werden, um einen Zusammenhang zwischen CPU- und GPU-Aktivität und daraus resultierenden Leistungsproblemen in Ihrer App herzustellen.  
  
 [Grafikprotokolldokument](../debugger/graphics-log-document.md)  
 Wählen Sie über das Dokumentfenster „Grafikprotokolle“ einen aufgezeichneten Frame – oder sogar ein bestimmtes Pixel, damit Sie dann die *Ereignisse* genauer untersuchen können (d. h. die DirectX-API-Aufrufe), die eine Auswirkung auf den Frame oder das Pixel haben. So können die Überprüfung eines aufgezeichneten Grafikprotokolls starten.  
  
 [Frame-Analyse](../debugger/graphics-frame-analysis.md)  
 Nach der Auswahl eines Frames verwenden Sie die Grafikframe-Analyse, um Ihre Renderingleistung zu untersuchen und anzupassen.  
  
 [Ereignisliste](../debugger/graphics-event-list.md)  
 Nachdem Sie einen Frame ausgewählt haben, untersuchen Sie mithilfe der **Grafikereignisliste** dessen Ereignisse, und überprüfen Sie, ob diese mit dem Renderingproblem zusammenhängen.  
  
 [State](../debugger/graphics-state.md)  
 Das Statusfenster hilft Ihnen, den während des aktuellen Ereignisses aktiven Status der Grafik zu verstehen.  
  
 [Pipelinestufen](../debugger/graphics-pipeline-stages.md)  
 Untersuchen Sie im Fenster **Grafikpipelinestufen**, wie das aktuell ausgewählte Ereignis in den einzelnen Stufen der Grafikpipeline verarbeitet wird, damit Sie feststellen können, wo das Renderingproblem zuerst auftritt. Die Untersuchung der Pipelinephasen ist besonders hilfreich, wenn ein Objekt aufgrund einer falschen Transformation nicht angezeigt wird, oder wenn eine der Stufen eine Ausgabe erzeugt, die nicht mit der in der nächsten Phase erwarteten Ausgabe übereinstimmt.  
  
 [Ereignisaufrufliste](../debugger/graphics-event-call-stack.md)  
 Mithilfe der **Aufrufliste des Grafikereignisses** können Sie die Aufrufliste des aktuell ausgewählten Ereignisses überprüfen und so zum App-Code navigieren, der mit dem Renderingproblem zusammenhängt.  
  
 [Pixelverlauf](../debugger/graphics-pixel-history.md)  
 Im Fenster **Grafikpixelverlauf** können Sie analysieren, wie sich die Ereignisse auf das derzeit ausgewählte Pixel auswirken, und Sie können das Ereignis oder die Kombination der Ereignisse identifizieren, die bestimmte Arten von Renderingproblemen verursachen. Der Pixelverlauf ist besonders hilfreich, wenn ein Objekt falsch gerendert wird, da entweder die Ausgabe des Pixel-Shaders falsch ist oder falsch mit dem Framepuffer kombiniert wurde. Der Pixelverlauf ist ebenfalls aufschlussreich, wenn ein Objekt gar nicht angezeigt wird, da seine Pixel verworfen wurden, bevor sie den Framepuffer erreicht haben.  
  
 [Objekttabelle](../debugger/graphics-object-table.md)  
 Mithilfe der **Grafikobjekttabelle** können Sie die Eigenschaften und Inhalte bestimmter Direct3D-Objekte und -ressourcen untersuchen, die für das aktuell ausgewählte Ereignis gültig sind. Die Objekttabelle unterstützt Sie bei der Ermittlung des Grafikgerätekontexts, der während eines Ereignisses aktiv ist, und bei der Untersuchung von Inhalten aus Grafikressourcen, wie Konstantenpuffer, Vertexpuffer und Texturen.  
  
 [HLSL-Debugger](../debugger/hlsl-shader-debugger.md)  
 Verwenden Sie den **HLSL-Debugger**, um zu untersuchen, wie sich der Shadercode für die aktuell ausgewählte Ereignis- und Grafikpipelinestufe verhält. Mit dem HLSL-Debugger können Sie den Code schrittweise ausführen, den Inhalt von Variablen untersuchen und andere typische Debugaufgaben durchführen. Mit dem HLSL-Debugger können Sie auch den Compute-Shader-Code unabhängig davon untersuchen, ob die Ergebnisse weiter durch die Grafikpipeline verarbeitet oder nur von der Anwendung eingelesen werden.  
  
 [Befehlszeilen-Erfassungstool](../debugger/command-line-capture-tool.md)  
 Verwenden Sie das Befehlszeilen-Erfassungstool, umGrafikinformationen schnell aufzuzeichnen und ohne Verwendung von Visual Studio oder programmgesteuerter Erfassung wiederzugeben. Insbesondere können Sie das Befehlszeilen-Erfassungstool für die Automatisierung oder in einer Testumgebung verwenden.  
  
 [Beispiele](../debugger/graphics-diagnostics-examples.md)  
 Hier finden Sie einige Beispiele, die zeigen, wie die Grafikdiagnosetools gemeinsam zur Diagnose unterschiedlicher Renderingprobleme verwendet werden.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
  
|Titel|BESCHREIBUNG|  
|-----------|-----------------|  
|[Debuggen in Visual Studio](../debugger/debugging-in-visual-studio.md)|Stellt die Debuggingfunktionen in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] vor.|  
|[DirectX-Grafiken und -Spiele](https://msdn.microsoft.com/library/ee663274(v=vs.85).aspx)|Enthält Artikel, in denen die DirectX-Grafiktechnologien erläutert werden.|

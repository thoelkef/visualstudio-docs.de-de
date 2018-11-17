---
title: HLSL-Shaderdebugger | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.graphics.shaderviewer
ms.assetid: 4ccec541-3c49-42bd-972a-686eb3a88fbc
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e2c79491703ba2e20ae7bbb8c1303cfd5496a686
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51760943"
---
# <a name="hlsl-shader-debugger"></a>HLSL-Shaderdebugger
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mit dem HLSL-Debugger in der Visual Studio-Grafikanalyse können Sie nachvollziehen, wie Ihr HLSL-Shader-Code unter echten Bedingungen Ihrer App ausgeführt wird.  
  
 Dies ist der HLSL-Debugger:  
  
 ![Debugging von HSL mit Fenstern für Überwachung und Aufrufliste. ](../debugger/media/gfx-diag-demo-hlsl-debugger-orientation.png "Gfx_diag_demo_hlsl_debugger_orientation")  
  
## <a name="understanding-the-hlsl-debugger"></a>Grundlegendes zum HLSL-Debugger  
 Der HLSL-Debugger kann Ihnen helfen, Probleme zu verstehen, die im Shader-Code auftreten. Das Debuggen von HLSL-Code in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ähnelt dem Debuggen von Code, der in anderen Sprachen wie C++, C# oder Visual Basic geschrieben wird. Sie können den Inhalt von Variablen überprüfen, Haltepunkte festlegen, den Code durchlaufen und die Aufrufliste abarbeiten, so wie Sie es auch beim Debuggen anderer Sprachen können.  
  
 Da GPUs jedoch durch gleichzeitiges Ausführen von Shader-Codes auf Hunderten von Threads eine hohe Leistungsfähigkeit erreichen, wurde der HLSL-Debugger so entworfen, dass er gemeinsam mit anderen Grafikanalysetools verwendet werden kann, um alle Informationen auf sinnvolle Art und Weise zu präsentieren. Die Grafikanalyse erstellt aufgezeichnete Frames mithilfe der in Grafikprotokollen aufgezeichneten Informationen neu. Der HLSL-Debugger überwacht die GPU-Ausführung beim Ausführen des Shader-Codes nicht in Echtzeit. Da ein Grafikprotokoll genügend Informationen enthält, um einen beliebigen Teil der Ausgabe neu zu erstellen, und da die Grafikanalyse Tools bereitstellt, die Ihnen helfen können, das genaue Pixel und das Ereignis festzulegen, in dem ein Fehler auftritt, muss der HLSL-Debugger den genauen Shaderthread nur simulieren, der Sie interessiert. Dies bedeutet, dass die Arbeit des Shaders für die CPU simuliert werden kann, in der die internen Funktionen in der Vollansicht angezeigt werden. Aus diesem Grund bietet der HLSL-Debugger eine CPU-ähnliche Debugleistung.  
  
 Allerdings unterliegt der HLSL-Debugger gerade folgenden Einschränkungen:  
  
- Der Vorgang zum Bearbeiten und Fortfahren wird durch den HLSL-Debugger nicht unterstützt. Sie können jedoch Änderungen an Ihren Shadern vornehmen und anschließend das Frame erneut generieren, um die Ergebnisse anzuzeigen.  
  
- Es ist nicht möglich, eine Anwendung und ihren Shader-Code gleichzeitig zu debuggen. Sie können jedoch zwischen beiden wechseln.  
  
- Sie können dem Überwachungsfenster Variablen und Register hinzufügen, aber Ausdrücke werden nicht unterstützt.  
  
  Dennoch stellt der HLSL-Debugger eine bessere, CPU-ähnlichere Debugleistung zur Verfügung, als andernfalls möglich wäre.  
  
## <a name="hlsl-shader-edit--apply"></a>HLSL-Shader bearbeiten und anwenden  
 Der HLSL-Shader-Debugger unterstützt Bearbeiten und Fortfahren nicht auf die gleiche Weise wie der CPU-Debugger, da das GPU-Ausführungsmodell keine Umkehrung des Shader-Zustands ermöglicht. Stattdessen unterstützt der HLSL-Debugger, bearbeiten und anwenden, wodurch Sie HLSL-Quelldateien bearbeiten, und wählen Sie dann **übernehmen** , den Rahmen, um die Auswirkungen Ihrer Änderungen finden Sie unter erneut zu generieren. Ihr geänderter Shader-Code befindet sich in einer separaten Datei, die Integrität der ursprünglichen HLSL-Quelldatei des Projekts beizubehalten, aber wenn Sie mit Ihren Änderungen zufrieden sind können Sie **kopieren in...** um die Änderungen in Ihr Projekt kopieren. Mit dieser Funktion können Sie den Shader-Code, der Fehler enthält, schnell durchlaufen und kostspielige Wiederherstellungs- und Erfassungsschritte aus Ihrem Workflow HLSL debuggen beseitigen.  
  
## <a name="hlsl-disassembly"></a>HLSL-Disassembly  
 Der HLSL-Shader-Debugger enthält eine Liste der HLSL-Shader-Assembly rechts neben der Auflistung des HLSL-Quellcodes.  
  
## <a name="debugging-hlsl-code"></a>Debuggen von HLSL-Code  
 Sie können über das Fenster „Pipelinestufen“ oder „Pixelverlauf“ auf den HLSL-Debugger zugreifen.  
  
#### <a name="to-start-the-hlsl-debugger-from-the-graphics-pipeline-stages-window"></a>So starten Sie den HLSL-Debugger im Fenster "Grafikpipelinestufen"  
  
1.  In der **Grafikpipelinestufen** Fenster Suchen Sie die Pipelinestufe, die mit dem Shader zugeordnet sind, die Sie debuggen möchten.  
  
2.  Wählen Sie unterhalb des Titels der Pipelinestufe, **Debuggen starten**, was als kleiner grüner Pfeil angezeigt wird.  
  
    > [!NOTE]
    >  Dieser Einstiegspunkt in den HLSL-Debugger debuggt nur den ersten Shader-Thread für die entsprechende Stufe, d. h. für den ersten Vertex oder das erste Pixel, der bzw. das verarbeitet wird. Sie können „Pixelverlauf“ verwenden, um auf andere Threads dieser Shader-Stufen zuzugreifen.  
  
#### <a name="to-start-the-hlsl-debugger-from-the-graphics-pixel-history"></a>So starten Sie den HLSL-Debugger im Fenster "Grafikpixelverlauf"  
  
1. In der **Grafikpixelverlauf** Fenster, erweitern Sie den Draw-Aufruf, der mit dem Shader zugeordnet sind, die Sie debuggen möchten. Jeder Zeichnen-Befehl kann mehreren Primitiva entsprechen.  
  
2. Erweitern Sie in den Eigenschaften des Zeichnen-Befehls das Primitivum, dessen resultierender Farbbeitrag auf einen Fehler im Shadercode hindeutet. Wenn für mehrere Primitiva ein Fehler zu vermuten ist, wählen Sie davon das erste Primitivum aus, um eine Häufung von Fehlern zu vermeiden, durch die eine Diagnose des Problems schwieriger wird.  
  
3. In den Eigenschaften des primitivums wählen, ob zum Debuggen der **Vertex-Shader** oder **Pixel-Shader**. Debuggen Sie den Vertex-Shader, wenn Sie vermuten, dass der Pixel-Shader fehlerfrei ist, aber einen falschen Farbbeitrag generiert, weil der Vertex-Shader ihm falsche Konstanten übergibt. Andernfalls debuggen Sie den Pixel-Shader.  
  
    Wählen Sie rechts vom ausgewählten Shader, **Debuggen starten**, was als kleiner grüner Pfeil angezeigt wird.  
  
   > [!NOTE]
   >  Dieser Einstiegspunkt in den HLSL-Debugger debuggt entweder den Pixel-Shader-Thread, der dem ausgewählten Zeichnen-Befehl, Primitivum und Pixel entspricht, oder die Vertex-Shader-Threads, deren Ergebnisse durch den Zeichnen-Befehl, die Primitiva und Pixel interpoliert werden, die Sie ausgewählt haben. Für Vertex-Shader können Sie den Einstiegspunkt auf einen bestimmten Vertex festlegen, indem Sie die Details des Vertex-Shaders erweitern.  
  
   Beispiele zur Verwendung der HLSL-Debugger zum Debuggen von Shader-Fehlern finden Sie in [Beispiele](../debugger/graphics-diagnostics-examples.md) oder die exemplarischen Vorgehensweisen im Abschnitt Siehe auch verknüpft.  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Fehlende Objekte durch Vertex-Shading](../debugger/walkthrough-missing-objects-due-to-vertex-shading.md)   
 [Exemplarische Vorgehensweise: Debuggen von Renderingfehlern, die durch Schattierungen entstanden sind](../debugger/walkthrough-debugging-rendering-errors-due-to-shading.md)   
 [Exemplarische Vorgehensweise: Debuggen eines Compute-Shaders mithilfe der Grafikdiagnose](../debugger/walkthrough-using-graphics-diagnostics-to-debug-a-compute-shader.md)




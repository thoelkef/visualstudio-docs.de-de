---
title: "Exemplarische Vorgehensweise: Debuggen von Renderingfehlern, die durch Schattierungen entstanden sind | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 01875b05-cc7b-4add-afba-f2b776f86974
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Exemplarische Vorgehensweise: Debuggen von Renderingfehlern, die durch Schattierungen entstanden sind
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese exemplarische Vorgehensweise veranschaulicht, wie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Grafikdiagnose verwendet wird, um ein Objekt zu untersuchen, das aufgrund eines Shaderfehlers eine falsche Farbe hat.  
  
 In dieser exemplarischen Vorgehensweise wird Folgendes veranschaulicht:  
  
-   Auswerten des Grafikprotokolldokuments, um die Pixel zu identifizieren, für die das Problem auftritt  
  
-   Verwenden des Fensters **Grafikpixelverlauf**, um den Pixelstatus genauer zu untersuchen  
  
-   Verwenden des **HLSL\-Debuggers**, um den Pixel\- und den Vertexshader zu überprüfen  
  
## Szenario  
 Eine falsche Farbgebung von Objekten tritt häufig auf, wenn ein Vertexshader einem Pixelshader falsche oder unvollständige Informationen übergibt.  
  
 In diesem Szenario haben Sie kürzlich ein Objekt sowie einen neuen Vertex\- und einen neuen Pixelshader zur App hinzugefügt, um das Objekt zu transformieren und ihm ein einzigartiges Aussehen zu verleihen. Wenn Sie die App während eines Tests ausführen, wird das Objekt vollständig schwarz gerendert. Mithilfe der Grafikdiagnose erfassen Sie das Problem in einer Grafikprotokolldatei, um die App zu debuggen. Das Problem sieht in der App wie folgt aus:  
  
 ![Das Objekt wird mit falschen Farben gerendert.](~/debugger/graphics/media/gfx_diag_demo_render_error_shader_problem.png "gfx\_diag\_demo\_render\_error\_shader\_problem")  
  
## Untersuchung  
 Mithilfe der Grafikdiagnosetools können Sie das Grafikprotokolldokument laden, um die Frames zu untersuchen, die während des Tests erfasst wurden.  
  
#### So überprüfen Sie einen Frame in einem Grafikprotokoll  
  
1.  Laden Sie in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ein Grafikprotokoll, das einen Frame enthält, der das fehlende Modell darstellt. Ein neues Grafikprotokoll\-Dokumentfenster wird in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] angezeigt. Im oberen Teil dieses Fensters befindet sich die Renderzielausgabe des ausgewählten Frames. Im unteren Teil befindet sich die **Frameliste**, in der alle aufgezeichneten Frames als Miniaturansichten angezeigt werden.  
  
2.  Wählen Sie in der **Frameliste** einen Frame aus, in dem das Objekt nicht richtig dargestellt wird. Das Renderziel wird aktualisiert und gibt den ausgewählten Frame wieder. In diesem Szenario sieht das Grafikprotokolldokumentfenster wie folgt aus:  
  
     ![Das Dokument mit dem Diagrammprotokoll in Visual Studio](../debugger/media/gfx_diag_demo_render_error_shader_step_1.png "gfx\_diag\_demo\_render\_error\_shader\_step\_1")  
  
 Nachdem Sie einen Frame ausgewählt haben, der das Problem veranschaulicht, können Sie das Fenster **Grafikpixelverlauf** verwenden, um das Problem zu diagnostizieren. Im Fenster **Grafikpixelverlauf** werden die Grundtypen, die möglicherweise Auswirkungen auf ein bestimmtes Pixel hatten, deren Shader sowie deren Auswirkungen auf das Renderziel gezeigt \(in zeitlicher Reihenfolge\).  
  
#### So überprüfen Sie ein Pixel  
  
1.  Öffnen Sie das Fenster **Grafikpixelverlauf**. Wählen Sie auf der Symbolleiste **Grafikdiagnose** das Symbol für **Pixelverlauf** aus.  
  
2.  Wählen Sie das Pixel aus, das Sie überprüfen möchten. Wählen Sie im Grafikprotokolldokumentfenster eines der Pixel des Objekts aus, das die falsche Farbe hat:  
  
     ![Beim Auswählen eines Pixels werden Informationen zu seinem Verlauf angezeigt.](../debugger/media/gfx_diag_demo_render_error_shader_step_2.png "gfx\_diag\_demo\_render\_error\_shader\_step\_2")  
  
     Das Fenster **Grafikpixelverlauf** wird entsprechend dem ausgewählten Pixel aktualisiert. In diesem Szenario sieht das Fenster **Grafikpixelverlauf** wie folgt aus:  
  
     ![Der Pixelverlauf zeigt ein DrawIndexed&#45;Ereignis.](../debugger/media/gfx_diag_demo_render_error_shader_step_3.png "gfx\_diag\_demo\_render\_error\_shader\_step\_3")  
  
     Sie sehen, dass das Ergebnis des Pixelshaders vollständig deckendes Schwarz ist \(0, 0, 0, 1\) und dass die **Ausgabezusammenführung** dieses mit der **vorherigen Farbe** des Pixels so kombiniert, dass das **Ergebnis** ebenfalls vollständig deckend schwarz ist.  
  
 Nachdem Sie ein Pixel mit falscher Farbe überprüft und festgestellt haben, dass die Ausgabe des Pixelshaders nicht die erwartete Farbe angibt, können Sie den HLSL\-Debugger dazu verwenden, den Pixelshader zu untersuchen und herauszufinden, was mit der Farbe des Objekts geschehen ist. Mit dem HLSL\-Debugger können Sie den Zustand von HLSL\-Variablen während der Ausführung feststellen, den HLSL\-Code schrittweise durchlaufen sowie Haltepunkte festlegen, um sich die Problemdiagnose zu erleichtern.  
  
#### So überprüfen Sie den Pixelshader  
  
1.  Starten Sie das Debuggen des Pixelshaders. Wählen Sie im Fenster **Grafikpixelverlauf** unter dem Primitiv des Objekts neben **Pixelshader** die Schaltfläche **Debuggen starten** aus.  
  
2.  Da der Pixelshader die Farbe in diesem Szenario lediglich vom Vertexshader übernimmt und ungeändert weitergibt, ist leicht zu sehen, dass der Pixelshader nicht die Ursache des Problems ist.  
  
3.  Setzen Sie den Mauszeiger auf `input.color`. Sie sehen, dass der Wert vollständig deckendem Schwarz entspricht \(0, 0, 0, 1\).  
  
     !["color"&#45;Member von "input" ist "Schwarz".](~/debugger/graphics/media/gfx_diag_demo_render_error_shader_step_5.png "gfx\_diag\_demo\_render\_error\_shader\_step\_5")  
  
     In diesem Szenario ergibt die Untersuchung, dass die falsche Farbe wahrscheinlich das Ergebnis eines Vertexshaders ist, der dem Pixelshader nicht die richtigen Farbinformationen zur Verarbeitung bereitstellt.  
  
 Nachdem Sie festgestellt haben, dass der Vertexshader wahrscheinlich nicht die richtigen Informationen an den Pixelshader übergibt, überprüfen Sie im nächsten Schritt den Vertexshader.  
  
#### So überprüfen Sie den Vertexshader  
  
1.  Starten Sie das Debuggen des Vertexshaders. Wählen Sie im Fenster **Grafikpixelverlauf** unter dem Primitiv des Objekts neben **Vertexshader** die Schaltfläche **Debuggen starten** aus.  
  
2.  Suchen Sie nach der Ausgabestruktur des Vertexshaders, denn diese ist die Eingabe für den Pixelshader. In diesem Szenario hat diese Struktur den Namen `output`. Überprüfen Sie den Code des Vertexshaders. Sie stellen fest, dass der `color`\-Member der `output`\-Struktur explizit auf vollständig deckendes Schwarz festgelegt wird, möglicherweise als Ergebnis von Debugaktionen einer anderen Person.  
  
3.  Vergewissern Sie sich, dass der color\-Member nie aus der Eingabestruktur \(input\) kopiert wird. Da der Wert von `output.color` unmittelbar vor der Rückgabe der `output`\-Struktur auf vollständig deckendes Schwarz festgelegt wird, sollten Sie sich vergewissern, dass der Wert von `output` in keiner vorherigen Zeile korrekt initialisiert wurde. Durchlaufen Sie den der Vertexshadercode bis zu der Zeile, in der `output.color` auf Schwarz festgelegt wird. Beobachten Sie dabei den Wert von `output.color`. Sie stellen fest, dass der Wert von `output.color` nicht initialisiert wird, bis er auf Schwarz festgelegt wird. Dadurch wird bestätigt, dass die Codezeile, in der `output.color` auf Schwarz festgelegt wird, nicht gelöscht, sondern geändert werden sollte.  
  
     ![Der Wert von "output.color" ist "Schwarz".](~/debugger/graphics/media/gfx_diag_demo_render_error_shader_step_7.png "gfx\_diag\_demo\_render\_error\_shader\_step\_7")  
  
 Nachdem Sie festgestellt haben, dass die Ursache des Renderproblems darin besteht, dass der Vertexshader dem Pixelshader einen falschen Farbwert bereitstellt, können Sie das Problem beheben. In diesem Szenario können Sie das Problem beheben, indem Sie den folgenden Code im Vertexshader ändern  
  
```  
output.color = float3(0.0f, 0.0f, 0.0f);  
```  
  
 auf  
  
```hlsl  
output.color = input.color;  
```  
  
 In diesem Code wird die Vertexfarbe aus den Scheitelpunkten des Objekts lediglich unverändert durchgereicht. In komplexeren Vertexshadern könnte die Farbe geändert werden, bevor sie weitergereicht wird. Der korrigierte Vertexshadercode sollte im Wesentlichen so aussehen:  
  
 ![Der korrigierte Vertex&#45;Shader&#45;Code.](~/debugger/graphics/media/gfx_diag_demo_render_error_shader_step_8.png "gfx\_diag\_demo\_render\_error\_shader\_step\_8")  
  
 Nachdem Sie den Code korrigiert haben, erstellen Sie die App neu und führen diese erneut aus, um nun festzustellen, dass das Renderproblem behoben ist.  
  
 ![Das Objekt wird mit den richtigen Farben gerendert.](~/debugger/graphics/media/gfx_diag_demo_render_error_shader_resolution.png "gfx\_diag\_demo\_render\_error\_shader\_resolution")
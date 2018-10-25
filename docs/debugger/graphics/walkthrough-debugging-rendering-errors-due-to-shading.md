---
title: 'Exemplarische Vorgehensweise: Debuggen von Renderingfehlern, die durch Schattierungen entstanden sind | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 01875b05-cc7b-4add-afba-f2b776f86974
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 202f2fb0cdbfec6e52a2938365105f3d15327445
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49920535"
---
# <a name="walkthrough-debugging-rendering-errors-due-to-shading"></a>Exemplarische Vorgehensweise: Debuggen von Renderingfehlern, die durch Schattierungen entstanden sind
In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie Sie mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Grafikdiagnose, um ein Objekt zu untersuchen, die aufgrund eines shaderfehlers falsche Farbe hat.  
  
 In dieser exemplarischen Vorgehensweise wird Folgendes veranschaulicht:  
  
-   Auswerten des Grafikprotokolldokuments, um die Pixel zu identifizieren, für die das Problem auftritt  
  
-   Verwenden des Fensters **Grafikpixelverlauf** , um den Pixelstatus genauer zu untersuchen  
  
-   Verwenden des **HLSL-Debuggers** , um den Pixel- und den Vertexshader zu überprüfen  
  
## <a name="scenario"></a>Szenario  
 Eine falsche Farbgebung von Objekten tritt häufig auf, wenn ein Vertexshader einem Pixelshader falsche oder unvollständige Informationen übergibt.  
  
 In diesem Szenario haben Sie kürzlich ein Objekt zu Ihrer app hinzugefügt. Sie auch hinzugefügt einen neuen Vertex "und" Pixel-Shader, transformieren Sie das Objekt, und weisen Sie ihm eine eindeutige Darstellung. Wenn Sie die App während eines Tests ausführen, wird das Objekt vollständig schwarz gerendert. Mithilfe der Grafikdiagnose erfassen Sie das Problem in einer Grafikprotokolldatei, um die App zu debuggen. Das Problem sieht aus wie die folgende Abbildung, in der app:  
  
 ![Das Objekt wird mit falschen Farben gerendert. ](media/gfx_diag_demo_render_error_shader_problem.png "Gfx_diag_demo_render_error_shader_problem")  
  
## <a name="investigation"></a>Untersuchung  
 Mithilfe der Grafikdiagnosetools können Sie das Grafikprotokolldokument laden, um die Frames zu untersuchen, die während des Tests erfasst wurden.  
  
#### <a name="to-examine-a-frame-in-a-graphics-log"></a>So überprüfen Sie einen Frame in einem Grafikprotokoll  
   
1. In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], laden Sie ein grafikprotokoll, das einen Rahmen besitzt, der das fehlende Modell anzeigt. Ein neues grafisches Log-Dokumentfenster angezeigt wird, im [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Im oberen Teil dieses Fensters befindet sich die Renderzielausgabe des ausgewählten Frames. Im unteren Teil befindet sich die **Frameliste**, in der alle aufgezeichneten Frames als Miniaturansichten angezeigt werden.  
  
2. In der **Frameliste**, wählen Sie einen Frame in der das Objekt nicht richtig dargestellt. Das Renderziel wird aktualisiert und gibt den ausgewählten Frame wieder. In diesem Szenario grafikprotokoll die sieht wie in dieser Abbildung:  
  
    ![Das grafikprotokolldokument in Visual Studio. ](media/gfx_diag_demo_render_error_shader_step_1.png "gfx_diag_demo_render_error_shader_step_1")  
  
   Nachdem Sie einen Frame ausgewählt haben, der das Problem veranschaulicht, können Sie das Fenster **Grafikpixelverlauf** verwenden, um das Problem zu diagnostizieren. Im Fenster **Grafikpixelverlauf** werden die Grundtypen, die möglicherweise Auswirkungen auf ein bestimmtes Pixel hatten, deren Shader sowie deren Auswirkungen auf das Renderziel gezeigt (in zeitlicher Reihenfolge).  
  
#### <a name="to-examine-a-pixel"></a>So überprüfen Sie ein Pixel  
  
1. Öffnen Sie das Fenster **Grafikpixelverlauf** . Wählen Sie auf der Symbolleiste **Grafikdiagnose** das Symbol für **Pixelverlauf**aus.  
  
2. Wählen Sie das Pixel aus, das Sie überprüfen möchten. Wählen Sie auf das grafikprotokolldokumentfenster eines der Pixel für das Objekt, das falsche Farbe hat:  
  
    ![Auswählen eines Pixels werden Informationen zu seinem Verlauf angezeigt. ](media/gfx_diag_demo_render_error_shader_step_2.png "gfx_diag_demo_render_error_shader_step_2")  
  
    Das Fenster **Grafikpixelverlauf** wird entsprechend dem ausgewählten Pixel aktualisiert. In diesem Szenario sieht das Fenster **Grafikpixelverlauf** wie folgt aus:  
  
    ![Der pixelverlauf zeigt ein DrawIndexed-Ereignis. ](media/gfx_diag_demo_render_error_shader_step_3.png "gfx_diag_demo_render_error_shader_step_3")  
  
    Beachten Sie, dass Ergebnis des Pixelshaders vollständig deckendes Schwarz (0, 0, 0, 1), und dass die **Ausgabemerge** kombiniert diese Pixel-Shader, mit der **zurück** Farbe des Pixels so, die die  **Ergebnis** ist ebenfalls vollständig deckend Schwarz.  
  
   Nachdem Sie eine Pixel, die mit falscher Farbe ist untersuchen und ermitteln, dass die Ausgabe des Pixelshaders nicht die erwartete Farbe angibt, können Sie den HLSL-Debugger den Pixel-Shader überprüfen und erfahren Sie, was mit der Farbe des Objekts geschehen ist. Mit dem HLSL-Debugger können Sie den Zustand von HLSL-Variablen während der Ausführung feststellen, den HLSL-Code schrittweise durchlaufen sowie Haltepunkte festlegen, um sich die Problemdiagnose zu erleichtern.  
  
#### <a name="to-examine-the-pixel-shader"></a>So überprüfen Sie den Pixelshader  
  
1. Starten Sie das Debuggen des Pixelshaders. Wählen Sie im Fenster **Grafikpixelverlauf** unter dem Primitiv des Objekts neben **Pixelshader**die Schaltfläche **Debuggen starten** aus.  
  
2. Da der Pixelshader die Farbe in diesem Szenario lediglich vom Vertexshader übernimmt und ungeändert weitergibt, ist leicht zu sehen, dass der Pixelshader nicht die Ursache des Problems ist.  
  
3. Setzen Sie den Mauszeiger auf `input.color`. Sie sehen, dass der Wert vollständig deckendem Schwarz entspricht (0, 0, 0, 1).  
  
    ![Das Element "Color" von "Input" ist schwarz. ](media/gfx_diag_demo_render_error_shader_step_5.png "gfx_diag_demo_render_error_shader_step_5")  
  
    In diesem Szenario ergibt die Untersuchung, dass die falsche Farbe wahrscheinlich das Ergebnis eines Vertexshaders ist, der dem Pixelshader nicht die richtigen Farbinformationen zur Verarbeitung bereitstellt.  
  
   Nachdem Sie festgestellt haben, dass der Vertexshader wahrscheinlich nicht die richtigen Informationen an den Pixelshader übergibt, überprüfen Sie im nächsten Schritt den Vertexshader.  
  
#### <a name="to-examine-the-vertex-shader"></a>So überprüfen Sie den Vertexshader  
  
1. Starten Sie das Debuggen des Vertexshaders. Wählen Sie im Fenster **Grafikpixelverlauf** unter dem Primitiv des Objekts neben **Vertexshader**die Schaltfläche **Debuggen starten** aus.  
  
2. Suchen Sie nach der Ausgabestruktur des Vertexshaders, denn diese ist die Eingabe für den Pixelshader. In diesem Szenario hat diese Struktur den Namen `output`. Überprüfen Sie den Code des Vertexshaders. Sie stellen fest, dass der `color` -Member der `output` -Struktur explizit auf vollständig deckendes Schwarz festgelegt wird, möglicherweise als Ergebnis von Debugaktionen einer anderen Person.  
  
3. Vergewissern Sie sich, dass der color-Member nie aus der Eingabestruktur (input) kopiert wird. Da der Wert des `output.color` kurz vor dem Ausführen auf vollständig deckendes Schwarz festgelegt ist die `output` Struktur wird zurückgegeben, es ist eine gute Idee, um sicherzustellen, dass der Wert des `output` wurde nicht in einer vorherigen Zeile korrekt initialisiert. Durchlaufen Sie den der Vertexshadercode bis zu der Zeile, in der `output.color` auf Schwarz festgelegt wird. Beobachten Sie dabei den Wert von `output.color`. Sie stellen fest, dass der Wert von `output.color` nicht initialisiert wird, bis er auf Schwarz festgelegt wird. Dadurch wird bestätigt, dass die Codezeile, in der `output.color` auf Schwarz festgelegt wird, nicht gelöscht, sondern geändert werden sollte.  
  
    ![Der Wert von "output.color" ist schwarz. ](media/gfx_diag_demo_render_error_shader_step_7.png "gfx_diag_demo_render_error_shader_step_7")  
  
   Nachdem Sie festgestellt haben, dass die Ursache des Renderproblems darin besteht, dass der Vertexshader dem Pixelshader einen falschen Farbwert bereitstellt, können Sie das Problem beheben. In diesem Szenario können Sie das Problem beheben, indem Sie den folgenden Code im Vertexshader ändern  
  
```hlsl  
output.color = float3(0.0f, 0.0f, 0.0f);  
```  
  
 auf  
  
```hlsl  
output.color = input.color;  
```  
  
 In diesem Code wird die Vertexfarbe aus den Scheitelpunkten des Objekts lediglich unverändert durchgereicht. In komplexeren Vertexshadern könnte die Farbe geändert werden, bevor sie weitergereicht wird. Der korrigierte Vertexshadercode sollte im Wesentlichen so aussehen:  
  
 ![Der korrigierte Vertex-Shader-Code. ](media/gfx_diag_demo_render_error_shader_step_8.png "gfx_diag_demo_render_error_shader_step_8")  
  
 Nachdem Sie den Code korrigiert haben, erstellen Sie die App neu und führen diese erneut aus, um nun festzustellen, dass das Renderproblem behoben ist.  
  
 ![Das Objekt wird mit den richtigen Farben gerendert. ](media/gfx_diag_demo_render_error_shader_resolution.png "Gfx_diag_demo_render_error_shader_resolution")

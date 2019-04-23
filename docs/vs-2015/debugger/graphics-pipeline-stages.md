---
title: Grafikpipelinestufen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.pipeline
ms.assetid: 2bf5c12e-2a00-401c-8163-4e373d08ad3f
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cd93ddb6e1d574460593f992f880ccd53d800842
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60097335"
---
# <a name="graphics-pipeline-stages"></a>Grafikpipelinestufen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Anhand des Fensters „Grafikpipelinestufen“ können Sie nachvollziehen, wie ein einzelner Zeichnen-Befehl in jeder Stufe der Direct3D-Grafikpipeline umgewandelt wird.  
  
 Im Folgenden finden Sie das Fenster „Pipelinestufen“:  
  
 ![Eine 3&#45;D-Objekt durchläuft die Pipelinestufen. ](../debugger/media/gfx-diag-demo-pipeline-stages-orientation.png "Gfx_diag_demo_pipeline_stages_orientation")  
  
## <a name="understanding-the-graphics-pipeline-stages-window"></a>Verstehen des Fensters Grafikpipelinestufen  
 Im Fenster „Pipelinestufen“ wird das Ergebnis jeder Stufe der Grafikpipeline einzeln veranschaulicht, und zwar für jeden Zeichnen-Befehl. Für gewöhnlich werden die Ergebnisse von Stufen in der Mitte der Pipeline ausgeblendet, wodurch es schwierig wird, den Ursprung des Renderingproblems zu finden. Durch die Veranschaulichung jeder einzelnen Stufe erleichtert das Fenster „Pipelinestufen“ das Auffinden des Problemursprungs. Beispielsweise können Sie problemlos nachvollziehen, wenn die Vertex-Shader-Stufe dazu führt, dass ein Objekt unerwartet neben dem Bildschirm gezeichnet wird.  
  
 Nach dem Ermitteln der problembehafteten Stufe können Sie andere Grafikanalysetools verwenden, um zu überprüfen, wie die Daten interpretiert oder transformiert wurden. Renderingprobleme, die in den Pipelinestufen angezeigt werden, beziehen sich häufig auf falsche Vertex-Format-Deskriptoren, fehlerbehaftete Shader-Programme oder falsch konfigurierte Status.  
  
### <a name="links-to-related-graphics-objects"></a>Links zu verwandten Grafikobjekten  
 In einigen Fällen ist ein zusätzlicher Kontext erforderlich, um zu ermitteln, weshalb ein Zeichnen-Befehl mit der Grafikpipeline in bestimmter Art und Weise interagiert. Damit dieser zusätzliche Kontext einfacher gefunden werden kann, stellt das Fenster „Grafikpipelinestufen“ eine Verknüpfung zu mindestens einem Objekt her, das zusätzlichen Kontext bereitstellt, der mit dem, was in der Grafikpipeline vor sich geht, verknüpft ist.  
  
- In Direct3D 12 ist dieses Objekt für gewöhnlich eine Befehlsliste.  
  
- In Direct3D 11 ist dieses Objekt für gewöhnlich der Grafikgerätkontext.  
  
  Diese Links sind Bestandteil der aktuellen Grafikereignissignatur, die sich in der oberen linken Ecke des Fensters „Grafikpipelinestufen“ befindet. Folgen Sie diesen Links, um weitere Details zum Objekt zu untersuchen.  
  
### <a name="viewing-and-debugging-shader-code"></a>Anzeigen und Debuggen des Shader-Codes  
 Sie können mithilfe der Steuerelemente unten von den entsprechenden Stufen im Fenster „Pipelinestufen“ Code für Vertex-, Hull-, Domänen-, Geometrie- und Pixel-Shader überprüfen und debuggen.  
  
##### <a name="to-view-a-shaders-source-code"></a>Um einen Shader-Quellcode anzuzeigen  
  
- Suchen Sie im Fenster **Grafikpipelinestufen** nach der Shader-Stufe, die dem zu überprüfenden Shader entspricht. Folgen Sie unter dem Vorschaubild anschließend dem Shader-Stufentitellink, folgen Sie beispielsweise dem Link **Vertex Shader obj:30**, um den Quellcode des Vertex-Shaders anzuzeigen.  
  
    > [!TIP]
    >  Die Objektnummer **obj:30** identifiziert diesen Shader über die gesamte Grafikanalyseoberfläche hinweg, beispielsweise in der Objekttabelle und im Pixelverlaufsfenster.  
  
##### <a name="to-debug-a-shader"></a>Um einen Shader zu debuggen  
  
- Suchen Sie im Fenster **Grafikpipelinestufen** nach der Shader-Stufe, die dem zu debuggenden Shader entspricht. Wählen Sie dann unter dem Vorschaubild **Debuggen starten** aus. Durch diesen Einstiegspunkt in den HLSL-Debugger erfolgt die standardmäßige Festlegung auf den ersten Aufruf des Shaders für die entsprechende Stufe, d. h. das erste Pixel, Vertex oder Primitiv, das während dieses Zeichnen-Befehls durch den Shader verarbeitet wird. Der Zugriff auf Aufrufe dieses Shaders für ein bestimmtes Pixel oder Vertex ist über **Grafikpixelverlauf** möglich.  
  
### <a name="the-pipeline-stages"></a>Die Pipelinestufen  
 Im Fenster „Pipelinestufen“ werden nur die Stufen der Pipeline veranschaulicht, die während des Zeichnen-Befehls aktiv waren. Auf jeder Stufe der Grafikpipeline werden Eingaben aus der vorherigen Stufe umgewandelt, und das Ergebnis wird an die nächste Stufe weitergegeben. Auf der ersten Stufe (der Eingabe-Assembler) werden Index- und Vertexdaten Ihrer App aus entsprechende Eingabe verwendet. Auf der letzten Stufe (die Ausgabezusammenführung) werden die neu gerenderten Pixel mit den aktuellen Inhalten des Framepuffers oder Renderziels kombiniert, wie es ausgegeben wird, um das endgültige Bild zu generieren, wie es auf Ihrem Bildschirm angezeigt wird.  
  
> [!NOTE]
>  Compute-Shader werden nicht im Fenster **Grafikpipelinestufen** unterstützt.  
  
 **Eingabe-Assembler**  
 Der Eingabe-Assembler liest durch Ihre App angegebene Index- und Vertexdaten und assembliert sie für die Grafikhardware.  
  
 Im Fenster „Pipelinestufen“ wird die Ausgabe „Eingabe-Assembler“ in einem Drahtmodell veranschaulicht. Wählen Sie zur detaillierten Anzeige des Ergebnisses im Fenster **Grafikpipelinestufen** die Option **Eingabe-Assembler** aus, um die assemblierten Scheitelpunkte mithilfe des Modell-Editors in vollständigem 3D anzuzeigen.  
  
> [!NOTE]
>  Wenn die `POSITION`-Semantik nicht in der Eingabe-Assembler-Ausgabe vorhanden ist, dann wird in der **Eingabe-Assembler**-Phase nichts angezeigt.  
  
 **Vertex-Shader**  
 Die Vertex-Shader-Stufe verarbeitet Scheitelpunkte, wobei für gewöhnlich Vorgänge wie die Transformation, das Skinning und die Beleuchtung ausgeführt werden. Vertex-Shader generieren die gleiche Anzahl an Scheitelpunkten, die sie als Eingabe verwenden.  
  
 Im Fenster „Pipelinestufen“ wird die Ausgabe „Vertex-Shader“ als ein Drahtmodell-Rasterbild veranschaulicht. Wählen Sie zum genaueren Anzeigen des Ergebnisses im Fenster **Grafikpipelinestufen** die Option **Vertex-Shader** aus, um die verarbeiteten Scheitelpunkte im Bild-Editor anzuzeigen.  
  
> [!NOTE]
>  Wenn die `POSITION`- oder `SV_POSITION`-Semantik nicht in der Vertex-Shader-Ausgabe vorhanden ist, dann wird in der **Vertex-Shader**-Phase nichts angezeigt.  
  
 **Hull-Shader** (nur Direct3D 11 und Direct3D 12)  
 Die Hull-Shader-Stufe verarbeitet Kontrollpunkte, die eine Oberfläche mit geringer Ordnung wie eine Line, ein Dreieck oder ein Quadrupel definieren. Als Ausgabe werden ein Geometriepatch mit höherer Ordnung und Patchkonstanten generiert, die an die Mosaikphase einer festen Funktion weitergegeben werden.  
  
 Die Hull-Shader-Stufe wird im Fenster „Pipelinestufen“ nicht visualisiert.  
  
 **Mosaikstufe** (nur Direct3D 11 und Direct3D 12)  
 Bei der Mosaikstufe handelt es sich um eine feste (nicht programmierbare) Funktionshardwareeinheit, die die Domäne vorverarbeitet, die durch die Ausgabe des Hull-Shaders repräsentiert wird. In der Ausgabe wird ein Samplingmuster der Domäne und ein Satz von kleineren Primitiven erstellt (Punkte, Linien, Dreiecke), die diese Beispiele verbinden.  
  
 Die Mosaikstufe wird im Fenster „Pipelinestufen“ nicht veranschaulicht.  
  
 **Domain-Shader** (nur Direct3D 11 und Direct3D 12)  
 Die Domänen-Shader-Stufe verarbeitet Geometriepatches höherer Ordnung aus dem Hull-Shader zusammen mit Mosaikfaktoren aus der Mosaikstufe. Die Mosaikfaktoren können Mosaikeingabefaktoren und -ausgabefaktoren enthalten. In der Ausgabe wird die Vertexposition eines Punkts im Ausgabepatch gemäß den Mosaikfaktoren berechnet.  
  
 Die Domain-Shader-Stufe wird im Fenster „Pipelinestufen“ nicht visualisiert.  
  
 **Geometrie-Shader**  
 Die Geometrie-Shader-Stufe verarbeitet gesamte Primitive (Punkte, Linien oder Dreiecke) zusammen mit optionalen Vertexdaten für direkt benachbarte Primitive. Im Gegensatz zu Vertex-Shadern können Geometrie-Shader mehr oder weniger Primitive generieren, als sie als Eingabe verwenden.  
  
 Im Fenster „Pipelinestufen“ wird die Geometrie-Shader-Ausgabe als ein Drahtmodell-Rasterbild veranschaulicht. Wählen Sie zum genaueren Anzeigen des Ergebnisses im Fenster **Grafikpipelinestufen** die Option **Geometrie-Shader** aus, um die verarbeiteten Primitive im Bild-Editor anzuzeigen.  
  
 **Stream-Ausgabestufe**  
 In der Stream-Ausgabestufe können Primitive vor der Rasterung und dem Schreiben in den Arbeitsspeicher abgefangen werden. Von dort aus können die Daten erneut als Eingabe in den Kreislauf zu den vorherigen Stufen der Grafikpipeline gelangen oder durch die CPU eingelesen werden.  
  
 Die Stream-Ausgabestufe wird im Fenster „Pipelinestufen“ nicht veranschaulicht.  
  
 **Stufe des Rasterizers**  
 Bei der Stufe des Rasterizers handelt es sich um eine feste (nicht programmierbare) Funktionshardwareeinheit, die durch Ausführung der Abtastlinienkonvertierung Vektorprimitive (Punkte, Linien, Dreiecke) in ein Rasterbild verarbeitet. Während der Rasterung werden Scheitelpunkte in homogene Clipräume umgewandelt und abgeschnitten. In der Ausgabe werden Pixel-Shader zugeordnet, und Pro-Vertex-Attribute werden primitivübergreifend interpoliert und für den Pixel-Shader zur Verfügung gestellt.  
  
 Die Stufe des Rasterizers wird im Fenster „Pipelinestufen“ nicht veranschaulicht.  
  
 **Pixel-Shader**  
 Die Pixel-Shader-Stufe verarbeitet gerasterte Primitive zusammen mit interpolierten Vertexdaten zum Genieren von Pro-Pixel-Werten wie Farbe und Tiefe.  
  
 Im Fenster „Pipelinestufen“ wird die Pixel-Shader-Ausgabe als ein Rasterbild ganz in Farbe veranschaulicht. Wählen Sie zum genaueren Anzeigen des Ergebnisses im Fenster **Grafikpipelinestufen** die Option **Pixel-Shader** aus, um die verarbeiteten Primitive im Bild-Editor anzuzeigen.  
  
 **Ausgabezusammenführung**  
 In der Ausgabemergestufe werden die Auswirkung der neu gerenderten Pixel zusammen mit den vorhandenen Inhalten der entsprechenden Puffer (Farbe, Tiefe und Schablone) kombiniert, um neue Werte in diesen Puffern zu generieren.  
  
 Im Fenster „Pipelinestufen“ wird die Ausgabezusammenführungsausgabe als ein Rasterbild ganz in Farbe veranschaulicht. Wählen Sie zum genaueren Anzeigen der Ergebnisse im Fenster **Grafikpipelinestufen** die Option **Ausgabezusammenführung** aus, um den zusammengeführten Framepuffer anzuzeigen.  
  
### <a name="vertex-shader-preview"></a>Vertex-Shader-Vorschau  
 Bei Auswahl die Vertexshader-Stufe in der **Grafikpipelinestufen** Fenster die **Eingabepuffer** wird eingeblendet. Hier werden die Details über die Liste der Scheitelpunkte angezeigt, die dem Vertex-Shader übermittelt werden, nachdem sie durch die Eingabe-Assembler-Stufe assembliert wurden.  
  
 ![Der Vertex-Shader-Phase Eingabepuffer Viewer](../debugger/media/gfx-diag-vertex-shader-inbuffers.png "Gfx_diag_vertex_shader_inbuffers")  
  
 Wählen Sie zum Anzeigen des Ergebnisses der Vertex-Shader-Stufe die Vertex-Shader-Stufenminiaturansicht aus, um ein gerastertes Drahtmodell in voller Größe des Gitters anzuzeigen, nachdem es durch den Vertex-Shader transformiert wurde.  
  
 ![Der Vertex-Shader-Stufe Ergebnisvorschau](../debugger/media/gfx-diag-vertex-shader-preview.png "Gfx_diag_vertex_shader_preview")  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Fehlende Objekte durch Vertex-Shading](../debugger/walkthrough-missing-objects-due-to-vertex-shading.md)   
 [Exemplarische Vorgehensweise: Debuggen von Renderingfehlern, die durch Schattierungen entstanden sind](../debugger/walkthrough-debugging-rendering-errors-due-to-shading.md)

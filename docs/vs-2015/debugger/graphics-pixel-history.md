---
title: Grafikpixelverlauf | Microsoft-Dokumentation
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
- vs.graphics.pixelhistory
ms.assetid: 0a2cbde5-1ad9-487e-857c-a3664158c268
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9ac64d352bfb6d6a35ea1bd9027d30f527aab116
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49208363"
---
# <a name="graphics-pixel-history"></a>Grafikpixelverlauf
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mit dem Fenster „Grafikpixelverlauf“ in der Visual Studio-Grafikanalyse können Sie nachvollziehen, wie sich Direct3D-Ereignisse, die während eines Frames Ihres Spiels oder Ihre App auftreten, auf ein bestimmtes Pixel auswirken.  
  
 Im Folgenden finden Sie das Pixelverlaufsfenster:  
  
 ![Ein Pixel mit drei Direct3D-Ereignissen im Verlauf. ](../debugger/media/gfx-diag-demo-pixel-history-orientation.png "Gfx_diag_demo_pixel_history_orientation")  
  
## <a name="understanding-the-pixel-history-window"></a>Grundlegendes zum Pixelverlaufsfenster  
 Mithilfe des Pixelverlaufs können Sie analysieren, wie sich Direct3D-Ereignisse während eines Frames auf ein bestimmtes Pixel oder Renderziel auswirken. Sie können ein Rendering-Problem auf ein bestimmtes Ereignis für Direct3D zurückführen, selbst wenn die nachfolgenden Ereignisse – oder nachfolgende Primitive im selben Ereignis – weiterhin den endgültigen Farbwert des Pixel verändern. Beispielsweise wird ein Pixel nicht ordnungsgemäß erzeugt und dann unleserlich durch ein anderes, halbtransparenten Pixel, dessen Farben in den Framebuffer-Kontrastwerten auftreten. Diese Art von Problem wäre nur schwer zu diagnostizieren, wenn Sie nur den endgültigen Inhalt des Renderingziels als Unterstützung zur Verfügung hätten.  
  
 Das Pixelverlaufsfenster zeigt den vollständigen Verlauf eines Pixels im Verlauf des ausgewählten Frames an. Die **letzte Framepuffer** am oberen Rand des Fensters zeigt die Farbe an, die am Framepuffer am Ende des Frames zusammen mit zusätzlichen Informationen über das Pixel wie z. B. der Frame, der sie stammen und des Bildschirms geschrieben wird koordiniert. Dieser Bereich enthält auch die **Alpha wiedergeben** Kontrollkästchen. Wenn dieses Kontrollkästchen aktiviert ist, die **letzte Framepuffer** werden Farbe und die Zwischenfarbe transparent über einem Schachbrettmuster angezeigt. Wenn das Kontrollkästchen deaktiviert ist, wird der Alphakanal der Farbwerte ignoriert.  
  
 Der untere Teil des Fensters zeigt die Ereignisse, die keine Gelegenheit hatten, die die Farbe des Pixels, zusammen mit Auswirkungen auf die **anfängliche** und **endgültige** Pseudo-Ereignissen an, die die ersten und endgültigen Farbwerte der darstellen. die Pixel in der framepufferausgabe. Der ursprüngliche Farbwert wird bestimmt durch das erste Ereignis, das die Farbe des Pixels änderte (in der Regel ein `Clear`-Ereignis). Eine Pixel hat immer diese beiden Pseudo-Ereignisse in dessen Verlauf, auch wenn keine weiteren Ereignisse betroffen sind. Wenn andere Ereignisse auf die Pixels auswirken konnten, werden sie angezeigt, zwischen den **anfängliche** und **endgültige** Ereignisse. Die Ereignisse können erweitert werden, um ihre Details anzuzeigen. Bei einfachen Ereignissen, wie der Deaktivierung eines Renderingziels, wirkt sich das Ereignis nur einen Farbwert aus. Komplexere Ereignisse, wie Zeichnen-Aufrufe, generieren mindestens eine Primitive, die zur Farbe des Pixels beitragen könnten.  
  
 Primitive, die vom Ereignis gezeichnet wurden, werden durch ihren Primitivtyp und Index zusammen mit der Gesamtzahl der Primitive für das Objekt angegeben. Angenommen, ein Bezeichner wie **Dreieck (1456) von (6214)** bedeutet, die der Primitiv dem 1456. Dreieck in einem Objekt entspricht, die aus 6214 Dreiecken besteht. Auf der linken Seite jeder Primitiv-ID befindet sich ein Symbol, das den Effekt des Primitivs auf das Pixel zusammenfasst. Primitive, die Auswirkungen auf die Pixelfarbe haben, werden durch ein abgerundetes Rechteck dargestellt, die mit der Ergebnisfarbe gefüllt ist. Primitive, die keine Auswirkungen auf die Pixelfarbe haben, werden durch Symbole dargestellt, die den Grund für den Ausschluss des Pixels angeben. Diese Symbole werden im Abschnitt beschriebenen [Ausschluss eines Primitivs](../debugger/graphics-pixel-history.md#exclusion) weiter unten in diesem Artikel.  
  
 Sie können jeden Primitiv erweitern, um zu untersuchen, wie die Pixel-Shader-Ausgabe mit der vorhandenen Pixelfarbe zusammengeführt wurde, um die Ergebnisfarbe zu erzeugen. Von hier aus können Sie den Pixel Shader-Code prüfen oder debuggen, der dem Primitiv-Typ zugeordnet ist, und Sie können den Vertex-Shader Knoten zum Überprüfen der Vertex-Shaders-Eingaben erweitern.  
  
###  <a name="exclusion"></a> Ausschluss eines Primitivs  
 Wenn ein Primitiv die Pixelfarbe nicht beeinflusst, kann der Ausschluss für eine Vielzahl von Gründen erfolgen. Jeder Grund wird durch ein Symbol dargestellt, das in dieser Tabelle beschrieben wird:  
  
|Symbol|Grund für den Ausschluss|  
|----------|--------------------------|  
|![Symbol für Tiefe Test Fehler. ](../debugger/media/vsg-hist-icon-failed-depth.png "Vsg_hist_icon_failed_depth")|Das Pixel wurde ausgeschlossen, weil der Tiefentest fehlgeschlagen ist.|  
|![Fehlerhafter scherentest Test-Symbol ("Fehler". ](../debugger/media/vsg-hist-icon-failed-scissor.png "Vsg_hist_icon_failed_scissor")|Das Pixel wurde ausgeschlossen, weil der Scherentest fehlgeschlagen ist.|  
|![Schablone Test-Symbol ("Fehler". ](../debugger/media/vsg-hist-icon-failed-stencil.png "Vsg_hist_icon_failed_stencil")|Das Pixel wurde ausgeschlossen, weil der Schablonentest fehlgeschlagen ist.|  
  
### <a name="draw-call-exclusion"></a>Ausschluss des Zeichenaufrufs  
 Wenn alle Primitive in einem Zeichnen-Aufruf von der Auswirkung auf das Renderingziel ausgeschlossen werden, da sie einen Test nicht bestehen, kann der Aufruf einer Zeichnung nicht erweitert werden, und ein Symbol, das dem Grund für den Ausschluss entspricht, wird daneben angezeigt. Die Gründe für den Ausschluss des Aufrufs einer Zeichnung ähneln den Gründen für den Ausschluss von Primitiven, und die Symbole sind ähnlich.  
  
### <a name="viewing-and-debugging-shader-code"></a>Anzeigen und Debuggen des Shader-Codes  
 Sie können mithilfe der Steuerelemente unter dem mit dem Shader verknüpften Primitiv Code für Vertex-, Hull-, Domain-, Geometry- und Pixel-Shader überprüfen und debuggen.  
  
##### <a name="to-view-a-shaders-source-code"></a>Um einen Shader-Quellcode anzuzeigen  
  
1.  In der **Grafikpixelverlauf** Fenster die Draw-Aufruf, der an den Shader entspricht Sie untersuchen, und erweitern es möchten.  
  
2.  Wählen Sie unter dem von Ihnen soeben erweiterten Zeichnen-Befehl ein Primitiv aus, welches das entsprechende Problem demonstriert, und erweitern Sie es.  
  
3.  Unter den Grundtyp, Sie möchten, führen Sie auf der Shader-Titellink, z. B. auf den Link **Vertex Shader obj: 30** um den Vertex-Shader-Quellcode anzuzeigen.  
  
    > [!TIP]
    >  Die Objektnummer **Obj:30**, identifiziert diesen Shader über die Grafikanalyse-Schnittstelle wie die Objekt-Tabelle und im pipelinestufenfenster.  
  
##### <a name="to-debug-a-shader"></a>Um einen Shader zu debuggen  
  
1.  In der **Grafikpixelverlauf** Fenster die Draw-Aufruf, der an den Shader entspricht Sie untersuchen, und erweitern es möchten.  
  
2.  Wählen Sie dann unter dem von Ihnen soeben erweiterten Zeichnen-Befehl ein Primitiv aus, welches das entsprechende Problem demonstriert, und erweitern Sie es.  
  
3.  Wählen Sie unter den Grundtyp, die Sie interessiert, **Debuggen starten**. Durch diesen Einstiegspunkt in den HLSL-Debugger erfolgt die standardmäßige Festlegung auf den ersten Aufruf des Shaders für das entsprechende Primitiv, d. h. das erste Pixel oder Vertex, das bzw. der durch den Shader verarbeitet wird. Es ist nur ein Pixel mit dem Primitiv verknüpft. Es liegen jedoch mehrere Vertex-Shader-Aufrufe für Linien und Dreiecke vor.  
  
     Um den Vertex-Shader-Aufruf für einen bestimmten Vertex Debuggen, erweitern die Titellink, und suchen Sie den Vertex, das Sie interessiert, und wählen Sie dann **Debuggen starten** daneben.  
  
### <a name="links-to-graphics-objects"></a>Links zu Grafikobjekten  
 Um die Grafikereignisse im Pixelverlauf zu verstehen, benötigen Sie möglicherweise Informationen über den Gerätezustand zum Zeitpunkt des Ereignisses oder über die Direct3D-Objekte, auf die das Ereignis verweist. Für jedes Ereignis im pixelverlauf der **Grafikpixelverlauf** Links zu den aktuellen Gerätestatus und zu verwandte Objekten.  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Fehlende Objekte durch Gerätestatus](../debugger/walkthrough-missing-objects-due-to-device-state.md)   
 [Exemplarische Vorgehensweise: Debuggen von Renderingfehlern, die durch Schattierungen entstanden sind](../debugger/walkthrough-debugging-rendering-errors-due-to-shading.md)




---
title: 'Exemplarische Vorgehensweise: Verwenden der Grafikdiagnose zum Debuggen eines Compute-Shaders | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 69287456-644b-4aff-bd03-b1bbb2abb82a
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9742fa2c17bf982cde7c919648d76c63ff761ac4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49250145"
---
# <a name="walkthrough-using-graphics-diagnostics-to-debug-a-compute-shader"></a>Exemplarische Vorgehensweise: Debuggen eines Compute-Shaders mithilfe der Grafikdiagnose
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie die Visual Studio-Grafikdiagnosetools zur Untersuchung eines Compute-Shaders verwendet werden, der falsche Ergebnisse generiert.  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben beschrieben:  
  
-   Verwenden der **Grafikereignisliste** , um mögliche Quellen des Problems zu suchen.  
  
-   Mithilfe der **Aufrufliste des Grafikereignisses** um zu bestimmen, welcher Shader wird ausgeführt, indem eine DirectCompute `Dispatch` Ereignis.  
  
-   Mithilfe der **Grafikpipelinestufen** Fenster und HLSL-debugger um den Compute-Shader zu untersuchen, die die Quelle des Problems ist.  
  
## <a name="scenario"></a>Szenario  
 In diesem Szenario haben Sie eine Fluiddynamiksimulation geschrieben, die DirectCompute zur Ausführung der berechnungsintensivsten Teile des Simulationsupdates verwendet. Beim Ausführen der App werden Dataset und Benutzeroberfläche korrekt wiedergegeben, die Simulation verhält sich jedoch nicht wie erwartet. Mithilfe der Grafikdiagnose können Sie den Fehler in einer Grafikprotokolldatei erfassen, um die App zu debuggen. Das Problem sieht in der App wie folgt aus:  
  
 ![Das simulierte Fluid verhält sich falsch. ](../debugger/media/gfx-diag-demo-compute-shader-fluid-problem.png "Gfx_diag_demo_compute_shader_fluid_problem")  
  
 Informationen zum Erfassen von Grafikproblemen in einem Grafikprotokoll finden Sie unter [Capturing Graphics Information](../debugger/capturing-graphics-information.md).  
  
## <a name="investigation"></a>Untersuchung  
 Sie können die Grafikprotokolldatei mithilfe der Grafikdiagnosetools laden, um die aufgezeichneten Frames zu überprüfen.  
  
#### <a name="to-examine-a-frame-in-a-graphics-log"></a>So überprüfen Sie einen Frame in einem Grafikprotokoll  
  
1.  Laden Sie ein Grafikprotokoll in Visual Studio, das einen Frame mit falschen Simulationsergebnissen enthält. Eine neue Grafikdiagnose-Registerkarte wird in Visual Studio angezeigt. Ganz oben auf dieser Registerkarte befindet sich die Renderingzielausgabe des ausgewählten Frames. Im unteren Teil befindet der **Frameliste**, die alle aufgezeichneten Frames als Miniaturansichten angezeigt.  
  
2.  In der **Frameliste**, wählen Sie einen Frame aus, die das falsche simulationsverhalten auftritt. Obwohl sich der Fehler scheinbar im Simulationscode und nicht im Renderingode befindet, müssen Sie trotzdem einen Frame auswählen, da DirectCompute-Ereignisse von einem Frame zum nächsten, gemeinsam mit Direct3D-Ereignissen aufgezeichnet werden. In diesem Szenario sieht die Grafikprotokoll-Registerkarte wie folgt aus:  
  
     ![Das grafikprotokolldokument in Visual Studio. ](../debugger/media/gfx-diag-demo-compute-shader-fluid-step-1.png "gfx_diag_demo_compute_shader_fluid_step_1")  
  
 Wenn Sie einen Frame ausgewählt haben, der das Problem demonstriert, können Sie die **Grafikereignisliste** verwenden, um das Problem zu diagnostizieren. Die **Graphics Event List** enthält ein Ereignis für jeden directcompute- und Direct3D-API-Aufruf, der während des aktiven Frames erfolgt, z. B. API-Aufrufe, um eine Berechnung auf dem GPU ausgeführt oder um das Dataset oder der Benutzeroberfläche zu rendern. In diesem Fall interessieren uns die `Dispatch`-Ereignisse, die Teile der im GPU ausgeführten Simulation darstellen.  
  
#### <a name="to-find-the-dispatch-event-for-the-simulation-update"></a>So finden Sie das Dispatchereignis für das Simulationsupdate  
  
1.  Auf der **Grafikdiagnose** Symbolleiste wählen **Ereignisliste** zum Öffnen der **Graphics Event List** Fenster.  
  
2.  Überprüfen Sie die **Graphics Event List** für das Zeichnen-Ereignis, das das Dataset gerendert wird. Um dies zu vereinfachen, geben Sie `Draw` in die **Suche** der oberen rechten Ecke des Dialogfelds die **Graphics Event List** Fenster. Damit wird die Liste gefiltert und enthält nur Ereignisse, die "Zeichnen" im Titel haben. In diesem Szenario ermitteln Sie, dass die folgenden Zeichnen-Ereignisse aufgetreten sind:  
  
     ![Die Ereignisliste &#40;EL&#41; zeigt zeichnen-Ereignisse. ](../debugger/media/gfx-diag-demo-compute-shader-fluid-step-2.png "gfx_diag_demo_compute_shader_fluid_step_2")  
  
3.  Navigieren Sie durch die einzelnen Zeichnen-Ereignisse, und beobachten Sie das Renderziel in der Dokumentregisterkarte "Grafikprotokolle".  
  
4.  Halten Sie an, wenn das gerenderte Dataset erstmals im Renderziel angezeigt wird. In diesem Szenario wird das Dataset im ersten Zeichnen-Ereignis gerendert. Der Fehler in der Simulation wird angezeigt:  
  
     ![Dieses draw-Ereignis rendert das simulationsdataset. ](../debugger/media/gfx-diag-demo-compute-shader-fluid-step-3.png "gfx_diag_demo_compute_shader_fluid_step_3")  
  
5.  Jetzt überprüfen die **Graphics Event List** für die `Dispatch` -Ereignis, das die Simulation aktualisiert. Da es wahrscheinlich ist, dass die Simulation vor dem Rendering aktualisiert wird, können Sie sich zunächst auf die `Dispatch`-Ereignisse konzentrieren, die vor dem Zeichnen-Ereignis auftreten, das die Ergebnisse rendert. Um dies zu vereinfachen, Ändern der **Suche** Feld lesen `Draw;Dispatch;CSSetShader(`. Dadurch wird die Liste gefiltert, sodass sie zusätzlich zu den Zeichnen-Ereignissen auch `Dispatch`- und `CSSetShader`-Ereignisse enthält. In diesem Szenario ermitteln Sie, dass mehrere `Dispatch`-Ereignisse vor dem Zeichnen-Ereignis aufgetreten sind:  
  
     ![Der EREIGNISLISTE werden Draw-, Dispatch- und CSSetShader-Ereignisse](../debugger/media/gfx-diag-demo-compute-shader-fluid-step-4.png "gfx_diag_demo_compute_shader_fluid_step_4")  
  
 Nachdem Sie nun wissen, welche der vielen `Dispatch`-Ereignisse möglicherweise mit dem Problem in Verbindung stehen, können diese ausführlicher überprüfen.  
  
#### <a name="to-determine-which-compute-shader-a-dispatch-call-executes"></a>So ermitteln Sie, welcher Compute-Shader von einem Dispatchaufruf ausgeführt wird  
  
1.  Auf der **Grafikdiagnose** Symbolleiste wählen **Ereignisaufrufliste** Öffnen der **Aufrufliste des Grafikereignisses** Fenster.  
  
2.  Bewegen Sie sich ausgehend vom Zeichnen-Ereignis, das die Simulationsergebnisse rendert, rückwärts durch die vorherigen `CSSetShader`-Ereignisse. Klicken Sie auf die **Aufrufliste des Grafikereignisses** Fenster die oberste Funktion verwenden, zu der Aufrufsite zu navigieren. An der Aufrufsite können Sie den ersten Parameter die [CSSetShader](http://msdn.microsoft.com/library/ff476402.aspx) Funktionsaufruf, um zu bestimmen, welcher Shader durch das nächste ausgeführt wird `Dispatch` Ereignis.  
  
 In diesem Szenario befinden sich in jedem Frame drei Paare mit `CSSetShader`- und `Dispatch`-Ereignissen. Von hinten angefangen stellt das dritte Paar den Integrationsschritt dar (in dem die flüssigen Partikel tatsächlich verschoben werden), das zweite Paare stellt den Schritt der Kräfteberechnung dar (in dem die Kräfte berechnet werden, die jedes einzelne Partikel beeinflussen), und das dritte Paar enthält den Schritt der Dichteberechnung.  
  
#### <a name="to-debug-the-compute-shader"></a>So debuggen Sie den Compute-Shader  
  
1.  Auf der **Grafikdiagnose** Symbolleiste wählen **Pipelinestufen** zum Öffnen der **Grafikpipelinestufen** Fenster.  
  
2.  Wählen Sie das dritte `Dispatch` Ereignis (diejenige, die das Zeichnen-Ereignis unmittelbar vorangestellt) und dann auf die **Grafikpipelinestufen** Fenster unter dem **Compute-Shader** -Stufe  **Starten Sie das Debuggen**.  
  
     ![Wählen das dritte Dispatch-Ereignis in der EL.](../debugger/media/gfx-diag-demo-compute-shader-fluid-step-6.png "gfx_diag_demo_compute_shader_fluid_step_6")  
  
     Der HLSL-Debugger wird am Shader gestartet, der den Integrationsschritt ausführt.  
  
3.  Überprüfen Sie den Quellcode des Compute-Shaders auf den Integrationsschritt, um die Fehlerursache zu finden. Wenn Sie die Grafikdiagnose verwenden, um den HLSL-Compute-Shader-Code zu debuggen, können Sie den Code schrittweise ausführen und andere Ihnen vertraute Debugtools wie Überwachungsfenster verwenden. In diesem Szenario ermitteln Sie, dass scheinbar kein Fehler im Compute-Shader vorhanden ist, der den Integrationsschritt ausführt.  
  
     ![Debuggen des IntegrateCS-Compute-Shaders. ](../debugger/media/gfx-diag-demo-compute-shader-fluid-step-7.png "gfx_diag_demo_compute_shader_fluid_step_7")  
  
4.  Zum Beenden des Debuggens im Compute-Shaders in der **Debuggen** Symbolleiste wählen **Debuggen beenden** (Tastatur: UMSCHALT + F5).  
  
5.  Wählen Sie danach Sie das zweite `Dispatch`-Ereignis aus, und starten Sie das Debugging des Compute-Shaders, wie Sie dies bereits im vorherigen Schritt getan haben.  
  
     ![Wählen das zweite Dispatch-Ereignis in der EL.](../debugger/media/gfx-diag-demo-compute-shader-fluid-step-8.png "gfx_diag_demo_compute_shader_fluid_step_8")  
  
     Der HLSL-Debugger wird am Shader gestartet, der die Kräfte berechnet, die auf alle flüssigen Partikel einwirken.  
  
6.  Überprüfen Sie den Schritt der Kräfteberechnung im Quellcode des Compute-Shaders. In diesem Szenario ermitteln Sie, dass die Fehlerquelle sich hier befindet.  
  
     ![Debuggen der ForceCS&#95;einfache compute-Shader. ](../debugger/media/gfx-diag-demo-compute-shader-fluid-step-9.png "gfx_diag_demo_compute_shader_fluid_step_9")  
  
 Nachdem Sie den Ursprung des Fehlers bestimmt haben, können Sie das Debuggen beenden und den Quellcode des Compute-Shaders dahingehend ändern, dass der Abstand zwischen den interagierenden Partikeln ordnungsgemäß berechnet wird. In diesem Szenario ändern Sie nur die Zeile `float2 diff = N_position + P_position;` in `float2 diff = N_position - P_position;`:  
  
 ![Der korrigierte Compute&#45;Shader-Code. ](../debugger/media/gfx-diag-demo-compute-shader-fluid-step-10.png "gfx_diag_demo_compute_shader_fluid_step_10")  
  
 Da die Compute-Shader zur Laufzeit kompiliert werden, können Sie in diesem Szenario die App nach Durchführung der Änderungen einfach neu starten und beobachten, welche Auswirkung die Änderungen auf die Simulation haben. Sie müssen die App nicht neu erstellen. Wenn Sie die App ausführen, können Sie feststellen, dass sich die Simulation nun ordnungsgemäß verhält.  
  
 ![Das simulierte Fluid verhält sich korrekt. ](../debugger/media/gfx-diag-demo-compute-shader-fluid-resolution.png "Gfx_diag_demo_compute_shader_fluid_resolution")




---
title: Aufzeichnen von Grafikinformationen | Microsoft Docs
ms.custom: ''
ms.date: 02/09/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.frame
- vs.graphics.capturewindow
- VS.ToolsOptionsPages.Graphics_Diagnostics.Capture
ms.assetid: 187ce86e-e340-4f6c-8937-8e8f1027a17f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e00dd4d0fae184f092efabb5df4a4f27e76a653a
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
---
# <a name="capturing-graphics-information"></a>Erfassen von Grafikinformationen
Erfassen Sie Grafikinformationen aus Ihrer Direct3D-App, damit Sie die Visual Studio-Grafikanalyse zum Diagnostizieren von Rendering- und Leistungsproblemen verwenden können.  
  
## <a name="capturing-graphics-information"></a>Aufzeichnen von Grafikinformationen  
 Das Aufzeichnen von Grafikinformationen ist ein zweistufiger Prozess. Führen Sie zuerst Ihre App unter der Grafikdiagnose aus, und geben Sie dann einen oder mehrere Frames an, aus denen ausführliche Informationen erfasst werden sollen.  
  
### <a name="to-run-your-app-under-graphics-diagnostics"></a>So führen Sie die App unter der Grafikdiagnose aus  
  
-   Wählen Sie in der Menüleiste **Debuggen**, **Grafiken**, **Debuggen Grafiken**. (Tastatur: Drücken Sie ALT+F5)  
  
-   Auf der **Grafiken** Symbolleiste, wählen Sie die **Debuggen Grafiken** Schaltfläche.  
  
 Wenn eine App unter der Grafikdiagnose ausgeführt wird, werden laufend bestimmte Arten von Grafikinformationen aufgezeichnet, beispielsweise Geräteinstallation, Erstellung der Swapkette, Erstellung von Grafikobjekten und Ressourcen sowie andere wichtige Ereignisse, die Auswirkungen auf einen oder mehrere Frames haben. Gleichzeitig können Sie ausführliche Informationen über bestimmte Frames erfassen. Dazu gehören Zeichnen-Aufrufe und Compute-Shader-Dispatchvorgänge gemeinsam mit Direct3D-Objekten und -Ressourcen, die diese unterstützen.  
  
### <a name="to-capture-a-frame"></a>So erfassen Sie einen Frame  
  
-   In Visual Studio auf die **Grafiken** -Symbolleiste klicken Sie auf die **Frame erfassen** Schaltfläche ![grafikerfassung Symbol "Bildschaltfläche"](media/debuggingdirectxgraphics.png "DebuggingDirectXGraphics").  
  
-   Drücken Sie auf der Tastatur die Taste "Druck" aus.
  
    > [!NOTE]
    >  Während der Ausführung einer app unter **Grafikdiagnose**, die Taste "Druck" kann nur verwendet werden, um Frames von Grafikinformationen aufzuzeichnen; wird nicht tastenfunktion ausgeführt. Dieses Verhalten bleibt bestehen, bis Sie die Aufzeichnung von Grafikinformationen beenden (üblicherweise durch Beenden des Debuggings oder das normale Verlassen der App), auch wenn der Fokus auf einer anderen Anwendung liegt.  
  
-   In der Visual Studio-erfassungsschnittstelle gewählt haben die **Frame erfassen** Schaltfläche unterhalb der **diagnosesitzung** Zeitachse, oder wählen Sie die große **Frame erfassen** Schaltfläche unterhalb der **Frames pro Sekunde** eine Lane und rechts von zuvor erfassten Frames. Beide Schaltflächen werden in der folgenden Abbildung hervorgehoben.  
  
     ![Sammeln von Frames mithilfe des GPU-Auslastungstools.](media/pix_gpu_usage_tool_capture_frame.png)  
  
     Wenn Sie bereit sind, die Frames zu untersuchen Sie erfasst haben, starten Sie den **Visual Studio-Grafikanalyse** anhand der **Frame...**  Link über den Bildminiaturansichten oder durch Doppelklicken auf die Miniaturansicht.  
  
 Nur ganze Frames können erfasst werden, wenn Sie eine Aufzeichnung starten, es daher wirklich die Grafikinformationen aus dem nächsten Frame, die aufgezeichnet werden. Die Aufzeichnung beginnt sofort nach Darstellung des Frames, in dem Sie die Aufzeichnung gestartet haben, und endet, wenn der aufgezeichnete Frame dargestellt wird. Während die App unter der Grafikdiagnose ausgeführt wird, können Sie so viele Frames aufzeichnen, wie Sie möchten. Wenn Sie keine Frames aufzeichnen, wird das Grafikprotokoll verworfen.  
  
 Beim Erfassen von Frames zeigt Visual Studio das Diagnosesitzungsfenster (.diagsession) an. Wenn Sie dieses Fenster schließen, beenden Sie das Debuggen oder die app zu schließen, können keine Sie keine Frames mehr in dieses Protokoll erfassen. Wenn Sie weitere Grafikinformationen erfassen möchten, müssen Sie die App erneut unter der Grafikdiagnose ausführen, um ein neue Diagnosesitzung zu starten.  
  
### <a name="graphics-diagnostics-capture-options"></a>Erfassungsoptionen der Grafikdiagnose  
 Sie können die Aufzeichnung konfigurieren, um Aufruflisten für alle Grafikereignisse oder eine eingeschränkte Teilmenge zu sammeln, die HUD-Aufzeichnung zu deaktivieren und den Capture-Kompatibilitätsmodus zu deaktivieren oder zu aktivieren.  
  
#### <a name="to-configure-graphics-diagnostics-capture-options"></a>So konfigurieren Sie die Aufnahmeoptionen für die Grafikdiagnose  
  
1.  Klicken Sie in der Menüleiste auf Extras, Optionen. Das Dialogfeld Optionen wird angezeigt.  
  
2.  Wählen Sie Grafikdiagnose in der Kategorieliste auf der linken Seite und konfigurieren Sie die gewünschten Optionen für die Grafikdiagnose.  
  
     **Sammeln von Aufruflisten während der Aufzeichnung (verlangsamt die Aufzeichnung)**  
     Aktivieren Sie dieses Kontrollkästchen, um die Aufruflisten zu sammeln. Standardmäßig werden die Aufruflisten nicht erfasst. Um Aufruflisten zu erfassen, stellen sicher, dass die **Aufrufstapel während der Aufzeichnung (verlangsamt die Erfassung** Kontrollkästchen wird festgelegt, zum Aktivieren der Sammlung, und legen Sie entweder die **für zeichnen, Versand, vorhanden und bezogen Marker**Option (Standard), um nur die wichtigsten Aufruflisten zu sammeln oder den **für alles, was** Option aus, um alle Aufruflisten zu sammeln. Zum Beenden der Erfassung von Aufruflisten zu einem späteren Zeitpunkt Deaktivieren der **Aufrufstapel während der Aufzeichnung (verlangsamt die Erfassung** Kontrollkästchen.  
  
     **In-Game-HUD während der Aufzeichnung deaktivieren**  
     Aktivieren Sie dieses Kontrollkästchen, um die HUD-Überlagerung zu deaktivieren, die eine Anwendung unter der Grafikdiagnose in der Regel anzeigt. Deaktivieren Sie das Kontrollkästchen Sie, um die HUD-Überlagerung anzuzeigen.  
  
     **Erfassen im Kompatibilitätsmodus**  
     Aktivieren Sie dieses Kontrollkästchen, um Grafikinformationen im Kompatibilitätsmodus zu erfassen. Erfassen im Kompatibilitätsmodus ist die Standardeinstellung. Unter dem Kompatibilitätsmodus wird Direct3D nicht melden, dass die GPU zusätzliche Features unterstützt, die über die in der Basis-KE-Ebene definierten Features hinausgehen. Dadurch wird verhindert, dass die Anwendung bei Verwendung von Hardware-spezifischen Erweiterungen der GPU erfasst wird, und es wird sichergestellt, dass das Grafikprotokoll mit jeder GPU, die die gleiche oder eine höhere Funktionsebene unterstützt, wiedergegeben werden kann. Deaktivieren Sie dieses Kontrollkästchen, um den Kompatibilitätsmodus zu deaktivieren; Protokolle mit deaktiviertem Kompatibilitätsmodus werden nicht auf allen GPUs wiedergegeben, die nicht die gleichen zusätzlichen Funktionen unterstützen, die von der Anwendung während der Aufnahme verwendet wurden.  
  
     **Beenden Sie Erfassung, wenn alle SDK-Ebenen-Fehler gefunden werden**  
     Aktivieren Sie dieses Kontrollkästchen, um die Erfassung sofort anzuhalten, wenn Fehler ermittelt werden.  
  
## <a name="capturing-graphics-information-remotely"></a>Grafikinformationen remote aufzeichnen  
 Grafikinformationen können von einer App aufgezeichnet werden, die auf dem lokalen Computer, einem Remotecomputer oder einem Remotegerät ausgeführt wird. Die Remoteerfassung wird auf [!INCLUDE[winblue_client_2](../includes/winblue_client_2_md.md)]-Computern und [!INCLUDE[winblue_winrt_2](../includes/winblue_winrt_2_md.md)]-Geräten unterstützt. Konfigurieren Sie Ihr Projekt für das Remotedebugging, wenn Sie Grafikinformationen von einer remote ausgeführten App aufzeichnen möchten, und führen Sie die App wie zuvor beschrieben unter der Grafikdiagnose aus. Die App wird auf dem Remotecomputer ausgeführt, und die erfassten Grafikinformationen werden auf dem Entwicklungscomputer aufgezeichnet.  
  
 Wie Sie Ihr Projekt für das Remotedebugging konfigurieren, hängt von der Art der App ab, die Sie entwickeln, und von der dabei verwendeten Programmiersprache. Informationen zum Konfigurieren des Remotedebuggings für eine uwp-app finden Sie unter [ausführen uwp-apps auf einem Remotecomputer](../run-windows-store-apps-on-a-remote-machine.md). Informationen zum Konfigurieren des Remotedebuggings für eine Windows-desktop-app finden Sie unter [Remotedebuggen](../remote-debugging.md).  
  
 Sie können später einen Remotecomputer oder ein Remotegerät verwenden, um die Grafikinformationen unabhängig vom Gerät wiederzugeben, auf dem sie erfasst wurden. Weitere Informationen finden Sie unter [Vorgehensweise: Ändern des Grafikdiagnose-Wiedergabecomputers](how-to-change-the-graphics-diagnostics-playback-machine.md).  
  
## <a name="capturing-graphics-information-from-the-command-line"></a>Das Aufzeichnen von Grafikinformationen von der Befehlszeile aus  
 Grafikinformationen können von einer Anwendung mit einem Befehlszeilentool erfasst werden. Dieses Tool DXCap.exe kann Grafikinformationen schnell erfassen und ohne Verwendung von Visual Studio oder programmgesteuerte Aufnahme wiedergeben. Insbesondere können Sie DXCap.exe für die Automatisierung oder in einer Testumgebung verwenden. Weitere Informationen zu DXCap.exe, finden Sie unter [Befehlszeilen-Erfassungs-Tool](command-line-capture-tool.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Erfassen von Grafikinformationen](walkthrough-capturing-graphics-information.md)
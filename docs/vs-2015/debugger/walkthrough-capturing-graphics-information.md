---
title: 'Exemplarische Vorgehensweise: Erfassen von Grafikinformationen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 48f12f6e-57b4-48ec-a145-89fa71a42424
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9ebd0453347084d1662c6bc7837fc1e96f498fbd
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60053883"
---
# <a name="walkthrough-capturing-graphics-information"></a>Exemplarische Vorgehensweise: Aufzeichnen von Grafikinformationen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese exemplarische Vorgehensweise veranschaulicht, wie die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Grafikdiagnose verwendet wird, um Grafikinformationen aus einer Direct3D-App manuell zu erfassen.  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben beschrieben:  
  
- Verbinden der Grafikdiagnose mit der App  
  
- Aufzeichnen von Grafikinformationen  
  
## <a name="capturing-graphics-information"></a>Aufzeichnen von Grafikinformationen  
 Sie müssen zunächst die benötigten Grafikinformationen erfassen, um die Grafikdiagnosetools verwenden zu können. Verwenden Sie den Befehl **Diagnose starten** , um die Erfassung zu aktivieren und die Grafikdiagnose mit der App zu verbinden, wenn diese gestartet wird.  
  
#### <a name="to-enable-the-capture-of-graphics-information-after-a-project-or-solution-is-loaded"></a>So aktivieren Sie die Erfassung von Grafikinformationen, nachdem Sie ein Projekt oder eine Projektmappe geladen haben  
  
1. Laden Sie in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]eine Projekt- oder eine Projektmappendatei für die App, von der Sie Grafikinformationen erfassen möchten.  
  
2. Klicken Sie in der Grafikdiagnose-Symbolleiste auf **Diagnose starten**.  
  
#### <a name="to-enable-the-capture-of-graphics-information-without-loading-a-project-or-solution"></a>So aktivieren Sie die Erfassung von Grafikinformationen, ohne ein Projekt oder eine Projektmappe zu laden  
  
1. Klicken Sie in der Menüleiste auf **Datei**, dann auf **Öffnen**und **Projekt/Projektmappe**. Das Dialogfeld **Projekt öffnen** wird angezeigt.  
  
2. Anstelle einer Projekt- oder einer Projektmappendatei geben Sie die ausführbare Datei für die Anwendung an, von der Sie Grafikinformationen von erfassen möchten, und wählen Sie dann **Öffnen**aus.  
  
3. Klicken Sie in der Menüleiste auf **Debuggen**, dann auf **Grafik**und **Diagnose starten**.  
  
   Wenn die App gestartet ist und Frames rendert, können Sie Grafikinformationen erfassen.  
  
#### <a name="to-capture-graphics-information"></a>So erfassen Grafikinformationen  
  
- Wählen Sie in der Grafikdiagnose-Symbolleiste die Schaltfläche **Erfassen** aus. ![Grafikerfassung Schaltflächensymbol](../debugger/media/debuggingdirectxgraphics.png "DebuggingDirectXGraphics")  
  
   - oder -   
  
   Wenn die App auf dem Bildschirm angezeigt wird, drücken Sie die **Drucktaste**.  
  
  Immer wenn Sie Informationen über Frames erfassen, zeichnet die Grafikdiagnose die Direct3D-Ereignisse und den zugeordneten Zustand auf und fügt die Daten einem Grafikprotokoll hinzu. Für jede Grafikdiagnosesitzung wird ein neues Grafikprotokoll erstellt. Weitere Informationen zu grafikprotokollen finden Sie unter [Übersicht](../debugger/overview-of-visual-studio-graphics-diagnostics.md).  
  
## <a name="next-steps"></a>Nächste Schritte  
 Diese exemplarische Vorgehensweise veranschaulicht, wie Grafikinformationen manuell erfasst werden. Im nächsten Schritt haben Sie folgende Möglichkeit:  
  
- Erfahren Sie, wie Sie aufgezeichnete Grafikinformationen mithilfe der Grafikdiagnosetools analysieren können. Finden Sie unter [Übersicht](../debugger/overview-of-visual-studio-graphics-diagnostics.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Capturing Graphics Information](../debugger/capturing-graphics-information.md)

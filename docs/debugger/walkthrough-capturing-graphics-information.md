---
title: "Exemplarische Vorgehensweise: Erfassen von Grafikinformationen | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 48f12f6e-57b4-48ec-a145-89fa71a42424
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Exemplarische Vorgehensweise: Erfassen von Grafikinformationen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese exemplarische Vorgehensweise veranschaulicht, wie die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Grafikdiagnose verwendet wird, um Grafikinformationen aus einer Direct3D\-App manuell zu erfassen.  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben beschrieben:  
  
-   Verbinden der Grafikdiagnose mit der App  
  
-   Aufzeichnen von Grafikinformationen  
  
## Aufzeichnen von Grafikinformationen  
 Sie müssen zunächst die benötigten Grafikinformationen erfassen, um die Grafikdiagnosetools verwenden zu können. Verwenden Sie den Befehl **Diagnose starten**, um die Erfassung zu aktivieren und die Grafikdiagnose mit der App zu verbinden, wenn diese gestartet wird.  
  
#### So aktivieren Sie die Erfassung von Grafikinformationen, nachdem Sie ein Projekt oder eine Projektmappe geladen haben  
  
1.  Laden Sie in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] eine Projekt\- oder eine Projektmappendatei für die App, von der Sie Grafikinformationen erfassen möchten.  
  
2.  Klicken Sie in der Grafikdiagnose\-Symbolleiste auf **Diagnose starten**.  
  
#### So aktivieren Sie die Erfassung von Grafikinformationen, ohne ein Projekt oder eine Projektmappe zu laden  
  
1.  Klicken Sie in der Menüleiste auf **Datei**, dann auf **Öffnen** und **Projekt\/Projektmappe**. Das Dialogfeld **Projekt öffnen** wird angezeigt.  
  
2.  Anstelle einer Projekt\- oder einer Projektmappendatei geben Sie die ausführbare Datei für die Anwendung an, von der Sie Grafikinformationen von erfassen möchten, und wählen Sie dann **Öffnen** aus.  
  
3.  Klicken Sie in der Menüleiste auf **Debuggen**, dann auf **Grafik** und **Diagnose starten**.  
  
 Wenn die App gestartet ist und Frames rendert, können Sie Grafikinformationen erfassen.  
  
#### So erfassen Grafikinformationen  
  
-   Wählen Sie in der Grafikdiagnose\-Symbolleiste die Schaltfläche **Erfassen** aus.![Symbol "Schaltfläche Grafikerfassung“](~/docs/debugger/graphics/media/debuggingdirectxgraphics.png "DebuggingDirectXGraphics")  
  
     \- oder \-  
  
     Wenn die App auf dem Bildschirm angezeigt wird, drücken Sie die **Drucktaste**.  
  
 Immer wenn Sie Informationen über Frames erfassen, zeichnet die Grafikdiagnose die Direct3D\-Ereignisse und den zugeordneten Zustand auf und fügt die Daten einem Grafikprotokoll hinzu. Für jede Grafikdiagnosesitzung wird ein neues Grafikprotokoll erstellt. Informationen zu Grafikprotokollen finden Sie unter [Übersicht](../debugger/overview-of-visual-studio-graphics-diagnostics.md).  
  
## Nächste Schritte  
 Diese exemplarische Vorgehensweise veranschaulicht, wie Grafikinformationen manuell erfasst werden. Im nächsten Schritt haben Sie folgende Möglichkeit:  
  
-   Erfahren Sie, wie Sie aufgezeichnete Grafikinformationen mithilfe der Grafikdiagnosetools analysieren können. Siehe [Übersicht](../debugger/overview-of-visual-studio-graphics-diagnostics.md).  
  
## Siehe auch  
 [Erfassen von Grafikinformationen](../debugger/capturing-graphics-information.md)
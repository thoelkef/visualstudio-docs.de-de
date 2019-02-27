---
title: 'Exemplarische Vorgehensweise: Erfassen von Grafikinformationen | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 48f12f6e-57b4-48ec-a145-89fa71a42424
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 24ddbcef7c4ebfaa61dfd225c2d1fa13a23b3344
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56711773"
---
# <a name="walkthrough-capturing-graphics-information"></a>Exemplarische Vorgehensweise: Erfassen von Grafikinformationen
Diese exemplarische Vorgehensweise veranschaulicht, wie die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] -Grafikdiagnose verwendet wird, um Grafikinformationen aus einer Direct3D-App manuell zu erfassen.

 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben beschrieben:

-   Verbinden der Grafikdiagnose mit der App

-   Aufzeichnen von Grafikinformationen

## <a name="capturing-graphics-information"></a>Aufzeichnen von Grafikinformationen
 Sie müssen zunächst die benötigten Grafikinformationen erfassen, um die Grafikdiagnosetools verwenden zu können. Verwenden Sie den Befehl **Diagnose starten** , um die Erfassung zu aktivieren und die Grafikdiagnose mit der App zu verbinden, wenn diese gestartet wird.

#### <a name="to-enable-the-capture-of-graphics-information-after-a-project-or-solution-is-loaded"></a>So aktivieren Sie die Erfassung von Grafikinformationen, nachdem Sie ein Projekt oder eine Projektmappe geladen haben

1. Laden Sie in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]eine Projekt- oder eine Projektmappendatei für die App, von der Sie Grafikinformationen erfassen möchten.

2. Klicken Sie in der Grafikdiagnose-Symbolleiste auf **Diagnose starten**.

#### <a name="to-enable-the-capture-of-graphics-information-without-loading-a-project-or-solution"></a>So aktivieren Sie die Erfassung von Grafikinformationen, ohne ein Projekt oder eine Projektmappe zu laden

1. Klicken Sie in der Menüleiste auf **Datei**, dann auf **Öffnen**und **Projekt/Projektmappe**. Das Dialogfeld **Projekt öffnen** wird angezeigt.

2. Anstelle einer Projekt- oder einer Projektmappendatei geben Sie die ausführbare Datei für die Anwendung an, von der Sie Grafikinformationen von erfassen möchten, und wählen Sie dann **Öffnen**aus.

3. Klicken Sie in der Menüleiste auf **Debuggen**, dann auf **Grafik**und **Diagnose starten**.

   Wenn die App gestartet ist und Frames rendert, können Sie Grafikinformationen erfassen.

#### <a name="to-capture-graphics-information"></a>So erfassen Grafikinformationen

- Wählen Sie in der Grafikdiagnose-Symbolleiste die Schaltfläche **Erfassen** aus. ![Grafikerfassung Schaltflächensymbol](media/debuggingdirectxgraphics.png "DebuggingDirectXGraphics")

   - oder - 

   Wenn die App auf dem Bildschirm angezeigt wird, drücken Sie die **Drucktaste**.

  Immer wenn Sie Informationen über Frames erfassen, zeichnet die Grafikdiagnose die Direct3D-Ereignisse und den zugeordneten Zustand auf und fügt die Daten einem Grafikprotokoll hinzu. Für jede Grafikdiagnosesitzung wird ein neues Grafikprotokoll erstellt. Weitere Informationen zu grafikprotokollen finden Sie unter [Übersicht](overview-of-visual-studio-graphics-diagnostics.md).

## <a name="next-steps"></a>Nächste Schritte
 Diese exemplarische Vorgehensweise veranschaulicht, wie Grafikinformationen manuell erfasst werden. Im nächsten Schritt haben Sie folgende Möglichkeit:

-   Erfahren Sie, wie Sie aufgezeichnete Grafikinformationen mithilfe der Grafikdiagnosetools analysieren können. Finden Sie unter [Übersicht](overview-of-visual-studio-graphics-diagnostics.md).

## <a name="see-also"></a>Siehe auch
- [Capturing Graphics Information](capturing-graphics-information.md)
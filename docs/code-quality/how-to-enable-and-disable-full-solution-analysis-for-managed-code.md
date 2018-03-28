---
title: 'Vorgehensweise: Aktivieren und deaktivieren Sie vollständige Projektmappenanalyse für verwalteten Code | Microsoft Docs'
ms.date: 03/23/2018
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-code-analysis
ms.workload:
- dotnet
ms.openlocfilehash: 4c5985792138d334de103523478841917555fc56
ms.sourcegitcommit: 768118d470da9c7164d2f23ca918dfe26a4be72f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Vorgehensweise: Aktivieren und deaktivieren Sie die vollständige projektmappenanalyse für verwalteten Code

*Vollständige projektmappenanalyse* ist eine Visual Studio-Funktion, ermöglicht es Ihnen, Codeanalysefehler nur in einem geöffneten Visual c# oder Visual Basic-Dateien in der Projektmappe finden Sie unter, oder im Code auch Dateien, die, geschlossen werden. Wird standardmäßig vollständige projektmappenanalyse *aktiviert* für Visual Basic und *deaktiviert* für Visual c#.

Es kann hilfreich sein, alle Probleme in allen Dateien finden Sie unter, aber sie können auch störend sein. Er verlangsamt Visual Studio Wenn Ihre Lösung sehr groß ist oder viele Dateien hat. Um die Anzahl der Probleme angezeigt und Visual Studio zur Leistungssteigerung, können Sie die vollständige projektmappenanalyse deaktivieren. Sie können diese Funktion problemlos aktivieren Sie bei Bedarf erneut.

## <a name="to-toggle-full-solution-analysis"></a>Vollständige projektmappenanalyse aktivieren bzw. deaktivieren

1. So öffnen die **Optionen** wählen Sie im Dialogfeld auf der Menüleiste in Visual Studio **Tools** > **Optionen**.

1. In der **Optionen** Dialogfeld Wählen Sie **Texteditor** > **c#** oder **grundlegende**  >   **Erweiterte**.

1. Wählen Sie die **vollständige projektmappenanalyse aktivieren** Kontrollkästchen, um vollständige projektmappenanalyse aktivieren oder deaktivieren Sie das Kontrollkästchen, um ihn zu deaktivieren. Wählen Sie **OK** Wenn Sie fertig sind.

    ![Vollständige Lösung Analysis Kontrollkästchen zu aktivieren.](../code-quality/media/options-enable-full-solution-analysis.png)

## <a name="results-of-enabling-and-disabling-full-solution-analysis"></a>Ergebnisse der aktivieren und deaktivieren die vollständige projektmappenanalyse

Im folgenden Screenshot sehen Sie die Ergebnisse, wenn vollständige projektmappenanalyse aktiviert ist. Alle Fehler und bei der Codeanalyse in *alle* der Dateien in der Projektmappe angezeigt, unabhängig davon, ob die Dateien geöffnet sind.

![Vollständige projektmappenanalyse aktiviert.](../code-quality/media/fsa_enabled.png)

Der folgende Screenshot zeigt die Ergebnisse aus derselben Projektmappe nach dem Deaktivieren von vollständige projektmappenanalyse. Nur Fehler und bei der Codeanalyse in der geöffneten Projektmappendateien werden in der **Fehlerliste**.

![Vollständige projektmappenanalyse deaktiviert.](../code-quality/media/fsa_disabled.png)

## <a name="automatically-disable-full-solution-analysis"></a>Vollständige projektmappenanalyse automatisch deaktivieren

Wenn Visual Studio ermittelt, dass 200 MB oder weniger Systemspeicher verfügbar ist, automatisch deaktiviert wird, vollständige projektmappenanalyse (und einige andere Funktionen), wenn diese Option aktiviert ist. In diesem Fall wird eine Warnung angezeigt, die darüber informiert, dass Visual Studio einige Funktionen deaktiviert hat. Eine Schaltfläche können Sie die vollständige projektmappenanalyse erneut zu aktivieren, wenn Sie möchten.

![Text der Warnung das vollständige projektmappenanalyse anhalten](../code-quality/media/fsa_alert.png)
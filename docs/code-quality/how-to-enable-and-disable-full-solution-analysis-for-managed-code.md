---
title: Aktivieren Sie und deaktivieren Sie der vollständigen projektmappenanalyse für verwalteten code
ms.date: 03/23/2018
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a445439014e3b1f68b634865265089eb68e790a6
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/28/2019
ms.locfileid: "66260876"
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Vorgehensweise: Aktivieren Sie und deaktivieren Sie der vollständigen projektmappenanalyse für verwalteten code

*Vollständige projektmappenanalyse* ist eine Visual Studio-Feature, das Ihnen ermöglicht, die Codeanalysefehler nur in einem geöffneten Visual finden Sie unter C# oder Visual Basic-Dateien in der Projektmappe oder auch in Codedateien, die geschlossen werden. Wird standardmäßig vollständige projektmappenanalyse *aktiviert* für Visual Basic und *deaktiviert* für visuelle C#.

Es kann hilfreich sein, alle Probleme in allen Dateien, aber es kann auch verwirrend sein. Sie verlangsamt Visual Studio Ihrer Lösung bei sehr großen oder viele Dateien. Um die Anzahl der angezeigten Probleme, und Verbessern der Leistung von Visual Studio, können Sie die vollständige projektmappenanalyse deaktivieren. Sie können diese Funktion problemlos wieder, bei Bedarf aktivieren.

## <a name="to-toggle-full-solution-analysis"></a>Zum Umschalten der vollständigen projektmappenanalyse

1. Zum Öffnen der **Optionen** wählen Sie im Dialogfeld auf der Menüleiste in Visual Studio **Tools** > **Optionen**.

1. In der **Optionen** Dialogfeld wählen **Text-Editor**  >  **C#** oder **grundlegende**  >  **Erweiterte**.

1. Wählen Sie die **vollständige projektmappenanalyse aktivieren** Kontrollkästchen, um die vollständige projektmappenanalyse aktivieren oder deaktivieren Sie das Kontrollkästchen, um es zu deaktivieren. Wählen Sie **OK** Wenn Sie fertig sind.

    ![Aktivieren Sie die vollständige Lösung Analysis-Kontrollkästchen.](../code-quality/media/options-enable-full-solution-analysis.png)

## <a name="results-of-enabling-and-disabling-full-solution-analysis"></a>Ergebnisse der aktivieren und Deaktivieren der vollständigen projektmappenanalyse

Im folgenden Screenshot sehen Sie die Ergebnisse, wenn vollständige projektmappenanalyse aktiviert ist. Alle Fehler und bei der Codeanalyse in *alle* der Dateien in der Projektmappe angezeigt, unabhängig davon, ob die Dateien geöffnet oder nicht sind.

![Vollständige projektmappenanalyse aktiviert.](../code-quality/media/fsa_enabled.png)

Der folgende Screenshot zeigt die Ergebnisse aus der gleichen Projektmappe nach dem Deaktivieren der vollständigen projektmappenanalyse. Nur Fehler und bei der Codeanalyse in Projektmappe öffnen von Dateien angezeigt, der **Fehlerliste**.

![Vollständige projektmappenanalyse deaktiviert.](../code-quality/media/fsa_disabled.png)

## <a name="automatically-disable-full-solution-analysis"></a>Deaktivieren Sie automatisch vollständige projektmappenanalyse

Wenn Visual Studio ermittelt, dass 200 MB oder weniger Arbeitsspeicher verfügbar ist, automatisch deaktiviert wird, vollständige projektmappenanalyse (und einige andere Features) wird aktiviert. In diesem Fall wird eine Warnung angezeigt, in der Sie darüber informiert werden, dass Visual Studio einige Funktionen deaktiviert hat. Eine Schaltfläche können Sie die vollständige projektmappenanalyse wieder zu aktivieren, wenn Sie möchten.

![Text der Warnung das Anhalten der vollständigen projektmappenanalyse](../code-quality/media/fsa_alert.png)
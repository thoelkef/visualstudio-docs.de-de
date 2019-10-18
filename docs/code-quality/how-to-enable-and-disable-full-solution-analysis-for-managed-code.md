---
title: Aktivieren & Deaktivieren der vollständigen projektmappenanalyse für verwalteten Code
ms.date: 03/23/2018
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 26cd267f80f8c7c220771a5c2220d22b66929051
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72448926"
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Gewusst wie: Aktivieren und Deaktivieren der vollständigen projektmappenanalyse für verwalteten Code

Die *vollständige projektmappenanalyse* bedeutet, dass C# die Code Analyse alle-oder-Visual Basic Dateien in der Projekt Mappe überprüft, unabhängig davon, ob Sie im Editor geöffnet sind oder nicht. Standardmäßig ist die vollständige projektmappenanalyse für Visual Basic *aktiviert* und für C# *deaktiviert* .

Es kann nützlich sein, alle Probleme in allen Dateien anzuzeigen, kann aber auch ablenkend sein. Sie verlangsamt Visual Studio, wenn Ihre Projekt Mappe sehr groß ist oder viele Dateien enthält. Um die Anzahl der angezeigten Probleme einzuschränken und die Leistung von Visual Studio zu verbessern, können Sie die vollständige projektmappenanalyse deaktivieren. Diese Funktion kann bei Bedarf problemlos erneut aktiviert werden.

In der folgenden Abbildung ist die vollständige projektmappenanalyse aktiviert. Compilerprobleme und Code Analyse Probleme in allen Dateien in der Projekt Mappe werden angezeigt, auch wenn Sie nicht geöffnet sind.

![Vollständige projektmappenanalyse aktiviert.](../code-quality/media/fsa_enabled.png)

Die folgende Abbildung zeigt die Ergebnisse der gleichen Lösung nach dem Deaktivieren der vollständigen projektmappenanalyse. Nur Compilerfehler und Code Analyse Probleme in geöffneten Projektmappendateien werden in der Fehlerliste angezeigt.

![Vollständige projektmappenanalyse deaktiviert.](../code-quality/media/fsa_disabled.png)

## <a name="toggle-full-solution-analysis"></a>Vollständige projektmappenanalyse umschalten

1. Um das Dialogfeld **Optionen** zu öffnen **, wählen Sie** in der Menüleiste von Visual Studio Extras  > **Optionen**aus.

1. Wählen Sie im Dialogfeld **Optionen die Option** Text-**C#** **Editor**  >  oder **Basic**  > **erweitert**aus.

1. Aktivieren Sie das Kontrollkästchen **vollständige projektmappenanalyse aktivieren** , um die vollständige projektmappenanalyse zu aktivieren, oder deaktivieren Sie das Kontrollkästchen Wählen Sie **OK** aus, wenn Sie fertig sind.

   ![Aktivieren Sie das Kontrollkästchen vollständige projektmappenanalyse.](../code-quality/media/options-enable-full-solution-analysis.png)

## <a name="automatically-disable-full-solution-analysis"></a>Vollständige projektmappenanalyse automatisch deaktivieren

Wenn Visual Studio feststellt, dass der System Arbeitsspeicher 200 MB oder weniger verfügbar ist, werden die vollständige projektmappenanalyse (und andere Features) automatisch deaktiviert, wenn Sie aktiviert ist. In diesem Fall wird eine Warnung angezeigt, die Sie darüber informiert, dass Visual Studio einige Features deaktiviert hat. Mit einer Schaltfläche können Sie die vollständige projektmappenanalyse bei Bedarf wieder aktivieren.

![Warnungs Text zum Anhalten der vollständigen Lösungs Analyse](../code-quality/media/fsa_alert.png)

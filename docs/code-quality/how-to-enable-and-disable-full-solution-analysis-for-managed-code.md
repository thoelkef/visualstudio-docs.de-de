---
title: "Vorgehensweise: Aktivieren und deaktivieren Sie vollständige Projektmappenanalyse für verwalteten Code | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- full solution analysis
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-code-analysis
ms.workload:
- dotnet
ms.openlocfilehash: 64b541093aaf1a710976c0f53a3214b5d2a47e0d
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2018
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Vorgehensweise: Aktivieren und deaktivieren Sie die vollständige projektmappenanalyse für verwalteten Code

*Vollständige projektmappenanalyse* ist eine Visual Studio-Funktion, ermöglicht es Ihnen, Codeanalysefehler nur in einem geöffneten Visual c# oder Visual Basic-Dateien in der Projektmappe finden Sie unter, oder im Code auch Dateien, die, geschlossen werden. Standardmäßig wird vollständige projektmappenanalyse für Visual Basic aktiviert und deaktiviert für Visual c#.

Werden alle Probleme in allen Dateien zu sehen ist, zwar hilfreich kann es störend sein. Sie können auch langsam Visual Studio nach unten Wenn Ihre Lösung sehr groß ist oder verfügt über viele Dateien. Um die Anzahl der Probleme angezeigt und Visual Studio zur Leistungssteigerung, können Sie die vollständige projektmappenanalyse deaktivieren. Sie können diese Funktion problemlos aktivieren Sie bei Bedarf erneut.

## <a name="to-toggle-full-solution-analysis"></a>Vollständige projektmappenanalyse aktivieren bzw. deaktivieren

1. So öffnen die **Optionen** wählen Sie im Dialogfeld auf der Menüleiste in Visual Studio **Tools** > **Optionen**.

1. In der **Optionen** Dialogfeld Wählen Sie **Texteditor** > **c#** oder **grundlegende**  >   **Erweiterte**.

1. Wählen Sie die **vollständige projektmappenanalyse aktivieren** Kontrollkästchen, um vollständige projektmappenanalyse aktivieren oder deaktivieren Sie das Kontrollkästchen, um ihn zu deaktivieren. Wählen Sie die **OK** Schaltfläche, wenn Sie fertig sind.

    ![Vollständige Lösung Analysis Kontrollkästchen zu aktivieren. ] (../code-quality/media/fsa_toolsoptions.png "FSA_ToolsOptions")

## <a name="results-of-enabling-and-disabling-full-solution-analysis"></a>Ergebnisse der aktivieren und deaktivieren die vollständige projektmappenanalyse

Im folgenden Screenshot sehen Sie die Ergebnisse, wenn vollständige projektmappenanalyse aktiviert ist. Alle Fehler und bei der Codeanalyse in *alle* der Dateien in der Projektmappe angezeigt, unabhängig davon, ob die Dateien geöffnet sind.

![Vollständige projektmappenanalyse aktiviert. ] (../code-quality/media/fsa_enabled.png "FSA_Enabled")

Der folgende Screenshot zeigt die Ergebnisse aus derselben Projektmappe nach dem Deaktivieren von vollständige projektmappenanalyse. Nur Fehler und bei der Codeanalyse in öffnen Lösung, die Dateien werden in der Fehlerliste.

![Vollständige projektmappenanalyse deaktiviert. ] (../code-quality/media/fsa_disabled.png "FSA_Disabled")

## <a name="automatically-disabling-full-solution-analysis"></a>Vollständige projektmappenanalyse deaktiviert automatisch

Wenn Visual Studio ermittelt, dass 200MB oder weniger Systemspeicher verfügbar ist, automatisch deaktiviert wird, vollständige projektmappenanalyse (sowie einige andere Funktionen), wenn diese Option aktiviert ist. In diesem Fall wird eine Warnung angezeigt, Sie über diese informiert. Eine Schaltfläche können Sie die vollständige projektmappenanalyse erneut zu aktivieren, falls gewünscht.

![Text der Warnung bis zum Anhalten der vollständige projektmappenanalyse](../code-quality/media/fsa_alert.png "FSA_Alert")
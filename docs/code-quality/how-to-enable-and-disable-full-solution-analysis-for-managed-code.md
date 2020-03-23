---
title: Aktivieren & deaktivieren Sie die vollständige Lösungsanalyse für verwalteten Code
ms.date: 03/23/2018
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d699dd74315cfc36820c1cdb4120543e0290b1a1
ms.sourcegitcommit: b32fbbcbc43910b0ed7ce79aa9a22f2ed36ab57e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79428188"
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Gewusst wie: Aktivieren und Deaktivieren der vollständigen Lösungsanalyse für verwalteten Code

*Die vollständige Lösungsanalyse* bedeutet, dass die Codeanalyse alle Dateien in der Projektmappe von C- oder Visual Basic untersucht, unabhängig davon, ob sie im Editor geöffnet sind oder nicht. Standardmäßig ist die vollständige Lösungsanalyse für Visual Basic *aktiviert* und für C-Code *deaktiviert.*

Es kann nützlich sein, alle Probleme in allen Dateien zu sehen, aber es kann auch ablenkend sein. Es verlangsamt Visual Studio, wenn Ihre Lösung sehr groß ist oder viele Dateien enthält. Um die Anzahl der angezeigten Probleme zu begrenzen und die Visual Studio-Leistung zu verbessern, können Sie die vollständige Lösungsanalyse deaktivieren. Sie können diese Funktion bei Bedarf einfach wieder aktivieren.

In der folgenden Abbildung ist die vollständige Lösungsanalyse aktiviert. Compiler- und Codeanalyseprobleme in allen Dateien in der Lösung werden angezeigt, auch wenn sie nicht geöffnet sind.

![Vollständige Lösungsanalyse aktiviert.](../code-quality/media/fsa_enabled.png)

Die folgende Abbildung zeigt die Ergebnisse derselben Lösung nach dem Deaktivieren der vollständigen Lösungsanalyse. In der Fehlerliste werden nur Compilerfehler und Codeanalyseprobleme in geöffneten Lösungsdateien angezeigt.

![Vollständige Lösungsanalyse deaktiviert.](../code-quality/media/fsa_disabled.png)

## <a name="toggle-full-solution-analysis"></a>Umschalten der vollständigen Lösungsanalyse

1. Um das Dialogfeld **Optionen zu** öffnen, wählen Sie in der Menüleiste in Visual Studio**Extras-Optionen** **Tools** > aus.

1. Wählen Sie im Dialogfeld **Optionen** die Option **Texteditor** > **C-** oder **Basic** > **Advanced aus.**

1. Aktivieren Sie das Kontrollkästchen **Vollständige Lösungsanalyse aktivieren,** um die vollständige Lösungsanalyse zu aktivieren, oder deaktivieren Sie das Kontrollkästchen, um sie zu deaktivieren. Wählen Sie **OK,** wenn Sie fertig sind.

   ![Aktivieren Sie das Kontrollkästchen vollständige Lösungsanalyse.](../code-quality/media/options-enable-full-solution-analysis.png)

## <a name="automatically-disable-full-solution-analysis"></a>Automatische deaktivierung der vollständigen Lösungsanalyse

Wenn Visual Studio erkennt, dass 200 MB oder weniger Systemspeicher verfügbar sind, deaktiviert es automatisch die vollständige Lösungsanalyse (und einige andere Features), wenn er aktiviert ist. In diesem Fall wird eine Warnung angezeigt, die Sie darüber informiert, dass Visual Studio einige Features deaktiviert hat. Mit einer Schaltfläche können Sie die vollständige Lösungsanalyse wieder aktivieren, wenn Sie möchten.

![Warnungstext, der die vollständige Lösungsanalyse aussetzt](../code-quality/media/fsa_alert.png)

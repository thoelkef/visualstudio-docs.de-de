---
title: Legacy Code Analyse deaktivieren
ms.date: 10/04/2019
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: eb4422a12620d7650b4fe150313b10fe59835064
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88801021"
---
# <a name="how-to-enable-and-disable-binary-code-analysis-for-managed-code"></a>Gewusst wie: Aktivieren und Deaktivieren der binären Code Analyse für verwalteten Code

Sie können die Legacy-Code Analyse (binäre Analyse) so konfigurieren, dass Sie nach jedem Build eines Projekts mit verwaltetem Code ausgeführt wird. Sie können auch andere Einstellungen für jede Buildkonfiguration haben, z. b. Debug und Release.

> [!NOTE]
> Die Legacy Analyse ist für neuere Projekttypen wie .net Core und .NET Standard-apps nicht verfügbar. Diese Projekte verwenden [.NET Compiler Platform basierten Code Analysen](roslyn-analyzers-overview.md) , um den Code zu analysieren, sowohl Live als auch zur Buildzeit. Informationen zum Deaktivieren der Quell Code Analyse in diesen Projekten finden Sie unter [Deaktivieren der Quell Code Analyse](disable-code-analysis.md).

So aktivieren oder deaktivieren Sie die Legacy Code Analyse:

1. Wählen Sie in **Projektmappen-Explorer**das Projekt aus, halten Sie es (oder klicken Sie mit der rechten Maustaste darauf), und wählen Sie **Eigenschaften**aus.

2. Wechseln Sie im Dialogfeld Eigenschaften für das Projekt zur Registerkarte **Code Analyse** .

3. Geben Sie den Buildtyp in der **Konfiguration** und die Zielplattform in der **Plattform**an. (Nur Non-.net Core/. NET Standard-Projekte.)

::: moniker range="vs-2017"

4. Aktivieren bzw. deaktivieren Sie das Kontrollkästchen **Code Analyse bei Build aktivieren** , um die automatische Code Analyse zu aktivieren bzw. zu deaktivieren.

::: moniker-end

::: moniker range=">=vs-2019"

4. Zum Aktivieren oder Deaktivieren der automatischen Code Analyse aktivieren bzw. deaktivieren Sie das Kontrollkästchen **auf Build ausführen** im Abschnitt **binäre Analysen** .

   ![Ausführen der binären Code Analyse für die Buildoption in Visual Studio](media/run-on-build-binary-analyzers.png)

::: moniker-end

> [!NOTE]
> Das Deaktivieren der binären Code Analyse beim Build wirkt sich nicht auf [.NET Compiler Platform basierten Code](roslyn-analyzers-overview.md)Analysen aus, die immer bei Build ausgeführt werden, wenn Sie Sie als nuget-Paket installiert haben. Weitere Informationen zum Deaktivieren der Analyse von diesen Analyzern finden [Sie unter Deaktivieren der Quell Code Analyse](disable-code-analysis.md).

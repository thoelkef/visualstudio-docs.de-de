---
title: Legacy Code Analyse deaktivieren
ms.date: 10/04/2019
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c00a66a856dccb0ccb488937b935d9150ffc0266
ms.sourcegitcommit: 39a04f42d23597b70053686d7e927ba78f38a9a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2019
ms.locfileid: "71975077"
---
# <a name="how-to-enable-and-disable-binary-code-analysis-for-managed-code"></a>Vorgehensweise: Aktivieren und Deaktivieren der binären Code Analyse für verwalteten Code

Sie können die Legacy-Code Analyse (binäre Analyse) so konfigurieren, dass Sie nach jedem Build eines Projekts mit verwaltetem Code ausgeführt wird. Sie können auch andere Einstellungen für jede Buildkonfiguration haben, z. b. Debug und Release.

> [!NOTE]
> Die Legacy Analyse ist für neuere Projekttypen wie .net Core und .NET Standard-apps nicht verfügbar. Diese Projekte verwenden [.NET Compiler Platform basierten Code Analysen](roslyn-analyzers-overview.md) , um den Code zu analysieren, sowohl Live als auch zur Buildzeit. Informationen zum Deaktivieren der Quell Code Analyse in diesen Projekten finden Sie unter [Deaktivieren der Quell Code Analyse](disable-code-analysis.md).

So aktivieren oder deaktivieren Sie die Legacy Code Analyse:

1. Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf das Projekt, und wählen Sie dann **Eigenschaften**aus.

2. Wählen Sie im Dialogfeld Eigenschaften für das Projekt die Registerkarte **Code Analyse** aus.

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
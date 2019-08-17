---
title: Aktivieren oder Deaktivieren der Code Analyse
ms.date: 10/25/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ec0a8a3f04830115d343fcef611cfbd338163395
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551035"
---
# <a name="how-to-enable-and-disable-automatic-code-analysis-for-managed-code"></a>Vorgehensweise: Aktivieren und Deaktivieren der automatischen Code Analyse für verwalteten Code

Sie können die (statische) Code Analyse so konfigurieren, dass Sie nach jedem Build eines Projekts mit verwaltetem Code ausgeführt wird. Sie können verschiedene Code Analyse Eigenschaften für jede Buildkonfiguration festlegen, z. b. Debug und Release.

Dieser Artikel gilt nur für ältere Analysen und keine Live-Code Analyse mithilfe von [Code](roslyn-analyzers-overview.md)Analysemodulen.

## <a name="to-enable-or-disable-automatic-code-analysis"></a>So aktivieren oder deaktivieren Sie die automatische Code Analyse

1. Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf das Projekt, und wählen Sie dann **Eigenschaften**aus.

1. Wählen Sie im Dialogfeld Eigenschaften für das Projekt die Registerkarte **Code Analyse** aus.

   > [!TIP]
   > Neuere Projekttypen wie .net Core und .NET Standard Anwendungen haben keine **Code Analyse** Registerkarte. Die Legacy Analyse ist für diese Projekttypen nicht verfügbar, aber Sie können eine Live-Code Analyse mit [.NET Compiler Platform basierten Code](roslyn-analyzers-overview.md)Analysen erhalten. Informationen zum Unterdrücken von Warnungen von Code Analysemodulen finden Sie im Hinweis am Ende dieses Artikels.

1. Geben Sie den Buildtyp in der **Konfiguration** und die Zielplattform in der **Plattform**an.

1. Aktivieren bzw. deaktivieren Sie das Kontrollkästchen **Code Analyse bei Build aktivieren** , um die automatische Code Analyse zu aktivieren bzw. zu deaktivieren.

> [!NOTE]
> Das Kontrollkästchen **Code Analyse für Build aktivieren** wirkt sich nur auf die Legacy Analyse aus. Es wirkt sich nicht auf [.NET Compiler Platform basierte Code Analysen](roslyn-analyzers-overview.md)aus, die immer bei Build ausgeführt werden, wenn Sie Sie als nuget-Paket installiert haben. Wenn Sie Analysefehler aus dem **Fehlerliste**löschen möchten, können Sie alle aktuellen Verstöße unterdrücken, indem Sie in der Menüleiste **analysieren** > **Code Analyse ausführen und aktive Probleme unterdrücken** auswählen. Weitere Informationen finden Sie unter unter [drücken von Verletzungen](use-roslyn-analyzers.md#suppress-violations).

---
title: 'Gewusst wie: Aktivieren und Deaktivieren der automatischen Codeanalyse für verwalteten Code'
ms.date: 09/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 3113143b07ccb6f765cd0cf1735b34be6e952c72
ms.sourcegitcommit: 6672a1e9d135d7e5cca3cceea07c6fe5a0871475
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2018
ms.locfileid: "47443544"
---
# <a name="how-to-enable-and-disable-automatic-code-analysis-for-managed-code"></a>Gewusst wie: Aktivieren und Deaktivieren der automatischen Codeanalyse für verwalteten Code

Sie können nach jedem Build von einem Projekt mit verwaltetem Code führen die Codeanalyse konfigurieren. Sie können festlegen anderer Code Analysis-Eigenschaften für jede Buildkonfiguration, z. B. debug und release.

## <a name="to-enable-or-disable-automatic-code-analysis"></a>So aktivieren oder Deaktivieren der automatischen Codeanalyse

1. In **Projektmappen-Explorer**mit der rechten Maustaste auf das Projekt, und wählen Sie dann **Eigenschaften**.

1. Wählen Sie im Dialogfeld Eigenschaften für das Projekt, das **Codeanalyse** Registerkarte.

1. Geben Sie den Build in **Konfiguration** und die Zielplattform in **Plattform**.

1. Klicken Sie zum Aktivieren oder Deaktivieren der automatischen Codeanalyse, aktivieren oder deaktivieren Sie die **Codeanalyse für Build aktivieren** Kontrollkästchen.

> [!NOTE]
> Die **Codeanalyse für Build aktivieren** Kontrollkästchen wirkt sich nur auf die Analyse von statischem Code. Es hat keine Auswirkungen auf [Roslyn-Code-Analyzer](roslyn-analyzers-overview.md), die immer auf der Build ausgeführt werden, wenn Sie Sie als NuGet-Paket installiert haben. Wenn Fehler der Analyzer aus gelöscht werden sollen die **Fehlerliste**, können Sie alle aktuellen Verstöße unterdrücken, indem Sie auswählen **analysieren** > **Codeanalyse ausführen und aktive unterdrücken Probleme** in der Menüleiste. Weitere Informationen finden Sie unter [unterdrücken Verstöße](use-roslyn-analyzers.md#suppress-violations).

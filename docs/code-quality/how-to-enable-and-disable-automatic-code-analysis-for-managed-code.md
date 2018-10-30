---
title: Aktivieren oder Deaktivieren der Codeanalyse
ms.date: 10/25/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 71a1c44ee775060a25946f79d7c23194e19f0ae9
ms.sourcegitcommit: 1abb9cf4c3ccb90e3481ea8079272c98aad12875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "50143397"
---
# <a name="how-to-enable-and-disable-automatic-code-analysis-for-managed-code"></a>Gewusst wie: Aktivieren und Deaktivieren der automatischen Codeanalyse für verwalteten Code

Sie können nach jedem Build von einem Projekt mit verwaltetem Code ausführen (statisch) Codeanalyse konfigurieren. Sie können festlegen anderer Code Analysis-Eigenschaften für jede Buildkonfiguration, z. B. debug und release.

Dieser Artikel bezieht sich nur auf statische Codeanalyse und nicht als live Codeanalyse mit [Roslyn-Code-Analyzer](roslyn-analyzers-overview.md).

## <a name="to-enable-or-disable-automatic-code-analysis"></a>So aktivieren oder Deaktivieren der automatischen Codeanalyse

1. In **Projektmappen-Explorer**mit der rechten Maustaste auf das Projekt, und wählen Sie dann **Eigenschaften**.

1. Wählen Sie im Dialogfeld Eigenschaften für das Projekt, das **Codeanalyse** Registerkarte.

   > [!TIP]
   > Neuere Projekttypen, z. B. .NET Core- sowie .NET Standard-Anwendungen besitzen eine **Codeanalyse** Registerkarte. Analyse von statischem Code ist nicht für diese Projekttypen verfügbar, aber Sie erhalten weiterhin live Codeanalyse mit [Roslyn-Code-Analyzer](roslyn-analyzers-overview.md). Um Warnungen von Roslyn-Code-Analyzer zu unterdrücken, finden Sie im Hinweis am Ende dieses Artikels aus.

1. Geben Sie den Build in **Konfiguration** und die Zielplattform in **Plattform**.

1. Klicken Sie zum Aktivieren oder Deaktivieren der automatischen Codeanalyse, aktivieren oder deaktivieren Sie die **Codeanalyse für Build aktivieren** Kontrollkästchen.

> [!NOTE]
> Die **Codeanalyse für Build aktivieren** Kontrollkästchen wirkt sich nur auf die Analyse von statischem Code. Es hat keine Auswirkungen auf [Roslyn-Code-Analyzer](roslyn-analyzers-overview.md), die immer auf der Build ausgeführt werden, wenn Sie Sie als NuGet-Paket installiert haben. Wenn Fehler der Analyzer aus gelöscht werden sollen die **Fehlerliste**, können Sie alle aktuellen Verstöße unterdrücken, indem Sie auswählen **analysieren** > **Codeanalyse ausführen und aktive unterdrücken Probleme** in der Menüleiste. Weitere Informationen finden Sie unter [unterdrücken Verstöße](use-roslyn-analyzers.md#suppress-violations).

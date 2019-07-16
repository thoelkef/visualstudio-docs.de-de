---
title: Unterdrücken von Verletzungen der Codeanalyse für generierten Code
ms.date: 05/13/2019
ms.topic: conceptual
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6a7990f5e9fa1893d8813b1307ab6a0a7fee46be
ms.sourcegitcommit: 77b4ca625674658d5c5766e684fa0e2a07cad4da
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/14/2019
ms.locfileid: "65613570"
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>Vorgehensweise: Unterdrücken von Codeanalysewarnungen für generierten Code

Generierter Code enthält Code, der vom Compiler für verwalteten Code oder Drittanbietertools zu Ihrem Projekt hinzugefügt wird. Sie möchten die Verletzungen von Namensregeln anzuzeigen, die Codeanalyse in generiertem Code ermittelt. Jedoch, da Sie können nicht anzeigen und verwalten den Code, der die Verstöße enthält, empfiehlt nicht, die angezeigt werden.

Die **Ergebnisse aus generiertem Code unterdrücken** Kontrollkästchen auf der Eigenschaftenseite des Code-Analyse eines Projekts können Sie wählen, ob Code analysewarnungen zu Code, die von einem Drittanbieter-Tool generierten angezeigt.

> [!NOTE]
> Allerdings werden durch diese Option keine Codeanalysefehler und -warnungen zu generiertem Code unterdrückt, wenn die Fehler und Warnungen in Formularen und Vorlagen auftreten. Der Quellcode für ein Formular oder eine Vorlage kann sowohl angezeigt als auch verwaltet werden.

### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>So unterdrücken Sie Warnungen für generierten Code in einem Projekt

1. Mit der rechten Maustaste in des Projekts im **Projektmappen-Explorer** , und klicken Sie dann auf **Eigenschaften**.

2. Wählen Sie die **Codeanalyse** Registerkarte.

3. Wählen Sie die **Ergebnisse aus generiertem Code unterdrücken** Kontrollkästchen.

> [!NOTE]
> Sie können nur Warnungen von der statischen Codeanalyse unterdrücken. Derzeit keine Sie Unterdrückung von Warnungen der Codeanalyse von [Analysen](roslyn-analyzers-overview.md).
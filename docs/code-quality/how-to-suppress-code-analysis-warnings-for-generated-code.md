---
title: Code Analyse Verletzungen für generierten Code unterdrücken
ms.date: 05/13/2019
ms.topic: conceptual
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 54b33eb92cec82a5a0327bac92f2a8909519784d
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72448900"
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>Gewusst wie: Unterdrücken von Code Analyse Warnungen für generierten Code

Generierter Code enthält Code, der von verwalteten Code Compilern oder Drittanbieter Tools zu Ihrem Projekt hinzugefügt wird. Möglicherweise möchten Sie die Regel Verletzungen sehen, die von der Code Analyse in generiertem Code erkannt werden. Da Sie jedoch den Code, der die Verstöße enthält, nicht anzeigen und verwalten können, sollten Sie ihn möglicherweise nicht sehen.

Mithilfe des Kontrollkästchens **Ergebnisse aus generiertem Code unterdrücken** der Code Analyse-Eigenschaften Seite eines Projekts können Sie auswählen, ob Code Analyse Warnungen aus Code angezeigt werden sollen, der von einem Drittanbieter Tool generiert wurde.

> [!NOTE]
> Allerdings werden durch diese Option keine Codeanalysefehler und -warnungen zu generiertem Code unterdrückt, wenn die Fehler und Warnungen in Formularen und Vorlagen auftreten. Der Quellcode für ein Formular oder eine Vorlage kann sowohl angezeigt als auch verwaltet werden.

### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>So unterdrücken Sie Warnungen für generierten Code in einem Projekt

1. Klicken Sie mit der rechten Maustaste auf das Projekt in **Projektmappen-Explorer** und klicken Sie dann auf **Eigenschaften**.

2. Wählen Sie die Registerkarte **Code Analyse** aus.

3. Aktivieren Sie das Kontrollkästchen **Ergebnisse aus generiertem Code unterdrücken** .

> [!NOTE]
> Sie können nur Warnungen aus der Legacy Analyse unterdrücken. Derzeit können Sie keine Code Analyse Warnungen von [Analyzern](roslyn-analyzers-overview.md)unterdrücken.

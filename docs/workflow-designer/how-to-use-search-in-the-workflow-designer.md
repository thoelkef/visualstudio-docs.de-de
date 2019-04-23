---
title: 'Vorgehensweise: Verwenden der Suche im Workflow-Designer'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f42d3115-2ed2-4941-8f1e-92dac41c30fa
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 0a80bfecaa288eabc0161d0262535a7912411f78
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60091290"
---
# <a name="how-to-use-search-in-the-workflow-designer"></a>Vorgehensweise: Verwenden der Suche im Workflow-Designer

Um zu ermöglichen, größerer, komplexerer Workflows zu erstellen, können Sie im Workflow-Designer zum Suchen von Elementen nach Schlüsselwort suchen. Beachten Sie, dass Ersetzen vom Designer nicht unterstützt wird.

## <a name="quick-find"></a>Schnellsuche

Schnellsuche findet der Designer die folgenden:

- Eigenschaften von <xref:System.Activities.Activity>-Objekten, <xref:System.Activities.Statements.FlowNode>-Objekten, <xref:System.Activities.Statements.State>-Objekten, Übergängen und anderen benutzerdefinierten Flusssteuerungselementen.

- Variablen

- Argumente

- Ausdrücke

### <a name="use-quick-find"></a>Verwenden der Schnellsuche

1. Mit dem Workflow-Designer öffnen, drücken Sie die **STRG + F**, oder wählen Sie **bearbeiten** > **suchen und Ersetzen** > **Schnellsuche**.

2. Geben Sie den Suchbegriff in das **Suchen nach** Textfeld, und klicken Sie auf **Weitersuchen**.

3. Der Suchbegriff befindet sich im aktuellen Workflow. Die folgende Abbildung zeigt ein aktivitätsanzeigename im Designer gefunden werden:

   ![Suchergebnisse im Workflow Designer](../workflow-designer/media/designersearch.png)

## <a name="find-in-files"></a>Suchen in Dateien

Suche in Dateien sucht Zeichenfolgen in Workflowdateien, einschließlich XAML-Dateien.

### <a name="use-find-in-files"></a>Verwenden Sie in Dateien suchen

1. Drücken Sie in Visual Studio **STRG**+**UMSCHALT**+**F**, oder wählen Sie **bearbeiten**  >   **Suchen und Ersetzen** > **in Dateien suchen**.

2. Geben Sie den Suchbegriff in das **Suchen nach** Textfeld, und klicken Sie auf **alle suchen**.

3. Das Suchergebnis wird angezeigt, der **Suchergebnisse** anzeigen. Durch Doppelklicken auf ein Ergebniselement navigieren, auf die Aktivität, die die Übereinstimmung im Workflow-Designer enthält.
---
title: 'Vorgehensweise: Verwenden der Suche im Workflow-Designer'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: f42d3115-2ed2-4941-8f1e-92dac41c30fa
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: ecf4839cec08e9ffb0419aebcff9da145214b117
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49943062"
---
# <a name="how-to-use-search-in-the-workflow-designer"></a>Vorgehensweise: Verwenden der Suche im Workflow-Designer

Um zu ermöglichen, größerer, komplexerer Workflows zu erstellen, können Sie im Workflow-Designer zum Suchen von Elementen nach Schlüsselwort suchen. Beachten Sie, dass Ersetzen vom Designer nicht unterstützt wird.

## <a name="quick-find"></a>Schnellsuche

Schnellsuche findet der Designer die folgenden:

-   Eigenschaften von <xref:System.Activities.Activity>-Objekten, <xref:System.Activities.Statements.FlowNode>-Objekten, <xref:System.Activities.Statements.State>-Objekten, Übergängen und anderen benutzerdefinierten Flusssteuerungselementen.

-   Variablen

-   Argumente

-   Ausdrücke

### <a name="use-quick-find"></a>Verwenden der Schnellsuche

1. Mit dem Workflow-Designer öffnen, drücken Sie die **STRG + F**, oder wählen Sie **bearbeiten** > **suchen und Ersetzen** > **Schnellsuche**.

2. Geben Sie den Suchbegriff in das **Suchen nach** Textfeld, und klicken Sie auf **Weitersuchen**.

3. Der Suchbegriff befindet sich im aktuellen Workflow. Die folgende Abbildung zeigt ein aktivitätsanzeigename im Designer gefunden werden:

   ![Suchergebnisse im Workflow Designer](../workflow-designer/media/designersearch.png)

## <a name="find-in-files"></a>Suchen in Dateien

Suche in Dateien sucht Zeichenfolgen in Workflowdateien, einschließlich XAML-Dateien.

### <a name="use-find-in-files"></a>Verwenden Sie in Dateien suchen

1.  Drücken Sie in Visual Studio **STRG**+**UMSCHALT**+**F**, oder wählen Sie **bearbeiten**  >   **Suchen und Ersetzen** > **in Dateien suchen**.

2.  Geben Sie den Suchbegriff in das **Suchen nach** Textfeld, und klicken Sie auf **alle suchen**.

3.  Das Suchergebnis wird angezeigt, der **Suchergebnisse** anzeigen. Durch Doppelklicken auf ein Ergebniselement navigieren, auf die Aktivität, die die Übereinstimmung im Workflow-Designer enthält.
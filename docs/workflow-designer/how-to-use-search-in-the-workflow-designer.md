---
title: 'Vorgehensweise: Verwenden der Suche im Workflow-Designer'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f42d3115-2ed2-4941-8f1e-92dac41c30fa
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: 12bda4af085b8ab41d3e11841f24cd5dfd389738
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650298"
---
# <a name="how-to-use-search-in-the-workflow-designer"></a>Vorgehensweise: Verwenden der Suche im Workflow-Designer

Um das Erstellen größerer, komplexerer Workflows zu vereinfachen, können Sie im Workflow-Designer nach Elementen nach Schlüsselwort suchen. Beachten Sie, dass Ersetzen vom Designer nicht unterstützt wird.

## <a name="quick-find"></a>Schnellsuche

Die Schnellsuche findet Folgendes im Designer:

- Eigenschaften von <xref:System.Activities.Activity>-Objekten, <xref:System.Activities.Statements.FlowNode>-Objekten, <xref:System.Activities.Statements.State>-Objekten, Übergängen und anderen benutzerdefinierten Flusssteuerungselementen.

- Variablen

- Argumente

- Ausdrücke

### <a name="use-quick-find"></a>Schnellsuche verwenden

1. Wenn der Workflow-Designer geöffnet ist, drücken Sie **STRG + F**, oder klicken Sie auf  >  **Bearbeiten** , um  > **Schnellsuche**zu**Suchen und zu ersetzen** .

2. Geben Sie den Suchbegriff in **das Textfeld Suchen nach** ein, und klicken Sie auf **weiter**suchen.

3. Der Suchbegriff befindet sich im aktuellen Workflow. In der folgenden Abbildung wird ein Aktivitäts Anzeige Name im Designer angezeigt:

   ![Suchergebnisse im Workflow Designer](../workflow-designer/media/designersearch.png)

## <a name="find-in-files"></a>Suchen in Dateien

In Dateien suchen sucht Zeichen folgen in Workflow Dateien, einschließlich XAML-Dateien.

### <a name="use-find-in-files"></a>Verwenden von "in Dateien suchen"

1. Drücken Sie in Visual Studio **STRG** +**UMSCHALT** +**F**, oder wählen Sie **Bearbeiten**  > **Suchen und ersetzen**  > **in Dateien suchen**.

2. Geben Sie das Suchelement in **das Textfeld Suchen nach** ein, und klicken Sie auf **alle**suchen.

3. Das Suchergebnis wird in der Ansicht " **Ergebnis suchen** " angezeigt. Durch Doppelklicken auf ein Ergebnis Element gelangen Sie zu der Aktivität, die die Entsprechung im Workflow-Designer enthält.
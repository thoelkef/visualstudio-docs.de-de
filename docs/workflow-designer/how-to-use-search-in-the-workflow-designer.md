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
ms.openlocfilehash: 4b5dfdd4b4d05969406f93801bcf87880949e41a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-use-search-in-the-workflow-designer"></a>Vorgehensweise: Verwenden der Suche im Workflow-Designer

Um das Erstellen größerer, komplexerer Workflows zu erleichtern, können Elemente im Workflow-Designer nach Schlüsselwort gesucht werden. Beachten Sie, dass Ersetzen vom Designer nicht unterstützt wird. Die Suche findet folgende Elemente im Designer:

## <a name="quick-find"></a>Schnellsuche

Schnellsuche findet folgende im Designer:

-   Eigenschaften von <xref:System.Activities.Activity>-Objekten, <xref:System.Activities.Statements.FlowNode>-Objekten, <xref:System.Activities.Statements.State>-Objekten, Übergängen und anderen benutzerdefinierten Flusssteuerungselementen.

-   Variablen

-   Argumente

-   Ausdrücke

### <a name="using-quick-find"></a>Verwenden der Schnellsuche

1.  Mit dem Workflowdesigner öffnen, drücken Sie die **STRG + F**, oder wählen Sie **bearbeiten**, **suchen und Ersetzen**, **Schnellsuche**.

2.  Geben Sie den Suchbegriff in das **Suchen nach** Textfeld, und klicken Sie auf **Weitersuchen**.

3.  Der Suchbegriff wird im aktuellen Workflow gesucht. Im folgenden Screenshot wird der Anzeigenamen einer gesuchten Aktivität im Designer angezeigt.

     ![Suchergebnis im Workflow-Designer](../workflow-designer/media/designersearch.png "DesignerSearch")

## <a name="find-in-files"></a>Suchen in Dateien

Verwenden Sie "In Dateien suchen", um Zeichenfolgen in Workflowdateien, einschließlich XAML-Dateien, zu suchen.

### <a name="using-find-in-files"></a>Verwenden von In Dateien suchen

1.  Drücken Sie in Visual Studio **STRG + UMSCHALT + F**, oder wählen Sie **bearbeiten**, **suchen und Ersetzen**, **in Dateien suchen**

2.  Geben Sie den Suchbegriff in das **Suchen nach** Textfeld, und klicken Sie auf **alle suchen**

3.  Das Suchergebnis wird in Visual Studio angezeigt**Suchergebnisse** anzeigen. Durch Doppelklicken auf ein Ergebniselement navigieren Sie im Workflow-Designer zu der Aktivität, in der die Übereinstimmung enthalten ist.
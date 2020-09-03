---
title: 'Gewusst wie: Verwenden der Suche im Workflow-Designer | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: f42d3115-2ed2-4941-8f1e-92dac41c30fa
caps.latest.revision: 3
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 84f74b4718a7f976b386197a79692256ab49caa4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659121"
---
# <a name="how-to-use-search-in-the-workflow-designer"></a>Vorgehensweise: Verwenden der Suche im Workflow-Designer
Um das Erstellen größerer, komplexerer Workflows zu erleichtern, können Elemente im Workflow-Designer nach Schlüsselwort gesucht werden. Beachten Sie, dass Ersetzen vom Designer nicht unterstützt wird. Die Suche findet folgende Elemente im Designer:

## <a name="quick-find"></a>Schnellsuche
 Die Schnellsuche findet folgende Elemente im Designer:

- Eigenschaften von <xref:System.Activities.Activity>-Objekten, <xref:System.Activities.Statements.FlowNode>-Objekten, <xref:System.Activities.Statements.State>-Objekten, Übergängen und anderen benutzerdefinierten Flusssteuerungselementen.

- Variablen

- Argumente

- Ausdrücke

#### <a name="using-quick-find"></a>Verwenden der Schnellsuche

1. Wenn der Workflow-Designer geöffnet ist, drücken Sie **STRG + F**, oder wählen Sie **Bearbeiten**, **Suchen und ersetzen**, **Schnellsuche**aus.

2. Geben Sie den Suchbegriff in **das Textfeld Suchen nach** ein, und klicken Sie auf **weiter**suchen.

3. Der Suchbegriff wird im aktuellen Workflow gesucht. Im folgenden Screenshot wird der Anzeigenamen einer gesuchten Aktivität im Designer angezeigt.

     ![Suchergebnisse im Workflow Designer](../workflow-designer/media/designersearch.png "Designersearch")

## <a name="find-in-files"></a>Suchen in Dateien
 Verwenden Sie "In Dateien suchen", um Zeichenfolgen in Workflowdateien, einschließlich XAML-Dateien, zu suchen.

#### <a name="using-find-in-files"></a>Verwenden von In Dateien suchen

1. Drücken Sie in Visual Studio **STRG + UMSCHALT + F**, oder wählen Sie **Bearbeiten**, **Suchen und ersetzen**, **in Dateien suchen aus** .

2. Geben Sie das Suchelement in **das Textfeld Suchen nach** ein, und klicken Sie auf **alle** suchen.

3. Das Suchergebnis wird in der Ansicht " [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] **Ergebnis suchen** " angezeigt. Durch Doppelklicken auf ein Ergebniselement navigieren Sie im Workflow-Designer zu der Aktivität, in der die Übereinstimmung enthalten ist.
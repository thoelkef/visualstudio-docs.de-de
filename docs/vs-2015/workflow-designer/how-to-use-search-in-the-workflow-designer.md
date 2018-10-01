---
title: 'Vorgehensweise: Verwenden Sie die Suche im Workflow-Designer | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: f42d3115-2ed2-4941-8f1e-92dac41c30fa
caps.latest.revision: 3
author: steved0x
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 5c66286aa8647644bf32e0d805c2ff8d0f574991
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47509721"
---
# <a name="how-to-use-search-in-the-workflow-designer"></a>Vorgehensweise: Verwenden der Suche im Workflow-Designer
Um das Erstellen größerer, komplexerer Workflows zu erleichtern, können Elemente im Workflow-Designer nach Schlüsselwort gesucht werden. Beachten Sie, dass Ersetzen vom Designer nicht unterstützt wird. Die Suche findet folgende Elemente im Designer:  
  
## <a name="quick-find"></a>Schnellsuche  
 Die Schnellsuche findet folgende Elemente im Designer:  
  
-   Eigenschaften von <xref:System.Activities.Activity>-Objekten, <xref:System.Activities.Statements.FlowNode>-Objekten, <xref:System.Activities.Statements.State>-Objekten, Übergängen und anderen benutzerdefinierten Flusssteuerungselementen.  
  
-   Variablen  
  
-   Argumente  
  
-   Ausdrücke  
  
#### <a name="using-quick-find"></a>Verwenden der Schnellsuche  
  
1.  Mit dem Workflow-Designer öffnen, drücken Sie die **STRG + F**, oder wählen Sie **bearbeiten**, **suchen und Ersetzen**, **Schnellsuche**.  
  
2.  Geben Sie den Suchbegriff in das **Suchen nach** Textfeld, und klicken Sie auf **Weitersuchen**.  
  
3.  Der Suchbegriff wird im aktuellen Workflow gesucht. Im folgenden Screenshot wird der Anzeigenamen einer gesuchten Aktivität im Designer angezeigt.  
  
     ![Suchergebnis im Workflow-Designer](../workflow-designer/media/designersearch.png "DesignerSearch")  
  
## <a name="find-in-files"></a>Suchen in Dateien  
 Verwenden Sie "In Dateien suchen", um Zeichenfolgen in Workflowdateien, einschließlich XAML-Dateien, zu suchen.  
  
#### <a name="using-find-in-files"></a>Verwenden von In Dateien suchen  
  
1.  Drücken Sie in Visual Studio **STRG + UMSCHALT + F**, oder wählen Sie **bearbeiten**, **suchen und Ersetzen**, **in Dateien suchen**  
  
2.  Geben Sie den Suchbegriff in das **Suchen nach** Textfeld, und klicken Sie auf **alle suchen**  
  
3.  Das Suchergebnis wird angezeigt der [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] **Suchergebnisse** anzeigen. Durch Doppelklicken auf ein Ergebniselement navigieren Sie im Workflow-Designer zu der Aktivität, in der die Übereinstimmung enthalten ist.
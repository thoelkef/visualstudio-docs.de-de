---
title: 'Vorgehensweise: Verwenden des Variablen-Designers | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Presentation.View.DesignTimeVariable.UI
ms.assetid: 0318dfb0-bf8f-4f92-9b86-ae4c1b2161ad
caps.latest.revision: "14"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 064080a2446858123dd7b259dd5d2752f4253a80
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-use-the-variable-designer"></a>Vorgehensweise: Verwenden des Variablen-Designers
Der Variablen-Designer dient zum Erstellen von Variablen in Datenbindungsszenarien und bedingten Anweisungen. Der Designer zugegriffen wird, indem Sie auf die **Variablen** Schaltfläche in der unteren linken Ecke des Zeichenbereichs. Der Designer enthält eine Liste von Variablen, die in einer Tabelle angezeigt und können nach jedem Spaltenkopf, sortiert werden, mit Ausnahme von der **Standard** Spalte. Jede Variable verfügt über einen Namen, einen Variablentyp, einen Gültigkeitsbereich und ggf. über einen Standardwert. Der Name und der Standardwert sind bearbeitbare Textfelder, der Typ und der Gültigkeitsbereich sind Dropdownlisten. Der Gültigkeitsbereich entspricht der Aktivität, die beim Aufrufen des Variablen-Designers ausgewählt wurde. Wenn eine Variable nicht innerhalb des Gültigkeitsbereichs der Auswahl erstellt werden kann, wird standardmäßig der Gültigkeitsbereich der nächsten Vorgängeraktivität der Auswahl verwendet, in dem die Variable erstellt werden kann. [! UMFASSEN[Crabout](/dotnet/framework/windows-workflow-foundation/variables-and-arguments).  
  
 Die Sortierreihenfolge wird erst übernommen, wenn der Benutzer eines der Sortiersteuerelemente explizit verwendet, den Variablen-Designer schließt und erneut öffnet oder eine andere Variable erstellt.  
  
### <a name="to-create-a-new-variable"></a>So erstellen Sie eine neue Variable  
  
1.  Öffnen Sie in [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] eine Workflow- oder Aktivitätsprojektmappe.  
  
2.  Wählen Sie im Zeichenbereich eine Aktivität im Workflow aus.  
  
3.  Öffnen Sie den Variablen-Designer, indem Sie auf die **Variablen** Schaltfläche in der unteren linken Ecke des Zeichenbereichs. Der Variablen-Designer wird angezeigt.  
  
4.  Klicken Sie auf die leere Zeile, die mit der Bezeichnung **Variable erstellen**. Dadurch wird eine neue Zeile mit einer neuen Variablen, die mit den folgenden Standardwerten hinzugefügt: Bereichsgrenzen für die **Namen** , wobei x eine ganze Zahl mit einem Anfangswert von 1 ist, die zum Erstellen von eindeutiger Variablennamen automatisch erhöht  **Zeichenfolge** für die **Variablentyp**, und **Sequenz** für die **Bereich**. Wird kein Wert für hinzugefügt **Standard**. Sie können diese Werte jederzeit während des Workflowentwurfs ändern.  
  
    > [!NOTE]
    >  Um eine Variable zu löschen, wählen Sie die Variable, indem Sie darauf klicken, und drücken Sie dann die **löschen** Schlüssel.  
  
## <a name="see-also"></a>Siehe auch  
 [Mithilfe des Workflowdesigners](../workflow-designer/using-the-workflow-designer.md)   
 [Variablen und Argumente](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)   
 [Vorgehensweise: Verwenden des Argument-Designers](../workflow-designer/how-to-use-the-argument-designer.md)
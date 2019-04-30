---
title: 'Vorgehensweise: Verwenden Sie den Argument-Designer | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.ArgumentDesigner.UI
- System.Activities.Presentation.View.DesignTimeArgument.UI
ms.assetid: 64813fd5-1ea1-499a-98b4-ab2a44b7ee5e
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 90e259d9d5e71ab5e6837cc4aa9cd22ebf43aaac
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432368"
---
# <a name="how-to-use-the-argument-designer"></a>Vorgehensweise: Verwenden des Argument-Designers
Verglichen mit früheren Versionen von [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], ist es mit dem Argument-Designer einfach, Daten in eine und aus einer Aktivität fließen zu lassen. Der Designer erfolgt durch Klicken auf die **Argumente** -Schaltfläche in der unteren linken Ecke des Zeichenbereichs. Der Designer enthält eine Liste von Argumenten, die in Tabellenform angezeigt und können nach jedem die Spaltenüberschriften sortiert werden, mit Ausnahme der **Standardwert** Spalte. Für jedes Argument werden der Name, die Richtung (ein/aus/ein/aus/Eigenschaft), der Typ und ein Standardausdruckswert (sofern vorhanden) angegeben. Der Name und der Standardausdruckswert sind bearbeitbare Textfelder, und der Typ und die Richtung sind Dropdownlisten. [!INCLUDE[crabout](../includes/crabout-md.md)] Argumente finden Sie unter [Variablen und Argumente](http://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8).  
  
### <a name="to-create-a-new-argument"></a>So erstellen Sie ein neues Argument  
  
1. Öffnen Sie in [!INCLUDE[vs2010](../includes/vs2010-md.md)] eine Workflow- oder Aktivitätsprojektmappe.  
  
2. Öffnen Sie den Argument-Designer, indem Sie auf die **Argumente** -Schaltfläche in der unteren linken Ecke des Zeichenbereichs. Der Argument-Designer wird angezeigt.  
  
3. Klicken Sie auf die leere Zeile, die mit der Bezeichnung **Argument erstellen**. Dadurch wird eine neue Zeile hinzugefügt, mit einem neuen Argument mit den folgenden Standardwerten: Argumentx für den **Namen** , wobei x eine ganze Zahl mit einem Anfangswert von 1, die automatisch inkrementiert wird ist, um eindeutige Argumentnamen, erstellen **In**  für die **Richtung**, und **Zeichenfolge** für die **Argumenttyp**. Wird kein Wert hinzugefügt, für die **Standardwert**. Sie können diese Werte jederzeit während des Workflowentwurfs ändern.  
  
    > [!NOTE]
    > Um ein Argument zu löschen, wählen Sie das Argument, indem Sie darauf klicken, und drücken Sie dann die **löschen** Schlüssel.  
  
## <a name="see-also"></a>Siehe auch  
 [Mithilfe des Workflowdesigners](../workflow-designer/using-the-workflow-designer.md)   
 [Variablen und Argumente](http://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8)
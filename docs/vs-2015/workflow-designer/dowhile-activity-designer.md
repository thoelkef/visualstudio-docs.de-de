---
title: DoWhile-Aktivitätsdesigner | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d09954409baccfdc5d9eb083a15bd02f5d16cb85
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58957398"
---
# <a name="dowhile-activity-designer"></a>DoWhile-Aktivitätsdesigner
Die <xref:System.Activities.Statements.DoWhile> Aktivität ausgeführt wird, die im enthaltene Aktivität die <xref:System.Activities.Statements.DoWhile.Body%2A> mindestens einmal, bis eine angegebene Bedingung ergibt **"false"**. Wenn die in einem Schleifentext enthaltene Anwendung der 0 (null) oder mehrmals ausgeführt werden soll, verwenden Sie stattdessen die <xref:System.Activities.Statements.While>-Aktivität.  
  
## <a name="dowhile-properties-in-the-workflow-designer"></a>DoWhile- Eigenschaften im Workflow-Designer  
 In der folgenden Tabelle werden die nützlichsten Eigenschaften der <xref:System.Activities.Statements.DoWhile>-Aktivität aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.DoWhile.Body%2A>|False|Die Aktivität, die ausgeführt werden, solange die Bedingung **"true"**. Hinzufügen der <xref:System.Activities.Statements.DoWhile.Body%2A> -Aktivität, indem Sie eine Aktivität aus der Toolbox in die **Text** Feld der **DoWhile** Aktivitäts-Designer, mit dem Hinweistext "Aktivität hier ablegen".|  
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|True|Die Bedingung, die nach jedem Schleifendurchlauf ausgewertet werden soll. Festlegen der <xref:System.Activities.Statements.DoWhile.Condition%2A>, geben Sie einen [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] Ausdruck in der **Bedingung** Feld der **DoWhile** -Aktivitätsdesigner oder im Eigenschaftenraster.|  
  
## <a name="see-also"></a>Siehe auch  
 [While](../workflow-designer/while-activity-designer.md)   
 [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)
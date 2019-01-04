---
title: Workflow-Designer - DoWhile-Aktivitätsdesigner
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bc96d44a38a0cf8a1865de236b9f7ef473c960a7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53960429"
---
# <a name="dowhile-activity-designer"></a>DoWhile-Aktivitätsdesigner

Die <xref:System.Activities.Statements.DoWhile> Aktivität ausgeführt wird, die im enthaltene Aktivität die <xref:System.Activities.Statements.DoWhile.Body%2A> mindestens einmal, bis eine angegebene Bedingung ergibt **"false"**. Wenn die in einem Schleifentext enthaltene Anwendung der 0 (null) oder mehrmals ausgeführt werden soll, verwenden Sie stattdessen die <xref:System.Activities.Statements.While>-Aktivität.

## <a name="dowhile-properties-in-the-workflow-designer"></a>DoWhile- Eigenschaften im Workflow-Designer

In der folgende Tabelle werden die nützlichsten <xref:System.Activities.Statements.DoWhile> Aktivitätseigenschaften, und beschreibt, wie Sie diese in den Designer verwenden:

|Eigenschaftenname|Erforderlich|Verwendung|
|-|--------------|-|
|<xref:System.Activities.Statements.DoWhile.Body%2A>|False|Die Aktivität, die ausgeführt werden, solange die Bedingung **"true"**. Hinzufügen der <xref:System.Activities.Statements.DoWhile.Body%2A> -Aktivität, indem Sie eine Aktivität aus der Toolbox in die **Text** Feld der **DoWhile** Aktivitäts-Designer, mit dem Hinweistext "Aktivität hier ablegen".|
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|True|Die Bedingung, die nach jedem Schleifendurchlauf ausgewertet werden soll. Festlegen der <xref:System.Activities.Statements.DoWhile.Condition%2A>, geben Sie einen Visual Basic-Ausdruck in der **Bedingung** Feld der **DoWhile** -Aktivitätsdesigner oder im Eigenschaftenraster.|

## <a name="see-also"></a>Siehe auch

- [While](../workflow-designer/while-activity-designer.md)
- [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)
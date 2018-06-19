---
title: Workflow-Designer - DoWhile-Aktivitätsdesigner
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 23588a044596ce5250cc68d01263f5d80775866a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31969977"
---
# <a name="dowhile-activity-designer"></a>DoWhile-Aktivitätsdesigner

Die <xref:System.Activities.Statements.DoWhile> Aktivität ausgeführt wird, die im enthaltene Aktivität seine <xref:System.Activities.Statements.DoWhile.Body%2A> mindestens einmal, bis eine angegebene Bedingung ergibt **"false"**. Wenn die in einem Schleifentext enthaltene Anwendung der 0 (null) oder mehrmals ausgeführt werden soll, verwenden Sie stattdessen die <xref:System.Activities.Statements.While>-Aktivität.

## <a name="dowhile-properties-in-the-workflow-designer"></a>DoWhile- Eigenschaften im Workflow-Designer

In der folgenden Tabelle werden die nützlichsten <xref:System.Activities.Statements.DoWhile> Eigenschaften der Aktivität, und beschreibt, wie sie im Designer zu verwenden:

|Eigenschaftenname|Erforderlich|Verwendung|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.DoWhile.Body%2A>|False|Die Aktivität ausführen, während die Bedingung **"true"**. Hinzufügen der <xref:System.Activities.Statements.DoWhile.Body%2A> Aktivität, indem Sie eine Aktivität aus der Toolbox in den **Text** Feld der **DoWhile** Aktivitäts-Designer mit dem Hinweistext "Aktivität hier ablegen".|
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|True|Die Bedingung, die nach jedem Schleifendurchlauf ausgewertet werden soll. Festlegen der <xref:System.Activities.Statements.DoWhile.Condition%2A>, geben Sie einen Visual Basic-Ausdruck in der **Bedingung** Feld der **DoWhile** -Aktivitätsdesigner oder im Eigenschaftenraster.|

## <a name="see-also"></a>Siehe auch

- [While](../workflow-designer/while-activity-designer.md)
- [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)
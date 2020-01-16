---
title: Workflow-Designer-while-Aktivitäts Designer
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.While.UI
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 77954925533c51885a056f7156121e68851ad769
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2020
ms.locfileid: "76115166"
---
# <a name="while-activity-designer"></a>While-Aktivitätsdesigner

Die <xref:System.Activities.Statements.While>-Aktivität führt die in der <xref:System.Activities.Statements.While.Body%2A> enthaltene Aktivität aus, während die angegebene <xref:System.Activities.Statements.While.Condition%2A> als **true**ausgewertet wird. Die enthaltene Aktivität wird möglicherweise nie ausgeführt. Wenn die enthaltene Aktivität wenigstens einmal ausgeführt werden soll, verwenden Sie stattdessen die <xref:System.Activities.Statements.DoWhile>-Aktivität.

## <a name="while-properties-in-workflow-designer"></a>While-Eigenschaften im Workflow-Designer

In der folgenden Tabelle werden die nützlichsten Eigenschaften der <xref:System.Activities.Statements.While>-Aktivität aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.

|Eigenschaftsname|Erforderlich|Verwendungs-|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falsch|Gibt den benutzerfreundlichen Namen der <xref:System.Activities.Statements.While>Aktivität im Header an. Der Standardwert lautet While. Der Wert kann im **Eigenschaften** Fenster oder direkt im Header des Aktivitäts Designers bearbeitet werden.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.While.Body%2A>|Falsch|Enthält die Aktivität, die ausgeführt werden soll, während die <xref:System.Activities.Statements.While.Condition%2A> als **true**ausgewertet wird.|
|<xref:System.Activities.Statements.While.Condition%2A>|True|Enthält den Visual Basic Ausdruck, der ausgewertet wird, um zu bestimmen, ob die Aktivität in der <xref:System.Activities.Statements.While.Body%2A> ausgeführt werden soll.|

## <a name="see-also"></a>Siehe auch

- [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)
- [DoWhile](../workflow-designer/dowhile-activity-designer.md)

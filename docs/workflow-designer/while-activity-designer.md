---
title: Workflow-Designer - beim Aktivitäts-Designer
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.While.UI
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: de41c8351c7767cbfe0882cffb48b145e341f923
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49835864"
---
# <a name="while-activity-designer"></a>While-Aktivitätsdesigner

Die <xref:System.Activities.Statements.While> Aktivität ausgeführt wird, die im enthaltene Aktivität die <xref:System.Activities.Statements.While.Body%2A> die angegebene <xref:System.Activities.Statements.While.Condition%2A> ergibt **"true"**. Die enthaltene Aktivität wird möglicherweise nie ausgeführt. Wenn die enthaltene Aktivität wenigstens einmal ausgeführt werden soll, verwenden Sie stattdessen die <xref:System.Activities.Statements.DoWhile>-Aktivität.

## <a name="while-properties-in-workflow-designer"></a>While-Eigenschaften im Workflow-Designer

In der folgenden Tabelle werden die nützlichsten Eigenschaften der <xref:System.Activities.Statements.While>-Aktivität aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den benutzerfreundlichen Namen der <xref:System.Activities.Statements.While>Aktivität im Header an. Der Standardwert lautet While. Der Wert kann bearbeitet werden, der **Eigenschaften** Fenster oder direkt im Header Aktivitätsdesigners.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.While.Body%2A>|False|Enthält die auszuführende Aktivität während der <xref:System.Activities.Statements.While.Condition%2A> ergibt **"true"**.|
|<xref:System.Activities.Statements.While.Condition%2A>|True|Enthält den Visual Basic-Ausdruck, der ausgewertet wird, um zu bestimmen, ob die Aktivität in der <xref:System.Activities.Statements.While.Body%2A> ausgeführt werden soll.|

## <a name="see-also"></a>Siehe auch

- [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)
- [DoWhile](../workflow-designer/dowhile-activity-designer.md)
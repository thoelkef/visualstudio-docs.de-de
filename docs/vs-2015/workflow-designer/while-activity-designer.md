---
title: While-Aktivitäts Designer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.While.UI
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fae1b4905d66a5162591fd7c720ba81ed7ffda82
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72606609"
---
# <a name="while-activity-designer"></a>While-Aktivitätsdesigner

Die <xref:System.Activities.Statements.While>-Aktivität führt die in der <xref:System.Activities.Statements.While.Body%2A> enthaltene Aktivität aus, während die angegebene Bedingung als **true**ausgewertet wird. Die enthaltene Aktivität wird möglicherweise nie ausgeführt. Wenn die enthaltene Aktivität wenigstens einmal ausgeführt werden soll, verwenden Sie stattdessen die <xref:System.Activities.Statements.DoWhile>-Aktivität.

## <a name="while-properties-in-workflow-designer"></a>While-Eigenschaften im Workflow-Designer

In der folgenden Tabelle werden die nützlichsten Eigenschaften der <xref:System.Activities.Statements.While>-Aktivität aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den benutzerfreundlichen Namen der <xref:System.Activities.Statements.While>Aktivität im Header an. Der Standardwert lautet While. Der Wert kann im **Eigenschaften** Fenster oder direkt im Header des Aktivitäts Designers bearbeitet werden.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.While.Body%2A>|False|Enthält die Aktivität, die ausgeführt werden soll, während die <xref:System.Activities.Statements.While.Condition%2A> als **true**ausgewertet wird.|
|<xref:System.Activities.Statements.While.Condition%2A>|True|Enthält den [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]-Ausdruck, dessen Auswertung bestimmt, ob die Aktivität im <xref:System.Activities.Statements.While.Body%2A> ausgeführt wird.|

## <a name="see-also"></a>Siehe auch

- [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)
- [DoWhile](../workflow-designer/dowhile-activity-designer.md)
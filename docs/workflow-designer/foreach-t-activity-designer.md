---
title: ForEach&lt;T&gt; Aktivitäts-Designer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ForEach`1.UI
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3a9f62f8b3fcb96d0d0abc8ba52b2d0ccfb42473
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="foreachlttgt-activity-designer"></a>ForEach&lt;T&gt; Aktivitäts-Designer
Die <xref:System.Activities.Statements.ForEach%601>-Aktivität führt die in ihrem <xref:System.Activities.Statements.ForEach%601.Body%2A> enthaltene Aktivität für jedes Element einer angegebenen <xref:System.Activities.Statements.ForEach%601.Values%2A>-Auflistung aus.

## <a name="foreacht-properties-in-the-workflow-designer"></a>ForEach < T\> Eigenschaften im Workflow-Designer
 In der folgenden Tabelle werden die nützlichsten Eigenschaften der <xref:System.Activities.Statements.ForEach%601>-Aktivität aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der Anzeigename der <xref:System.Activities.Statements.ForEach%601>-Aktivität. Der Standardwert lautet ForEach < Int32\>. Obwohl der <xref:System.Activities.Activity.DisplayName%2A>-Wert nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|True|Die Auflistung, deren Elemente durchlaufen werden. Festlegen der <xref:System.Activities.Statements.ForEach%601.Values%2A>, geben Sie einen [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Ausdruck in der **Werte** Feld der **ForEach < T\>**  -Aktivitätsdesigner oder im Eigenschaftenraster.|
|*TypeArgument*|True|Der Typ der Elemente in der <xref:System.Activities.Statements.ForEach%601.Values%2A> durch den generischen Parameter angegebene Sammlung *T*. Standardmäßig *TypeArgument* festgelegt ist, um **Int32**. Um den Typ zu ändern, ändern Sie den Wert von der *TypeArgument* Kombinationsfeld im Eigenschaftenraster.|

 Standardmäßig lautet der schleifeniterator **Element**. Sie können den Namen der Iteratorvariablen im <xref:System.Activities.Statements.ForEach%601>-Aktivitätsdesigner ändern. Der Schleifeniterator kann in den untergeordneten Elementen der <xref:System.Activities.Statements.ForEach%601>-Aktivität in Ausdrücken verwendet werden.

## <a name="see-also"></a>Siehe auch

- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)
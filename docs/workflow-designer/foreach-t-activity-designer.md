---
title: Workflow-Designer - ForEach&lt;T&gt; Aktivitäts-Designer
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.ForEach`1.UI
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 99531f690e9dcbd1b35453acd17f1c52b8afb1d2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836215"
---
# <a name="foreachlttgt-activity-designer"></a>ForEach&lt;T&gt; Aktivitäts-Designer

Die <xref:System.Activities.Statements.ForEach%601>-Aktivität führt die in ihrem <xref:System.Activities.Statements.ForEach%601.Body%2A> enthaltene Aktivität für jedes Element einer angegebenen <xref:System.Activities.Statements.ForEach%601.Values%2A>-Auflistung aus.

## <a name="foreacht-properties-in-the-workflow-designer"></a>ForEach < T\> Eigenschaften im Workflow-Designer

In der folgenden Tabelle werden die nützlichsten Eigenschaften der <xref:System.Activities.Statements.ForEach%601>-Aktivität aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der Anzeigename der <xref:System.Activities.Statements.ForEach%601>-Aktivität. Der Standardwert lautet ForEach < Int32\>. Obwohl der <xref:System.Activities.Activity.DisplayName%2A>-Wert nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|True|Die Auflistung, deren Elemente durchlaufen werden. Festlegen der <xref:System.Activities.Statements.ForEach%601.Values%2A>, geben Sie einen Visual Basic-Ausdruck in der **Werte** Feld der **ForEach < T\>**  -Aktivitätsdesigner oder im Eigenschaftenraster.|
|*TypeArgument*|True|Der Typ der Elemente in der <xref:System.Activities.Statements.ForEach%601.Values%2A> durch den generischen Parameter angegebene Sammlung *T*. In der Standardeinstellung *TypeArgument* nastaven NA hodnotu **Int32**. Um den Typ zu ändern, ändern Sie den Wert des der *TypeArgument* Kombinationsfeld im Eigenschaftenraster.|

In der Standardeinstellung der schleifeniterator die Bezeichnung **Element**. Sie können den Namen der Iteratorvariablen im <xref:System.Activities.Statements.ForEach%601>-Aktivitätsdesigner ändern. Der Schleifeniterator kann in den untergeordneten Elementen der <xref:System.Activities.Statements.ForEach%601>-Aktivität in Ausdrücken verwendet werden.

## <a name="see-also"></a>Siehe auch

- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)
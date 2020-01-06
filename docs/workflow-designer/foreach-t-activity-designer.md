---
title: Workflow-Designer foreach&lt;t&gt; Aktivitäts Designer
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ForEach`1.UI
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 30d43351211a6ff857630b47f05be77e27bd7951
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593914"
---
# <a name="foreachlttgt-activity-designer"></a>Foreach-&lt;t&gt; Aktivitäts Designer

Die <xref:System.Activities.Statements.ForEach%601>-Aktivität führt die in ihrem <xref:System.Activities.Statements.ForEach%601.Body%2A> enthaltene Aktivität für jedes Element einer angegebenen <xref:System.Activities.Statements.ForEach%601.Values%2A>-Auflistung aus.

## <a name="foreacht-properties-in-the-workflow-designer"></a>Foreach < T\> Eigenschaften im Workflow-Designer

In der folgenden Tabelle werden die nützlichsten Eigenschaften der <xref:System.Activities.Statements.ForEach%601>-Aktivität aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.

|Eigenschaftsname|Erforderlich|Verwendungs-|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falsch|Der Anzeigename der <xref:System.Activities.Statements.ForEach%601>-Aktivität. Der Standardwert ist foreach < Int32\>. Obwohl der <xref:System.Activities.Activity.DisplayName%2A>-Wert nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|True|Die Auflistung, deren Elemente durchlaufen werden. Um die <xref:System.Activities.Statements.ForEach%601.Values%2A>festzulegen, geben Sie im Feld **Werte** des **foreach-< t\>** -Aktivitäts Designers oder im Eigenschaften Raster einen Visual Basic Ausdruck ein.|
|*TypeArgument*|True|Der Typ der Elemente in der <xref:System.Activities.Statements.ForEach%601.Values%2A> Auflistung, der durch den generischen Parameter *t*angegeben wird. Standardmäßig ist *TypeArgument* auf **Int32**festgelegt. Ändern Sie den Wert des Kombinations Felds *TypeArgument* im Eigenschaften Raster, um den Typ zu ändern.|

Standardmäßig wird als Schleifen Iterator " **Item**" bezeichnet. Sie können den Namen der Iteratorvariablen im <xref:System.Activities.Statements.ForEach%601>-Aktivitätsdesigner ändern. Der Schleifeniterator kann in den untergeordneten Elementen der <xref:System.Activities.Statements.ForEach%601>-Aktivität in Ausdrücken verwendet werden.

## <a name="see-also"></a>Siehe auch

- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)

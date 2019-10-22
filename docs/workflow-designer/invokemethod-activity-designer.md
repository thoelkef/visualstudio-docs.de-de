---
title: Workflow-Designer-InvokeMethod-Aktivitäts Designer
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.InvokeMethod.UI
ms.assetid: 15e6efdc-52ca-46d8-9c5e-063f7c8265a6
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 593ec198cdfdd8acd1967abb046384711e1fa9ac
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650167"
---
# <a name="invokemethod-activity-designer"></a>InvokeMethod-Aktivitätsdesigner

Der **InvokeMethod** -Designer wird verwendet, um eine <xref:System.Activities.Statements.InvokeMethod>-Aktivität zu erstellen und zu konfigurieren.

## <a name="the-invokemethod-activity"></a>Die InvokeMethod-Aktivität

Die <xref:System.Activities.Statements.InvokeMethod>-Aktivität ruft eine öffentliche Methode eines angegebenen Objekts oder Typs auf.

### <a name="use-the-invokemethod-activity-designer"></a>Verwenden des InvokeMethod-Aktivitäts Designers

Greifen Sie in der Kategorie **Primitives** der **Toolbox**auf den **InvokeMethod** -Aktivitäts Designer zu. Der **InvokeMethod** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der Workflow-Designer Oberfläche abgelegt werden, wo Aktivitäten normalerweise platziert werden, z. b. innerhalb eines <xref:System.Activities.Statements.Sequence>. Beim Löschen des Aktivitäts Designers wird eine <xref:System.Activities.Statements.InvokeMethod>-Aktivität mit einem Standard <xref:System.Activities.Activity.DisplayName%2A> von InvokeMethod erstellt. Der <xref:System.Activities.Activity.DisplayName%2A> kann im Header des **InvokeMethod** -Aktivitäts Designers oder im Feld **Display Name** des Eigenschaften Rasters bearbeitet werden.

### <a name="the-invokemethod-properties"></a>InvokeMethod-Eigenschaften

In der folgenden Tabelle sind die <xref:System.Activities.Statements.InvokeMethod> Eigenschaften aufgeführt, und es wird beschrieben, wie Sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaften Raster bearbeitet werden, und einige können auf Workflow-Designer Oberfläche bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der Anzeigename der <xref:System.Activities.Statements.InvokeMethod>-Aktivität. Der Standardwert lautet InvokeMethod.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht unbedingt erforderlich ist, empfiehlt es sich, einen zu verwenden.|
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|True|Der Name der Methode, die bei Ausführung der Aktivität aufgerufen werden soll. Die aufgerufene Methode muss als **öffentlich**deklariert werden. Diese Eigenschaft kann auf der Designer Oberfläche bearbeitet werden und ist obligatorisch.|
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|False|Die Parameterauflistung der aufgerufenen Methode. Die Parameter müssen der Auflistung in derselben Reihenfolge wie in der Methodensignatur hinzugefügt werden. Um das Dialogfeld " **Parameter** " anzuzeigen, in dem Sie diese Eigenschaft festlegen können, klicken Sie im Eigenschaften Raster **auf die Schalt** Fläche mit den Auslassungs Punkten. Klicken Sie auf die Schaltfläche **Argument erstellen** , um die Parameter hinzuzufügen.|
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|False|Der Rückgabewert des Methodenaufrufs.|
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|True|Gibt an, ob die Methode asynchron aufgerufen wird. Der Standardwert ist **false**.|
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|False|Das Objekt, das die aufzurufende Methode enthält. Diese Eigenschaft kann in der Designeroberfläche bearbeitet werden.<br /><br /> Es muss entweder das <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>-Objekt oder der <xref:System.Activities.Statements.InvokeMethod.TargetType%2A>-Typ festgelegt werden.|
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|False|Der <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>-Typ. Diese Eigenschaft kann in der Designeroberfläche bearbeitet werden. Diese Eigenschaft muss nur festgelegt werden, wenn die aufgerufene Methode statisch ist.|

Wenn Sie Parameter als C# **out** -Parameter übergeben möchten (z. b. `Method1(out myParam))`, verwenden Sie **OutArgument** anstelle von **InOutArgument** .

Methoden mit Argumenten, die als **TargetObject** oder **Result** bezeichnet werden, können nicht mithilfe der <xref:System.Activities.Statements.InvokeMethod> Aktivität aufgerufen werden. Der Grund dafür ist, dass die <xref:System.Activities.Statements.InvokeMethod>-Aktivität <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A>, <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> und <xref:System.Activities.Statements.InvokeMethod.Result%2A> in <xref:System.Activities.Activity.CacheMetadata%2A> registriert.

Der Algorithmus zum Registrieren der Parameter in <xref:System.Activities.Activity.CacheMetadata%2A> wird in der folgenden Liste dargestellt:

1. Registrieren Sie das <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>-Argument.

2. Registrieren Sie das <xref:System.Activities.Statements.InvokeMethod.Result%2A>-Argument.

3. Durchlaufen Sie die <xref:System.Activities.Statements.InvokeMethod.Parameters%2A>-Auflistung, und registrieren Sie jedes Argument.

Die resultierende Ausnahme hat den Typ <xref:System.Activities.InvalidWorkflowException> mit der folgenden Meldung: 'InvokeMethod': Eine Variable, RuntimeArgument oder ein DelegateArgument ist bereits mit dem Namen 'TargetObject' vorhanden. Namen müssen innerhalb einer Umgebung eindeutig sein.

Diese Einschränkung gilt nicht für <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> und <xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>. Dabei handelt es sich nicht um Workflow Argumente, die daher nicht in der <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A>-Auflistung der <xref:System.Activities.Statements.InvokeMethod> Aktivität in der <xref:System.Activities.Activity.CacheMetadata%2A>-Methode registriert sind.

## <a name="see-also"></a>Siehe auch

- [Primitive](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [Delay](../workflow-designer/delay-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)
---
title: Workflow-Designer - InvokeMethod-Aktivitätsdesigner
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.InvokeMethod.UI
ms.assetid: 15e6efdc-52ca-46d8-9c5e-063f7c8265a6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eed5d81cce05b316ef7593639e868936e7f2fa69
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62537640"
---
# <a name="invokemethod-activity-designer"></a>InvokeMethod-Aktivitätsdesigner

**InvokeMethod** -Designer dient zum Erstellen und Konfigurieren einer <xref:System.Activities.Statements.InvokeMethod> Aktivität.

## <a name="the-invokemethod-activity"></a>Die InvokeMethod-Aktivität

Die <xref:System.Activities.Statements.InvokeMethod>-Aktivität ruft eine öffentliche Methode eines angegebenen Objekts oder Typs auf.

### <a name="use-the-invokemethod-activity-designer"></a>Verwenden der InvokeMethod-Aktivitätsdesigner

Zugriff die **InvokeMethod** Aktivitäts-Designer in der **primitive** Kategorie der **Toolbox**. Die **InvokeMethod** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** und sich der Workflow-Designer-Oberfläche gelöscht wird, egal wo Aktivitäten normalerweise platziert werden, z. B. in einem <xref:System.Activities.Statements.Sequence>. Löschen die Aktivitäts-Designer erstellt eine <xref:System.Activities.Statements.InvokeMethod> -Aktivität mit dem standardmäßigen <xref:System.Activities.Activity.DisplayName%2A> -Standardwert InvokeMethod. Die <xref:System.Activities.Activity.DisplayName%2A> kann im Header des bearbeitet werden die **InvokeMethod** Aktivitäts-Designer oder in der **"DisplayName"** Feld des Eigenschaftenrasters.

### <a name="the-invokemethod-properties"></a>Die InvokeMethod-Eigenschaften

Die folgende Tabelle zeigt die <xref:System.Activities.Statements.InvokeMethod> Eigenschaften und beschreibt, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster bearbeitet werden, und einige auf die Oberfläche des Workflow-Designer bearbeitet werden kann.

|Eigenschaftenname|Erforderlich|Verwendung|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der Anzeigename der <xref:System.Activities.Statements.InvokeMethod>-Aktivität. Der Standardwert lautet InvokeMethod.<br /><br /> Obwohl die <xref:System.Activities.Activity.DisplayName%2A> ist nicht zwingend erforderlich, es wird empfohlen, einen verwenden.|
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|True|Der Name der Methode, die bei Ausführung der Aktivität aufgerufen werden soll. Die aufgerufene Methode muss deklariert werden, als **öffentliche**. Diese Eigenschaft auf der Designeroberfläche bearbeitet werden kann, und es ist zwingend erforderlich.|
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|False|Die Parameterauflistung der aufgerufenen Methode. Die Parameter müssen der Auflistung in derselben Reihenfolge wie in der Methodensignatur hinzugefügt werden. Zum Anzeigen der **Parameter** Dialogfeld, in dem Sie diese Eigenschaft festlegen können, klicken Sie auf die Schaltfläche mit den Auslassungspunkten, in der **Parameter** Feld des Eigenschaftenrasters. Klicken Sie auf die **Argument erstellen** , um die Parameter hinzuzufügen.|
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|False|Der Rückgabewert des Methodenaufrufs.|
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|True|Gibt an, ob die Methode asynchron aufgerufen wird. Der Standardwert ist **"false"**.|
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|False|Das Objekt, das die aufzurufende Methode enthält. Diese Eigenschaft kann in der Designeroberfläche bearbeitet werden.<br /><br /> Es muss entweder das <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>-Objekt oder der <xref:System.Activities.Statements.InvokeMethod.TargetType%2A>-Typ festgelegt werden.|
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|False|Der <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>-Typ. Diese Eigenschaft kann in der Designeroberfläche bearbeitet werden. Diese Eigenschaft muss nur festgelegt werden, wenn die aufgerufene Methode statisch ist.|

Zum Übergeben von Parametern als c# **out** Parameter (z. B. `Method1(out myParam))`, verwenden Sie **OutArgument** anstelle von **InOutArgument**

Methoden mit Argumenten namens **TargetObject** oder **Ergebnis** kann nicht aufgerufen werden, mithilfe der <xref:System.Activities.Statements.InvokeMethod> Aktivität. Der Grund dafür ist, dass die <xref:System.Activities.Statements.InvokeMethod>-Aktivität <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A>, <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> und <xref:System.Activities.Statements.InvokeMethod.Result%2A> in <xref:System.Activities.Activity.CacheMetadata%2A> registriert.

Der Algorithmus zum Registrieren der Parameter in <xref:System.Activities.Activity.CacheMetadata%2A> wird in der folgenden Liste dargestellt:

1. Registrieren Sie das <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>-Argument.

2. Registrieren Sie das <xref:System.Activities.Statements.InvokeMethod.Result%2A>-Argument.

3. Durchlaufen Sie die <xref:System.Activities.Statements.InvokeMethod.Parameters%2A>-Auflistung, und registrieren Sie jedes Argument.

Die resultierende Ausnahme ist vom Typ <xref:System.Activities.InvalidWorkflowException> mit folgender Meldung: 'InvokeMethod': Mit dem Namen 'TargetObject' ist eine Variable, RuntimeArgument oder ein DelegateArgument ist bereits vorhanden. Namen müssen innerhalb einer Umgebung eindeutig sein.

Diese Einschränkung gilt nicht für <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> und <xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>. Sie sind sich nicht um workflowargumente und aus diesem Grund sind nicht registriert die <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> Auflistung von der <xref:System.Activities.Statements.InvokeMethod> -Aktivität in der <xref:System.Activities.Activity.CacheMetadata%2A> Methode.

## <a name="see-also"></a>Siehe auch

- [Primitive](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [Delay](../workflow-designer/delay-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)
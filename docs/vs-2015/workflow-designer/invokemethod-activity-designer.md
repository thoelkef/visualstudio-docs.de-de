---
title: InvokeMethod-Aktivitäts Designer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.InvokeMethod.UI
ms.assetid: 15e6efdc-52ca-46d8-9c5e-063f7c8265a6
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fcfba979ba7fce4aeffab1fe9e9a5a3728e513af
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658990"
---
# <a name="invokemethod-activity-designer"></a>InvokeMethod-Aktivitätsdesigner
Der **InvokeMethod** -Designer wird verwendet, um eine Aktivität zu erstellen und zu konfigurieren <xref:System.Activities.Statements.InvokeMethod> .

## <a name="the-invokemethod-activity"></a>Die InvokeMethod-Aktivität
 Die <xref:System.Activities.Statements.InvokeMethod>-Aktivität ruft eine öffentliche Methode eines angegebenen Objekts oder Typs auf.

### <a name="using-the-invokemethod-activity-designer"></a>Verwenden des InvokeMethod-Aktivitätsdesigners
 Der **InvokeMethod** -Aktivitäts Designer befindet sich in der Kategorie **Primitives** der **Toolbox**, auf die Sie zugreifen können, indem Sie auf die Registerkarte **Toolbox** klicken. (Sie können auch im [!INCLUDE[wfd2](../includes/wfd2-md.md)] Menü **Ansicht** den Befehl **Symbolleiste** auswählen, oder Crtl + ALT + X.)

 Der **InvokeMethod** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der- [!INCLUDE[wfd2](../includes/wfd2-md.md)] Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden, z. b. in einer <xref:System.Activities.Statements.Sequence> . Daraufhin wird eine <xref:System.Activities.Statements.InvokeMethod>-Aktivität mit dem <xref:System.Activities.Activity.DisplayName%2A>-Standardwert InvokeMethod erstellt. Der <xref:System.Activities.Activity.DisplayName%2A> kann im Header des **InvokeMethod** -Aktivitäts Designers oder im Feld **Display Name** des Eigenschaften Rasters bearbeitet werden.

### <a name="the-invokemethod-properties"></a>Die InvokeMethod-Eigenschaften
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.InvokeMethod>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster bearbeitet werden, einige davon können auch in der [!INCLUDE[wfd2](../includes/wfd2-md.md)]-Designeroberfläche bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verbrauch|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Falsch|Der Anzeigename der <xref:System.Activities.Statements.InvokeMethod>-Aktivität. Der Standardwert lautet InvokeMethod.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|Richtig|Der Name der Methode, die bei Ausführung der Aktivität aufgerufen werden soll. Die aufgerufene Methode muss als **öffentlich**deklariert werden. Diese Eigenschaft kann in der Designeroberfläche bearbeitet werden. Dies ist eine obligatorische Eigenschaft.|
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|Falsch|Die Parameterauflistung der aufgerufenen Methode. Die Parameter müssen der Auflistung in derselben Reihenfolge wie in der Methodensignatur hinzugefügt werden. Klicken Sie im Eigenschaften Raster im Feld **Parameter** auf die Schaltfläche mit den Auslassungs Punkten. Daraufhin wird das Dialogfeld **Parameter** angezeigt, in dem Sie diese Eigenschaft festlegen können. Klicken Sie auf die Schaltfläche **Argument erstellen** , um die Parameter hinzuzufügen.|
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|Falsch|Der Rückgabewert des Methodenaufrufs.|
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|Richtig|Gibt an, ob die Methode asynchron aufgerufen wird. Der Standardwert ist **False**.|
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|Falsch|Das Objekt, das die aufzurufende Methode enthält. Diese Eigenschaft kann in der Designeroberfläche bearbeitet werden.<br /><br /> Es muss entweder das <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>-Objekt oder der <xref:System.Activities.Statements.InvokeMethod.TargetType%2A>-Typ festgelegt werden.|
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|Falsch|Der <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>-Typ. Diese Eigenschaft kann in der Designeroberfläche bearbeitet werden. Diese Eigenschaft muss nur festgelegt werden, wenn die aufgerufene Methode statisch ist.|

 Zum Übergeben von Parametern als c#- **out** -Parameter (z. b. `Method1(out myParam)),` sollten Sie **OutArgument** anstelle von **InOutArgument** verwenden).

 Methoden mit Argumenten, die als **TargetObject** oder **Result** bezeichnet werden, können nicht mithilfe der-Aktivität aufgerufen werden <xref:System.Activities.Statements.InvokeMethod> . Der Grund dafür ist, dass die <xref:System.Activities.Statements.InvokeMethod>-Aktivität <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A>, <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> und <xref:System.Activities.Statements.InvokeMethod.Result%2A> in <xref:System.Activities.Activity.CacheMetadata%2A> registriert.

 Der Algorithmus zum Registrieren der Parameter in <xref:System.Activities.Activity.CacheMetadata%2A> wird in der folgenden Liste dargestellt:

1. Registrieren Sie das <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>-Argument.

2. Registrieren Sie das <xref:System.Activities.Statements.InvokeMethod.Result%2A>-Argument.

3. Durchlaufen Sie die <xref:System.Activities.Statements.InvokeMethod.Parameters%2A>-Auflistung, und registrieren Sie jedes Argument.

   Die resultierende Ausnahme hat den Typ <xref:System.Activities.InvalidWorkflowException> mit der folgenden Meldung: 'InvokeMethod': Eine Variable, RuntimeArgument oder ein DelegateArgument ist bereits mit dem Namen 'TargetObject' vorhanden. Namen müssen innerhalb einer Umgebung eindeutig sein.

   Diese Einschränkung gilt nicht für <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> und <xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>, da sie keine Workflowargumente sind und daher nicht in der <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A>-Auflistung der <xref:System.Activities.Statements.InvokeMethod>-Aktivität in der <xref:System.Activities.Activity.CacheMetadata%2A>-Methode registriert werden.

## <a name="see-also"></a>Weitere Informationen
 [Primitives](../workflow-designer/primitives-activity-designers.md) [Assign](../workflow-designer/assign-activity-designer.md) "" [Verzögert](../workflow-designer/delay-activity-designer.md) " [Write teline](../workflow-designer/writeline-activity-designer.md) "
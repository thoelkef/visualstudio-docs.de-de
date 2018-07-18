---
title: Workflow-Designer - ExistsInCollection&lt;T&gt; Aktivitäts-Designer
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.ExistsInCollection`1.UI
ms.assetid: 0acf9a13-caf5-4bb4-ba22-ec37d2b7267a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4c5625f42489752647da57fad9956cff8c64b8f5
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31974399"
---
# <a name="existsincollectiont-activity-designer"></a>ExistsInCollection\<T >-Aktivitätsdesigners

Die **ExistsInCollection\<T >** Aktivitäts-Designer dient zum Erstellen und Konfigurieren einer <xref:System.Activities.Statements.ExistsInCollection%601> Aktivität.

## <a name="the-existsincollectiont-activity"></a>Die ExistsInCollection\<T >-Aktivität
 Mit der <xref:System.Activities.Statements.ExistsInCollection%601>-Aktivität wird bestimmt, ob ein angegebenes Element in einer bestimmten Auflistung vorhanden ist.

### <a name="using-the-existsincollectiont-activity-designer"></a>Verwenden die ExistsInCollection\<T >-Aktivitätsdesigners
 Die **ExistsInCollection\<T >** Aktivitäts-Designer finden Sie in der **Auflistung** Kategorie von der **Toolbox**, indem Sie auf die zugegriffenwird **Toolbox** des Workflow-Designers (Wählen Sie alternativ **Symbolleiste** aus der **Ansicht** Menüs oder STRG + ALT + X.)

 Die **ExistsInCollection\<T >** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** und sich der Workflow-Designer-Oberfläche gelöscht wird, wo Aktivitäten normalerweise platziert werden, z. B. in eine <xref:System.Activities.Statements.Sequence>. Dies erstellt eine <xref:System.Activities.Statements.ExistsInCollection%601> -Aktivität mit dem standardmäßigen <xref:System.Activities.Activity.DisplayName%2A> des ExistsInCollection < Int32\>. (Standardmäßig der *TypeArgument* ist **Int32**. Diese Einstellung kann im Eigenschaftenraster geändert werden.)  Die <xref:System.Activities.Activity.DisplayName%2A> Wert kann im Header des bearbeitet werden die **ExistsInCollection < T\>**  Aktivitäts-Designer oder in der **DisplayName** Feld des Eigenschaftenrasters. Die anderen Eigenschaften müssen im Eigenschaftenraster bearbeitet werden.

### <a name="the-existsincollectiont-properties"></a>Die ExistsInCollection\<T > Eigenschaften
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.ExistsInCollection%601>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der Anzeigename der <xref:System.Activities.Statements.ExistsInCollection%601>-Aktivität. Der Standardwert ist ExistsInCollection < Int32\>. Obwohl der <xref:System.Activities.Activity.DisplayName%2A>-Wert nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Item%2A>|True|Das Element der Auflistung hinzuzufügende\<T >. Dieses Element ist vom Typ *T* ist vom Typ *TypeArgument*. Zum Angeben des Elements geben Sie im Eigenschaftenraster einen Visual Basic-Ausdruck ein.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Collection%2A>|True|Die Auflistung, zu der das Element hinzugefügt werden soll. Diese Sammlung ist vom Typ **ICollection < TypeArgument\>.** Geben Sie im Eigenschaftenraster einen Visual Basic-Ausdruck ein, um die Auflistung anzugeben.|
|*TypeArgument*|True|Der Typ T der in der <xref:System.Collections.Generic.ICollection%601> enthaltenen Elemente. Standardmäßig dies *TypeArgument* Typ festgelegt ist, um **Int32**. Um den Typ zu ändern, ändern Sie den Wert von der *TypeArgument* im Kombinationsfeld im Eigenschaftenraster.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Ein Wert, der angibt, ob das angegebene Element in der Auflistung vorhanden ist. Um eine Variable anzugeben, die an das Ergebnis gebunden wird, geben Sie im Eigenschaftenraster eine Visual Basic-Variable ein.|

## <a name="see-also"></a>Siehe auch

- [Auflistung](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)
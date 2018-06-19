---
title: Workflow-Designer - AddToCollection<T> Aktivitäts-Designer
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.AddToCollection`1.UI
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2b32df48f79d60500cb23a40c5273ceeedfc9c56
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31976701"
---
# <a name="addtocollectiont-activity-designer"></a>AddToCollection\<T >-Aktivitätsdesigners

Die **AddToCollection\<T >** Aktivitäts-Designer dient zum Erstellen und Konfigurieren einer <xref:System.Activities.Statements.AddToCollection%601> Aktivität.

## <a name="the-addtocollectiont-activity"></a>Die AddToCollection\<T >-Aktivität

Die <xref:System.Activities.Statements.AddToCollection%601>-Aktivität fügt einer Auflistung ein Element hinzu.

### <a name="using-the-addtocollectiont-activity-designer"></a>Verwenden die AddToCollection\<T >-Aktivitätsdesigners

Die **AddToCollection\<T >** Aktivitäts-Designer finden Sie in der **Auflistung** Kategorie von der **Toolbox**, indem Sie auf die zugegriffenwird **Toolbox** Registerkarte im Workflow-Designer (Wählen Sie alternativ **Symbolleiste** aus der **Ansicht** Menüs oder STRG + ALT + X.)

Die **AddToCollection\<T >** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** und sich der Workflow-Designer-Oberfläche gelöscht wird, wo Aktivitäten platziert werden, etwa innerhalb einer <xref:System.Activities.Statements.Sequence>. Löschen der **AddToCollection\<T >** Aktivitäts-Designer erstellt eine <xref:System.Activities.Statements.AddToCollection%601> -Aktivität mit dem standardmäßigen <xref:System.Activities.Activity.DisplayName%2A> von AddToCollection < Int32\>. (Standardmäßig der *TypeArgument* ist **Int32**. TypeArgument kann im Eigenschaftenraster geändert werden.) Die <xref:System.Activities.Activity.DisplayName%2A> Wert kann im Header des bearbeitet werden die **AddToCollection < T\>**  Aktivitäts-Designer oder in der **DisplayName** Feld des Eigenschaftenrasters. Die anderen Eigenschaften müssen im Eigenschaftenraster bearbeitet werden.

### <a name="the-addtocollectiont-properties"></a>Die AddToCollection\<T > Eigenschaften

In der folgenden Tabelle werden die <xref:System.Activities.Statements.AddToCollection%601>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der Anzeigename der <xref:System.Activities.Statements.AddToCollection%601>-Aktivität. Der Standardname lautet AddToCollection < Int32\>. Obwohl der <xref:System.Activities.Activity.DisplayName%2A>-Wert nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|True|Das Element der Auflistung hinzuzufügende\<T >. Dieses Element ist vom Typ *T*, vom Typ *TypeArgument*. Geben Sie im Eigenschaftenraster einen Visual Basic-Ausdruck ein, um das Element anzugeben.|
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|True|Die Auflistung, zu der das Element hinzugefügt werden soll. Diese Sammlung ist vom Typ **ICollection < TypeArgument\>**. Geben Sie im Eigenschaftenraster einen Visual Basic-Ausdruck ein, um die Auflistung anzugeben.|
|*TypeArgument*|True|Der Typ T der in der <xref:System.Collections.Generic.ICollection%601> enthaltenen Elemente. Standardmäßig dies *TypeArgument* Typ festgelegt ist, um **Int32**. Um den Typ zu ändern, ändern Sie den Wert von der *TypeArgument* im Kombinationsfeld im Eigenschaftenraster.|

## <a name="see-also"></a>Siehe auch

- [Auflistung](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T >-Aktivitätsdesigners](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)
---
title: Workflow-Designer - AddToCollection<T> Aktivitäts-Designer
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.AddToCollection`1.UI
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bc59628de24af3d0e4910f3ff566791a508127fe
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54953538"
---
# <a name="addtocollectiont-activity-designer"></a>AddToCollection\<T >-Aktivitätsdesigner

Die **AddToCollection\<T >** Aktivitäts-Designer dient zum Erstellen und Konfigurieren einer <xref:System.Activities.Statements.AddToCollection%601> Aktivität.

## <a name="the-addtocollectiont-activity"></a>Die AddToCollection\<T >-Aktivität

Die <xref:System.Activities.Statements.AddToCollection%601>-Aktivität fügt einer Auflistung ein Element hinzu.

### <a name="using-the-addtocollectiont-activity-designer"></a>Verwenden des AddToCollection\<T >-Aktivitätsdesigner

Die **AddToCollection\<T >** Aktivitäts-Designer finden Sie in der **Auflistung** Kategorie der **Toolbox**, die erfolgt durch Klicken auf die  **Toolbox** Registerkarte des Workflow-Designers. Wählen Sie alternativ **Toolbox** aus der **Ansicht** Menü, oder drücken Sie **STRG**+**Alt** + **X**.

Die **AddToCollection\<T >** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** und sich der Workflow-Designer-Oberfläche gelöscht werden, wo Aktivitäten platziert werden, z. B. wie in einem <xref:System.Activities.Statements.Sequence>. Löschen der **AddToCollection\<T >** Aktivitäts-Designer erstellt eine <xref:System.Activities.Statements.AddToCollection%601> -Aktivität mit dem standardmäßigen <xref:System.Activities.Activity.DisplayName%2A> von AddToCollection < Int32\>. (Standardmäßig die *TypeArgument* ist **Int32**. TypeArgument kann im Eigenschaftenraster geändert werden.) Die <xref:System.Activities.Activity.DisplayName%2A> Wert kann im Header des bearbeitet werden die **AddToCollection < T\>**  Aktivitäts-Designer oder in der **"DisplayName"** Feld des Eigenschaftenrasters. Die anderen Eigenschaften müssen im Eigenschaftenraster bearbeitet werden.

### <a name="the-addtocollectiont-properties"></a>Die AddToCollection\<T > Eigenschaften

In der folgenden Tabelle werden die <xref:System.Activities.Statements.AddToCollection%601>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der Anzeigename der <xref:System.Activities.Statements.AddToCollection%601>-Aktivität. Der Standardname lautet AddToCollection < Int32\>. Obwohl der <xref:System.Activities.Activity.DisplayName%2A>-Wert nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|True|Das Element der Auflistung hinzuzufügende\<T >. Dieses Element ist vom Typ *T*, vom Typ *TypeArgument*. Geben Sie im Eigenschaftenraster einen Visual Basic-Ausdruck ein, um das Element anzugeben.|
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|True|Die Auflistung, zu der das Element hinzugefügt werden soll. Diese Sammlung wird vom Typ **ICollection < TypeArgument\>**. Geben Sie im Eigenschaftenraster einen Visual Basic-Ausdruck ein, um die Auflistung anzugeben.|
|*TypeArgument*|True|Der Typ T der in der <xref:System.Collections.Generic.ICollection%601> enthaltenen Elemente. In der Standardeinstellung dies *TypeArgument* Typ nastaven NA hodnotu **Int32**. Um den Typ zu ändern, ändern Sie den Wert des der *TypeArgument* im Eigenschaftenraster im Kombinationsfeld.|

## <a name="see-also"></a>Siehe auch

- [Auflistung](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T >-Aktivitätsdesigner](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)
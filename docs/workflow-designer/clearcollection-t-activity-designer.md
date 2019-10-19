---
title: Workflow-Designer ClearCollection-<T> Aktivitäts Designer
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ClearCollection`1.UI
ms.assetid: db0e5da2-7b5a-4f1a-864c-f3aeeeeb51a7
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a4808c046c4da23bc5c95d3978965afd938962f5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650688"
---
# <a name="clearcollectiont-activity-designer"></a>ClearCollection-\<T > Aktivitäts Designer

Der **ClearCollection-\<T >** Aktivitäts Designer wird verwendet, um eine <xref:System.Activities.Statements.ClearCollection%601>-Aktivität zu erstellen und zu konfigurieren.

## <a name="the-clearcollectiont-activity"></a>Der ClearCollection-\<T >-Aktivität

Die <xref:System.Activities.Statements.ClearCollection%601>-Aktivität löscht alle Elemente einer angegebenen Auflistung.

### <a name="using-the-clearcollectiont-activity-designer"></a>Verwenden des ClearCollection-\<T >-Aktivitäts Designers

Der **ClearCollection-\<T >** -Aktivitäts Designer befindet sich in **der Kategorie Auflistung** der **Toolbox**, auf die Sie zugreifen können, indem Sie im Workflow-Designer auf die Registerkarte **Toolbox** klicken. Sie können auch im Menü **Ansicht** die Option **Toolbox** auswählen oder **STRG** +**alt** +**X**drücken.

Der **ClearCollection-\<T >** Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der Workflow-Designer-Oberfläche dort abgelegt werden, wo Aktivitäten platziert werden, z. b. innerhalb einer <xref:System.Activities.Statements.Sequence>. Beim Löschen des Aktivitäts Designers wird eine <xref:System.Activities.Statements.ClearCollection%601>-Aktivität mit einem Standard <xref:System.Activities.Activity.DisplayName%2A> der ClearCollection < Int32-\> erstellt. (Standardmäßig ist das *TypeArgument* **Int32**. TypeArgument kann im Eigenschaften Raster geändert werden.) Der <xref:System.Activities.Activity.DisplayName%2A> Wert kann im Header des **ClearCollection < t \>** -Aktivitäts Designers oder im Feld **Display Name** des Eigenschaften Rasters bearbeitet werden. Die anderen Eigenschaften müssen im Eigenschaftenraster bearbeitet werden.

### <a name="the-clearcollectiont-properties"></a>Die ClearCollection-\<T > Eigenschaften

In der folgenden Tabelle werden die <xref:System.Activities.Statements.ClearCollection%601>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den optionalen Anzeigenamen der <xref:System.Activities.Statements.ClearCollection%601>-Aktivität an. Der Standardwert ist ClearCollection < Int32 \>. Obwohl der <xref:System.Activities.Activity.DisplayName%2A>-Wert nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|True|Gibt die Auflistung an, deren Elemente gelöscht werden sollen. Diese Sammlung ist vom Typ **ICollection \<TypeArgument >.** Geben Sie im Eigenschaftenraster einen Visual Basic-Ausdruck ein, um die Auflistung anzugeben.|
|*TypeArgument*|True|Gibt den Typ T der in <xref:System.Collections.Generic.ICollection%601> enthaltenen Elemente an. Standardmäßig ist dieser *TypeArgument* -Typ auf **Int32**festgelegt. Ändern Sie den Wert von *TypeArgument* im Kombinations Feld des Eigenschaften Rasters, um den Typ zu ändern.|

## <a name="see-also"></a>Siehe auch

- [Auflistung](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)
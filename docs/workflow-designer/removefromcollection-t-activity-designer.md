---
title: Workflow-Designer-RemoveFromCollection &lt;T &gt; Aktivitäts Designer
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.RemoveFromCollection`1.UI
ms.assetid: 6617ba26-c8bc-4aed-b746-112bf490d288
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1a8885505607d654327ad9dc36ab88708ab708c3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649999"
---
# <a name="removefromcollectiont-activity-designer"></a>RemoveFromCollection-\<T >-Aktivitäts Designer

Der **RemoveFromCollection-\<T >** -Aktivitäts Designer wird verwendet, um eine <xref:System.Activities.Statements.RemoveFromCollection%601>-Aktivität zu erstellen und zu konfigurieren.

## <a name="the-removefromcollectiontactivity"></a>RemoveFromCollection-\<T >-Aktivität

Die <xref:System.Activities.Statements.RemoveFromCollection%601>-Aktivität entfernt ein angegebenes Element aus der angegebenen Auflistung.

### <a name="using-the-removefromcollectiont-activity-designer"></a>Verwenden des RemoveFromCollection-\<T >-Aktivitäts Designers

Zugreifen auf den **RemoveFromCollection-\<T >** -Aktivitäts Designer in **der Kategorie Auflistung der** **Toolbox**.
Der **RemoveFromCollection-\<T >** Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der Workflow-Designer-Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden, z. b. innerhalb einer <xref:System.Activities.Statements.Sequence>. Dadurch wird eine <xref:System.Activities.Statements.RemoveFromCollection%601>-Aktivität mit einem Standard <xref:System.Activities.Activity.DisplayName%2A> von RemoveFromCollection < Int32 \> erstellt. Der <xref:System.Activities.Activity.DisplayName%2A> Wert kann im Header des **RemoveFromCollection < t \>** -Aktivitäts Designers oder im Feld **Display Name** des Eigenschaften Rasters bearbeitet werden. Die anderen Eigenschaften müssen im Eigenschaftenraster bearbeitet werden.

### <a name="the-removefromcollectiont-properties"></a>Die RemoveFromCollection-< T-\> Eigenschaften

In der folgenden Tabelle sind die <xref:System.Activities.Statements.RemoveFromCollection%601> Eigenschaften aufgeführt, und es wird beschrieben, wie Sie im Designer verwendet werden:

|Eigenschaftenname|Erforderlich|Verwendung|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der optionale Anzeigename der <xref:System.Activities.Statements.RemoveFromCollection%601>-Aktivität. Der Standardwert ist der RemoveFromCollection-< Int32 \>.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Item%2A>|True|Das Element, das aus der Auflistung entfernt werden soll, **\<T >** . Dieses Element ist vom Typ *T*, der vom Typ *TypeArgument*ist. Geben Sie im Eigenschaftenraster einen Visual Basic-Ausdruck ein, um das Element anzugeben.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Collection%2A>|True|Die Auflistung, aus der das Element entfernt werden soll. Diese Auflistung ist vom Typ **ICollection-< TypeArgument \>.** Geben Sie im Eigenschaften Raster einen Visual Basic Ausdruck ein, um die Sammlung anzugeben.|
|*TypeArgument*|True|Der Typ T der in der <xref:System.Collections.Generic.ICollection%601> enthaltenen Elemente. Standardmäßig ist dieser *TypeArgument* -Typ auf **Int32**festgelegt. Ändern Sie den Wert von *TypeArgument* im Kombinations Feld des Eigenschaften Rasters, um den Typ zu ändern.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Ein Wert, der angibt, ob das angegebene Element aus der Auflistung entfernt wurde. Um eine Variable anzugeben, die an das Ergebnis gebunden werden soll, geben Sie im Eigenschaftenraster eine Variable ein.|

## <a name="see-also"></a>Siehe auch

- [Auflistung](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)
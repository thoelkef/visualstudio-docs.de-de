---
title: Workflow-Designer - RemoveFromCollection&lt;T&gt; Aktivitäts-Designer
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.RemoveFromCollection`1.UI
ms.assetid: 6617ba26-c8bc-4aed-b746-112bf490d288
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b3a43c05f8be4806cf10098a4df673903494756
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62933734"
---
# <a name="removefromcollectiont-activity-designer"></a>RemoveFromCollection\<T >-Aktivitätsdesigner

Die **RemoveFromCollection\<T >** Aktivitäts-Designer dient zum Erstellen und Konfigurieren einer <xref:System.Activities.Statements.RemoveFromCollection%601> Aktivität.

## <a name="the-removefromcollectiontactivity"></a>Die RemoveFromCollection\<T >-Aktivität

Die <xref:System.Activities.Statements.RemoveFromCollection%601>-Aktivität entfernt ein angegebenes Element aus der angegebenen Auflistung.

### <a name="using-the-removefromcollectiont-activity-designer"></a>Verwenden des RemoveFromCollection\<T >-Aktivitätsdesigner

Zugriff die **RemoveFromCollection\<T >** Aktivitäts-Designer in der **Auflistung** Kategorie der **Toolbox**.
Die **RemoveFromCollection\<T >** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** und sich der Workflow-Designer-Oberfläche gelöscht werden, wo Aktivitäten normalerweise, z. B. platziert werden innerhalb einer <xref:System.Activities.Statements.Sequence>. Dies erstellt eine <xref:System.Activities.Statements.RemoveFromCollection%601> -Aktivität mit dem standardmäßigen <xref:System.Activities.Activity.DisplayName%2A> -Standardnamen RemoveFromCollection < Int32\>. Die <xref:System.Activities.Activity.DisplayName%2A> Wert kann im Header des bearbeitet werden die **RemoveFromCollection < T\>**  Aktivitäts-Designer oder in der **"DisplayName"** Feld des Eigenschaftenrasters. Die anderen Eigenschaften müssen im Eigenschaftenraster bearbeitet werden.

### <a name="the-removefromcollectiont-properties"></a>Die RemoveFromCollection < T\> Eigenschaften

Die folgende Tabelle zeigt die <xref:System.Activities.Statements.RemoveFromCollection%601> Eigenschaften und beschreibt, wie sie im Designer verwendet werden:

|Eigenschaftenname|Erforderlich|Verwendung|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der optionale Anzeigename der <xref:System.Activities.Statements.RemoveFromCollection%601>-Aktivität. Der Standardname lautet RemoveFromCollection < Int32\>.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Item%2A>|True|Das Element, das Entfernen aus der **Auflistung\<T >**. Dieses Element ist vom Typ *T*, vom Typ *TypeArgument*. Geben Sie im Eigenschaftenraster einen Visual Basic-Ausdruck ein, um das Element anzugeben.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Collection%2A>|True|Die Auflistung, aus der das Element entfernt werden soll. Diese Sammlung wird vom Typ **ICollection < TypeArgument\>.** Um die Sammlung anzugeben, geben Sie im Eigenschaftenraster einen Visual Basic-Ausdruck.|
|*TypeArgument*|True|Der Typ T der in der <xref:System.Collections.Generic.ICollection%601> enthaltenen Elemente. In der Standardeinstellung dies *TypeArgument* Typ nastaven NA hodnotu **Int32**. Um den Typ zu ändern, ändern Sie den Wert des der *TypeArgument* im Eigenschaftenraster im Kombinationsfeld.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Ein Wert, der angibt, ob das angegebene Element aus der Auflistung entfernt wurde. Um eine Variable anzugeben, die an das Ergebnis gebunden werden soll, geben Sie im Eigenschaftenraster eine Variable ein.|

## <a name="see-also"></a>Siehe auch

- [Auflistung](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)
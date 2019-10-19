---
title: ExistsInCollection-&lt;T &gt; Aktivitäts Designer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ExistsInCollection`1.UI
ms.assetid: 0acf9a13-caf5-4bb4-ba22-ec37d2b7267a
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 08aabbcb7dbef2df9a3affa8589a9c6d4205ac58
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656738"
---
# <a name="existsincollectionlttgt-activity-designer"></a>ExistsInCollection-&lt;T &gt; Aktivitäts Designer
Der **ExistsInCollection-\<T >** Aktivitäts Designer wird verwendet, um eine <xref:System.Activities.Statements.ExistsInCollection%601>-Aktivität zu erstellen und zu konfigurieren.

## <a name="the-existsincollectiont-activity"></a>Die ExistsInCollection-\<T >-Aktivität
 Mit der <xref:System.Activities.Statements.ExistsInCollection%601>-Aktivität wird bestimmt, ob ein angegebenes Element in einer bestimmten Auflistung vorhanden ist.

### <a name="using-the-existsincollectiont-activity-designer"></a>Verwenden des ExistsInCollection-\<T >-Aktivitäts Designers
 Der **ExistsInCollection-\<T >** -Aktivitäts Designer befindet sich in **der Kategorie Auflistung** der **Toolbox**, auf die Sie zugreifen können, indem Sie auf die Registerkarte **Toolbox** von [!INCLUDE[wfd2](../includes/wfd2-md.md)] klicken (Sie können auch **Symbolleiste** auf der Registerkarte Menü " **Ansicht** " oder STRG + ALT + X.)

 Der **ExistsInCollection-\<T >** Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der [!INCLUDE[wfd2](../includes/wfd2-md.md)]-Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden, z. b. innerhalb einer <xref:System.Activities.Statements.Sequence>. Dadurch wird eine <xref:System.Activities.Statements.ExistsInCollection%601>-Aktivität mit einem Standard <xref:System.Activities.Activity.DisplayName%2A> der ExistsInCollection-\<Int32 > erstellt. (Standardmäßig ist das *TypeArgument* **Int32**. Der Wert kann im Eigenschaften Raster geändert werden.)  Der <xref:System.Activities.Activity.DisplayName%2A> Wert kann im Header des **ExistsInCollection-\<T >** -Aktivitäts Designers oder im Feld **Display Name** des Eigenschaften Rasters bearbeitet werden. Die anderen Eigenschaften müssen im Eigenschaftenraster bearbeitet werden.

### <a name="the-existsincollectiont-properties"></a>Die Eigenschaften des ExistsInCollection-\<T >
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.ExistsInCollection%601>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der Anzeigename der <xref:System.Activities.Statements.ExistsInCollection%601>-Aktivität. Der Standardwert ist ExistsInCollection \<Int32 >. Obwohl der <xref:System.Activities.Activity.DisplayName%2A>-Wert nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Item%2A>|True|Das Element, das der Auflistung hinzugefügt werden soll, \<T >. Dieses Element ist vom Typ " *T* " vom Typ " *TypeArgument*". Zum Angeben des Elements geben Sie im Eigenschaftenraster einen Visual Basic-Ausdruck ein.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Collection%2A>|True|Die Auflistung, zu der das Element hinzugefügt werden soll. Diese Sammlung ist vom Typ **ICollection \<TypeArgument >.** Geben Sie im Eigenschaftenraster einen Visual Basic-Ausdruck ein, um die Auflistung anzugeben.|
|*TypeArgument*|True|Der Typ T der in der <xref:System.Collections.Generic.ICollection%601> enthaltenen Elemente. Standardmäßig ist dieser *TypeArgument* -Typ auf **Int32**festgelegt. Ändern Sie den Wert von *TypeArgument* im Kombinations Feld des Eigenschaften Rasters, um den Typ zu ändern.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Ein Wert, der angibt, ob das angegebene Element in der Auflistung vorhanden ist. Um eine Variable anzugeben, die an das Ergebnis gebunden wird, geben Sie im Eigenschaftenraster eine Visual Basic-Variable ein.|

## <a name="see-also"></a>Siehe auch
 [Sammlung](../workflow-designer/collection-activity-designers.md) [addaufcollection-\<T >](../workflow-designer/addtocollection-t-activity-designer.md) [ClearCollection-\<T >](../workflow-designer/clearcollection-t-activity-designer.md) [RemoveFromCollection \<T >](../workflow-designer/removefromcollection-t-activity-designer.md)
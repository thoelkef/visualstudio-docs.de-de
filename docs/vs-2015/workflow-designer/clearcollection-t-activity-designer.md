---
title: ClearCollection &lt; T- &gt; Aktivitäts Designer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ClearCollection`1.UI
ms.assetid: db0e5da2-7b5a-4f1a-864c-f3aeeeeb51a7
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8c2f1e0264d39c65601a70e8c24b51c7eceadf4a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657024"
---
# <a name="clearcollectionlttgt-activity-designer"></a>ClearCollection &lt; T- &gt; Aktivitäts Designer
Der **ClearCollection \<T> ** -Aktivitäts Designer wird verwendet, um eine-Aktivität zu erstellen und zu konfigurieren <xref:System.Activities.Statements.ClearCollection%601> .

## <a name="the-clearcollectiont-activity"></a>Die ClearCollection- \<T> Aktivität
 Die <xref:System.Activities.Statements.ClearCollection%601>-Aktivität löscht alle Elemente einer angegebenen Auflistung.

### <a name="using-the-clearcollectiont-activity-designer"></a>Verwenden des ClearCollection- \<T> Aktivitäts Designers
 Der **ClearCollection \<T> ** -Aktivitäts Designer befindet sich in der **Kategorie Auflistung** der **Toolbox**, auf die Sie zugreifen können, indem Sie in auf die Registerkarte **Toolbox** klicken (Sie können auch im [!INCLUDE[wfd2](../includes/wfd2-md.md)] Menü **Ansicht** den Befehl **Symbolleiste** auswählen oder STRG + ALT + X drücken).

 Der **ClearCollection \<T> ** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der- [!INCLUDE[wfd2](../includes/wfd2-md.md)] Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden, z. b. innerhalb eines <xref:System.Activities.Statements.Sequence> . Dadurch wird eine- <xref:System.Activities.Statements.ClearCollection%601> Aktivität mit dem-Standardwert <xref:System.Activities.Activity.DisplayName%2A> ClearCollection erstellt \<Int32> . (Standardmäßig ist das *TypeArgument* **Int32**. Dies kann im Eigenschaften Raster geändert werden.) Der <xref:System.Activities.Activity.DisplayName%2A> Wert kann im Header des ** \<T> ClearCollection** -Aktivitäts Designers oder im Feld **Display Name** des Eigenschaften Rasters bearbeitet werden. Die anderen Eigenschaften müssen im Eigenschaftenraster bearbeitet werden.

### <a name="the-clearcollectiont-properties"></a>ClearCollection- \<T> Eigenschaften
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.ClearCollection%601>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den optionalen Anzeigenamen der <xref:System.Activities.Statements.ClearCollection%601>-Aktivität an. Der Standardwert ist ClearCollection \<Int32> . Obwohl der <xref:System.Activities.Activity.DisplayName%2A>-Wert nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|True|Gibt die Auflistung an, deren Elemente gelöscht werden sollen. Diese Auflistung ist vom Typ **ICollection \<TypeArgument> .** Geben Sie im Eigenschaftenraster einen Visual Basic-Ausdruck ein, um die Auflistung anzugeben.|
|*TypeArgument*|True|Gibt den Typ T der in <xref:System.Collections.Generic.ICollection%601> enthaltenen Elemente an. Standardmäßig ist dieser *TypeArgument* -Typ auf **Int32**festgelegt. Ändern Sie den Wert von *TypeArgument* im Kombinations Feld des Eigenschaften Rasters, um den Typ zu ändern.|

## <a name="see-also"></a>Weitere Informationen
 [Sammlung](../workflow-designer/collection-activity-designers.md) " [AddTo \<T> Collection](../workflow-designer/addtocollection-t-activity-designer.md) [ExistsInCollection \<T> ](../workflow-designer/existsincollection-t-activity-designer.md) " [RemoveFromCollection \<T> ](../workflow-designer/removefromcollection-t-activity-designer.md)
---
title: Addchancollection &lt; T- &gt; Aktivitäts Designer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.AddToCollection`1.UI
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 50deab447b3dcb93d352e73fc4765d913b4d24bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659208"
---
# <a name="addtocollectionlttgt-activity-designer"></a>Addchancollection &lt; T- &gt; Aktivitäts Designer
Der **AddTo Collection \<T> ** -Aktivitäts Designer wird verwendet, um eine-Aktivität zu erstellen und zu konfigurieren <xref:System.Activities.Statements.AddToCollection%601> .

## <a name="the-addtocollectiont-activity"></a>Die AddTo Collection- \<T> Aktivität
 Die <xref:System.Activities.Statements.AddToCollection%601>-Aktivität fügt einer Auflistung ein Element hinzu.

### <a name="using-the-addtocollectiont-activity-designer"></a>Verwenden des AddTo Collection- \<T> Aktivitäts Designers
 Der **adddecollection \<T> ** -Aktivitäts Designer befindet sich in der **Kategorie Auflistung** der **Toolbox**, auf die Sie zugreifen können, indem Sie in auf die Registerkarte **Toolbox** klicken (Sie können auch im [!INCLUDE[wfd2](../includes/wfd2-md.md)] Menü **Ansicht** den Befehl **Symbolleiste** auswählen oder STRG + ALT + X drücken).

 Der **addescollection \<T> ** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der- [!INCLUDE[wfd2](../includes/wfd2-md.md)] Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden, z. b. innerhalb eines <xref:System.Activities.Statements.Sequence> . Dadurch wird eine- <xref:System.Activities.Statements.AddToCollection%601> Aktivität mit dem-Standardwert <xref:System.Activities.Activity.DisplayName%2A> addtcollection erstellt \<Int32> . (Standardmäßig ist das *TypeArgument* **Int32**. Dies kann im Eigenschaften Raster geändert werden.) Der <xref:System.Activities.Activity.DisplayName%2A> Wert kann im Header des **AddTo Collection \<T> ** -Aktivitäts Designers oder im Feld **Display Name** des Eigenschaften Rasters bearbeitet werden. Die anderen Eigenschaften müssen im Eigenschaftenraster bearbeitet werden.

### <a name="the-addtocollectiont-properties"></a>Die AddTo Collection- \<T> Eigenschaften
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.AddToCollection%601>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der Anzeigename der <xref:System.Activities.Statements.AddToCollection%601>-Aktivität. Der Standardwert ist AddTo Collection \<Int32> . Obwohl der <xref:System.Activities.Activity.DisplayName%2A>-Wert nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|True|Das Element, das der Auflistung hinzugefügt werden soll \<T> . Dieses Element ist vom Typ *T*, der vom Typ *TypeArgument*ist. Geben Sie im Eigenschaftenraster einen Visual Basic-Ausdruck ein, um das Element anzugeben.|
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|True|Die Auflistung, zu der das Element hinzugefügt werden soll. Diese Auflistung ist vom Typ **ICollection \<TypeArgument> **. Geben Sie im Eigenschaftenraster einen Visual Basic-Ausdruck ein, um die Auflistung anzugeben.|
|*TypeArgument*|True|Der Typ T der in der <xref:System.Collections.Generic.ICollection%601> enthaltenen Elemente. Standardmäßig ist dieser *TypeArgument* -Typ auf **Int32**festgelegt. Ändern Sie den Wert von *TypeArgument* im Kombinations Feld des Eigenschaften Rasters, um den Typ zu ändern.|

## <a name="see-also"></a>Weitere Informationen
 [Collection](../workflow-designer/collection-activity-designers.md) [AddTo Collection- \<T> Aktivitäts Designer](../workflow-designer/addtocollection-t-activity-designer.md) [ClearCollection \<T> ](../workflow-designer/clearcollection-t-activity-designer.md) [ExistsInCollection \<T> ](../workflow-designer/existsincollection-t-activity-designer.md) [RemoveFromCollection \<T> ](../workflow-designer/removefromcollection-t-activity-designer.md)
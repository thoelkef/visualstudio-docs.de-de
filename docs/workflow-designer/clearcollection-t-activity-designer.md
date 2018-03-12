---
title: "ClearCollection&lt;T&gt; Aktivitäts-Designer | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ClearCollection`1.UI
ms.assetid: db0e5da2-7b5a-4f1a-864c-f3aeeeeb51a7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 6f4a89d062fe8adeb06c05ba25929bce6d466511
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2018
---
# <a name="clearcollectionlttgt-activity-designer"></a>ClearCollection&lt;T&gt; Aktivitäts-Designer
Die **ClearCollection\<T >** Aktivitäts-Designer dient zum Erstellen und Konfigurieren einer <xref:System.Activities.Statements.ClearCollection%601> Aktivität.

## <a name="the-clearcollectiont-activity"></a>Die ClearCollection < T\> Aktivität
 Die <xref:System.Activities.Statements.ClearCollection%601>-Aktivität löscht alle Elemente einer angegebenen Auflistung.

### <a name="using-the-clearcollectiont-activity-designer"></a>Verwenden die ClearCollection\<T >-Aktivitätsdesigners
 Die **ClearCollection\<T >** Aktivitäts-Designer finden Sie in der **Auflistung** Kategorie von der **Toolbox**, indem Sie auf die zugegriffenwird **Toolbox** auf der Registerkarte die [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (Wählen Sie alternativ **Symbolleiste** aus der **Ansicht** Menüs oder STRG + ALT + X.)

 Die **ClearCollection\<T >** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** gezogen und auf die [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] -Oberfläche ablegen, wo Aktivitäten normalerweise platziert werden, z. B. in einem <xref:System.Activities.Statements.Sequence>. Dies erstellt eine <xref:System.Activities.Statements.ClearCollection%601> -Aktivität mit dem standardmäßigen <xref:System.Activities.Activity.DisplayName%2A> von ClearCollection < Int32\>. (Standardmäßig der *TypeArgument* ist **Int32**. Dies kann im Eigenschaftenraster geändert werden.) Die <xref:System.Activities.Activity.DisplayName%2A> Wert kann im Header des bearbeitet werden die **ClearCollection < T\>**  Aktivitäts-Designer oder in der **DisplayName** Feld des Eigenschaftenrasters. Die anderen Eigenschaften müssen im Eigenschaftenraster bearbeitet werden.

### <a name="the-clearcollectiont-properties"></a>Die ClearCollection < T\> Eigenschaften
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.ClearCollection%601>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den optionalen Anzeigenamen der <xref:System.Activities.Statements.ClearCollection%601>-Aktivität an. Der Standardname lautet ClearCollection < Int32\>. Obwohl der <xref:System.Activities.Activity.DisplayName%2A>-Wert nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|True|Gibt die Auflistung an, deren Elemente gelöscht werden sollen. Diese Sammlung ist vom Typ **ICollection\<TypeArgument >.** Geben Sie im Eigenschaftenraster einen Visual Basic-Ausdruck ein, um die Auflistung anzugeben.|
|*TypeArgument*|True|Gibt den Typ T der in <xref:System.Collections.Generic.ICollection%601> enthaltenen Elemente an. Standardmäßig dies *TypeArgument* Typ festgelegt ist, um **Int32**. Um den Typ zu ändern, ändern Sie den Wert von der *TypeArgument* im Kombinationsfeld im Eigenschaftenraster.|

## <a name="see-also"></a>Siehe auch

- [Auflistung](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)
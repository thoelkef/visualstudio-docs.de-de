---
title: AddToCollection&lt;T&gt; Aktivitäts-Designer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.AddToCollection`1.UI
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4e63486ca7e057fdd1bfe0de73e44dc4951462e2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977220"
---
# <a name="addtocollectionlttgt-activity-designer"></a>AddToCollection&lt;T&gt; Aktivitäts-Designer
Die **AddToCollection\<T >** Aktivitäts-Designer dient zum Erstellen und Konfigurieren einer <xref:System.Activities.Statements.AddToCollection%601> Aktivität.  
  
## <a name="the-addtocollectiont-activity"></a>Die AddToCollection\<T >-Aktivität  
 Die <xref:System.Activities.Statements.AddToCollection%601>-Aktivität fügt einer Auflistung ein Element hinzu.  
  
### <a name="using-the-addtocollectiont-activity-designer"></a>Verwenden des AddToCollection\<T >-Aktivitätsdesigner  
 Die **AddToCollection\<T >** Aktivitäts-Designer finden Sie in der **Auflistung** Kategorie der **Toolbox**, die erfolgt durch Klicken auf die  **Toolbox** Registerkarte die [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Wählen Sie alternativ **Symbolleiste** aus der **Ansicht** Menü- oder STRG + ALT + X.)  
  
 Die **AddToCollection\<T >** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** und auf die [!INCLUDE[wfd2](../includes/wfd2-md.md)] -Oberfläche ganz egal, wo Aktivitäten normalerweise platziert werden, etwa innerhalb einer <xref:System.Activities.Statements.Sequence>. Dies erstellt eine <xref:System.Activities.Statements.AddToCollection%601> -Aktivität mit dem standardmäßigen <xref:System.Activities.Activity.DisplayName%2A> von AddToCollection\<Int32 >. (Standardmäßig die *TypeArgument* ist **Int32**. Dies kann im Eigenschaftenraster geändert werden.) Die <xref:System.Activities.Activity.DisplayName%2A> Wert kann im Header des bearbeitet werden die **AddToCollection\<T >** Aktivitäts-Designer oder in der **"DisplayName"** Feld des Eigenschaftenrasters. Die anderen Eigenschaften müssen im Eigenschaftenraster bearbeitet werden.  
  
### <a name="the-addtocollectiont-properties"></a>Die AddToCollection\<T > Eigenschaften  
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.AddToCollection%601>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der Anzeigename der <xref:System.Activities.Statements.AddToCollection%601>-Aktivität. Der Standardname lautet AddToCollection\<Int32 >. Obwohl der <xref:System.Activities.Activity.DisplayName%2A>-Wert nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|  
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|True|Das Element der Auflistung hinzuzufügende\<T >. Dieses Element ist vom Typ *T*, vom Typ *TypeArgument*. Geben Sie im Eigenschaftenraster einen Visual Basic-Ausdruck ein, um das Element anzugeben.|  
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|True|Die Auflistung, zu der das Element hinzugefügt werden soll. Diese Sammlung wird vom Typ **ICollection\<TypeArgument >**. Geben Sie im Eigenschaftenraster einen Visual Basic-Ausdruck ein, um die Auflistung anzugeben.|  
|*TypeArgument*|True|Der Typ T der in der <xref:System.Collections.Generic.ICollection%601> enthaltenen Elemente. In der Standardeinstellung dies *TypeArgument* Typ nastaven NA hodnotu **Int32**. Um den Typ zu ändern, ändern Sie den Wert des der *TypeArgument* im Eigenschaftenraster im Kombinationsfeld.|  
  
## <a name="see-also"></a>Siehe auch  
 [Auflistung](../workflow-designer/collection-activity-designers.md)   
 [AddToCollection\<T >-Aktivitätsdesigner](../workflow-designer/addtocollection-t-activity-designer.md)   
 [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)   
 [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)   
 [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)
---
title: ClearCollection&lt;T&gt; Aktivitäts-Designer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ClearCollection`1.UI
ms.assetid: db0e5da2-7b5a-4f1a-864c-f3aeeeeb51a7
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 240e634115e7602c66d69f0dba9cfa52504dc89a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977164"
---
# <a name="clearcollectionlttgt-activity-designer"></a>ClearCollection&lt;T&gt; Aktivitäts-Designer
Die **ClearCollection\<T >** Aktivitäts-Designer dient zum Erstellen und Konfigurieren einer <xref:System.Activities.Statements.ClearCollection%601> Aktivität.  
  
## <a name="the-clearcollectiont-activity"></a>Die ClearCollection\<T >-Aktivität  
 Die <xref:System.Activities.Statements.ClearCollection%601>-Aktivität löscht alle Elemente einer angegebenen Auflistung.  
  
### <a name="using-the-clearcollectiont-activity-designer"></a>Verwenden des ClearCollection\<T >-Aktivitätsdesigner  
 Die **ClearCollection\<T >** Aktivitäts-Designer finden Sie in der **Auflistung** Kategorie der **Toolbox**, die erfolgt durch Klicken auf die  **Toolbox** Registerkarte die [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Wählen Sie alternativ **Symbolleiste** aus der **Ansicht** Menü- oder STRG + ALT + X.)  
  
 Die **ClearCollection\<T >** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** und auf die [!INCLUDE[wfd2](../includes/wfd2-md.md)] -Oberfläche ganz egal, wo Aktivitäten normalerweise platziert werden, etwa innerhalb einer <xref:System.Activities.Statements.Sequence>. Dies erstellt eine <xref:System.Activities.Statements.ClearCollection%601> -Aktivität mit dem standardmäßigen <xref:System.Activities.Activity.DisplayName%2A> von ClearCollection\<Int32 >. (Standardmäßig die *TypeArgument* ist **Int32**. Dies kann im Eigenschaftenraster geändert werden.) Die <xref:System.Activities.Activity.DisplayName%2A> Wert kann im Header des bearbeitet werden die **ClearCollection\<T >** Aktivitäts-Designer oder in der **"DisplayName"** Feld des Eigenschaftenrasters. Die anderen Eigenschaften müssen im Eigenschaftenraster bearbeitet werden.  
  
### <a name="the-clearcollectiont-properties"></a>Die ClearCollection\<T > Eigenschaften  
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.ClearCollection%601>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den optionalen Anzeigenamen der <xref:System.Activities.Statements.ClearCollection%601>-Aktivität an. Der Standardname lautet ClearCollection\<Int32 >. Obwohl der <xref:System.Activities.Activity.DisplayName%2A>-Wert nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|  
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|True|Gibt die Auflistung an, deren Elemente gelöscht werden sollen. Diese Sammlung wird vom Typ **ICollection\<TypeArgument >.** Geben Sie im Eigenschaftenraster einen Visual Basic-Ausdruck ein, um die Auflistung anzugeben.|  
|*TypeArgument*|True|Gibt den Typ T der in <xref:System.Collections.Generic.ICollection%601> enthaltenen Elemente an. In der Standardeinstellung dies *TypeArgument* Typ nastaven NA hodnotu **Int32**. Um den Typ zu ändern, ändern Sie den Wert des der *TypeArgument* im Eigenschaftenraster im Kombinationsfeld.|  
  
## <a name="see-also"></a>Siehe auch  
 [Auflistung](../workflow-designer/collection-activity-designers.md)   
 [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)   
 [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)   
 [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)
---
title: "Throw-Aktivitätsdesigner | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.Throw.UI
ms.assetid: 5e97c947-be39-4a1f-af04-000e2e09528a
caps.latest.revision: "4"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: a4dcc10419d5c1dbc0552aba62057cba2e82647f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="throw-activity-designer"></a>Throw-Aktivitätsdesigner
Die **auslösen** Aktivitäts-Designer dient zum Erstellen und Konfigurieren einer <xref:System.Activities.Statements.Throw> Aktivität.  
  
## <a name="the-throw-activity"></a>Die Throw-Aktivität  
 Die <xref:System.Activities.Statements.Throw>-Aktivität löst eine Ausnahme aus.  
  
### <a name="using-the-throw-activity-designer"></a>Verwenden des Throw-Aktivitätsdesigners  
 Die **auslösen** Aktivitäts-Designer finden Sie in der **Fehlerbehandlung** Kategorie der **Toolbox**, die erfolgt durch Klicken auf die **Toolbox**auf der linken Seite der Registerkarte die [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (Wählen Sie alternativ **Symbolleiste** aus der **Ansicht** Menüs oder STRG + ALT + X drücken.)  
  
 Die **auslösen** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** gezogen und auf die [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] -Oberfläche ablegen, wo Aktivitäten normalerweise platziert werden, z. B. in einem <xref:System.Activities.Statements.Sequence>. Dies erstellt eine <xref:System.Activities.Statements.Throw> -Aktivität mit dem standardmäßigen **DisplayName** -Standardwert Rethrow. Die <xref:System.Activities.Activity.DisplayName%2A> Wert kann im Header des bearbeitet werden die **auslösen** Aktivitäts-Designer oder in der **DisplayName** Feld des Eigenschaftenrasters. Diese <xref:System.Activities.Statements.Throw.Exception%2A>-Eigenschaft muss im Eigenschaftenraster bearbeitet werden.  
  
### <a name="the-throw-properties"></a>Die Throw-Eigenschaften  
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.Throw>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den optionalen Anzeigenamen der <xref:System.Activities.Statements.Throw>-Aktivität an. Der Standardwert lautet Throw.|  
|<xref:System.Activities.Statements.Throw.Exception%2A>|True|Die auszulösende Ausnahme. Diese Ausnahme muss sich von <xref:System.Exception> ableiten. Geben Sie im Eigenschaftenraster einen Visual Basic-Ausdruck ein, um die Ausnahme anzugeben.|  
  
## <a name="see-also"></a>Siehe auch  
 [Auflistung](../workflow-designer/collection-activity-designers.md)   
 [Rethrow](../workflow-designer/rethrow-activity-designer.md)   
 [Throw-Aktivitätsdesigner](../workflow-designer/throw-activity-designer.md)   
 [TryCatch](../workflow-designer/trycatch-activity-designer.md)
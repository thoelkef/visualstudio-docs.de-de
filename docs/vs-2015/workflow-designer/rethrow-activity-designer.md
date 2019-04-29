---
title: Rethrow-Aktivitätsdesigner | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Rethrow.UI
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8b023a42da1c862927606c4bec0215120a5e5a11
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62937756"
---
# <a name="rethrow-activity-designer"></a>Rethrow-Aktivitätsdesigner
Die **Rethrow** Aktivitäts-Designer dient zum Erstellen und Konfigurieren einer <xref:System.Activities.Statements.Rethrow> Aktivität.  
  
## <a name="the-rethrow-activity"></a>Die Rethrow-Aktivität  
 Die <xref:System.Activities.Statements.Rethrow>-Aktivität löst eine zuvor ausgelöste Ausnahme aus. Diese Aktivität kann nur in einem <xref:System.Activities.Statements.Catch>-Handler in der <xref:System.Activities.Statements.TryCatch> -Aktivität verwendet werden.  
  
### <a name="using-the-rethrow-activity-designer"></a>Verwenden des Rethrow-Aktivitätsdesigners  
 Die **erneut auslösen** Aktivitäts-Designer finden Sie in der **Fehlerbehandlung** Kategorie der **Toolbox**, die erfolgt durch Klicken auf die **Toolbox**auf der linken Seite der Registerkarte die [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Wählen Sie alternativ **Symbolleiste** aus der **Ansicht** Menü- oder STRG + ALT + X.)  
  
 Die **erneut auslösen** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** und auf die [!INCLUDE[wfd2](../includes/wfd2-md.md)] -Oberfläche ganz egal, wo Aktivitäten normalerweise platziert werden, etwa innerhalb einer <xref:System.Activities.Statements.Sequence>. Erstellt eine <xref:System.Activities.Statements.Rethrow> -Aktivität mit dem standardmäßigen **"DisplayName"** -Standardwert Rethrow. Die <xref:System.Activities.Activity.DisplayName%2A> Wert kann im Header des bearbeitet werden die **Rethrow** Aktivitäts-Designer oder in der **"DisplayName"** Feld des Eigenschaftenrasters.  
  
### <a name="the-rethrow-properties"></a>Die Rethrow-Eigenschaften  
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.Rethrow>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den optionalen Anzeigenamen der <xref:System.Activities.Statements.Rethrow>-Aktivität an. Der Standardwert lautet Rethrow.|  
  
## <a name="see-also"></a>Siehe auch  
 [Auflistung](../workflow-designer/collection-activity-designers.md)   
 [Throw](../workflow-designer/throw-activity-designer.md)   
 [TryCatch](../workflow-designer/trycatch-activity-designer.md)
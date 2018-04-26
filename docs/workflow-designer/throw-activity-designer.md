---
title: Workflow-Designer - Throw-Aktivitätsdesigner
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Throw.UI
ms.assetid: 5e97c947-be39-4a1f-af04-000e2e09528a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 02bb94ad17b78b1264129b8a5ba00a964edbd2f2
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="throw-activity-designer"></a>Throw-Aktivitätsdesigner

Die **auslösen** Aktivitäts-Designer dient zum Erstellen und Konfigurieren einer <xref:System.Activities.Statements.Throw> Aktivität.

## <a name="the-throw-activity"></a>Die Throw-Aktivität
 Die <xref:System.Activities.Statements.Throw>-Aktivität löst eine Ausnahme aus.

### <a name="using-the-throw-activity-designer"></a>Verwenden des Throw-Aktivitätsdesigners
 Die **auslösen** Aktivitäts-Designer finden Sie in der **Fehlerbehandlung** Kategorie der **Toolbox**, die erfolgt durch Klicken auf die **Toolbox**Registerkarte auf der linken Seite im Workflow-Designer (Wählen Sie alternativ **Symbolleiste** aus der **Ansicht** Menüs oder STRG + ALT + X drücken.)

 Die **auslösen** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** und sich der Workflow-Designer-Oberfläche gelöscht wird, wo Aktivitäten normalerweise platziert werden, z. B. in einem <xref:System.Activities.Statements.Sequence>. Dies erstellt eine <xref:System.Activities.Statements.Throw> -Aktivität mit dem standardmäßigen **DisplayName** -Standardwert Rethrow. Die <xref:System.Activities.Activity.DisplayName%2A> Wert kann im Header des bearbeitet werden die **auslösen** Aktivitäts-Designer oder in der **DisplayName** Feld des Eigenschaftenrasters. Diese <xref:System.Activities.Statements.Throw.Exception%2A>-Eigenschaft muss im Eigenschaftenraster bearbeitet werden.

### <a name="the-throw-properties"></a>Die Throw-Eigenschaften
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.Throw>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den optionalen Anzeigenamen der <xref:System.Activities.Statements.Throw>-Aktivität an. Der Standardwert lautet Throw.|
|<xref:System.Activities.Statements.Throw.Exception%2A>|True|Die auszulösende Ausnahme. Diese Ausnahme muss sich von <xref:System.Exception> ableiten. Geben Sie im Eigenschaftenraster einen Visual Basic-Ausdruck ein, um die Ausnahme anzugeben.|

## <a name="see-also"></a>Siehe auch

- [Auflistung](../workflow-designer/collection-activity-designers.md)
- [Rethrow](../workflow-designer/rethrow-activity-designer.md)
- [Throw-Aktivitätsdesigner](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)
---
title: Workflow-Designer - Throw-Aktivitätsdesigners
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
ms.openlocfilehash: 71cf547a1ea3599de8926e40ca5a43f3bdea0f71
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2018
ms.locfileid: "36758320"
---
# <a name="throw-activity-designer"></a>Throw-Aktivitätsdesigner

Die **auslösen** Aktivitäts-Designer dient zum Erstellen und Konfigurieren einer <xref:System.Activities.Statements.Throw> Aktivität.

## <a name="the-throw-activity"></a>Die Throw-Aktivität

Die <xref:System.Activities.Statements.Throw>-Aktivität löst eine Ausnahme aus.

### <a name="using-the-throw-activity-designer"></a>Verwenden des Throw-Aktivitätsdesigners

Zugriff die **auslösen** Aktivitäts-Designer in der **Fehlerbehandlung** Kategorie der **Toolbox**.

Die **auslösen** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** und sich der Workflow-Designer-Oberfläche gelöscht werden, wo Aktivitäten normalerweise platziert werden, z. B. in einem <xref:System.Activities.Statements.Sequence>. Erstellt eine <xref:System.Activities.Statements.Throw> -Aktivität mit dem standardmäßigen **"DisplayName"** -Standardwert Rethrow. Die <xref:System.Activities.Activity.DisplayName%2A> Wert kann im Header des bearbeitet werden die **auslösen** Aktivitäts-Designer oder in der **"DisplayName"** Feld des Eigenschaftenrasters. Diese <xref:System.Activities.Statements.Throw.Exception%2A>-Eigenschaft muss im Eigenschaftenraster bearbeitet werden.

### <a name="the-throw-properties"></a>Die Throw-Eigenschaften

In der folgenden Tabelle werden die <xref:System.Activities.Statements.Throw>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den optionalen Anzeigenamen der <xref:System.Activities.Statements.Throw>-Aktivität an. Der Standardwert lautet Throw.|
|<xref:System.Activities.Statements.Throw.Exception%2A>|True|Die auszulösende Ausnahme. Diese Ausnahme muss sich von <xref:System.Exception> ableiten. Geben Sie im Eigenschaftenraster einen Visual Basic-Ausdruck ein, um die Ausnahme anzugeben.|

## <a name="see-also"></a>Siehe auch

- [Auflistung](../workflow-designer/collection-activity-designers.md)
- [Lösen Sie erneut aus](../workflow-designer/rethrow-activity-designer.md)
- [Throw-Aktivitätsdesigner](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)
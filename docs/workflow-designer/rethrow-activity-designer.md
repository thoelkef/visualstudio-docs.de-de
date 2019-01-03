---
title: Workflow-Designer - Rethrow-Aktivitätsdesigners
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.Rethrow.UI
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 929007c878be0313c4e90d4bb2a14bc0613d9dbd
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53930946"
---
# <a name="rethrow-activity-designer"></a>Rethrow-Aktivitätsdesigner

Die **Rethrow** Aktivitäts-Designer dient zum Erstellen und Konfigurieren einer <xref:System.Activities.Statements.Rethrow> Aktivität.

## <a name="the-rethrow-activity"></a>Die Rethrow-Aktivität

Die <xref:System.Activities.Statements.Rethrow>-Aktivität löst eine zuvor ausgelöste Ausnahme aus. Diese Aktivität kann nur in einem <xref:System.Activities.Statements.Catch>-Handler in der <xref:System.Activities.Statements.TryCatch> -Aktivität verwendet werden.

### <a name="use-the-rethrow-activity-designer"></a>Verwenden des ReThrow-Aktivitätsdesigners

Zugriff die **Rethrow** Aktivitäts-Designer in der **Fehlerbehandlung** Kategorie der **Toolbox**. Der **Rethrow** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** und sich der Workflow-Designer-Oberfläche gelöscht werden, wo Aktivitäten normalerweise platziert werden, z. B. in einer <xref:System.Activities.Statements.Sequence>. Löschen die Aktivitäts-Designer erstellt eine <xref:System.Activities.Statements.Rethrow> -Aktivität mit dem standardmäßigen **"DisplayName"** -Standardwert Rethrow. Die <xref:System.Activities.Activity.DisplayName%2A> Wert kann im Header des bearbeitet werden die **erneut auslösen** Aktivitäts-Designer oder in der **"DisplayName"** Feld des Eigenschaftenrasters.

### <a name="the-rethrow-properties"></a>Die Rethrow-Eigenschaften

Die folgende Tabelle zeigt die <xref:System.Activities.Statements.Rethrow> Eigenschaften, und beschreibt, wie sie im Designer verwendet werden:

|Eigenschaftenname|Erforderlich|Verwendung|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den optionalen Anzeigenamen der <xref:System.Activities.Statements.Rethrow>-Aktivität an. Der Standardwert lautet Rethrow.|

## <a name="see-also"></a>Siehe auch

- [Auflistung](../workflow-designer/collection-activity-designers.md)
- [Throw](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)
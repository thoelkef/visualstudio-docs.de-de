---
title: Workflow-Designer Throw-Aktivitäts Designer
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Throw.UI
ms.assetid: 5e97c947-be39-4a1f-af04-000e2e09528a
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fe6a530888c7c28c5c1556114db03a6cd7369fe6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649853"
---
# <a name="throw-activity-designer"></a>Throw-Aktivitätsdesigner

Der **throw** -Aktivitäts Designer wird verwendet, um eine <xref:System.Activities.Statements.Throw>-Aktivität zu erstellen und zu konfigurieren.

## <a name="the-throw-activity"></a>Die Throw-Aktivität

Die <xref:System.Activities.Statements.Throw>-Aktivität löst eine Ausnahme aus.

### <a name="using-the-throw-activity-designer"></a>Verwenden des Throw-Aktivitätsdesigners

Greifen Sie in der Kategorie **Fehlerbehandlung** der **Toolbox**auf den **throw** -Aktivitäts Designer zu.

Der **throw** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der Workflow-Designer-Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden, z. b. innerhalb eines <xref:System.Activities.Statements.Sequence>. Dadurch wird eine <xref:System.Activities.Statements.Throw>-Aktivität mit dem **Display Name** -Standardwert Throw erstellt. Der <xref:System.Activities.Activity.DisplayName%2A> Wert kann im Header des **throw** -Aktivitäts Designers oder im Feld **Display Name** des Eigenschaften Rasters bearbeitet werden. Diese <xref:System.Activities.Statements.Throw.Exception%2A>-Eigenschaft muss im Eigenschaftenraster bearbeitet werden.

### <a name="the-throw-properties"></a>Die Throw-Eigenschaften

In der folgenden Tabelle werden die <xref:System.Activities.Statements.Throw>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den optionalen Anzeigenamen der <xref:System.Activities.Statements.Throw>-Aktivität an. Der Standardwert lautet Throw.|
|<xref:System.Activities.Statements.Throw.Exception%2A>|True|Die auszulösende Ausnahme. Diese Ausnahme muss sich von <xref:System.Exception> ableiten. Geben Sie im Eigenschaftenraster einen Visual Basic-Ausdruck ein, um die Ausnahme anzugeben.|

## <a name="see-also"></a>Siehe auch

- [Auflistung](../workflow-designer/collection-activity-designers.md)
- [Rethrow](../workflow-designer/rethrow-activity-designer.md)
- [Throw-Aktivitätsdesigner](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)
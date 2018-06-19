---
title: Workflow-Designer - Persist-Aktivitätsdesigners
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Persist.UI
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 04c7989f5cc37ec295f9fa778f2120dd372fd99a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31971115"
---
# <a name="persist-activity-designer"></a>Persist-Aktivitätsdesigners

Die **Persist** Aktivitäts-Designer dient zum Erstellen und Konfigurieren einer <xref:System.Activities.Statements.Persist> Aktivität.

## <a name="the-persist-activity"></a>Die Persist-Aktivität

Wenn möglich, speichert die <xref:System.Activities.Statements.Persist>-Aktivität einen Workflow auf dem Datenträger. Die <xref:System.Activities.Statements.Persist>-Aktivität kann nicht in einem Bereich ohne Persistenz ausgeführt werden, z. B. innerhalb einer <xref:System.Activities.Statements.TransactionScope>-Aktivität. Wenn Sie eine <xref:System.Activities.Statements.Persist>-Aktivität in einem Bereich ohne Persistenz verwenden, wird zur Laufzeit eine Ausnahme ausgelöst.

### <a name="using-the-persist-activity-designer"></a>Verwenden des Persist-Aktivitätsdesigners

Die **Persist** Aktivitäts-Designer finden Sie in der **Runtime** Kategorie von der **Toolbox**, die erfolgt durch Klicken auf die **Toolbox** Registerkarte "(Wählen Sie alternativ **Toolbox** aus der **Ansicht** Menüs oder STRG + ALT + X.)

Die **Persist** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** und sich der Workflow-Designer-Oberfläche gelöscht wird, wo Aktivitäten normalerweise platziert werden, z. B. in einem <xref:System.Activities.Statements.Sequence>. Dies erstellt eine <xref:System.Activities.Statements.Persist> -Aktivität mit dem standardmäßigen **DisplayName** -Standardwert Persist. Die <xref:System.Activities.Activity.DisplayName%2A> kann im Header des bearbeitet werden die **Persist** Aktivitäts-Designer oder in der **DisplayName** Feld des Eigenschaftenrasters.

### <a name="the-persist-properties"></a>Die Persist-Eigenschaften

In der folgenden Tabelle werden die <xref:System.Activities.Statements.Persist>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster bearbeitet werden, und einige davon können auf die Oberfläche des Workflow-Designer bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der Anzeigename der <xref:System.Activities.Statements.Persist>-Aktivität. Der Standardwert lautet Persist. Obwohl der Anzeigename nicht unbedingt erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|

## <a name="see-also"></a>Siehe auch

- [Laufzeit](../workflow-designer/runtime-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)
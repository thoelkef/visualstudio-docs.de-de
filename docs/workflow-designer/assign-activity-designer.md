---
title: Workflow-Designer - Assign-Aktivitätsdesigners
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Assign.UI
ms.assetid: ba3feb3c-f144-47ea-926d-cf752b804153
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 600f38d7bcd387915ba61fc148805705e8609431
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49905249"
---
# <a name="assign-activity-designer"></a>Assign-Aktivitätsdesigner

Die **weisen** Aktivitäts-Designer dient zum Erstellen und Konfigurieren einer <xref:System.Activities.Statements.Assign> Aktivität.

## <a name="the-assign-activity"></a>Die Assign-Aktivität

Die <xref:System.Activities.Statements.Assign>-Aktivität weist einer Variablen oder einem Argument einen Wert zu.

### <a name="using-the-assign-activity-designer"></a>Verwenden des Assign-Aktivitätsdesigners

Die **weisen** Aktivitäts-Designer finden Sie in der **primitive** Kategorie der **Toolbox**, die erfolgt durch Klicken auf die **Toolbox**Registerkarte (Wählen Sie alternativ **Toolbox** aus der **Ansicht** Menü- oder STRG + ALT + X.)

Die **zuweisen** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** und sich der Workflow-Designer-Oberfläche gelöscht wird, egal wo Aktivitäten platziert werden, z. B. in einem <xref:System.Activities.Statements.Sequence>. Löschen der **zuweisen** Aktivitäts-Designer erstellt eine <xref:System.Activities.Statements.Assign> -Aktivität mit dem standardmäßigen **"DisplayName"** von zuweisen. Die <xref:System.Activities.Activity.DisplayName%2A> kann im Header des bearbeitet werden die **weisen** Aktivitäts-Designer oder in der **"DisplayName"** Feld des Eigenschaftenrasters.

### <a name="the-assign-properties"></a>Die Assign-Eigenschaften

In der folgenden Tabelle werden die <xref:System.Activities.Statements.Assign>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster bearbeitet werden, und einige davon können auf die Oberfläche des Workflow-Designer bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der Anzeigename der <xref:System.Activities.Statements.Assign>-Aktivität. Der Standardwert lautet Assign. Obwohl der <xref:System.Activities.Activity.DisplayName%2A>-Wert nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.Assign.To%2A>|True|Die Variable oder das Argument, dem der <xref:System.Activities.Statements.Assign.Value%2A> zugewiesen wird. Der Wert muss ein gültiger Visual Basic-Bezeichner sein. Um die Eigenschaft festzulegen, geben Sie einen Visual Basic-Ausdruck in der **zu** Feld der **weisen** -Aktivitätsdesigner oder im Eigenschaftenraster.|
|<xref:System.Activities.Statements.Assign.Value%2A>|True|Der der Variablen zugewiesene Wert. Festlegen der <xref:System.Activities.Statements.Assign.Value%2A>, geben Sie einen Visual Basic-Ausdruck in der **Wert** Feld der **weisen** -Aktivitätsdesigner oder im Eigenschaftenraster.|

## <a name="see-also"></a>Siehe auch

- [Primitive](../workflow-designer/primitives-activity-designers.md)
- [Delay](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)
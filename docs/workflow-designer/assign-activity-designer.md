---
title: "Assign-Aktivitätsdesigner | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Assign.UI
ms.assetid: ba3feb3c-f144-47ea-926d-cf752b804153
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 875a05866a85084b58236ab6bf918201d1848b1d
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2018
---
# <a name="assign-activity-designer"></a>Assign-Aktivitätsdesigner
Die **zuweisen** Aktivitäts-Designer dient zum Erstellen und Konfigurieren einer <xref:System.Activities.Statements.Assign> Aktivität.

## <a name="the-assign-activity"></a>Die Assign-Aktivität
 Die <xref:System.Activities.Statements.Assign>-Aktivität weist einer Variablen oder einem Argument einen Wert zu.

### <a name="using-the-assign-activity-designer"></a>Verwenden des Assign-Aktivitätsdesigners
 Die **zuweisen** Aktivitäts-Designer finden Sie in der **primitive** Kategorie der **Toolbox**, die erfolgt durch Klicken auf die **Toolbox**Registerkarte (Wählen Sie alternativ **Toolbox** aus der **Ansicht** Menüs oder STRG + ALT + X drücken.)

 Die **zuweisen** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** gezogen und auf die [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] -Oberfläche, wo Aktivitäten normalerweise platziert werden, etwa innerhalb einer <xref:System.Activities.Statements.Sequence>. Dies erstellt eine <xref:System.Activities.Statements.Assign> -Aktivität mit dem standardmäßigen **DisplayName** von zuweisen. Die <xref:System.Activities.Activity.DisplayName%2A> kann im Header des bearbeitet werden die **zuweisen** Aktivitäts-Designer oder in der **DisplayName** Feld des Eigenschaftenrasters.

### <a name="the-assign-properties"></a>Die Assign-Eigenschaften
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.Assign>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster bearbeitet werden, einige davon können auch auf der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]-Oberfläche bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der Anzeigename der <xref:System.Activities.Statements.Assign>-Aktivität. Der Standardwert lautet Assign. Obwohl der <xref:System.Activities.Activity.DisplayName%2A>-Wert nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.Assign.To%2A>|True|Die Variable oder das Argument, dem der <xref:System.Activities.Statements.Assign.Value%2A> zugewiesen wird. Dies muss ein gültiger Visual Basic-Bezeichner sein. Geben Sie zum Festlegen der Eigenschaft einen Visual Basic-Ausdruck in der **auf** Feld der **zuweisen** -Aktivitätsdesigner oder im Eigenschaftenraster.|
|<xref:System.Activities.Statements.Assign.Value%2A>|True|Der der Variablen zugewiesene Wert. Festlegen der <xref:System.Activities.Statements.Assign.Value%2A>, geben Sie einen Visual Basic-Ausdruck in der **Wert** Feld der **zuweisen** -Aktivitätsdesigner oder im Eigenschaftenraster.|

## <a name="see-also"></a>Siehe auch

- [Primitive](../workflow-designer/primitives-activity-designers.md)
- [Delay](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)
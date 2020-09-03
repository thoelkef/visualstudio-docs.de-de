---
title: Assign-Aktivitäts Designer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Assign.UI
ms.assetid: ba3feb3c-f144-47ea-926d-cf752b804153
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 40ebe465d5eeb12a956d285a8313b0acdbcfb8d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659189"
---
# <a name="assign-activity-designer"></a>Assign-Aktivitätsdesigner
Der **assign** -Aktivitäts Designer wird verwendet, um eine-Aktivität zu erstellen und zu konfigurieren <xref:System.Activities.Statements.Assign> .

## <a name="the-assign-activity"></a>Die Assign-Aktivität
 Die <xref:System.Activities.Statements.Assign>-Aktivität weist einer Variablen oder einem Argument einen Wert zu.

### <a name="using-the-assign-activity-designer"></a>Verwenden des Assign-Aktivitätsdesigners
 Der **assign** -Aktivitäts Designer befindet sich in der Kategorie **Primitives** der **Toolbox**, auf die Sie zugreifen können, indem Sie auf die Registerkarte **Toolbox** klicken (Sie können auch im Menü **Ansicht** den Befehl **Toolbox** auswählen oder STRG + ALT + X drücken).

 Der **assign** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der- [!INCLUDE[wfd2](../includes/wfd2-md.md)] Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden, z. b. in einer <xref:System.Activities.Statements.Sequence> . Dadurch wird eine <xref:System.Activities.Statements.Assign> Aktivität mit dem **Display Name** -Standardwert Assign erstellt. Der <xref:System.Activities.Activity.DisplayName%2A> kann im Header des **assign** -Aktivitäts Designers oder im Feld **Display Name** des Eigenschaften Rasters bearbeitet werden.

### <a name="the-assign-properties"></a>Die Assign-Eigenschaften
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.Assign>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster bearbeitet werden, einige davon können auch auf der [!INCLUDE[wfd2](../includes/wfd2-md.md)]-Oberfläche bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der Anzeigename der <xref:System.Activities.Statements.Assign>-Aktivität. Der Standardwert lautet Assign. Obwohl der <xref:System.Activities.Activity.DisplayName%2A>-Wert nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.Assign.To%2A>|True|Die Variable oder das Argument, dem der <xref:System.Activities.Statements.Assign.Value%2A> zugewiesen wird. Dies muss ein gültiger Visual Basic-Bezeichner sein. Um die-Eigenschaft festzulegen, geben Sie im **assign** -Aktivitäts Designer oder im Eigenschaften Raster einen Visual Basic-Ausdruck in das Feld **an** ein.|
|<xref:System.Activities.Statements.Assign.Value%2A>|True|Der der Variablen zugewiesene Wert. Um die festzulegen <xref:System.Activities.Statements.Assign.Value%2A> , geben Sie im Feld **Wert** des **assign** -Aktivitäts Designers oder im Eigenschaften Raster einen Visual Basic Ausdruck ein.|

## <a name="see-also"></a>Weitere Informationen
 [Primitives](../workflow-designer/primitives-activity-designers.md) Methode zum [verzögerten](../workflow-designer/delay-activity-designer.md) Rückschreiben von " [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md) [WriteLine](../workflow-designer/writeline-activity-designer.md) "
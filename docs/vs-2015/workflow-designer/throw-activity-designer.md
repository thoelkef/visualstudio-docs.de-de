---
title: Throw-Aktivitäts Designer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Throw.UI
ms.assetid: 5e97c947-be39-4a1f-af04-000e2e09528a
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1855daa5016241fb6eb04f05d7218e02083fc0a8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655163"
---
# <a name="throw-activity-designer"></a>Throw-Aktivitätsdesigner
Der **throw** -Aktivitäts Designer wird verwendet, um eine-Aktivität zu erstellen und zu konfigurieren <xref:System.Activities.Statements.Throw> .

## <a name="the-throw-activity"></a>Die Throw-Aktivität
 Die <xref:System.Activities.Statements.Throw>-Aktivität löst eine Ausnahme aus.

### <a name="using-the-throw-activity-designer"></a>Verwenden des Throw-Aktivitätsdesigners
 Der **throw** -Aktivitäts Designer befindet sich in der Kategorie **Fehlerbehandlung** der **Toolbox**, auf die Sie zugreifen können, indem Sie auf der linken Seite von auf die Registerkarte **Toolbox** klicken (Sie können auch im [!INCLUDE[wfd2](../includes/wfd2-md.md)] Menü **Ansicht** den Befehl **Symbolleiste** auswählen oder STRG + ALT + X drücken).

 Der **throw** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der- [!INCLUDE[wfd2](../includes/wfd2-md.md)] Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden, z. b. innerhalb eines <xref:System.Activities.Statements.Sequence> . Dadurch wird eine- <xref:System.Activities.Statements.Throw> Aktivität mit dem **Display Name** -Standardwert Throw erstellt. Der <xref:System.Activities.Activity.DisplayName%2A> Wert kann im Header des **throw** -Aktivitäts Designers oder im Feld **Display Name** des Eigenschaften Rasters bearbeitet werden. Diese <xref:System.Activities.Statements.Throw.Exception%2A>-Eigenschaft muss im Eigenschaftenraster bearbeitet werden.

### <a name="the-throw-properties"></a>Die Throw-Eigenschaften
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.Throw>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den optionalen Anzeigenamen der <xref:System.Activities.Statements.Throw>-Aktivität an. Der Standardwert lautet Throw.|
|<xref:System.Activities.Statements.Throw.Exception%2A>|True|Die auszulösende Ausnahme. Diese Ausnahme muss sich von <xref:System.Exception> ableiten. Geben Sie im Eigenschaftenraster einen Visual Basic-Ausdruck ein, um die Ausnahme anzugeben.|

## <a name="see-also"></a>Weitere Informationen
 [Collection](../workflow-designer/collection-activity-designers.md) [Erfassungs](../workflow-designer/rethrow-activity-designer.md) - [throw-Aktivitäts Designer](../workflow-designer/throw-activity-designer.md) ( [trycatch](../workflow-designer/trycatch-activity-designer.md) )
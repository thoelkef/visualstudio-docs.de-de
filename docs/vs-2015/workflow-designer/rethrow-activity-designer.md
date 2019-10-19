---
title: Rethrow-Aktivitäts Designer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Rethrow.UI
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c65469242a60c64d6f31bfaea4fdbbf2d5251a34
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663361"
---
# <a name="rethrow-activity-designer"></a>Rethrow-Aktivitätsdesigner
Der **Rethrow** -Aktivitäts Designer wird verwendet, um eine <xref:System.Activities.Statements.Rethrow>-Aktivität zu erstellen und zu konfigurieren.

## <a name="the-rethrow-activity"></a>Die Rethrow-Aktivität
 Die <xref:System.Activities.Statements.Rethrow>-Aktivität löst eine zuvor ausgelöste Ausnahme aus. Diese Aktivität kann nur in einem <xref:System.Activities.Statements.Catch>-Handler in der <xref:System.Activities.Statements.TryCatch> -Aktivität verwendet werden.

### <a name="using-the-rethrow-activity-designer"></a>Verwenden des Rethrow-Aktivitätsdesigners
 Der **Rethrow** -Aktivitäts Designer befindet sich in der Kategorie **Fehlerbehandlung** der **Toolbox**, auf die Sie zugreifen können, indem Sie auf der linken Seite der [!INCLUDE[wfd2](../includes/wfd2-md.md)] auf die Registerkarte **Toolbox** klicken. (Sie können auch **Symbolleiste** **im** Menü "Ansicht" oder STRG + ALT + X.)

 Der **Rethrow** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der [!INCLUDE[wfd2](../includes/wfd2-md.md)]-Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden, z. b. innerhalb eines <xref:System.Activities.Statements.Sequence>. Dadurch wird eine <xref:System.Activities.Statements.Rethrow>-Aktivität mit dem **Display Name** -Standardwert Throw erstellt. Der <xref:System.Activities.Activity.DisplayName%2A> Wert kann im Header des **Rethrow** -Aktivitäts Designers oder im Feld **Display Name** des Eigenschaften Rasters bearbeitet werden.

### <a name="the-rethrow-properties"></a>Die Rethrow-Eigenschaften
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.Rethrow>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den optionalen Anzeigenamen der <xref:System.Activities.Statements.Rethrow>-Aktivität an. Der Standardwert lautet Rethrow.|

## <a name="see-also"></a>Siehe auch
 [Sammlung](../workflow-designer/collection-activity-designers.md) [throw](../workflow-designer/throw-activity-designer.md) [trycatch](../workflow-designer/trycatch-activity-designer.md)
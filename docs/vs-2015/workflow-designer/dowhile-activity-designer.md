---
title: DoWhile-Aktivitäts Designer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b63c3e2e0907bcaf13ada4cbb20ce5527a240fe3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656771"
---
# <a name="dowhile-activity-designer"></a>DoWhile-Aktivitätsdesigner
Die- <xref:System.Activities.Statements.DoWhile> Aktivität führt die in der enthaltenen Aktivität mindestens <xref:System.Activities.Statements.DoWhile.Body%2A> einmal aus, bis eine angegebene Bedingung als **false**ausgewertet wird. Wenn die in einem Schleifentext enthaltene Anwendung der 0 (null) oder mehrmals ausgeführt werden soll, verwenden Sie stattdessen die <xref:System.Activities.Statements.While>-Aktivität.

## <a name="dowhile-properties-in-the-workflow-designer"></a>DoWhile- Eigenschaften im Workflow-Designer
 In der folgenden Tabelle werden die nützlichsten Eigenschaften der <xref:System.Activities.Statements.DoWhile>-Aktivität aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.

|Eigenschaftenname|Erforderlich|Verbrauch|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.DoWhile.Body%2A>|Falsch|Die Aktivität, die ausgeführt werden soll, während die Bedingung **true**ist. Um die-Aktivität hinzuzufügen, legen Sie <xref:System.Activities.Statements.DoWhile.Body%2A> eine Aktivität aus der Toolbox in das Feld **Body** mit dem Hinweis Text "Aktivität hier ablegen" des **DoWhile** -Aktivitäts Designers ab.|
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|Richtig|Die Bedingung, die nach jedem Schleifendurchlauf ausgewertet werden soll. Um die festzulegen <xref:System.Activities.Statements.DoWhile.Condition%2A> , geben Sie im [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] Feld **Bedingung** im **DoWhile** -Aktivitäts Designer oder im Eigenschaften Raster einen-Ausdruck ein.|

## <a name="see-also"></a>Weitere Informationen
 [Während](../workflow-designer/while-activity-designer.md) der [Ablauf Steuerung](../workflow-designer/control-flow-activity-designers.md)
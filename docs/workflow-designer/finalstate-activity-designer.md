---
title: "FinalState-Aktivitäts-Designer | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: aa186893-8775-40dd-981f-8593ead831d0
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: a5b9b8cc1fc0bdb390e1bf32a6a8f262b435a157
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2018
---
# <a name="finalstate-activity-designer"></a>FinalState-Aktivitäts-Designer
Der <xref:System.Activities.Core.Presentation.FinalState>-Designer wird verwendet, um einen <xref:System.Activities.Statements.State> zu erstellen, der eine Instanz des Zustandsautomaten beendet.

## <a name="using-the-finalstate-activity-designer"></a>Verwenden des FinalState-Aktivitäts-Designers
 Die **FinalState** -Designer dient zum Erstellen einer <xref:System.Activities.Statements.State> , der als beendender Zustand in einem Zustandsautomaten vorkonfiguriert ist. Ein <xref:System.Activities.Statements.State> , erstellt wird, mithilfe der <xref:System.Activities.Core.Presentation.FinalState> Aktivitäts-Designer hat seine <xref:System.Activities.Statements.State.IsFinal%2A> -Eigenschaftensatz auf **"true"**, hat keine <xref:System.Activities.Statements.State.Exit%2A> Aktivität und keine Übergänge ausgehen. Verwenden der <xref:System.Activities.Core.Presentation.FinalState> Aktivitäts-Designer zum Hinzufügen einer <xref:System.Activities.Statements.State> Aktivität, die in einem Zustandsautomaten in einem beendenden Zustand vorkonfiguriert ist ziehen die **FinalState** Aktivitäts-Designer aus der **Zustandsautomat**Teil der **Toolbox** und legen ihn auf die Workflow-Designer. Der <xref:System.Activities.Core.Presentation.FinalState>-Aktivitäts-Designer kann auf einem <xref:System.Activities.Statements.StateMachine> abgelegt werden, und es können später Übergänge hinzugefügt werden, oder es kann ein Übergang erstellt werden, wenn der <xref:System.Activities.Core.Presentation.FinalState>-Aktivitäts-Designer abgelegt wird. Weitere Informationen zum Erstellen von Übergängen finden Sie unter [Übergang](../workflow-designer/transition-activity-designer.md).

### <a name="state-activity-properties-in-the-workflow-designer"></a>Zustandsaktivitätseigenschaften im Workflow-Designer
 In der folgenden Tabelle sind die Eigenschaften aufgeführt, die mithilfe des <xref:System.Activities.Core.Presentation.FinalState>-Designers festgelegt werden können, und es wird beschrieben, wie sie im Designer verwendet werden. Einige dieser Eigenschaften können im Eigenschaftenraster und einige auf der Designeroberfläche bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.State.DisplayName%2A>|False|Gibt den benutzerfreundlichen Namen der <xref:System.Activities.Statements.State>Aktivität im Header an. Der Standardwert ist **Zustand**. Der Wert kann im Eigenschaftenraster oder direkt im Header des Aktivitätsdesigners bearbeitet werden. <xref:System.Activities.Statements.State.DisplayName%2A> wird in der Breadcrumbnavigation verwendet, die am oberen Rand des Workflow-Designers angezeigt wird.<br /><br /> Obwohl der <xref:System.Activities.Statements.State.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.State.Entry%2A>|False|Gibt die Aktion an, die eintritt, wenn ein Übergang in diesen Zustand stattfindet. Dieser Wert kann festgelegt werden, ziehen Sie eine Aktivität aus der **Toolbox** per Drag & Drop auf die <xref:System.Activities.Statements.State.Entry%2A> -Abschnitt des Zustands.|

## <a name="see-also"></a>Siehe auch

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [Zustand](../workflow-designer/state-activity-designer.md)
- [Übergang](../workflow-designer/transition-activity-designer.md)
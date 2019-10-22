---
title: Workflow-Designer-FinalState-Aktivitäts Designer
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: aa186893-8775-40dd-981f-8593ead831d0
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: b8f25167f3a67e2d1349354ce568c076697e3e73
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650470"
---
# <a name="finalstate-activity-designer"></a>FinalState-Aktivitäts-Designer

Der <xref:System.Activities.Core.Presentation.FinalState>-Designer wird verwendet, um einen <xref:System.Activities.Statements.State> zu erstellen, der eine Instanz des Zustandsautomaten beendet.

## <a name="using-the-finalstate-activity-designer"></a>Verwenden des FinalState-Aktivitäts-Designers

Der **FinalState** -Designer wird verwendet, um eine <xref:System.Activities.Statements.State> zu erstellen, die als Beendigungs Zustand in einem Zustands Automaten vorkonfiguriert ist. Für eine <xref:System.Activities.Statements.State>, die mit dem <xref:System.Activities.Core.Presentation.FinalState>-Aktivitäts Designer erstellt wird, ist die <xref:System.Activities.Statements.State.IsFinal%2A>-Eigenschaft auf **true**festgelegt, es sind keine <xref:System.Activities.Statements.State.Exit%2A> Aktivitäten und keine Übergänge von der Datei. Wenn Sie den <xref:System.Activities.Core.Presentation.FinalState>-Aktivitäts Designer verwenden möchten, um eine <xref:System.Activities.Statements.State> Aktivität hinzuzufügen, die als Beendigungs Zustand in einem Zustands Automaten vorkonfiguriert ist, ziehen Sie den **FinalState** -Aktivitäts Designer aus dem Abschnitt **Zustands Automat** der **Toolbox** , und legen Sie ihn auf dem Workflow-Designer. Der <xref:System.Activities.Core.Presentation.FinalState>-Aktivitäts-Designer kann auf einem <xref:System.Activities.Statements.StateMachine> abgelegt werden, und es können später Übergänge hinzugefügt werden, oder es kann ein Übergang erstellt werden, wenn der <xref:System.Activities.Core.Presentation.FinalState>-Aktivitäts-Designer abgelegt wird. Weitere Informationen zum Erstellen von Übergängen finden Sie unter [Transition](../workflow-designer/transition-activity-designer.md).

### <a name="state-activity-properties-in-the-workflow-designer"></a>Zustandsaktivitätseigenschaften im Workflow-Designer

In der folgenden Tabelle sind die Eigenschaften aufgeführt, die mithilfe des <xref:System.Activities.Core.Presentation.FinalState>-Designers festgelegt werden können, und es wird beschrieben, wie sie im Designer verwendet werden. Einige dieser Eigenschaften können im Eigenschaftenraster und einige auf der Designeroberfläche bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-|--------------|-|
|<xref:System.Activities.Statements.State.DisplayName%2A>|False|Gibt den benutzerfreundlichen Namen der <xref:System.Activities.Statements.State>Aktivität im Header an. Der Standardwert ist **State**. Der Wert kann im Eigenschaftenraster oder direkt im Header des Aktivitätsdesigners bearbeitet werden. <xref:System.Activities.Statements.State.DisplayName%2A> wird in der Breadcrumbnavigation verwendet, die am oberen Rand des Workflow-Designers angezeigt wird.<br /><br /> Obwohl der <xref:System.Activities.Statements.State.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.State.Entry%2A>|False|Gibt die Aktion an, die eintritt, wenn ein Übergang in diesen Zustand stattfindet. Dieser Wert kann festgelegt werden, indem Sie eine Aktivität aus der **Toolbox** ziehen und auf dem <xref:System.Activities.Statements.State.Entry%2A> Abschnitt des Zustands ablegen.|

## <a name="see-also"></a>Siehe auch

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [Zustand](../workflow-designer/state-activity-designer.md)
- [Transition](../workflow-designer/transition-activity-designer.md)
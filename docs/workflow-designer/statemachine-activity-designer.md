---
title: Workflow-Designer - StateMachine-Aktivitätsdesigner
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- StateMachine Designer
- System.Activities.Statements.StateMachine.UI
ms.assetid: 474d5fb3-1049-4b3f-bc6b-7524dbbe1672
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 52cbd0e27934d5d13c0e83c6c8e3e87281aa1b5a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54972900"
---
# <a name="statemachine-activity-designer"></a>StateMachine-Aktivitäts-Designer

Die <xref:System.Activities.Statements.StateMachine>-Aktivität enthält eine Auflistung von Zustands- und Modellworkflows, die das bekannte Zustandsautomatenparadigma verwenden.

## <a name="using-the-statemachine-activity-designer"></a>Verwenden des StateMachine-Aktivitäts-Designers

Hinzufügen einer <xref:System.Activities.Statements.StateMachine> -Aktivität ziehen Sie die **StateMachine** Aktivitäts-Designer aus der **State Machine** Teil der **Toolbox** und legen Sie es sich bei der Workflow-Designer Oberfläche. Um einen untergeordneten Zustand hinzufügen <xref:System.Activities.Statements.StateMachine> -Aktivität ziehen Sie eine <xref:System.Activities.Statements.State> oder <xref:System.Activities.Core.Presentation.FinalState> aus der **Toolbox** und legen ihn auf die **StateMachine**.

### <a name="statemachine-activity-properties-in-the-workflow-designer"></a>Eigenschaften der StateMachine-Aktivität im Workflow-Designer

In der folgenden Tabelle sind die <xref:System.Activities.Statements.StateMachine>-Eigenschaften aufgeführt, die mithilfe des Workflow-Designers festgelegt werden können, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster, einige davon auf der Designeroberfläche bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den benutzerfreundlichen Namen der <xref:System.Activities.Statements.StateMachine>Aktivität im Header an. Der Standardwert ist **StateMachine**. Der Wert kann im Eigenschaftenraster oder direkt im Header des Aktivitätsdesigners bearbeitet werden. <xref:System.Activities.Activity.DisplayName%2A> wird in der Breadcrumbnavigation verwendet, die am oberen Rand des Workflow-Designers angezeigt wird.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|

## <a name="see-also"></a>Siehe auch

- [Flussdiagramm](../workflow-designer/flowchart-activity-designer.md)
- [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)
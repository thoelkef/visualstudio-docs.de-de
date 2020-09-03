---
title: StateMachine-Aktivitäts Designer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- StateMachine Designer
- System.Activities.Statements.StateMachine.UI
ms.assetid: 474d5fb3-1049-4b3f-bc6b-7524dbbe1672
caps.latest.revision: 5
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5fc9d34e06ca443b39a1a57aa88fee1155f47a8c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660117"
---
# <a name="statemachine-activity-designer"></a>StateMachine-Aktivitäts-Designer
Die <xref:System.Activities.Statements.StateMachine>-Aktivität enthält eine Auflistung von Zustands- und Modellworkflows, die das bekannte Zustandsautomatenparadigma verwenden.

## <a name="using-the-statemachine-activity-designer"></a>Verwenden des StateMachine-Aktivitäts-Designers
 Zum Hinzufügen einer- <xref:System.Activities.Statements.StateMachine> Aktivität ziehen Sie den **StateMachine** -Aktivitäts-Designer aus dem Abschnitt **Zustands Automat** der **Toolbox** , und legen Sie ihn auf der- [!INCLUDE[wfd1](../includes/wfd1-md.md)] Oberfläche ab. Um dieser Aktivität einen untergeordneten Zustand hinzuzufügen <xref:System.Activities.Statements.StateMachine> , ziehen <xref:System.Activities.Statements.State> Sie eine oder <xref:System.Activities.Core.Presentation.FinalState> aus der **Toolbox** , und legen Sie Sie auf dem **StateMachine**-Element ab.

### <a name="statemachine-activity-properties-in-the-workflow-designer"></a>Eigenschaften der StateMachine-Aktivität im Workflow-Designer
 In der folgenden Tabelle sind die <xref:System.Activities.Statements.StateMachine>-Eigenschaften aufgeführt, die mithilfe des Workflow-Designers festgelegt werden können, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster, einige davon auf der Designeroberfläche bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verbrauch|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Falsch|Gibt den benutzerfreundlichen Namen der <xref:System.Activities.Statements.StateMachine>Aktivität im Header an. Der Standardwert ist **StateMachine**. Der Wert kann im Eigenschaftenraster oder direkt im Header des Aktivitätsdesigners bearbeitet werden. <xref:System.Activities.Activity.DisplayName%2A> wird in der Breadcrumbnavigation verwendet, die am oberen Rand des Workflow-Designers angezeigt wird.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|

## <a name="see-also"></a>Weitere Informationen
 Fluss [Diagramm](../workflow-designer/flowchart-activity-designer.md) - [Ablauf Steuerung](../workflow-designer/control-flow-activity-designers.md)
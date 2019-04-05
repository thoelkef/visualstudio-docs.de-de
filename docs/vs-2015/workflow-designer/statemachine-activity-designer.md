---
title: StateMachine-Aktivitäts-Designer | Microsoft-Dokumentation
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
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 96965a2b0861e7c4df4a43e4d258afc0a48090bd
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58957174"
---
# <a name="statemachine-activity-designer"></a>StateMachine-Aktivitäts-Designer
Die <xref:System.Activities.Statements.StateMachine>-Aktivität enthält eine Auflistung von Zustands- und Modellworkflows, die das bekannte Zustandsautomatenparadigma verwenden.  
  
## <a name="using-the-statemachine-activity-designer"></a>Verwenden des StateMachine-Aktivitäts-Designers  
 Hinzufügen einer <xref:System.Activities.Statements.StateMachine> -Aktivität ziehen Sie die **StateMachine** Aktivitäts-Designer aus der **Zustandsautomat** im Abschnitt der **Toolbox** und legen ihn auf die [!INCLUDE[wfd1](../includes/wfd1-md.md)] Oberfläche. Um einen untergeordneten Zustand hinzufügen <xref:System.Activities.Statements.StateMachine> -Aktivität ziehen Sie eine <xref:System.Activities.Statements.State> oder <xref:System.Activities.Core.Presentation.FinalState> aus der **Toolbox** und legen ihn auf die **StateMachine**.  
  
### <a name="statemachine-activity-properties-in-the-workflow-designer"></a>Eigenschaften der StateMachine-Aktivität im Workflow-Designer  
 In der folgenden Tabelle sind die <xref:System.Activities.Statements.StateMachine>-Eigenschaften aufgeführt, die mithilfe des Workflow-Designers festgelegt werden können, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster, einige davon auf der Designeroberfläche bearbeitet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den benutzerfreundlichen Namen der <xref:System.Activities.Statements.StateMachine>Aktivität im Header an. Der Standardwert ist **StateMachine**. Der Wert kann im Eigenschaftenraster oder direkt im Header des Aktivitätsdesigners bearbeitet werden. <xref:System.Activities.Activity.DisplayName%2A> wird in der Breadcrumbnavigation verwendet, die am oberen Rand des Workflow-Designers angezeigt wird.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|  
  
## <a name="see-also"></a>Siehe auch  
 [Flussdiagramm](../workflow-designer/flowchart-activity-designer.md)   
 [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)
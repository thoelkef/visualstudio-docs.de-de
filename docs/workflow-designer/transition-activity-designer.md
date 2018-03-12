---
title: "Ein Übergang erfolgt, Aktivitäts-Designer | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Transition.UI
ms.assetid: f6e8b5cc-7fb8-4699-9703-f3c9fc7cc316
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: e245df7132075c0a7b691e5fee1069ebffd47ca0
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2018
---
# <a name="transition-activity-designer"></a>Übergangsaktivitäts-Designer
Ein <xref:System.Activities.Statements.Transition> stellt den Übergang zwischen zwei Zuständen dar.

## <a name="using-the-transition-activity-designer"></a>Verwenden des Transition-Aktivitäts-Designers
 Der Transition-Aktivitäts-Designer ermöglicht es Ihnen, einen Übergang zwischen zwei Zuständen zu konfigurieren.

### <a name="transition-properties-in-the-workflow-designer"></a>Transition-Eigenschaften im Workflow-Designer
 In der folgenden Tabelle sind die <xref:System.Activities.Statements.Transition>-Eigenschaften aufgeführt, die mithilfe des Workflow-Designers festgelegt werden können, und es wird beschrieben, wie sie im Designer verwendet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.Transition.DisplayName%2A>|False|Gibt den optionalen Anzeigenamen des <xref:System.Activities.Statements.Transition>-Aktivitätsdesigners an. Der Standardwert ist **T1**. Der Wert kann im Eigenschaftenraster im Header des erweiterten Übergangs-Designers und im Header des Aktionsabschnitts innerhalb des erweiterten Übergangs-Designers bearbeitet werden. <xref:System.Activities.Activity.DisplayName%2A> wird in der Breadcrumbnavigation verwendet, die am oberen Rand des Workflow-Designers angezeigt wird.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.Transition.Condition%2A>|False|Gibt an, falls vorhanden, ein Ausdruck, der ausgewertet werden muss **"true"** , bevor die Steuerung an den Zielzustand übergeben wird. Diese Bedingung kann im Eigenschaftenraster und im erweiterten Übergangs-Designer bearbeitet werden. Mehrere Bedingungen in einem gemeinsamen Übergang werden in der Reihenfolge ausgewertet, in der sie im Übergangs-Designer angezeigt werden. **Hinweis:** Beachten Sie, dass bei der <xref:System.Activities.Statements.Transition.Condition%2A> eines Übergangs ergibt **"false"** (oder alle Bedingungen eines Übergangs mit freigegebenem Trigger auswerten **"false"**), erfolgt der Übergang nicht und alle Trigger aller Übergänge aus dem Zustand werden neu geplant. In diesem Lernprogramm kann diese Situation aufgrund der Konfigurationsmethode für die Bedingungen (es gibt spezielle Aktionen für richtige oder falsche Schätzungen) nicht auftreten.|
|**Quelle**|True|Gibt den Zustand an, von dem dieser Übergang ausgeht. Indem Sie auf den Namen des Quellzustands klicken, wechselt die Designeransicht in eine erweiterte Ansicht dieses Zustands. Dieser Wert wird festgelegt, wenn der Übergang erstellt wird, und kann nicht geändert werden.|
|<xref:System.Activities.Statements.Transition.Trigger%2A>|False|Gibt die Aktivität an, deren Abschluss den Übergang initiiert. Um diese Aktivität festzulegen, ziehen Sie eine Aktivität aus der **Toolbox** und legen ihn auf die **Trigger** Abschnitt des Übergangs.|
|<xref:System.Activities.Statements.Transition.Action%2A>|False|Gibt die Aktivität, die ausgeführt wird, wenn der triggeraktivität abgeschlossen und die <xref:System.Activities.Statements.Transition.Condition%2A>, sofern es vorhanden ist, ergibt **"true"**. Diese Aktivität wird ausgeführt, wenn der Übergang in den Zielzustand erfolgt, nachdem die <xref:System.Activities.Statements.State.Exit%2A>-Aktivität für den Quellzustand, falls vorhanden, ausgeführt wurde. Wenn der Übergangs-Designer erweitert wird, kann dieser Wert festgelegt werden, ziehen Sie eine Aktivität aus der **Toolbox** per Drag & Drop auf die **Aktion** Abschnitt des Übergangs. Ein Übergang kann mehrere Aktionen aufweisen. Die einzelnen Aktionen können erweitert, verkürzt und geordnet werden, indem Sie auf den Pfeil nach oben oder nach unten klicken, der für die Aktion angezeigt wird, wenn mehrere Aktionen in einem Übergang vorhanden sind.|
|**Ziel**|True|Gibt den Zustand an, in den der Zustandsautomat übergeht, nachdem der Übergang abgeschlossen ist. Dies entspricht der <xref:System.Activities.Statements.Transition.To%2A>-Eigenschaft des Übergangs im Objektmodell. Indem Sie auf den Namen des Zielzustands klicken, wechselt die Designeransicht in eine erweiterte Ansicht dieses Zustands. Dieser Wert wird festgelegt, wenn der Übergang erstellt wird, und kann geändert werden, indem Sie im Designer den Pfeil ziehen, der den Übergang mit dem Zielzustand verbindet.|

### <a name="creating-transitions"></a>Erstellen von Übergängen
 Übergänge werden erstellt, indem eine Linie von einem Zustand zu einem anderen gezogen wird, oder indem ein Zustand auf den Dreiecken abgelegt wird, die angezeigt werden, wenn ein Zustand über einen anderen Zustand gezogen wird. Um einen Übergang durch Ziehen zu erstellen, zeigen Sie mit der Maus auf den Rand des Quellzustands und ziehen eine Linie vom Quell- zum Zielzustand. Um einen Übergang durch Ablegen zu erstellen, ziehen Sie den Zielzustand auf den Quellzustand und legen ihn auf einem der vier Dreiecke ab, die um den Quellzustand herum angezeigt werden. Der Zielzustand kann entweder ein neuer Zustand gezogen wird, aus der **Toolbox**, oder ein vorhandener Zustand, der aus dem Workflow-Designer gezogen.

> [!NOTE]
> Ein einzelner Zustand eines Zustandsautomaten kann bis zu 76 Übergänge aufweisen, die mithilfe des Workflow-Designers erstellt wurden. Die Anzahl der Zustandsübergänge für Workflows, die außerhalb des Designers erstellt werden, wird nur durch die verfügbaren Systemressourcen beschränkt.

 Übergänge mit gemeinsamem Trigger sind Übergänge, die dasselbe Triggerereignis verwenden. Ein gemeinsamer Trigger ermöglicht den bedingten Übergang zu einem Zielzustand auf Grundlage der Auswertung von Ausdrücken, die für mehrere Übergänge konfiguriert wurden, die über ein gemeinsames Triggerereignis verfügen. Um einem Übergang zusätzliche Aktionen hinzuzufügen und einen gemeinsamen Übergang zu erstellen, klicken Sie auf den Kreis, der den Anfang des gewünschten Übergangs angibt, und ziehen Sie ihn auf den gewünschten Zustand. Der neue Übergang verwendet denselben Trigger wie der Anfangsübergang, besitzt jedoch eine eindeutige Bedingung und Aktion. Gemeinsame Übergänge können auch aus erstellt werden innerhalb des Übergangs-Designers durch Klicken auf **gemeinsamen triggerübergang hinzufügen** am unteren Rand des Übergangs-Designers, und wählen Sie dann den gewünschten Zielzustand aus der  **Verfügbare Zustände für Verbindung** Dropdownliste aus.

## <a name="see-also"></a>Siehe auch

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [FinalState](../workflow-designer/finalstate-activity-designer.md)
- [Zustand](../workflow-designer/state-activity-designer.md)
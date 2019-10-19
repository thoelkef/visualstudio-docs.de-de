---
title: Pick-Aktivitäts Designer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: daefc48cfff2c5c73d9ecf14316777becf4d83c5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672598"
---
# <a name="pick-activity-designer"></a>Pick-Aktivitätsdesigner
Die <xref:System.Activities.Statements.Pick>-Aktivität stellt eine ereignisbasierte Ablaufsteuerung bereit. Die Aktivität führt einen von mehreren Branches als Reaktion auf die Auslösung eines Ereignisses aus.

## <a name="the-pick-activity"></a>Die Pick-Aktivität
 Eine <xref:System.Activities.Statements.Pick>-Aktivität enthält eine Auflistung von <xref:System.Activities.Statements.PickBranch>-Objekten, von denen die <xref:System.Activities.Statements.Pick>-Aktivität eines ausführen kann, wenn sie ein Ereignis empfängt, das als Trigger dient. Auf diese Weise stellt [!INCLUDE[wfd1](../includes/wfd1-md.md)] eine ereignisbasierte Ablaufsteuerungsmodellierung bereit. Jede <xref:System.Activities.Statements.PickBranch> enthält einen <xref:System.Activities.Statements.PickBranch.Trigger%2A> und eine <xref:System.Activities.Statements.PickBranch.Action%2A>. Am Anfang der Ausführung eines <xref:System.Activities.Statements.Pick>-Aktivität werden sämtliche Triggeraktivitäten der <xref:System.Activities.Statements.PickBranch>-Elemente geplant. Wenn die erste Aktivität abgeschlossen wird, wird die entsprechende Aktionsaktivität geplant, und alle anderen Triggeraktivitäten werden abgebrochen.

### <a name="how-to-use-the-pick-activity-designer"></a>So verwenden Sie den Pick-Aktivitätsdesigner
 Der **Pick** -Aktivitäts Designer befindet sich in der Kategorie **Ablauf Steuerung** der **Toolbox**, auf die Sie zugreifen können, indem Sie auf [!INCLUDE[wfd2](../includes/wfd2-md.md)] auf die Registerkarte **Toolbox** klicken (Sie können auch im Menü **Ansicht** den Befehl **Symbolleiste** auswählen oder STRG + ALT drücken). + X.)

 Der **Pick** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der [!INCLUDE[wfd2](../includes/wfd2-md.md)]-Oberfläche dort abgelegt werden, wo Aktivitäts Designer normalerweise platziert werden, z. b. innerhalb eines **Sequence** -Aktivitäts Designers. Nachdem er in [!INCLUDE[wfd2](../includes/wfd2-md.md)] abgelegt wurde, wird eine <xref:System.Activities.Statements.Pick>-Aktivität erstellt, die standardmäßig zwei leere <xref:System.Activities.Statements.PickBranch>-Aktivitäten als Elemente mit den Anzeigenamen von Branch1 und Branch2 enthält. Diese entsprechenden <xref:System.Activities.Statements.PickBranch.DisplayName%2A> Eigenschaftswerte können im Header des **PickBranch** -Aktivitäts Designers oder innerhalb des **Eigenschaften** Fensters für jede Verzweigung bearbeitet werden.

 Es gibt zwei Möglichkeiten, der Auflistung eines <xref:System.Activities.Statements.Pick> Objekts <xref:System.Activities.Statements.PickBranch> Aktivitäten hinzuzufügen: ziehen und Ablegen des **PickBranch** -Designers aus der **Toolbox** oder über das Kontextmenü in der **Pick** -Entwurfs Oberfläche. Weitere Informationen finden Sie im Thema [PickBranch](../workflow-designer/pickbranch-activity-designer.md) . Beachten Sie, dass das einzige Element, das in einem **Pick** -Aktivitäts Designer platziert werden kann, ein **PickBranch** -Aktivitäts Designer ist.

### <a name="pick-activity-properties-in-the-workflow-designer"></a>Eigenschaften für Pick-Aktivitäten im Workflow-Designer
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.Pick>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster oder auf der Designeroberfläche bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den benutzerfreundlichen Namen der <xref:System.Activities.Statements.Pick>Aktivität im Header an. Der Standardwert lautet Pick. Der Wert kann im Eigenschaftenraster oder direkt im Header des Aktivitätsdesigners bearbeitet werden.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|

## <a name="see-also"></a>Siehe auch
 [Ablaufsteuerungs](../workflow-designer/control-flow-activity-designers.md) - [Pick-Aktivität](https://msdn.microsoft.com/library/b3e49b7f-0285-4720-8c09-11ae18f0d53e) [mithilfe der Pick-Aktivität](https://msdn.microsoft.com/library/b89be812-a247-4025-b0e3-ffb20db027a6)
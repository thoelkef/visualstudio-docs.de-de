---
title: PickBranch-Aktivitäts Designer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.PickBranch.UI
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c7c70aa8282fb8f50ed6faca5bcee3177ef81e15
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672587"
---
# <a name="pickbranch-activity-designer"></a>PickBranch-Aktivitätsdesigner
Der <xref:System.Activities.Statements.PickBranch> stellt einen ereignisbasierten Ausführungspfad innerhalb einer <xref:System.Activities.Statements.Pick>-Aktivität bereit, der von einem eingehenden Ereignis ausgelöst werden kann.

## <a name="pickbranch"></a>PickBranch
 <xref:System.Activities.Statements.PickBranch>-Objekte sind in der <xref:System.Activities.Statements.Pick.Branches%2A>-Auflistung einer <xref:System.Activities.Statements.Pick>-Aktivität enthalten. Jede <xref:System.Activities.Statements.PickBranch> ist in einem Branch der <xref:System.Activities.Statements.Pick>-Aktivität enthalten und wird aufgrund eines eingehenden Ereignisses ausgeführt, das als Trigger dient. Auf diese Weise stellt [!INCLUDE[wfd1](../includes/wfd1-md.md)] ereignisbasierte Ablaufsteuerungsmodellierung bereit. Jede <xref:System.Activities.Statements.PickBranch> enthält einen <xref:System.Activities.Statements.PickBranch.Trigger%2A> und eine <xref:System.Activities.Statements.PickBranch.Action%2A>.

### <a name="how-to-use-the-pick-activity-designer"></a>So verwenden Sie den Pick-Aktivitätsdesigner
 Der **PickBranch** -Designer befindet sich in der Kategorie **Ablauf Steuerung** der **Toolbox**, auf die Sie zugreifen können, indem Sie auf [!INCLUDE[wfd2](../includes/wfd2-md.md)] auf die Registerkarte **Toolbox** klicken (Sie können auch im Menü **Ansicht** den Befehl **Symbolleiste** auswählen oder STRG + ALT + X).

 Standardmäßig werden zwei leere <xref:System.Activities.Statements.PickBranch> Objekte mit den anzeigen Amen **Branch1** und **Branch2** als Elemente einer <xref:System.Activities.Statements.Pick> Aktivität erstellt, wenn der **Pick** -Aktivitäts Designer anfänglich auf dem [!INCLUDE[wfd2](../includes/wfd2-md.md)] abgelegt wird. Diese entsprechenden <xref:System.Activities.Statements.PickBranch.DisplayName%2A> Eigenschaftswerte können im Header des **PickBranch** -Designers oder innerhalb des **Eigenschaften** Fensters für jede Verzweigung bearbeitet werden.

 Es gibt zwei Möglichkeiten, <xref:System.Activities.Statements.PickBranch> Objekte der-Auflistung eines <xref:System.Activities.Statements.Pick> Objekts hinzuzufügen: ziehen Sie den **PickBranch** -Designer aus der **Toolbox** , oder verwenden Sie das Kontextmenü in der **Pick** -Entwurfs Oberfläche, um Objekte hinzuzufügen:

1. Der **PickBranch** -Designer erstellt eine <xref:System.Activities.Statements.PickBranch>, wenn er aus der **Toolbox** gezogen und in einer der Verzweigungen eines **Pick** -Aktivitäts Designers auf der [!INCLUDE[wfd2](../includes/wfd2-md.md)] Oberfläche abgelegt wird. Die neuen <xref:System.Activities.Statements.PickBranch>-Objekte können im <xref:System.Activities.Statements.Pick>-Designer auf der linken oder rechten Seite jedes <xref:System.Activities.Statements.PickBranch>-Elements platziert werden, das bereits in der Auflistung enthalten ist. Wenn ein **PickBranch** -Designer mit der Maus auf den **Pick** -Designer gezogen wird, verwendet der **Pick** -Designer ein vertikales blaues graue Band, um anzugeben, wo die <xref:System.Activities.Statements.PickBranch> für eine bestimmte Maus Platzierung hinzugefügt wird.

2. Klicken Sie mit der rechten Maustaste auf **Pick** Activity Designer (jedoch nicht im **PickBranch** -Designer), um ein Kontextmenü zu erhalten, und wählen Sie **Branch erstellen** aus, um eine neue <xref:System.Activities.Statements.PickBranch> Beachten Sie, dass die neue <xref:System.Activities.Statements.PickBranch> rechts neben den vorhandenen <xref:System.Activities.Statements.PickBranch>-Objekten im **Pick** -Designer hinzugefügt wird.

   Der **PickBranch** -Designer kann erweitert werden, um die **Triggerfelder** und **Aktions** Felder anzuzeigen oder durch Klicken auf die doppelten Caretzeichen auf der rechten Seite Ihrer Header reduziert zu werden. Bearbeiten Sie die <xref:System.Activities.Statements.PickBranch.Trigger%2A> und <xref:System.Activities.Statements.PickBranch.Action%2A> jedes <xref:System.Activities.Statements.PickBranch>, indem Sie Aktivitäten in den **Triggern** und den **Aktions** Feldern ihrer Designer ablegen.

   Die <xref:System.Activities.Statements.PickBranch> Objekte in der <xref:System.Activities.Statements.Pick.Branches%2A> Auflistung eines <xref:System.Activities.Statements.Pick> Objekts können neu angeordnet werden, indem Sie per Drag & amp; Drop an einen neuen Speicherort im **Pick** -Designer abgelegt werden. Der **Pick** -Designer gibt mithilfe eines vertikalen blau grauen Bands an, wo der <xref:System.Activities.Statements.PickBranch> für eine bestimmte Maus Platzierung hinzugefügt wird.

   Es gibt zwei Möglichkeiten, ein <xref:System.Activities.Statements.PickBranch>-Objekt zu löschen:

3. Wählen Sie den **PickBranch** -Designer aus, und löschen Sie ihn.

4. Wählen Sie den **PickBranch** -Designer aus, klicken Sie mit der rechten Maustaste auf das Kontextmenü, und wählen Sie **Löschen**.

   Achten Sie darauf, den **PickBranch** -Designer auszuwählen. Wenn Sie eine der Aktivitäten in den **Triggern** oder **Aktions** Feldern versehentlich auswählen, wird eine dieser Aktivitäten und nicht das <xref:System.Activities.Statements.PickBranch> Objekt gelöscht.

### <a name="pickbranch-properties-in-the-workflow-designer"></a>PickBranch-Eigenschaften im Workflow-Designer
 In der folgenden Tabelle werden die nützlichsten Eigenschaften von <xref:System.Activities.Statements.PickBranch> aufgeführt, und es wird beschrieben, wie sie in [!INCLUDE[wfd2](../includes/wfd2-md.md)] verwendet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|False|Der Anzeige Name, der im Header des **PickBranch** -Designers angezeigt wird. Der Standardwert lautet Branch.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|True|Jedes <xref:System.Activities.Statements.PickBranch>-Objekt enthält eine <xref:System.Activities.Statements.PickBranch.Trigger%2A>-Aktion, die <xref:System.Activities.Statements.PickBranch.Action%2A> aufrufen kann.|
|<xref:System.Activities.Statements.PickBranch.Action%2A>|False|Jede <xref:System.Activities.Statements.PickBranch>-Objekt enthält eine <xref:System.Activities.Statements.PickBranch.Action%2A>, die ausgeführt wird, sobald sie ausgelöst wird.|

## <a name="see-also"></a>Siehe auch
 [Ablaufsteuerungs](../workflow-designer/control-flow-activity-designers.md) - [Pick-Aktivität](https://msdn.microsoft.com/library/b3e49b7f-0285-4720-8c09-11ae18f0d53e) [mithilfe der Pick-Aktivität](https://msdn.microsoft.com/library/b89be812-a247-4025-b0e3-ffb20db027a6)
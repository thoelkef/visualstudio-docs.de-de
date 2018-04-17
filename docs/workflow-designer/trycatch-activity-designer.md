---
title: TryCatch-Aktivitätsdesigner | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TryCatch.UI
- System.Activities.Statements.Catch`1.UI
ms.assetid: 02a326c2-4009-442f-b7cb-e42121fd2992
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9ae4cd4340bc30249ea649a2806afe3e027fc439
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="trycatch-activity-designer"></a>TryCatch-Aktivitätsdesigner
Die **TryCatch** Aktivitäts-Designer dient zum Erstellen und Konfigurieren einer <xref:System.Activities.Statements.TryCatch> Aktivität.

## <a name="the-trycatch-activity"></a>Die TryCatch-Aktivität
 Die <xref:System.Activities.Statements.TryCatch> Aktivität enthält einen <xref:System.Activities.Statements.TryCatch.Try%2A> Aktivität, eine Auflistung von **Catch\<TException >** und eine <xref:System.Activities.Statements.TryCatch.Finally%2A> Aktivität. Ein <xref:System.Activities.Statements.Catch%601> des Typs **TException** enthält ein <xref:System.Activities.Statements.Catch%601.ExceptionType%2A> und ein <xref:System.Activities.Statements.Catch%601.Action%2A>. Zusammen werden diese verwendet, um einen typischen ausnahmebasierten Fehlerbehandlungsmechanismus zu implementieren. Eine <xref:System.Activities.Statements.TryCatch>-Aktivität versucht, die zugehörige <xref:System.Activities.Statements.TryCatch.Try%2A>-Aktivität auszuführen. Wenn die <xref:System.Activities.Statements.TryCatch.Try%2A> Aktivität löst Ausnahme aus, die <xref:System.Activities.Statements.TryCatch> -Aktivität verwendet seine **Catch < TException\>**  -Auflistung, um die Ausnahme zu entsprechen. Wenn eine Übereinstimmung auftritt, wird das <xref:System.Activities.Statements.Catch%601.Action%2A> des entsprechenden **Catch\<TException >** ausgeführt und dient als Fehlerbehandlungslogik für die Ausnahme. Wenn die Aktivitäten im Abschnitt <xref:System.Activities.Statements.TryCatch.Try%2A> erfolgreich abgeschlossen werden oder die Aktivitäten in <xref:System.Activities.Statements.TryCatch.Catches%2A> erfolgreich abgeschlossen werden, führt die <xref:System.Activities.Statements.TryCatch>-Aktivität die zugehörige <xref:System.Activities.Statements.TryCatch.Finally%2A>-Aktivität aus. Weitere Informationen finden Sie unter [Ausnahmen der Windows-Workflow](/dotnet/framework/windows-workflow-foundation/exceptions).

### <a name="using-the-trycatch-activity-designer"></a>Verwenden des TryCatch-Aktivitätsdesigners
 Die **TryCatch** Aktivitäts-Designer finden Sie in der **Fehlerbehandlung** Kategorie der **Toolbox**, die erfolgt durch Klicken auf die **Toolbox** auf der linken Seite der Registerkarte die [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (Wählen Sie alternativ **Symbolleiste** aus der **Ansicht** Menüs oder STRG + ALT + X drücken.)

 Die **TryCatch** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** gezogen und auf die [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] -Oberfläche ablegen, wo Aktivitäten normalerweise platziert werden, z. B. in einem <xref:System.Activities.Statements.Sequence>. Hierdurch erstellen Sie eine <xref:System.Activities.Statements.TryCatch>-Aktivität mit dem <xref:System.Activities.Activity.DisplayName%2A>-Standardwert TryCatch. Die <xref:System.Activities.Activity.DisplayName%2A> Wert kann im Header des bearbeitet werden die **TryCatch** Aktivitäts-Designer oder in der **DisplayName** Feld des Eigenschaftenrasters. Die anderen Eigenschaften müssen auf der Oberfläche des bearbeitet werden die **TryCatch** Aktivitäts-Designer.

 Klicken Sie auf die Erweiterungsschaltfläche auf der rechten oberen Ecke des **TryCatch** -Designer finden Sie unter der **versuchen**, **fängt**, und **schließlich** Dialogfelder in der Erweiterte Ansicht. Um einen Catch hinzuzufügen, klicken Sie auf die **neuen Catch hinzufügen** Schaltfläche **TryCatch** Designer. Die Schaltfläche nimmt die Form eines Kombinationsfelds an. Wählen Sie einen Ausnahmetyp aus, und drücken Sie die EINGABETASTE, um den Catch hinzuzufügen. Nach dem Hinzufügen einer **Catch**, der Catch-Bereich erweitert und eine Aktivität kann Catch ablegen, die die Ausführungslogik für den Catch zu definieren. Auf der rechten Seite des erweiterten Catch-Bereichs befindet sich ein Textfeld. In dieses Textfeld können Sie den Namen einer Ausnahmevariablen eingeben. Die Ausnahmevariable kann nur verwendet werden, für die Aktivitäten im gleichen **Catch**.

 Die **TryCatch** Designer unterstützt keine Bearbeitung **Catch**. Wenn Sie den Ausnahmetyp ändern möchten, müssen Sie löschen die **Catch** und ein neues Konto hinzufügen. Ein **Catch** können gelöscht werden, durch auswählen und ihn löschen oder mithilfe der **löschen** Menü, in dem eingeblendeten Kontextmenü zugegriffen werden, indem Sie mit der rechten Maustaste auf.

### <a name="the-trycatch-properties"></a>Die TryCatch-Eigenschaften
 Die folgende Tabelle zeigt die <xref:System.Activities.Statements.TryCatch>Eigenschaften und es wird beschrieben, wie sie im Designer verwendet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den optionalen Anzeigenamen der <xref:System.Activities.Statements.TryCatch>-Aktivität an. Der Standardwert ist TryCatch.|
|<xref:System.Activities.Statements.TryCatch.Try%2A>|False|Die Aktivität wird erstmalig ausgeführt wird, wenn <xref:System.Activities.Statements.TryCatch> ausgeführt wird.|
|<xref:System.Activities.Statements.TryCatch.Catches%2A>|False|Die Auflistung der **Catch** Elemente, wenn überprüft werden soll die <xref:System.Activities.Statements.TryCatch.Try%2A> Aktivität löst eine Ausnahme aus.<br /><br /> Sie müssen mindestens eine Aktivität in der <xref:System.Activities.Statements.TryCatch.Catches%2A>-Auflistung oder eine Aktivität im <xref:System.Activities.Statements.TryCatch.Finally%2A>-Block hinzufügen.|
|<xref:System.Activities.Statements.TryCatch.Finally%2A>|False|Die Aktivität, die ausgeführt werden soll, wenn die Ausführung von <xref:System.Activities.Statements.TryCatch.Try%2A> und aller erforderlichen Aktivitäten in der <xref:System.Activities.Statements.TryCatch.Catches%2A>-Auflistung abgeschlossen wurde.<br /><br /> Sie müssen mindestens eine Aktivität in der <xref:System.Activities.Statements.TryCatch.Catches%2A>-Auflistung oder eine Aktivität im <xref:System.Activities.Statements.TryCatch.Finally%2A>-Block hinzufügen.|

## <a name="see-also"></a>Siehe auch

- [Auflistung](../workflow-designer/collection-activity-designers.md)
- [Rethrow](../workflow-designer/rethrow-activity-designer.md)
- [Throw](../workflow-designer/throw-activity-designer.md)
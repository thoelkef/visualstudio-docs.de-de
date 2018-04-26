---
title: Workflow-Designer - TransactionScope-Aktivitätsdesigner
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.TransactionScope.UI
ms.assetid: 8d7ebfc6-7478-4888-b3b0-b14f296096af
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 67c8a5c610492f298d3f2ef6de35444c96f7310f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="transactionscope-activity-designer"></a>TransactionScope-Aktivitätsdesigner

Die **TransactionScope** Aktivitäts-Designer dient zum Erstellen und Konfigurieren einer <xref:System.Activities.Statements.TransactionScope> Aktivität.

## <a name="the-transactionscope-activity"></a>Die TransactionScope-Aktivität
 Die <xref:System.Activities.Statements.TransactionScope>-Aktivität führt die in ihr enthaltene Aktivität in einer einzelnen Transaktion aus. Der Commit-Vorgang der Transaktion wird ausgeführt, sobald die <xref:System.Activities.Statements.TransactionScope.Body%2A>-Aktivität und alle anderen Teilnehmer der Transaktion erfolgreich abgeschlossen wurden.

### <a name="using-the-transactionscope-activity-designer"></a>Verwenden des TransactionScope-Aktivitätsdesigners
 Die **"TransactionScope"** Aktivitäts-Designer finden Sie in der **Transaktion** Kategorie der **Toolbox**, die erfolgt durch Klicken auf die **Toolbox**  des Workflow-Designers (Wählen Sie alternativ **Symbolleiste** aus der **Ansicht** Menüs oder STRG + ALT + X.)

 Die **"TransactionScope"** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** und sich der Workflow-Designer-Oberfläche gelöscht wird, wo Aktivitäten normalerweise platziert werden, z. B. in einem <xref:System.Activities.Statements.Sequence>. Daraufhin wird eine <xref:System.Activities.Statements.TransactionScope>-Aktivität mit dem <xref:System.Activities.Activity.DisplayName%2A>-Standardwert TransactionScope erstellt. Die <xref:System.Activities.Activity.DisplayName%2A> Wert kann im Header des bearbeitet werden die **TransactionScope** Aktivitäts-Designer oder in der **DisplayName** Feld des Eigenschaftenrasters.

### <a name="the-transactionscope-properties"></a>Die TransactionScope-Eigenschaften
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.TransactionScope>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Die <xref:System.Activities.Activity.DisplayName%2A> und <xref:System.Activities.Statements.TransactionScope.Body%2A> Eigenschaften können auf die Oberfläche des Workflow-Designer bearbeitet werden. Die anderen Eigenschaften müssen jedoch im Eigenschaftenraster bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der optionale Anzeigename der <xref:System.Activities.Statements.TransactionScope>-Aktivität. Der Standardwert lautet TransactionScope. Obwohl der <xref:System.Activities.Activity.DisplayName%2A>-Wert nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.TransactionScope.Body%2A>|True|Gibt die Aktivität an, die in einer einzelnen Transaktion ausgeführt werden soll. Hinzufügen der <xref:System.Activities.Statements.TransactionScope.Body%2A> Aktivität, indem Sie eine Aktivität aus der **Toolbox** in der **Text** Feld der **TransactionScope** Aktivitäts-Designer mit dem Hinweistext "Aktivität ablegen Hier".|
|<xref:System.Activities.Statements.TransactionScope.IsolationLevel%2A>|True|Gibt die <xref:System.Transactions.IsolationLevel>-Ebene für diesen <xref:System.Activities.Statements.TransactionScope>-Bereich an.|
|<xref:System.Activities.Statements.TransactionScope.Timeout%2A>|False|Gibt das Zeitintervall (im Format 00:00:00 für Stunden:Minuten:Sekunden) an, in dem die Transaktion abgeschlossen werden muss. Der Standardwert beträgt 1 Minute (00:01:00).|
|[System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure](https://msdn.microsoft.com/library/system.activities.statements.transactionscope.abortinstanceontransactionfailure.aspx)|True|Gibt den Wert an, der angibt, ob der Workflow abgebrochen werden soll, wenn die Transaktion abbricht.|

## <a name="see-also"></a>Siehe auch

- [Transaktion](../workflow-designer/transaction-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Kompensieren](../workflow-designer/compensate-activity-designer.md)
- [Vergewissern Sie sich](../workflow-designer/confirm-activity-designer.md)
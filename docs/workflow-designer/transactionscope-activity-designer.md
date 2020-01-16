---
title: Workflow-Designer-transaktionscope-Aktivitäts Designer
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TransactionScope.UI
ms.assetid: 8d7ebfc6-7478-4888-b3b0-b14f296096af
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eef35457b9f28864929ad42919fff4e9afdcb0d5
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114821"
---
# <a name="transactionscope-activity-designer"></a>TransactionScope-Aktivitätsdesigner

Der **transaktionscope** -Aktivitäts Designer wird verwendet, um eine <xref:System.Activities.Statements.TransactionScope>-Aktivität zu erstellen und zu konfigurieren.

## <a name="the-transactionscope-activity"></a>Die TransactionScope-Aktivität

Die <xref:System.Activities.Statements.TransactionScope>-Aktivität führt die in ihr enthaltene Aktivität in einer einzelnen Transaktion aus. Der Commit-Vorgang der Transaktion wird ausgeführt, sobald die <xref:System.Activities.Statements.TransactionScope.Body%2A>-Aktivität und alle anderen Teilnehmer der Transaktion erfolgreich abgeschlossen wurden.

### <a name="using-the-transactionscope-activity-designer"></a>Verwenden des TransactionScope-Aktivitätsdesigners

Greifen Sie in der Kategorie **Transaktion** der **Toolbox**auf den **transaktionscope** -Aktivitäts Designer zu. Der **transaktionscope** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der Workflow-Designer-Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden, z. b. innerhalb eines <xref:System.Activities.Statements.Sequence>. Daraufhin wird eine <xref:System.Activities.Statements.TransactionScope>-Aktivität mit dem <xref:System.Activities.Activity.DisplayName%2A>-Standardwert TransactionScope erstellt. Der <xref:System.Activities.Activity.DisplayName%2A> Wert kann im Header des **transaktionscope** -Aktivitäts Designers oder im Feld **Display Name** des Eigenschaften Rasters bearbeitet werden.

### <a name="the-transactionscope-properties"></a>Die TransactionScope-Eigenschaften

In der folgenden Tabelle werden die <xref:System.Activities.Statements.TransactionScope>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Die Eigenschaften <xref:System.Activities.Activity.DisplayName%2A> und <xref:System.Activities.Statements.TransactionScope.Body%2A> können auf Workflow-Designer-Oberfläche bearbeitet werden. Die anderen Eigenschaften müssen jedoch im Eigenschaftenraster bearbeitet werden.

|Eigenschaftsname|Erforderlich|Verwendungs-|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falsch|Der optionale Anzeigename der <xref:System.Activities.Statements.TransactionScope>-Aktivität. Der Standardwert lautet TransactionScope. Obwohl der <xref:System.Activities.Activity.DisplayName%2A>-Wert nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.TransactionScope.Body%2A>|True|Gibt die Aktivität an, die in einer einzelnen Transaktion ausgeführt werden soll. Um die <xref:System.Activities.Statements.TransactionScope.Body%2A>-Aktivität hinzuzufügen, legen Sie eine Aktivität aus der **Toolbox** in das Feld **Body** mit dem Hinweis Text "Aktivität hier ablegen" des **transaktionscope** -Aktivitäts Designers ab.|
|<xref:System.Activities.Statements.TransactionScope.IsolationLevel%2A>|True|Gibt die <xref:System.Transactions.IsolationLevel>-Ebene für diesen <xref:System.Activities.Statements.TransactionScope>-Bereich an.|
|<xref:System.Activities.Statements.TransactionScope.Timeout%2A>|Falsch|Gibt das Zeitintervall (im Format 00:00:00 für Stunden:Minuten:Sekunden) an, in dem die Transaktion abgeschlossen werden muss. Der Standardwert beträgt 1 Minute (00:01:00).|
|[System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure](https://msdn.microsoft.com/library/system.activities.statements.transactionscope.abortinstanceontransactionfailure.aspx)|True|Gibt den Wert an, der angibt, ob der Workflow abgebrochen werden soll, wenn die Transaktion abbricht.|

## <a name="see-also"></a>Siehe auch

- [Transaktion](../workflow-designer/transaction-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)

---
title: "TransactionScope-Aktivitätsdesigner | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.TransactionScope.UI
ms.assetid: 8d7ebfc6-7478-4888-b3b0-b14f296096af
caps.latest.revision: "8"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 9c9b9ab609825a68edc4e2862d64bdd7cb830202
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="transactionscope-activity-designer"></a>TransactionScope-Aktivitätsdesigner
Die **TransactionScope** Aktivitäts-Designer dient zum Erstellen und Konfigurieren einer <xref:System.Activities.Statements.TransactionScope> Aktivität.  
  
## <a name="the-transactionscope-activity"></a>Die TransactionScope-Aktivität  
 Die <xref:System.Activities.Statements.TransactionScope>-Aktivität führt die in ihr enthaltene Aktivität in einer einzelnen Transaktion aus. Der Commit-Vorgang der Transaktion wird ausgeführt, sobald die <xref:System.Activities.Statements.TransactionScope.Body%2A>-Aktivität und alle anderen Teilnehmer der Transaktion erfolgreich abgeschlossen wurden.  
  
### <a name="using-the-transactionscope-activity-designer"></a>Verwenden des TransactionScope-Aktivitätsdesigners  
 Die **"TransactionScope"** Aktivitäts-Designer finden Sie in der **Transaktion** Kategorie der **Toolbox**, die erfolgt durch Klicken auf die **Toolbox**  Registerkarte [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (Wählen Sie alternativ **Symbolleiste** aus der **Ansicht** Menüs oder STRG + ALT + X.)  
  
 Die **"TransactionScope"** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** gezogen und auf die [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] -Oberfläche ablegen, wo Aktivitäten normalerweise platziert werden, z. B. in einem <xref:System.Activities.Statements.Sequence>. Daraufhin wird eine <xref:System.Activities.Statements.TransactionScope>-Aktivität mit dem <xref:System.Activities.Activity.DisplayName%2A>-Standardwert TransactionScope erstellt. Die <xref:System.Activities.Activity.DisplayName%2A> Wert kann im Header des bearbeitet werden die **TransactionScope** Aktivitäts-Designer oder in der **DisplayName** Feld des Eigenschaftenrasters.  
  
### <a name="the-transactionscope-properties"></a>Die TransactionScope-Eigenschaften  
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.TransactionScope>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Die <xref:System.Activities.Activity.DisplayName%2A>-Eigenschaft und die <xref:System.Activities.Statements.TransactionScope.Body%2A>-Eigenschaft können in der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]-Oberfläche bearbeitet werden. Die anderen Eigenschaften müssen jedoch im Eigenschaftenraster bearbeitet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der optionale Anzeigename der <xref:System.Activities.Statements.TransactionScope>-Aktivität. Der Standardwert lautet TransactionScope. Obwohl der <xref:System.Activities.Activity.DisplayName%2A>-Wert nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|  
|<xref:System.Activities.Statements.TransactionScope.Body%2A>|True|Gibt die Aktivität an, die in einer einzelnen Transaktion ausgeführt werden soll. Hinzufügen der <xref:System.Activities.Statements.TransactionScope.Body%2A> Aktivität, indem Sie eine Aktivität aus der **Toolbox** in der **Text** Feld der **TransactionScope** Aktivitäts-Designer mit dem Hinweistext "Aktivität ablegen Hier".|  
|<xref:System.Activities.Statements.TransactionScope.IsolationLevel%2A>|True|Gibt die <xref:System.Transactions.IsolationLevel>-Ebene für diesen <xref:System.Activities.Statements.TransactionScope>-Bereich an.|  
|<xref:System.Activities.Statements.TransactionScope.Timeout%2A>|False|Gibt das Zeitintervall (im Format 00:00:00 für Stunden:Minuten:Sekunden) an, in dem die Transaktion abgeschlossen werden muss. Der Standardwert beträgt 1 Minute (00:01:00).|  
|[System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure](https://msdn.microsoft.com/library/system.activities.statements.transactionscope.abortinstanceontransactionfailure.aspx)|True|Gibt den Wert an, der angibt, ob der Workflow abgebrochen werden soll, wenn die Transaktion abbricht.|  
  
## <a name="see-also"></a>Siehe auch  
 [Transaktion](../workflow-designer/transaction-activity-designers.md)   
 [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [Kompensieren](../workflow-designer/compensate-activity-designer.md)   
 [Vergewissern Sie sich](../workflow-designer/confirm-activity-designer.md)
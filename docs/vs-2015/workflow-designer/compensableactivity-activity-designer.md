---
title: CompensableActivity-Aktivitätsdesigner | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CompensableActivity.UI
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 670d3e92b24e35979074df3817611ceff692f59d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49290445"
---
# <a name="compensableactivity-activity-designer"></a>CompensableActivity-Aktivitätsdesigner
Die **CompensableActivity** Aktivitäts-Designer dient zum Erstellen und Konfigurieren einer <xref:System.Activities.Statements.CompensableActivity> Aktivität.  
  
## <a name="the-compensableactivity-activity"></a>Die CompensableActivity-Aktivität  
 Die <xref:System.Activities.Statements.CompensableActivity> definiert eine Arbeitseinheit, die nach erfolgreichem Abschluss bestätigt oder kompensiert werden kann.  
  
### <a name="using-the-compensableactivity-activity-designer"></a>Verwenden des CompensableActivity-Aktivitätsdesigners  
 Die **CompensableActivity** Aktivitäts-Designer finden Sie in der **Transaktion** Kategorie der **Toolbox**, die erfolgt durch Klicken auf die **Toolbox**  auf der linken Seite der Registerkarte die [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Wählen Sie alternativ **Symbolleiste** aus der **Ansicht** Menü oder STRG + ALT + X.)  
  
 Die **CompensableActivity** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** und auf die [!INCLUDE[wfd2](../includes/wfd2-md.md)] -Oberfläche ganz egal, wo Aktivitäten normalerweise platziert werden, etwa innerhalb einer <xref:System.Activities.Statements.Sequence>. Dadurch wird eine <xref:System.Activities.Statements.CompensableActivity>-Aktivität mit dem standardmäßigen <xref:System.Activities.Activity.DisplayName%2A> CompensableActivity erstellt. Die <xref:System.Activities.Activity.DisplayName%2A> Wert kann im Header des bearbeitet werden die **CompensableActivity** Aktivitäts-Designer oder in der **"DisplayName"** Feld des Eigenschaftenrasters.  
  
### <a name="the-compensableactivity-properties"></a>Die CompensableActivity-Eigenschaften  
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.CompensableActivity>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Die Eigenschaften <xref:System.Activities.Activity.DisplayName%2A> und <xref:System.Activities.Activity%601.Result%2A> können im Eigenschaftenraster bearbeitet werden, die anderen Eigenschaften müssen jedoch auf der [!INCLUDE[wfd2](../includes/wfd2-md.md)]-Oberfläche bearbeitet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der optionale Anzeigename der <xref:System.Activities.Statements.CompensableActivity>-Aktivität. Der Standardwert lautet CompensableActivity.|  
|<xref:System.Activities.Activity%601.Result%2A>|False|Gibt den Rückgabewert der <xref:System.Activities.Statements.CompensableActivity> an. Diese Eigenschaft muss im Eigenschaftenraster bearbeitet werden.|  
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|True|Gibt die Aktivität an, für die Kompensations-, Abbruch- und Bestätigungslogik bereitgestellt wurde. Hinzufügen der <xref:System.Activities.Statements.CompensableActivity.Body%2A> -Aktivität, indem Sie eine Aktivität aus der **Toolbox** in die **Text** Feld der **CompensableActivity** Aktivitäts-Designer, mit dem Hinweistext "löschen Aktivität hier".|  
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|False|Gibt die Aktivität an, die im Fall eines Abbruchs ausgeführt wird. Fügen Sie die Aktivität hinzu, legen Sie ihren Designer aus der **Toolbox** in die **CancellationHandler** Feld der **CompensableActivity** Aktivitäts-Designer, mit dem Hinweistext "löschen Aktivität hier".|  
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|False|Gibt die Aktivität an, die beim Kompensieren der <xref:System.Activities.Statements.CompensableActivity.Body%2A>-Aktivität ausgeführt werden soll. Dieser Handler kann explizit mithilfe der <xref:System.Activities.Statements.Compensate>-Aktivität aufgerufen werden.<br /><br /> Fügen Sie die Aktivität hinzu, legen Sie ihren Aktivitätsdesigner aus der **Toolbox** in die **CompensationHandler** Feld der **CompensableActivity** Aktivitäts-Designer, mit dem Hinweistext " Aktivität hier ablegen".|  
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|False|Gibt die Aktivität an, die beim Bestätigen der <xref:System.Activities.Statements.CompensableActivity.Body%2A>-Aktivität ausgeführt werden soll. Dieser Handler kann explizit mithilfe der <xref:System.Activities.Statements.Confirm>-Aktivität aufgerufen werden.<br /><br /> Fügen Sie die Aktivität hinzu, legen Sie ihren Aktivitätsdesigner aus der **Toolbox** in die **ConfirmationHandler** Feld der **CompensableActivity** Aktivitäts-Designer, mit dem Hinweistext " Aktivität hier ablegen".|  
  
## <a name="see-also"></a>Siehe auch  
 [Transaktion](../workflow-designer/transaction-activity-designers.md)   
 [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)   
 [Kompensieren](../workflow-designer/compensate-activity-designer.md)   
 [Vergewissern Sie sich](../workflow-designer/confirm-activity-designer.md)   
 [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)
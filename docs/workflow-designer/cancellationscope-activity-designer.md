---
title: "CancellationScope-Aktivitätsdesigner | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
caps.latest.revision: "8"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4b2ad28e6b89273b5fdb55e4cfa35d1df292221a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="cancellationscope-activity-designer"></a>CancellationScope-Aktivitätsdesigner
Die **CancellationScope** Aktivitäts-Designer dient zum Erstellen und Konfigurieren einer <xref:System.Activities.Statements.CancellationScope> Aktivität.  
  
## <a name="the-cancellationscope-activity"></a>Die CancellationScope-Aktivität  
 Mit der <xref:System.Activities.Statements.CancellationScope>-Aktivität können Sie für eine Aktivität für die Ausführungs- und Abbruchlogik dieser Aktivität angeben.  
  
### <a name="using-the-cancellationscope-activity-designer"></a>Verwenden des CancellationScope-Aktivitätsdesigners  
 Die **CancellationScope** Aktivitäts-Designer finden Sie in der **Transaktion** Kategorie der **Toolbox**, die erfolgt durch Klicken auf die **Toolbox**  auf der Registerkarte die [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (Wählen Sie alternativ **Symbolleiste** aus der **Ansicht** Menüs oder STRG + ALT + X drücken.)  
  
 Die **CancellationScope** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** gezogen und auf die [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] -Oberfläche ablegen, wo Aktivitäten normalerweise platziert werden, z. B. in einem <xref:System.Activities.Statements.Sequence>. Dies erstellt eine <xref:System.Activities.Statements.CancellationScope>-Aktivität mit dem <xref:System.Activities.Activity.DisplayName%2A>-Standardwert CancellationScope. Die <xref:System.Activities.Activity.DisplayName%2A> Wert kann im Header des bearbeitet werden die **CancellationScope** Aktivitäts-Designer oder in der **DisplayName** Feld des Eigenschaftenrasters.  
  
### <a name="the-cancellationscope-properties"></a>Die CancellationScope-Eigenschaften  
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.CancellationScope>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Die <xref:System.Activities.Activity.DisplayName%2A>-Eigenschaften kann im Eigenschaftenraster bearbeitet werden, die anderen Eigenschaften müssen jedoch auf der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]-Oberfläche bearbeitet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der optionale Anzeigename der <xref:System.Activities.Statements.CancellationScope>-Aktivität. Der Standardwert lautet CancellationScope. Obwohl der <xref:System.Activities.Activity.DisplayName%2A>-Wert nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|  
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|True|Gibt die Aktivität an, für die Abbruchlogik bereitgestellt wird. Hinzufügen der <xref:System.Activities.Statements.CancellationScope.Body%2A> Aktivität, indem Sie eine Aktivität aus der **Toolbox** in der **Text** Feld der **CancellationScope** Aktivitäts-Designer mit dem Hinweistext "Ablage Aktivität hier".|  
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|True|Gibt die Aktivität an, die im Fall eines Abbruchs ausgeführt wird. Hinzufügen der <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> Aktivität, indem Sie eine Aktivität aus der **Toolbox** in der **CancellationHandler** Feld der **CancellationScope** Aktivitäts-Designer mit Hinweis der Text "Aktivität hier ablegen".|  
  
## <a name="see-also"></a>Siehe auch  
 [Transaktion](../workflow-designer/transaction-activity-designers.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [Kompensieren](../workflow-designer/compensate-activity-designer.md)   
 [Vergewissern Sie sich](../workflow-designer/confirm-activity-designer.md)   
 ["TransactionScope"](../workflow-designer/transactionscope-activity-designer.md)
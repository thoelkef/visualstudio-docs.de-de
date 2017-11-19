---
title: "TerminateWorkflow-Aktivitätsdesigner | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.TerminateWorkflow.UI
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
caps.latest.revision: "4"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0a3b7c7cf56aa465f88ae918056e2d71ad6c41e4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="terminateworkflow-activity-designer"></a>TerminateWorkflow-Aktivitätsdesigner
Die **TerminateWorkflow** Aktivitäts-Designer dient zum Erstellen und Konfigurieren einer <xref:System.Activities.Statements.TerminateWorkflow> Aktivität.  
  
## <a name="the-terminateworkflow-activity"></a>Die TerminateWorkflow-Aktivität  
 Mit der <xref:System.Activities.Statements.TerminateWorkflow>-Aktivität können Sie die Ausführung eines Workflows beenden.  
  
### <a name="using-the-terminateworkflow-activity-designer"></a>Verwenden des TerminateWorkflow-Aktivitätsdesigners  
 Die **TerminateWorkflow** Aktivitäts-Designer finden Sie in der **Runtime** Kategorie von der **Toolbox**, die erfolgt durch Klicken auf die **Toolbox** Registerkarte (Wählen Sie alternativ **Toolbox** aus der **Ansicht** Menüs oder STRG + ALT + X drücken.)  
  
 Die **TerminateWorkflow** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** gezogen und auf die [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] -Oberfläche ablegen, wo Aktivitäten normalerweise platziert werden, z. B. in einem <xref:System.Activities.Statements.Sequence>. Dies erstellt eine <xref:System.Activities.Statements.TerminateWorkflow> -Aktivität mit dem standardmäßigen **DisplayName** des TerminateWorkflow. Die <xref:System.Activities.Activity.DisplayName%2A> kann im Header des bearbeitet werden die **TerminateWorkflow** Aktivitäts-Designer oder in der **DisplayName** Feld des Eigenschaftenrasters.  
  
### <a name="the-terminateworkflow-properties"></a>Die TerminateWorkflow-Eigenschaften  
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.TerminateWorkflow>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster bearbeitet werden, einige davon können auch auf der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]-Oberfläche bearbeitet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der Anzeigename der <xref:System.Activities.Statements.TerminateWorkflow>-Aktivität. Der Standardwert ist TerminateWorkflow. Obwohl der Anzeigename nicht unbedingt erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|  
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|False|Die Ausnahme, die beim Beenden des Workflows ausgelöst werden soll. Legen Sie diese Eigenschaft im Eigenschaftenraster fest.|  
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|False|Die Ursache für das Beenden des Workflows. Legen Sie diese Eigenschaft im Eigenschaftenraster fest.|  
  
## <a name="see-also"></a>Siehe auch  
 [Common Language Runtime](../workflow-designer/runtime-activity-designers.md)   
 [Beibehalten](../workflow-designer/persist-activity-designer.md)
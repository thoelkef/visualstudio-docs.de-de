---
title: TerminateWorkflow-Aktivitätsdesigner | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TerminateWorkflow.UI
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: a00677390967f0cc0cff8a04b33895d7c88588f6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47516342"
---
# <a name="terminateworkflow-activity-designer"></a>TerminateWorkflow-Aktivitätsdesigner
Die **TerminateWorkflow** Aktivitäts-Designer dient zum Erstellen und Konfigurieren einer <xref:System.Activities.Statements.TerminateWorkflow> Aktivität.  
  
## <a name="the-terminateworkflow-activity"></a>Die TerminateWorkflow-Aktivität  
 Mit der <xref:System.Activities.Statements.TerminateWorkflow>-Aktivität können Sie die Ausführung eines Workflows beenden.  
  
### <a name="using-the-terminateworkflow-activity-designer"></a>Verwenden des TerminateWorkflow-Aktivitätsdesigners  
 Die **TerminateWorkflow** Aktivitäts-Designer finden Sie in der **Runtime** Kategorie der **Toolbox**, die erfolgt durch Klicken auf die **Toolbox** Registerkarte (Wählen Sie alternativ **Toolbox** aus der **Ansicht** Menü- oder STRG + ALT + X.)  
  
 Die **TerminateWorkflow** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** und auf die [!INCLUDE[wfd2](../includes/wfd2-md.md)] -Oberfläche ganz egal, wo Aktivitäten normalerweise platziert werden, etwa innerhalb einer <xref:System.Activities.Statements.Sequence>. Dies erstellt eine <xref:System.Activities.Statements.TerminateWorkflow> -Aktivität mit dem standardmäßigen **"DisplayName"** -Standardwert TerminateWorkflow. Die <xref:System.Activities.Activity.DisplayName%2A> kann im Header des bearbeitet werden die **TerminateWorkflow** Aktivitäts-Designer oder in der **"DisplayName"** Feld des Eigenschaftenrasters.  
  
### <a name="the-terminateworkflow-properties"></a>Die TerminateWorkflow-Eigenschaften  
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.TerminateWorkflow>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster bearbeitet werden, einige davon können auch auf der [!INCLUDE[wfd2](../includes/wfd2-md.md)]-Oberfläche bearbeitet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der Anzeigename der <xref:System.Activities.Statements.TerminateWorkflow>-Aktivität. Der Standardwert ist TerminateWorkflow. Obwohl der Anzeigename nicht unbedingt erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|  
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|False|Die Ausnahme, die beim Beenden des Workflows ausgelöst werden soll. Legen Sie diese Eigenschaft im Eigenschaftenraster fest.|  
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|False|Die Ursache für das Beenden des Workflows. Legen Sie diese Eigenschaft im Eigenschaftenraster fest.|  
  
## <a name="see-also"></a>Siehe auch  
 [Common Language Runtime](../workflow-designer/runtime-activity-designers.md)   
 [Persist](../workflow-designer/persist-activity-designer.md)
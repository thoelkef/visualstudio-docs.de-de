---
title: Persist-Aktivitätsdesigners | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Persist.UI
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 628082fc5130a17a14b273b4d1e35e962cc5e394
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49209299"
---
# <a name="persist-activity-designer"></a>Persist-Aktivitätsdesigners
Die **Persist** Aktivitäts-Designer dient zum Erstellen und Konfigurieren einer <xref:System.Activities.Statements.Persist> Aktivität.  
  
## <a name="the-persist-activity"></a>Die Persist-Aktivität  
 Wenn möglich, speichert die <xref:System.Activities.Statements.Persist>-Aktivität einen Workflow auf dem Datenträger. Die <xref:System.Activities.Statements.Persist>-Aktivität kann nicht in einem Bereich ohne Persistenz ausgeführt werden, z. B. innerhalb einer <xref:System.Activities.Statements.TransactionScope>-Aktivität. Wenn Sie eine <xref:System.Activities.Statements.Persist>-Aktivität in einem Bereich ohne Persistenz verwenden, wird zur Laufzeit eine Ausnahme ausgelöst.  
  
### <a name="using-the-persist-activity-designer"></a>Verwenden des Persist-Aktivitätsdesigners  
 Die **Persist** Aktivitäts-Designer finden Sie in der **Runtime** Kategorie der **Toolbox**, die erfolgt durch Klicken auf die **Toolbox** Registerkarte "(Wählen Sie alternativ **Toolbox** aus der **Ansicht** Menü- oder STRG + ALT + X.)  
  
 Die **Persist** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** und auf die [!INCLUDE[wfd2](../includes/wfd2-md.md)] -Oberfläche ganz egal, wo Aktivitäten normalerweise platziert werden, etwa innerhalb einer <xref:System.Activities.Statements.Sequence>. Dies erstellt eine <xref:System.Activities.Statements.Persist> -Aktivität mit dem standardmäßigen **"DisplayName"** -Standardwert Persist. Die <xref:System.Activities.Activity.DisplayName%2A> kann im Header des bearbeitet werden die **Persist** Aktivitäts-Designer oder in der **"DisplayName"** Feld des Eigenschaftenrasters.  
  
### <a name="the-persist-properties"></a>Die Persist-Eigenschaften  
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.Persist>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster bearbeitet werden, einige davon können auch auf der [!INCLUDE[wfd2](../includes/wfd2-md.md)]-Oberfläche bearbeitet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der Anzeigename der <xref:System.Activities.Statements.Persist>-Aktivität. Der Standardwert lautet Persist. Obwohl der Anzeigename nicht unbedingt erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|  
  
## <a name="see-also"></a>Siehe auch  
 [Common Language Runtime](../workflow-designer/runtime-activity-designers.md)   
 [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)
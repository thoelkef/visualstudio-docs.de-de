---
title: Verzögern der Aktivitäts-Designer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Delay.UI
ms.assetid: f51742a8-2c9a-47d1-8a23-18459d03ae19
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 012d5b9a9bb39221c5c9babdcf8010e28a24cb59
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47521253"
---
# <a name="delay-activity-designer"></a>Delay-Aktivitätsdesigner
Die **Verzögerung** Aktivitäts-Designer dient zum Erstellen und Konfigurieren einer <xref:System.Activities.Statements.Delay> Aktivität.  
  
## <a name="the-delay-activity"></a>Die Delay-Aktivität  
 Die <xref:System.Activities.Statements.Delay>-Aktivität verzögert die Ausführung eines Workflows während einer bestimmten Zeitspanne.  
  
### <a name="using-the-delay-activity-designer"></a>Verwenden des Delay-Aktivitätsdesigners  
 Die **Verzögerung** Aktivitäts-Designer finden Sie in der **primitive** Kategorie der **Toolbox**, die erfolgt durch Klicken auf die **Toolbox**Registerkarte die [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Wählen Sie alternativ **Symbolleiste** aus der **Ansicht** Menü oder STRG + ALT + X.)  
  
 Die **Verzögerung** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** und auf die [!INCLUDE[wfd2](../includes/wfd2-md.md)] -Oberfläche ganz egal, wo Aktivitäten normalerweise platziert werden, etwa innerhalb einer <xref:System.Activities.Statements.Sequence>. Dadurch wird eine <xref:System.Activities.Statements.Delay>-Aktivität mit dem standardmäßigen <xref:System.Activities.Activity.DisplayName%2A> Delay erstellt. Die <xref:System.Activities.Activity.DisplayName%2A> kann im Header des bearbeitet werden die **Verzögerung** Aktivitäts-Designer oder in der **"DisplayName"** Feld des Eigenschaftenrasters.  
  
### <a name="the-delay-properties"></a>Die Delay-Eigenschaften  
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.Delay>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster, einige davon auf der [!INCLUDE[wfd2](../includes/wfd2-md.md)]-Designeroberfläche bearbeitet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der Anzeigename der <xref:System.Activities.Statements.Delay>-Aktivität. Der Standardwert lautet Delay. Obwohl der <xref:System.Activities.Activity.DisplayName%2A>-Wert nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|  
|<xref:System.Activities.Statements.Delay.Duration%2A>|True|Die Zeitspanne, um die der Workflow verzögert werden soll. Diese Eigenschaft wird im Eigenschaftenraster festgelegt. Geben Sie in entweder einen literalen <xref:System.TimeSpan>-Wert im Format 00:00:00 oder einem Visual Basic-Ausdruck ein, um die Zeitspanne anzugeben.|  
  
## <a name="see-also"></a>Siehe auch  
 [Primitive Typen](../workflow-designer/primitives-activity-designers.md)   
 [Weisen Sie](../workflow-designer/assign-activity-designer.md)   
 [Delay-Aktivitätsdesigner](../workflow-designer/delay-activity-designer.md)   
 [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)   
 [WriteLine](../workflow-designer/writeline-activity-designer.md)
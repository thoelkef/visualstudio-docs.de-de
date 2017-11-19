---
title: InvokeDelegate | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- InvokeDelegate Designer
- System.Activities.Statements.InvokeDelegate.UI
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
caps.latest.revision: "3"
ms.author: sdanie
manager: erikre
ms.openlocfilehash: 180e9ca5ae635608ca3d7f9cf24abab13c8076a6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="invokedelegate"></a>InvokeDelegate
Die **InvokeDelegate** -Designer dient zum Erstellen und Konfigurieren einer <xref:System.Activities.Statements.InvokeDelegate> Aktivität.  
  
## <a name="the-invokedelegate-activity"></a>Die InvokeDelegate-Aktivität  
 <xref:System.Activities.Statements.InvokeDelegate> ruft einen öffentlichen Delegaten auf.  
  
### <a name="using-the-invokedelegate-activity-designer"></a>Verwenden des InvokeDelegate-Aktivitäts-Designers  
 Die **InvokeDelegate** Aktivitäts-Designer finden Sie in der **primitive** Kategorie der **Toolbox**, die erfolgt durch Klicken auf die **Toolbox** Registerkarte [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (Wählen Sie alternativ **Symbolleiste** aus der **Ansicht** Menüs oder STRG + ALT + X drücken.)  
  
 Die **InvokeDelegate** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** gezogen und auf die [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] -Oberfläche, wo Aktivitäten normalerweise platziert werden, etwa innerhalb einer <xref:System.Activities.Statements.Sequence>. Daraufhin wird eine <xref:System.Activities.Statements.InvokeDelegate>-Aktivität mit dem <xref:System.Activities.Activity.DisplayName%2A>-Standardwert InvokeDelegate erstellt. Die <xref:System.Activities.Activity.DisplayName%2A> kann im Header des bearbeitet werden die **InvokeDelegate** Aktivitäts-Designer oder in der **DisplayName** Feld des Eigenschaftenrasters.  
  
### <a name="the-invokedelegate-properties"></a>Die InvokeDelegate-Eigenschaften  
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.InvokeDelegate>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster bearbeitet werden, einige davon können auch in der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]-Designeroberfläche bearbeitet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der Anzeigename der <xref:System.Activities.Statements.InvokeDelegate>-Aktivität. Der Standardwert lautet InvokeDelegate.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|  
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|True|Der Name des <xref:System.Activities.ActivityDelegate>, der bei Ausführung der Aktivität aufgerufen werden soll. Diese Eigenschaft kann in der Designeroberfläche bearbeitet werden. Dies ist eine obligatorische Eigenschaft.|  
|<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|False|Die Argumentauflistung des aufgerufenen Delegaten. Die Schlüssel sind die Namen der Parameterobjekte, auf die <xref:System.Activities.ActivityDelegate> und die Werte sind die Argumente, deren Ausdrücke ausgewertet und die entsprechenden Parameterobjekte zugewiesen sind. Klicken Sie im Eigenschaftenraster auf die Schaltfläche mit den Auslassungspunkten, in der **DelegateArguments** -Feld der **DelegateArguments** Dialogfeld Sie diese Eigenschaft festlegen können. Klicken Sie auf die **Argument erstellen** ein, um die Argumente hinzuzufügen.|  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Definieren und Verarbeiten von Aktivitätsdelegaten im Workflow-Designer](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)
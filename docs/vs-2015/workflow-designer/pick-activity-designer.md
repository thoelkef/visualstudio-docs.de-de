---
title: Pick-Aktivitätsdesigner | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7de5d9189906d72c96372acb1a361d315f973df6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58961175"
---
# <a name="pick-activity-designer"></a>Pick-Aktivitätsdesigner
Die <xref:System.Activities.Statements.Pick>-Aktivität stellt eine ereignisbasierte Ablaufsteuerung bereit. Die Aktivität führt einen von mehreren Branches als Reaktion auf die Auslösung eines Ereignisses aus.  
  
## <a name="the-pick-activity"></a>Die Pick-Aktivität  
 Eine <xref:System.Activities.Statements.Pick>-Aktivität enthält eine Auflistung von <xref:System.Activities.Statements.PickBranch>-Objekten, von denen die <xref:System.Activities.Statements.Pick>-Aktivität eines ausführen kann, wenn sie ein Ereignis empfängt, das als Trigger dient. Auf diese Weise stellt [!INCLUDE[wfd1](../includes/wfd1-md.md)] eine ereignisbasierte Ablaufsteuerungsmodellierung bereit. Jede <xref:System.Activities.Statements.PickBranch> enthält einen <xref:System.Activities.Statements.PickBranch.Trigger%2A> und eine <xref:System.Activities.Statements.PickBranch.Action%2A>. Am Anfang der Ausführung eines <xref:System.Activities.Statements.Pick>-Aktivität werden sämtliche Triggeraktivitäten der <xref:System.Activities.Statements.PickBranch>-Elemente geplant. Wenn die erste Aktivität abgeschlossen wird, wird die entsprechende Aktionsaktivität geplant, und alle anderen Triggeraktivitäten werden abgebrochen.  
  
### <a name="how-to-use-the-pick-activity-designer"></a>So verwenden Sie den Pick-Aktivitätsdesigner  
 Die **auswählen** Aktivitäts-Designer finden Sie in der **Ablaufsteuerung** Kategorie der **Toolbox**, die erfolgt durch Klicken auf die **Toolbox**Registerkarte [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Wählen Sie alternativ **Symbolleiste** aus der **Ansicht** Menü- oder STRG + ALT + X.)  
  
 Die **auswählen** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** und auf die [!INCLUDE[wfd2](../includes/wfd2-md.md)] -Oberfläche ganz egal, wo Aktivitätsdesigner normalerweise platziert werden, z. B. innerhalb eines eine  **Sequenz** Aktivitäts-Designer. Nachdem er in [!INCLUDE[wfd2](../includes/wfd2-md.md)] abgelegt wurde, wird eine <xref:System.Activities.Statements.Pick>-Aktivität erstellt, die standardmäßig zwei leere <xref:System.Activities.Statements.PickBranch>-Aktivitäten als Elemente mit den Anzeigenamen von Branch1 und Branch2 enthält. Die jeweiligen <xref:System.Activities.Statements.PickBranch.DisplayName%2A> Eigenschaftswerte können bearbeitet werden, der **PickBranch** Aktivitäts-Designer-Header oder in der **Eigenschaften** für jeden Branch.  
  
 Es gibt zwei Möglichkeiten zum Hinzufügen von <xref:System.Activities.Statements.PickBranch> -Aktivitäten der Auflistung eine <xref:System.Activities.Statements.Pick> Objekt: Drag & Drop die **PickBranch** -Designer aus der **Toolbox** oder über das Kontextmenü in in der **auswählen** Entwurfsoberfläche. Weitere Informationen finden Sie unter den [PickBranch](../workflow-designer/pickbranch-activity-designer.md) Thema. Beachten Sie, dass als einziges Element platziert werden kann eine **auswählen** Aktivitäts-Designer eine **PickBranch** Aktivitäts-Designer.  
  
### <a name="pick-activity-properties-in-the-workflow-designer"></a>Eigenschaften für Pick-Aktivitäten im Workflow-Designer  
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.Pick>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster oder auf der Designeroberfläche bearbeitet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den benutzerfreundlichen Namen der <xref:System.Activities.Statements.Pick>Aktivität im Header an. Der Standardwert lautet Pick. Der Wert kann im Eigenschaftenraster oder direkt im Header des Aktivitätsdesigners bearbeitet werden.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|  
  
## <a name="see-also"></a>Siehe auch  
 [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)   
 [Auswählen der Aktivität](http://msdn.microsoft.com/library/b3e49b7f-0285-4720-8c09-11ae18f0d53e)   
 [Verwenden der Pick-Aktivität](http://msdn.microsoft.com/library/b89be812-a247-4025-b0e3-ffb20db027a6)
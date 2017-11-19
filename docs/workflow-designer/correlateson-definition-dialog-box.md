---
title: CorrelatesOn-Definition (Dialogfeld) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: babe684c0fd4eeec1a00e4f44868bfc0a67e5f9d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="correlateson-definition-dialog-box"></a>CorrelatesOn-Definition (Dialogfeld)
Die **CorrelatesOn** Dialogfeld werden in [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] so bearbeiten Sie die <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> Eigenschaft eine <xref:System.ServiceModel.Activities.Receive> Aktivität. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)]die [Receive](../workflow-designer/receive-activity-designer.md) Thema.  
  
 Die Korrelation zwischen <xref:System.ServiceModel.Activities.Receive>-Aktivitäten gibt an, in welcher Beziehung verschiedene Dienstvorgänge in einem Workflow miteinander stehen.  
  
 Die folgende Tabelle beschreibt die Elemente der Benutzeroberfläche (UI) von der **CorrelatesOn** (Dialogfeld).  
  
|Benutzeroberflächenelement|Beschreibung|  
|----------------|-----------------|  
|**CorrelatesWith**|Die <xref:System.ServiceModel.Activities.CorrelationHandle>-Instanz, die verwendet wird, um die Nachricht an die entsprechende Workflowinstanz weiterzuleiten.|  
|**XPath-Abfragen**|Ein Schlüssel-Wert-Paar, das die Abfragen enthält, mit denen Korrelationsdaten aus eingehenden Nachrichten extrahiert werden. Dies entspricht der <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>-Eigenschaft. Die XPath-Abfragen sind in einem <xref:System.ServiceModel.MessageQuerySet>-Objekt enthalten.|  
  
## <a name="to-launch-the-correlateson-dialog-box"></a>So öffnen Sie das Dialogfeld CorrelatesOn  
 Die **Receive** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** gezogen und auf die [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] -Oberfläche ablegen, wo Aktivitäten normalerweise platziert werden. Dadurch wird eine <xref:System.ServiceModel.Activities.Receive>-Aktivität mit dem standardmäßigen <xref:System.Activities.Activity.DisplayName%2A> Receive erstellt. Wählen Sie die **Receive** Aktivitäts-Designer, und klicken Sie auf die Schaltfläche mit den Auslassungspunkten neben dem (Collection) Text für die **CorrelatesOn** Eigenschaft im Eigenschaftenraster für die **CorrelatesOn-Definition**  Dialogfeld angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.ServiceModel.Activities.Receive>   
 [CorrelationInitializers Dialogfeld "hinzufügen"](../workflow-designer/add-correlationinitializers-dialog-box.md)   
 [Korrelation Dialogfeld "hinzufügen"](http://msdn.microsoft.com/en-us/9e41a149-e8ab-41b1-8886-ea06a63041b6)   
 [Korrelation initialisieren (Dialogfeld)](../workflow-designer/initialize-correlation-dialog-box.md)
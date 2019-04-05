---
title: CorrelatesOn-Definition (Dialogfeld) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: fd03e1a8615e75d3f00f79eb10b7a7ff97f0eb33
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "59001635"
---
# <a name="correlateson-definition-dialog-box"></a>CorrelatesOn-Definition (Dialogfeld)
Die **CorrelatesOn** Dialogfeld wird verwendet, [!INCLUDE[wfd1](../includes/wfd1-md.md)] so bearbeiten Sie die <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> Eigenschaft eine <xref:System.ServiceModel.Activities.Receive> Aktivität. [!INCLUDE[crdefault](../includes/crdefault-md.md)] die [Receive](../workflow-designer/receive-activity-designer.md) Thema.  
  
 Die Korrelation zwischen <xref:System.ServiceModel.Activities.Receive>-Aktivitäten gibt an, in welcher Beziehung verschiedene Dienstvorgänge in einem Workflow miteinander stehen.  
  
 Die folgende Tabelle beschreibt die Elemente der Benutzeroberfläche (UI) von der **CorrelatesOn** Dialogfeld.  
  
|Benutzeroberflächenelement|Beschreibung|  
|----------------|-----------------|  
|**CorrelatesWith**|Die <xref:System.ServiceModel.Activities.CorrelationHandle>-Instanz, die verwendet wird, um die Nachricht an die entsprechende Workflowinstanz weiterzuleiten.|  
|**XPath-Abfragen**|Ein Schlüssel-Wert-Paar, das die Abfragen enthält, mit denen Korrelationsdaten aus eingehenden Nachrichten extrahiert werden. Dies entspricht der <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>-Eigenschaft. Die XPath-Abfragen sind in einem <xref:System.ServiceModel.MessageQuerySet>-Objekt enthalten.|  
  
## <a name="to-launch-the-correlateson-dialog-box"></a>So öffnen Sie das Dialogfeld CorrelatesOn  
 Die **Receive** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** und auf die [!INCLUDE[wfd2](../includes/wfd2-md.md)] -Oberfläche ganz egal, wo Aktivitäten normalerweise platziert werden. Dadurch wird eine <xref:System.ServiceModel.Activities.Receive>-Aktivität mit dem standardmäßigen <xref:System.Activities.Activity.DisplayName%2A> Receive erstellt. Wählen Sie die **Receive** Aktivitäts-Designer, und klicken Sie auf die Schaltfläche mit den Auslassungspunkten neben dem (Collection) Text für die **CorrelatesOn** Eigenschaft im Eigenschaftenraster für das **CorrelatesOn-Definition**  Dialogfeld angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.ServiceModel.Activities.Receive>   
 [Dialogfeld "CorrelationInitializers" hinzufügen "](../workflow-designer/add-correlationinitializers-dialog-box.md)   
 [Korrelation initialisieren (Dialogfeld)](../workflow-designer/initialize-correlation-dialog-box.md)
---
title: CorrelatesOn-Definition (Dialogfeld) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 386d27e96ad1b3a04b9cdb8f76f96ee5e2ad6a46
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2018
---
# <a name="correlateson-definition-dialog-box"></a>CorrelatesOn-Definition (Dialogfeld)
Die **CorrelatesOn** wird im Dialogfeld zum Bearbeiten in Windows Workflow-Designer verwendet die <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> Eigenschaft eine <xref:System.ServiceModel.Activities.Receive> Aktivität. Weitere Informationen finden Sie unter der [Receive](../workflow-designer/receive-activity-designer.md) Thema.

 Die Korrelation zwischen <xref:System.ServiceModel.Activities.Receive>-Aktivitäten gibt an, in welcher Beziehung verschiedene Dienstvorgänge in einem Workflow miteinander stehen.

 Die folgende Tabelle beschreibt die Elemente der Benutzeroberfläche (UI) von der **CorrelatesOn** (Dialogfeld).

|Benutzeroberflächenelement|Beschreibung|
|----------------|-----------------|
|**CorrelatesWith**|Die <xref:System.ServiceModel.Activities.CorrelationHandle>-Instanz, die verwendet wird, um die Nachricht an die entsprechende Workflowinstanz weiterzuleiten.|
|**XPath-Abfragen**|Ein Schlüssel-Wert-Paar, das die Abfragen enthält, mit denen Korrelationsdaten aus eingehenden Nachrichten extrahiert werden. Dies entspricht der <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>-Eigenschaft. Die XPath-Abfragen sind in einem <xref:System.ServiceModel.MessageQuerySet>-Objekt enthalten.|

## <a name="to-launch-the-correlateson-dialog-box"></a>So öffnen Sie das Dialogfeld CorrelatesOn
 Die **Receive** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** gezogen und auf die [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] -Oberfläche ablegen, wo Aktivitäten normalerweise platziert werden. Dadurch wird eine <xref:System.ServiceModel.Activities.Receive>-Aktivität mit dem standardmäßigen <xref:System.Activities.Activity.DisplayName%2A> Receive erstellt. Wählen Sie die **Receive** Aktivitäts-Designer, und klicken Sie auf die Schaltfläche mit den Auslassungspunkten neben dem (Collection) Text für die **CorrelatesOn** Eigenschaft im Eigenschaftenraster für die **CorrelatesOn-Definition**  Dialogfeld angezeigt.

## <a name="see-also"></a>Siehe auch

- <xref:System.ServiceModel.Activities.Receive>
- [CorrelationInitializers hinzufügen (Dialogfeld)](../workflow-designer/add-correlationinitializers-dialog-box.md)
- [Korrelation Dialogfeld "hinzufügen"](http://msdn.microsoft.com/en-us/9e41a149-e8ab-41b1-8886-ea06a63041b6)
- [Korrelation initialisieren (Dialogfeld)](../workflow-designer/initialize-correlation-dialog-box.md)
---
title: CorrelatesOn-Definition (Dialog Feld) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e2a9a6f7ec6b8bf246ebfc03c166780b229e1aee
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656936"
---
# <a name="correlateson-definition-dialog-box"></a>CorrelatesOn-Definition (Dialogfeld)
Das Dialogfeld **CorrelatesOn** wird in [!INCLUDE[wfd1](../includes/wfd1-md.md)] verwendet, um die <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>-Eigenschaft einer <xref:System.ServiceModel.Activities.Receive>-Aktivität zu bearbeiten. [!INCLUDE[crdefault](../includes/crdefault-md.md)] das [Empfangs](../workflow-designer/receive-activity-designer.md) Thema.

 Die Korrelation zwischen <xref:System.ServiceModel.Activities.Receive>-Aktivitäten gibt an, in welcher Beziehung verschiedene Dienstvorgänge in einem Workflow miteinander stehen.

 In der folgenden Tabelle werden die Elemente der Benutzeroberfläche (UI) des Dialog Felds **CorrelatesOn** beschrieben.

|Benutzeroberflächenelement|Beschreibung|
|----------------|-----------------|
|**CorrelatesWith**|Die <xref:System.ServiceModel.Activities.CorrelationHandle>-Instanz, die verwendet wird, um die Nachricht an die entsprechende Workflowinstanz weiterzuleiten.|
|**XPath-Abfragen**|Ein Schlüssel-Wert-Paar, das die Abfragen enthält, mit denen Korrelationsdaten aus eingehenden Nachrichten extrahiert werden. Dies entspricht der <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>-Eigenschaft. Die XPath-Abfragen sind in einem <xref:System.ServiceModel.MessageQuerySet>-Objekt enthalten.|

## <a name="to-launch-the-correlateson-dialog-box"></a>So öffnen Sie das Dialogfeld CorrelatesOn
 Der **Receive** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der [!INCLUDE[wfd2](../includes/wfd2-md.md)]-Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden. Dadurch wird eine <xref:System.ServiceModel.Activities.Receive>-Aktivität mit dem standardmäßigen <xref:System.Activities.Activity.DisplayName%2A> Receive erstellt. Wählen Sie den **Receive** -Aktivitäts Designer aus, und klicken Sie auf die Schaltfläche mit den Auslassungs Punkten neben dem Text (Auflistung) für die **CorrelatesOn** -Eigenschaft im Eigenschaften Raster, damit das Dialogfeld **CorrelatesOn Definition** angezeigt wird.

## <a name="see-also"></a>Siehe auch
 Dialogfeld " [correlationinitializers hinzufügen](../workflow-designer/add-correlationinitializers-dialog-box.md) " <xref:System.ServiceModel.Activities.Receive> Dialog [Feld "Korrelation initialisieren](../workflow-designer/initialize-correlation-dialog-box.md) "
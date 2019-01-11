---
title: Workflow-Designer - CorrelatesOn-Definition (Dialogfeld)
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4bdc8dd059679c0ba1407585525d30a28dfd8440
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53988283"
---
# <a name="correlateson-definition-dialog-box"></a>CorrelatesOn-Definition (Dialogfeld)

Die **CorrelatesOn** wird das Dialogfeld zum Bearbeiten im Workflow-Designer verwendet die <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> Eigenschaft eine <xref:System.ServiceModel.Activities.Receive> Aktivität. Weitere Informationen finden Sie unter [Aktivitäts-Designer erhalten](../workflow-designer/receive-activity-designer.md).

Die Korrelation zwischen <xref:System.ServiceModel.Activities.Receive>-Aktivitäten gibt an, in welcher Beziehung verschiedene Dienstvorgänge in einem Workflow miteinander stehen.

Die folgende Tabelle beschreibt die Elemente der Benutzeroberfläche (UI) von der **CorrelatesOn** Dialogfeld.

|Benutzeroberflächenelement|Beschreibung|
|-|-----------------|
|**CorrelatesWith**|Die <xref:System.ServiceModel.Activities.CorrelationHandle>-Instanz, die verwendet wird, um die Nachricht an die entsprechende Workflowinstanz weiterzuleiten.|
|**XPath-Abfragen**|Ein Schlüssel-Wert-Paar, das die Abfragen enthält, mit denen Korrelationsdaten aus eingehenden Nachrichten extrahiert werden. Dieser Wert entspricht der <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> Eigenschaft. Die XPath-Abfragen sind in einem <xref:System.ServiceModel.MessageQuerySet>-Objekt enthalten.|

## <a name="to-launch-the-correlateson-dialog-box"></a>So öffnen Sie das Dialogfeld CorrelatesOn

Die **Receive** Aktivitäts-Designer gezogen werden kann, von **Toolbox** und sich der Workflow-Designer-Oberfläche gelöscht werden, wo Aktivitäten normalerweise platziert werden. Löschen die Aktivitäts-Designer erstellt eine <xref:System.ServiceModel.Activities.Receive> -Aktivität mit dem standardmäßigen <xref:System.Activities.Activity.DisplayName%2A> Receive. Zu öffnen der **CorrelatesOn-Definition** wählen Sie im Dialogfeld die **Receive** Aktivitäten, Designer, und klicken Sie dann im Eigenschaftenraster, wählen Sie Schaltfläche mit den Auslassungspunkten neben dem Text "Auflistung" für die  **CorrelatesOn** Eigenschaft.

## <a name="see-also"></a>Siehe auch

- <xref:System.ServiceModel.Activities.Receive>
- [CorrelationInitializers hinzufügen (Dialogfeld)](../workflow-designer/add-correlationinitializers-dialog-box.md)
- [Korrelations-Dialogfeld hinzufügen](http://msdn.microsoft.com/en-us/9e41a149-e8ab-41b1-8886-ea06a63041b6)
- [Korrelation initialisieren (Dialogfeld)](../workflow-designer/initialize-correlation-dialog-box.md)
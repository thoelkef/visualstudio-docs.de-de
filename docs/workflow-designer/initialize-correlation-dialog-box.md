---
title: Dialogfeld für die Korrelation initialisieren | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InitializeCorrelation.UI
ms.assetid: 2a0a1cd3-7b9e-493e-9264-fcf85289ffcf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aac62d4439c2280e977ef929c79bb103348c170a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="initialize-correlation-dialog-box"></a>Korrelation initialisieren (Dialogfeld)

Die **Korrelation initialisieren** wird im Dialogfeld zum Bearbeiten in Windows Workflow-Designer verwendet die <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> Eigenschaft ein <xref:System.ServiceModel.Activities.InitializeCorrelation> Aktivität. Weitere Informationen finden Sie unter der [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) Thema.

 Die folgende Tabelle beschreibt die Elemente der Benutzeroberfläche (UI) von der **Korrelation initialisieren** (Dialogfeld).

|Benutzeroberflächenelement|Beschreibung|
|----------------|-----------------|
|**Korrelation**|Das <xref:System.ServiceModel.Activities.CorrelationHandle>-Objekt der zu initialisierenden Korrelation.|
|**Initialisieren mit**|Ein Schlüssel-Wert-Paar, das die Daten zum Initialisieren enthält. Dies entspricht der <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>-Eigenschaft. Ein Beispiel für eine gültige Schlüssel-Wert-Paar wäre ein Schlüssel namens "OrderID" eine Variable mit dem Namen OrderID zugeordnet.|

## <a name="to-launch-the-initialize-correlation-dialog-box"></a>So starten Sie das Dialogfeld "Korrelation initialisieren"

-   Klicken Sie auf **Ansicht** auf die **InitializeCorrelation** -Aktivitätsdesigner oder wählen Sie ein <xref:System.ServiceModel.Activities.InitializeCorrelation> Aktivität in [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] , und klicken Sie dann auf die Schaltfläche mit den Auslassungszeichen neben der <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> Eigenschaft in das Eigenschaftenraster.

## <a name="see-also"></a>Siehe auch

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
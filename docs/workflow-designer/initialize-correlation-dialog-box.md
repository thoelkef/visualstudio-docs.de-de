---
title: Dialog Feld ' Korrelation Workflow-Designer initialisieren '
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InitializeCorrelation.UI
ms.assetid: 2a0a1cd3-7b9e-493e-9264-fcf85289ffcf
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d0b23f10184516ea4ffc3b00ac98e32ca8b387c1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650197"
---
# <a name="initialize-correlation-dialog-box"></a>Korrelation initialisieren (Dialogfeld)

Das Dialogfeld **Korrelation initialisieren** wird in Workflow-Designer verwendet, um die <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>-Eigenschaft einer <xref:System.ServiceModel.Activities.InitializeCorrelation>-Aktivität zu bearbeiten. Weitere Informationen finden Sie unter [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md).

In der folgenden Tabelle werden die Benutzeroberflächen Elemente des Dialog Felds " **Korrelation initialisieren** " beschrieben:

|Benutzeroberflächenelement|Beschreibung|
|-|-----------------|
|**Korrelation**|Das <xref:System.ServiceModel.Activities.CorrelationHandle>-Objekt der zu initialisierenden Korrelation.|
|**Initialisieren für**|Ein Schlüssel-Wert-Paar, das die Daten zum Initialisieren enthält. Dieser Wert entspricht der <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>-Eigenschaft. Ein Beispiel für ein gültiges Schlüssel-Wert-Paar ist ein Schlüssel mit dem Namen "OrderID", der mit einer Variablen namens OrderID gekoppelt ist.|

## <a name="to-launch-the-initialize-correlation-dialog-box"></a>So starten Sie das Dialogfeld "Korrelation initialisieren"

Klicken Sie im **InitializeCorrelation** -Aktivitäts Designer auf **Ansicht** , oder wählen Sie eine <xref:System.ServiceModel.Activities.InitializeCorrelation> Aktivität in Workflow-Designer aus. Klicken Sie dann auf die Schaltfläche mit den Auslassungs Punkten neben der <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>-Eigenschaft im Eigenschaften Raster.

## <a name="see-also"></a>Siehe auch

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
---
title: Workflow-Designer - Initialisierung Korrelation (Dialogfeld)
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- InitializeCorrelation.UI
ms.assetid: 2a0a1cd3-7b9e-493e-9264-fcf85289ffcf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: edfdef1c1f946e2c5f677d0ff1578a40ea7bcd8f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49906233"
---
# <a name="initialize-correlation-dialog-box"></a>Korrelation initialisieren (Dialogfeld)

Die **Korrelation initialisieren** wird das Dialogfeld zum Bearbeiten im Workflow-Designer verwendet die <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> Eigenschaft eine <xref:System.ServiceModel.Activities.InitializeCorrelation> Aktivität. Weitere Informationen finden Sie unter [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md).

Die folgende Tabelle beschreibt die Elemente der Benutzeroberfläche (UI) von der **Korrelation initialisieren** Dialogfeld:

|Benutzeroberflächenelement|Beschreibung|
|-|-----------------|
|**Korrelation**|Das <xref:System.ServiceModel.Activities.CorrelationHandle>-Objekt der zu initialisierenden Korrelation.|
|**Initialisiert auf**|Ein Schlüssel-Wert-Paar, das die Daten zum Initialisieren enthält. Dieser Wert entspricht der <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> Eigenschaft. Ein Beispiel für ein gültiges Schlüssel-Wert-Paar ist ein Schlüssel namens "OrderID" zusammen mit einer Variablen namens "OrderID".|

## <a name="to-launch-the-initialize-correlation-dialog-box"></a>So starten Sie das Dialogfeld "Korrelation initialisieren"

Klicken Sie auf **Ansicht** auf die **InitializeCorrelation** -Aktivitätsdesigner oder auf eine <xref:System.ServiceModel.Activities.InitializeCorrelation> Aktivität im Workflow-Designer. Klicken Sie dann ein, klicken Sie auf die Schaltfläche mit den Auslassungspunkten neben der <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> Eigenschaft im Eigenschaftenraster.

## <a name="see-also"></a>Siehe auch

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
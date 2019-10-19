---
title: Korrelation initialisieren (Dialog Feld) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- InitializeCorrelation.UI
ms.assetid: 2a0a1cd3-7b9e-493e-9264-fcf85289ffcf
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3ab913027a6a992494dad609b98ab11dbc6ae61c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659049"
---
# <a name="initialize-correlation-dialog-box"></a>Korrelation initialisieren (Dialogfeld)
Das Dialogfeld **Korrelation initialisieren** wird in [!INCLUDE[wfd1](../includes/wfd1-md.md)] verwendet, um die <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>-Eigenschaft einer <xref:System.ServiceModel.Activities.InitializeCorrelation>-Aktivität zu bearbeiten. [!INCLUDE[crdefault](../includes/crdefault-md.md)] des Themas [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) .

 In der folgenden Tabelle werden die Benutzeroberflächen Elemente des Dialog Felds **Korrelation initialisieren** beschrieben.

|Benutzeroberflächenelement|Beschreibung|
|----------------|-----------------|
|**Korrelation**|Das <xref:System.ServiceModel.Activities.CorrelationHandle>-Objekt der zu initialisierenden Korrelation.|
|**Initialisieren für**|Ein Schlüssel-Wert-Paar, das die Daten zum Initialisieren enthält. Dies entspricht der <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>-Eigenschaft. Ein Beispiel für ein gültiges Schlüssel-Wert-Paar wäre ein Schlüssel mit dem Namen von "OrderID", der einer Variablen mit dem Namen OrderID zugeordnet wurde.|

## <a name="to-launch-the-initialize-correlation-dialog-box"></a>So starten Sie das Dialogfeld "Korrelation initialisieren"

- Klicken Sie im **InitializeCorrelation** -Aktivitäts Designer auf **Ansicht** , oder wählen Sie eine <xref:System.ServiceModel.Activities.InitializeCorrelation> Aktivität in [!INCLUDE[wfd2](../includes/wfd2-md.md)] aus, und klicken Sie dann auf die Schaltfläche mit den Auslassungs Punkten neben der Eigenschaft <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> im Eigenschaften Raster.

## <a name="see-also"></a>Siehe auch
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
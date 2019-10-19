---
title: Debuggingoptionen (Legacy) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- branch stepping
- stepping, options in workflow debugging
- debugging, stepping options
- debugging workflows, stepping options
- instance stepping
ms.assetid: 3e9e3041-68c7-4f16-9bd6-da5e5144744b
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 443cbac0ea9d74c61f24d6714162ec08e2906a62
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656875"
---
# <a name="debug-stepping-options-legacy"></a>Optionen zum schrittweisen Debuggen (Vorgängerversion)
In diesem Thema wird beschrieben, wie [!INCLUDE[wf](../includes/wf-md.md)]-Anwendungen gedebuggt werden, die gleichzeitig ausgeführte Aktivitäten in der Vorgängerversion von [!INCLUDE[wfd1](../includes/wfd1-md.md)] aufweisen. Verwenden Sie die Vorgängerversion von [!INCLUDE[wfd2](../includes/wfd2-md.md)], wenn Sie entweder auf [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] oder [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] abzielen möchten.

 Wenn Sie Legacy Aktivitäten Debuggen, die gleichzeitig ausgeführt werden (z. b. **ParallelActivity** oder **ConditionedActivityGroup**), können Sie eine der beiden folgenden Optionen verwenden, um den Code schrittweise zu durchlaufen.

- **Verzweigung von Verzweigungen** Mit diesem Modus können Sie eine bestimmte Verzweigung einer zusammengesetzten Aktivität schrittweise durchlaufen und Debuggen, z. b. die **ParallelActivity** -Aktivität oder die **conditionalactivitygroup** -Aktivität. Wenn Sie diese Option zum Debuggen verwenden, bemerken Sie nicht, dass sich das Steuerungsverhalten ändert, weil andere Aktivitäten im Workflow gleichzeitig ausgeführt werden. Der Debugger durchläuft nur die Aktivitäten in de momentan ausgewähltem Branch schrittweise, während gleichzeitig ggf. andere Aktivitäten des Workflows ausgeführt werden. Beispielsweise werden standardmäßig die Verzweigung ganz links in einer **ParallelActivity** -Aktivität und die erste untergeordnete Aktivität einer **ConditionedActivityGroup** -Aktivität für die schrittweise Verwendung verwendet. Wenn der Benutzer eine andere Verzweigung oder untergeordnete Aktivität debuggen möchte, muss er in der jeweiligen Verzweigung bzw. untergeordneten Aktivität einen expliziten Haltepunkt einfügen. Der Branch wird weiter schrittweise durchlaufen, wenn der Haltepunkt ausgelöst wird.

- **Instanzschritt.** In diesem Modus können Sie gleichzeitig ausgeführte Aktivitäten des Workflows schrittweise durchlaufen und debuggen. Bei dieser Option ändert sich das Steuerungsverhalten, wenn im Workflow gleichzeitig ausgeführte Aktivitäten aktiv sind.

  Die Option zur schrittweisen Ausführung von Branches ist standardmäßig ausgewählt, und Benutzer können beim Debuggen eines Workflows der Vorgängerversion zwischen den beiden Optionen wechseln.

  Wählen Sie zum Debuggen von Zustandsautomatworkflows der Vorgängerversion die Option zum schrittweisen Ausführen von Instanzen aus.

## <a name="see-also"></a>Siehe auch
 [Debuggen von Legacy Workflows](../workflow-designer/debugging-legacy-workflows.md) Gewusst [wie: Ändern der Option zum schrittweise Debuggen](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)
---
title: "Optionen (Vorgängerversion) zum schrittweisen Debuggen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- branch stepping
- stepping, options in workflow debugging
- debugging, stepping options
- debugging workflows, stepping options
- instance stepping
ms.assetid: 3e9e3041-68c7-4f16-9bd6-da5e5144744b
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: fbdb0d481c0740310f40f6a75d8c84db765f847d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="debug-stepping-options-legacy"></a>Optionen zum schrittweisen Debuggen (Vorgängerversion)
In diesem Thema wird beschrieben, wie [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]-Anwendungen gedebuggt werden, die gleichzeitig ausgeführte Aktivitäten in der Vorgängerversion von [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] aufweisen. Verwenden Sie die Vorgängerversion von [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], wenn Sie entweder auf [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] oder [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] abzielen möchten.  
  
 Beim Debuggen von legacyaktivitäten, die gleichzeitig ausgeführt werden, z. B. auf **ParallelActivity** oder **ConditionedActivityGroup**, können Sie eine der beiden folgenden Optionen den Code schrittweise .  
  
-   **Verzweigungen Sie Schrittweises Ausführen von.** In diesem Modus können Sie schrittweise durchlaufen und Debuggen einen bestimmten Branch einer zusammengesetzten Aktivität, z. B. die **ParallelActivity** oder **ConditionalActivityGroup** Aktivität. Wenn Sie diese Option zum Debuggen verwenden, bemerken Sie nicht, dass sich das Steuerungsverhalten ändert, weil andere Aktivitäten im Workflow gleichzeitig ausgeführt werden. Der Debugger durchläuft nur die Aktivitäten in de momentan ausgewähltem Branch schrittweise, während gleichzeitig ggf. andere Aktivitäten des Workflows ausgeführt werden. Beispielsweise wird standardmäßig der Verzweigung ganz links in einer **ParallelActivity** Aktivität und die erste untergeordnete Aktivität eine **ConditionedActivityGroup** Aktivität für die schrittweise Ausführung verwendet werden. Wenn der Benutzer einen andere Branch oder eine untergeordnete Aktivität debuggen möchte, muss er in dem jeweiligen Branch bzw. der untergeordneten Aktivität einen expliziten Haltepunkt einfügen. Der Branch wird weiter schrittweise durchlaufen, wenn der Haltepunkt ausgelöst wird.  
  
-   **Instanzen Sie Schrittweises Ausführen von.** In diesem Modus können Sie gleichzeitig ausgeführte Aktivitäten des Workflows schrittweise durchlaufen und debuggen. Bei dieser Option ändert sich das Steuerungsverhalten, wenn im Workflow gleichzeitig ausgeführte Aktivitäten aktiv sind.  
  
 Die Option zur schrittweisen Ausführung von Verzweigungen ist standardmäßig ausgewählt, und Benutzer können beim Debuggen eines Workflows der Vorgängerversion zwischen den beiden Optionen wechseln.  
  
 Wählen Sie zum Debuggen von Zustandsautomatworkflows der Vorgängerversion die Option zum schrittweisen Ausführen von Instanzen aus.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von Legacyworkflows](../workflow-designer/debugging-legacy-workflows.md)   
 [Vorgehensweise: Ändern der Option zum schrittweisen Debuggen (Vorgängerversion)](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)
---
title: Workflow-Designer - Debug-Steppingoptionen (Vorgängerversion)
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- branch stepping
- stepping, options in workflow debugging
- debugging, stepping options
- debugging workflows, stepping options
- instance stepping
ms.assetid: 3e9e3041-68c7-4f16-9bd6-da5e5144744b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f46c0ab382a0e189c595e6e0f8aeb69c71814faf
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31969069"
---
# <a name="debug-stepping-options-legacy"></a>Optionen zum schrittweisen Debuggen (Vorgängerversion)

Dieses Thema beschreibt das Debuggen von Windows Workflow Foundation (WF)-Anwendungen, die gleichzeitig ausgeführte Aktivitäten in der älteren Windows-Workflow-Designer. Verwenden Sie die legacy-Workflow-Designer, wenn Sie .NET Framework, Version 3.5 oder die WinFX abzielen möchten.

Beim Debuggen von legacyaktivitäten, die gleichzeitig ausgeführt werden, z. B. auf **ParallelActivity** oder **ConditionedActivityGroup**, können Sie eine der beiden folgenden Optionen den Code schrittweise .

-   **Verzweigungen Sie Schrittweises Ausführen von.** In diesem Modus können Sie schrittweise durchlaufen und Debuggen einen bestimmten Branch einer zusammengesetzten Aktivität, z. B. die **ParallelActivity** oder **ConditionalActivityGroup** Aktivität. Wenn Sie diese Option zum Debuggen verwenden, bemerken Sie nicht, dass sich das Steuerungsverhalten ändert, weil andere Aktivitäten im Workflow gleichzeitig ausgeführt werden. Der Debugger durchläuft nur die Aktivitäten in de momentan ausgewähltem Branch schrittweise, während gleichzeitig ggf. andere Aktivitäten des Workflows ausgeführt werden. Beispielsweise wird standardmäßig der Verzweigung ganz links in einer **ParallelActivity** Aktivität und die erste untergeordnete Aktivität eine **ConditionedActivityGroup** Aktivität für die schrittweise Ausführung verwendet werden. Wenn der Benutzer einen andere Branch oder eine untergeordnete Aktivität debuggen möchte, muss er in dem jeweiligen Branch bzw. der untergeordneten Aktivität einen expliziten Haltepunkt einfügen. Der Branch wird weiter schrittweise durchlaufen, wenn der Haltepunkt ausgelöst wird.

-   **Instanzen Sie Schrittweises Ausführen von.** In diesem Modus können Sie gleichzeitig ausgeführte Aktivitäten des Workflows schrittweise durchlaufen und debuggen. Bei dieser Option ändert sich das Steuerungsverhalten, wenn im Workflow gleichzeitig ausgeführte Aktivitäten aktiv sind.

Die Option zur schrittweisen Ausführung von Verzweigungen ist standardmäßig ausgewählt, und Benutzer können beim Debuggen eines Workflows der Vorgängerversion zwischen den beiden Optionen wechseln.

Wählen Sie zum Debuggen von Zustandsautomatworkflows der Vorgängerversion die Option zum schrittweisen Ausführen von Instanzen aus.

## <a name="see-also"></a>Siehe auch

- [Debuggen von Legacyworkflows](../workflow-designer/debugging-legacy-workflows.md)
- [Vorgehensweise: Ändern der Option zum schrittweisen Debuggen (Vorgängerversion)](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)
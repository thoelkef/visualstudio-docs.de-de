---
title: 'Vorgehensweise: Debuggen von XAML mit dem Workflow-Designer | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: d9305dbc-af62-4bdd-b03f-c54e3fe9ecc7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- uwp
ms.openlocfilehash: 4d17d0a92bf3760e723bfa4ba26b45952634e7e2
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-debug-xaml-with-the-workflow-designer"></a>Vorgehensweise: Debuggen von XAML mit dem Workflow-Designer
Workflows werden in XAML definiert. In der Benutzeroberfläche werden Workflows in Form einer XAML-Struktur dargestellt, die den Workflow definiert. Das Debugverhalten ähnelt dem Debuggen von Workflows in Windows Workflow-Designer zur Verfügung. Während des Debuggens von XAML arbeiten beispielsweise die Fenster "Lokal", "Überwachen" und "Threads" genau wie während des [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]-Debuggens. Zusätzlich ist während des XAML-Debuggens die Aufruflistenansicht als zeilenbasierte hierarchische Ansicht des Ausführungsflusses für den Workflow verfügbar.

> [!NOTE]
> Wenn sich das XAML für einen Workflow in derselben Assembly wie die Aktivitäten befindet, wird der Assemblyteil der Klassennamen nicht eingeschlossen. Ohne diesen Teil der Klassen-(Aktivitäts-)namen kann das XAML zur Laufzeit nicht geladen werden. Es wird davon abgeraten, Aktivitäten in demselben Namespace wie das Hauptprojekt zu definieren; andernfalls muss das XAML manuell bearbeitet werden, nachdem es im Designer bearbeitet wurde.

### <a name="to-debug-workflow-xaml"></a>So debuggen Sie Workflow-XAML

1.  Öffnen Sie in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ein Workflow- oder ein Aktivitätsprojekt.

2.  Legen Sie einen Haltepunkt für die Aktivität oder Aktivitäten, die zu debuggende wie beschrieben in [Vorgehensweise: Festlegen von Haltepunkten in Workflows](../workflow-designer/how-to-set-breakpoints-in-workflows.md).

3.  Mit der rechten Maustaste in der XAML-Datei, die die Workflowdefinition, und wählen enthält **Code anzeigen**. Der Haltepunkt wird in der gleichen Zeile wie die XAML-Elementdeklaration der Aktivität angezeigt, für die Sie den Haltepunkt in der Entwurfsansicht festgelegt haben.

4.  Rufen Sie den Debugger aus, wie in beschrieben [Vorgehensweise: Aufrufen der Workflow-Debugger](../workflow-designer/how-to-invoke-the-workflow-debugger.md).

5.  Wenn die Codeausführung einen der Haltepunkte erreicht, wird das diesem Haltepunkt zugeordnete XAML-Element hervorgehoben dargestellt. Um zum nächsten Haltepunkt zu verschieben, verwenden die **F10** oder **F11** Schlüssel.

## <a name="see-also"></a>Siehe auch

- [Gewusst wie: Festlegen von Haltepunkten in Workflows](../workflow-designer/how-to-set-breakpoints-in-workflows.md)
- [Vorgehensweise: Aufrufen des Workflow-Debuggers](../workflow-designer/how-to-invoke-the-workflow-debugger.md)
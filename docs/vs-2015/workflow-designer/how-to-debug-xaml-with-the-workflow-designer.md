---
title: 'Gewusst wie: Debuggen von XAML mit dem Workflow-Designer | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: d9305dbc-af62-4bdd-b03f-c54e3fe9ecc7
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a696123551c24fd0d14fecde67826cf14f88826f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668647"
---
# <a name="how-to-debug-xaml-with-the-workflow-designer"></a>Vorgehensweise: Debuggen von XAML mit dem Workflow-Designer
Workflows werden in XAML definiert. In der Benutzeroberfläche werden Workflows in Form einer XAML-Struktur dargestellt, die den Workflow definiert. Der Debugprozess gestaltet sich ähnlich dem Debuggen von Workflows in [!INCLUDE[wfd1](../includes/wfd1-md.md)]. Während des Debuggens von XAML arbeiten beispielsweise die Fenster "Lokal", "Überwachen" und "Threads" genau wie während des [!INCLUDE[wfd2](../includes/wfd2-md.md)]-Debuggens. Zusätzlich ist während des XAML-Debuggens die Aufruflistenansicht als zeilenbasierte hierarchische Ansicht des Ausführungsflusses für den Workflow verfügbar.

> [!NOTE]
> Wenn sich das XAML für einen Workflow in derselben Assembly wie die Aktivitäten befindet, wird der Assemblyteil der Klassennamen nicht eingeschlossen. Ohne diesen Teil der Klassen-(Aktivitäts-)namen kann das XAML zur Laufzeit nicht geladen werden. Es wird davon abgeraten, Aktivitäten in demselben Namespace wie das Hauptprojekt zu definieren; andernfalls muss das XAML manuell bearbeitet werden, nachdem es im Designer bearbeitet wurde.

### <a name="to-debug-workflow-xaml"></a>So debuggen Sie Workflow-XAML

1. Öffnen Sie in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ein Workflow- oder ein Aktivitätsprojekt.

2. Legen Sie einen Haltepunkt für die Aktivität oder die Aktivitäten fest, die Sie debuggen möchten, wie unter Gewusst [wie: Festlegen von Breakpoints in Workflows](../workflow-designer/how-to-set-breakpoints-in-workflows.md)beschrieben.

3. Klicken Sie mit der rechten Maustaste auf die XAML-Datei, die die Workflow Definition enthält, und wählen Sie **Code anzeigen**aus. Der Haltepunkt wird in der gleichen Zeile wie die XAML-Elementdeklaration der Aktivität angezeigt, für die Sie den Haltepunkt in der Entwurfsansicht festgelegt haben.

4. Rufen Sie den Debugger auf, wie unter Gewusst [wie: Aufrufen des Workflow Debuggers](../workflow-designer/how-to-invoke-the-workflow-debugger.md)beschrieben.

5. Wenn die Codeausführung einen der Haltepunkte erreicht, wird das diesem Haltepunkt zugeordnete XAML-Element hervorgehoben dargestellt. Verwenden Sie die Taste **F10** oder **F11** , um zum nächsten Haltepunkt zu gelangen.

## <a name="see-also"></a>Siehe auch
 Gewusst [wie: Festlegen von Haltepunkten in Workflows](../workflow-designer/how-to-set-breakpoints-in-workflows.md) Gewusst [wie: Aufrufen des Workflow-Debuggers](../workflow-designer/how-to-invoke-the-workflow-debugger.md)
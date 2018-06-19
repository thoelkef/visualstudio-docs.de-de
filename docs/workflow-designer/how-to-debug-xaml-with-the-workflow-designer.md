---
title: 'Workflow-Designer - Vorgehensweise: Debuggen von XAML mit dem Workflow-Designer'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: d9305dbc-af62-4bdd-b03f-c54e3fe9ecc7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: eac6294861080614cbdd46e6ac1cc9a05d7124ff
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31969895"
---
# <a name="how-to-debug-xaml-with-the-workflow-designer"></a>Vorgehensweise: Debuggen von XAML mit dem Workflow-Designer

Workflows werden in XAML definiert. In der Benutzeroberfläche werden Workflows in Form einer XAML-Struktur dargestellt, die den Workflow definiert. Das Debugverhalten ähnelt dem Debuggen von Workflows in Windows Workflow-Designer zur Verfügung. Z. B. funktionieren während des Debuggens von XAML, die lokal, überwachen und Threads Windows die gleiche Weise wie im Workflow-Designer zu debuggen. Zusätzlich ist während des XAML-Debuggens die Aufruflistenansicht als zeilenbasierte hierarchische Ansicht des Ausführungsflusses für den Workflow verfügbar.

> [!NOTE]
> Wenn sich das XAML für einen Workflow in derselben Assembly wie die Aktivitäten befindet, wird der Assemblyteil der Klassennamen nicht eingeschlossen. Ohne diesen Teil der Klassen-(Aktivitäts-)namen kann das XAML zur Laufzeit nicht geladen werden. Es wird davon abgeraten, Aktivitäten in demselben Namespace wie das Hauptprojekt zu definieren; andernfalls muss das XAML manuell bearbeitet werden, nachdem es im Designer bearbeitet wurde.

## <a name="to-debug-workflow-xaml"></a>So debuggen Sie Workflow-XAML

1.  Öffnen Sie ein Workflow- oder aktivitätsprojektmappe-Projekt in Visual Studio.

2.  Legen Sie einen Haltepunkt für die Aktivität oder Aktivitäten, die zu debuggende wie beschrieben in [Vorgehensweise: Festlegen von Haltepunkten in Workflows](../workflow-designer/how-to-set-breakpoints-in-workflows.md).

3.  Mit der rechten Maustaste in der XAML-Datei, die die Workflowdefinition, und wählen enthält **Code anzeigen**. Der Haltepunkt wird in der gleichen Zeile wie die XAML-Elementdeklaration der Aktivität angezeigt, für die Sie den Haltepunkt in der Entwurfsansicht festgelegt haben.

4.  Rufen Sie den Debugger aus, wie in beschrieben [Vorgehensweise: Aufrufen der Workflow-Debugger](../workflow-designer/how-to-invoke-the-workflow-debugger.md).

5.  Wenn die Codeausführung einen der Haltepunkte erreicht, wird das diesem Haltepunkt zugeordnete XAML-Element hervorgehoben dargestellt. Um zum nächsten Haltepunkt zu verschieben, verwenden die **F10** oder **F11** Schlüssel.

## <a name="see-also"></a>Siehe auch

- [Gewusst wie: Festlegen von Haltepunkten in Workflows](../workflow-designer/how-to-set-breakpoints-in-workflows.md)
- [Vorgehensweise: Aufrufen des Workflow-Debuggers](../workflow-designer/how-to-invoke-the-workflow-debugger.md)
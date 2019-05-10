---
title: 'Workflow-Designer – Vorgehensweise: Debuggen von XAML mit dem Workflow-Designer'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d9305dbc-af62-4bdd-b03f-c54e3fe9ecc7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: cdbf5fa21c8fcf9069db9a7348d4ed576fc342c5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62949600"
---
# <a name="how-to-debug-xaml-with-the-workflow-designer"></a>Vorgehensweise: Debuggen von XAML mit dem Workflow-Designer

Workflows werden in XAML definiert. In der Benutzeroberfläche werden Workflows in Form einer XAML-Struktur dargestellt, die den Workflow definiert. Der Debugvorgang ähnelt dem Debuggen von Workflows im Workflow-Designer zur Verfügung. Beispielsweise funktionieren während des Debuggens von XAML, die lokal, überwachen und Threads Windows genauso wie in den Workflow-Designer zu debuggen. Zusätzlich ist während des XAML-Debuggens die Aufruflistenansicht als zeilenbasierte hierarchische Ansicht des Ausführungsflusses für den Workflow verfügbar.

> [!NOTE]
> Wenn sich das XAML für einen Workflow in derselben Assembly wie die Aktivitäten befindet, wird der Assemblyteil der Klassennamen nicht eingeschlossen. Ohne diesen Teil der Klassen-(Aktivitäts-)namen kann das XAML zur Laufzeit nicht geladen werden. Es wird davon abgeraten, Aktivitäten in demselben Namespace wie das Hauptprojekt zu definieren; andernfalls muss das XAML manuell bearbeitet werden, nachdem es im Designer bearbeitet wurde.

## <a name="to-debug-workflow-xaml"></a>So debuggen Sie Workflow-XAML

1. Öffnen Sie ein Workflow bzw. eine Aktivität-Projekt in Visual Studio.

2. Legen Sie einen Haltepunkt für die Aktivität oder Aktivitäten, die zu debuggende Siehe [Vorgehensweise: Festlegen von Haltepunkten in Workflows](../workflow-designer/how-to-set-breakpoints-in-workflows.md).

3. Mit der rechten Maustaste in der XAML-Datei mit der Workflowdefinition und wählen Sie **Ansichtscode**. Der Haltepunkt wird in der gleichen Zeile wie die XAML-Elementdeklaration der Aktivität angezeigt, für die Sie den Haltepunkt in der Entwurfsansicht festgelegt haben.

4. Aufrufen des Debuggers, siehe [Debuggen von Workflows](debugging-workflows-with-the-workflow-designer.md).

5. Wenn die Codeausführung einen der Haltepunkte erreicht, wird das diesem Haltepunkt zugeordnete XAML-Element hervorgehoben dargestellt. Um zum nächsten Haltepunkt zu verschieben, verwenden die **F10** oder **F11** Schlüssel.

## <a name="see-also"></a>Siehe auch

- [Vorgehensweise: Festlegen von Haltepunkten in Workflows](../workflow-designer/how-to-set-breakpoints-in-workflows.md)
- [Debuggen von workflows](debugging-workflows-with-the-workflow-designer.md)
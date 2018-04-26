---
title: 'Workflow-Designer - Vorgehensweise: Hinzufügen von Aktivitäten zur Toolbox (Vorgängerversion)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- Toolbox, adding activities
- activities, adding to Toolbox
ms.assetid: b66ea29c-120b-40ba-8a61-c1c8240850fa
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 99a8e1cef2ff5ddd526133355c608fa5218573d1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-add-activities-to-the-toolbox-legacy"></a>Vorgehensweise: Hinzufügen von Aktivitäten zur Toolbox (Vorgängerversion)

Beim Erstellen einer Workflowprojektmappe mit der älteren Windows-Workflow-Designer, die .NET Framework, Version 3.5 oder die WinFX abzielt, können benutzerdefinierte Aktivitäten hinzugefügt werden, dem Workflowprojekt und deren Designern platziert, der **Toolbox** für einfacher Zugriff. Sie können auch Aktivitäten direkt hinzufügen der **Toolbox** aus einer Dynamic Link Library (DLL).

## <a name="to-add-an-activity-to-the-toolbox-from-a-dll"></a>So fügen Sie eine Aktivität aus einer DLL zur Toolbox hinzu

1.  Mit der rechten Maustaste der toolboxfensteroberfläche unter **Windows Workflow**, und klicken Sie dann auf **Elemente auswählen**.

2.  In der **Toolboxelemente** (Dialogfeld), klicken Sie auf die **System.Activities-Komponenten** Registerkarte, und klicken Sie dann auf **Durchsuchen** in der unteren rechten Ecke des Fensters.

3.  Wählen Sie die DLL aus dem Verzeichnis, das die Implementierung der benutzerdefinierten Aktivität hinzufügen, enthält die **Toolbox**, und klicken Sie dann auf **öffnen**.

4.  Klicken Sie auf **OK** zum Hinzufügen der Aktivität zur Toolbox abzuschließen.

## <a name="see-also"></a>Siehe auch

- [Verwenden des Aktivitätsdesigners der Vorgängerversion](../workflow-designer/using-the-legacy-activity-designer.md)
- [Legacyworkflowaktivitäten](../workflow-designer/legacy-workflow-activities.md)
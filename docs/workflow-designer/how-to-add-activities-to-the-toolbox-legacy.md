---
title: 'Vorgehensweise: Hinzufügen von Aktivitäten zur Toolbox (Vorgängerversion) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Toolbox, adding activities
- activities, adding to Toolbox
ms.assetid: b66ea29c-120b-40ba-8a61-c1c8240850fa
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 779735cb1d163db9e7b05e2892d01a991a4a4c2c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-activities-to-the-toolbox-legacy"></a>Vorgehensweise: Hinzufügen von Aktivitäten zur Toolbox (Vorgängerversion)
Bei einer Workflowprojektmappe mit der älteren Windows-Workflow-Designer mit der Zielversion von der [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] oder [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)], benutzerdefinierte Aktivitäten können hinzugefügt werden, dem Workflowprojekt und deren Designern platziert, der **Toolbox** für einfacher Zugriff. Sie können auch Aktivitäten direkt hinzufügen der **Toolbox** aus einer Dynamic Link Library (DLL).

### <a name="to-add-an-activity-to-the-toolbox-from-a-dll"></a>So fügen Sie eine Aktivität aus einer DLL zur Toolbox hinzu

1.  Mit der rechten Maustaste der toolboxfensteroberfläche unter **Windows Workflow**, und klicken Sie dann auf **Elemente auswählen**.

2.  In der **Toolboxelemente** (Dialogfeld), klicken Sie auf die **System.Activities-Komponenten** Registerkarte, und klicken Sie dann auf **Durchsuchen** in der unteren rechten Ecke des Fensters.

3.  Wählen Sie die DLL aus dem Verzeichnis, das die Implementierung der benutzerdefinierten Aktivität hinzufügen, enthält die **Toolbox**, und klicken Sie dann auf **öffnen**.

4.  Klicken Sie auf **OK** zum Hinzufügen der Aktivität zur Toolbox abzuschließen.

## <a name="see-also"></a>Siehe auch

- [Verwenden des Aktivitätsdesigners der Vorgängerversion](../workflow-designer/using-the-legacy-activity-designer.md)
- [Legacyworkflowaktivitäten](../workflow-designer/legacy-workflow-activities.md)
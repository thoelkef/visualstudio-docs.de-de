---
title: 'Workflow-Designer - Vorgehensweise: Ändern Sie die Option zum schrittweisen Debuggen (Vorgängerversion)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- branch stepping
- debugging, stepping options
- debugging workflows, stepping options
- stepping, changing options
- instance stepping
ms.assetid: aedc06af-d58a-44d6-aee4-f397f1f923a0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 31047cedd4e8772b9ebab4ef238a8fe32bc07663
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-change-the-debug-stepping-option-legacy"></a>Vorgehensweise: Ändern der Option zum schrittweisen Debuggen (Vorgängerversion)

In diesem Thema wird beschrieben, wie so ändern Sie die Option für Windows Workflow Foundation (WF)-Anwendungen in älteren Windows Workflow-Designer, die über parallele Aktionen verfügen schrittweisen Debuggen wird. Verwenden Sie die legacy-Workflow-Designer, wenn Sie .NET Framework, Version 3.5 oder die WinFX abzielen möchten.

Beim Debuggen von legacyaktivitäten, die gleichzeitig ausgeführt werden, z. B. auf **ParallelActivity** oder **ConditionedActivityGroup**, können Sie eine der beiden Optionen den Code schrittweise.

Führen Sie die nachstehenden Schritte aus, um die Option zum schrittweisen Debuggen in Ihrem Legacyworkflowprojekt zu ändern.

## <a name="procedures"></a>Verfahren

### <a name="to-change-the-debug-stepping-option"></a>So ändern Sie die Option zum schrittweisen Debuggen

1.  Starten Sie Visual Studio.

2.  Öffnen Sie ein vorhandenes legacyworkflowprojekt, oder erstellen Sie ein neues Projekt, das gleichzeitig ausgeführte Aktivitäten und mit der Zielversion wurden, .NET Framework, Version 3.5 oder die WinFX.

3.  Auf der **Workflow** Menü im älteren Workflow-Designer, zeigen Sie auf **Debuggen**, und zeigen Sie dann auf **Steppingoptionen**.

4.  Wählen Sie entweder **Instanz** oder **Verzweigung**.

## <a name="see-also"></a>Siehe auch

- [Debuggen von Legacyworkflows](../workflow-designer/debugging-legacy-workflows.md)
- [Optionen zum schrittweisen Debuggen (Vorgängerversion)](../workflow-designer/debug-stepping-options-legacy.md)
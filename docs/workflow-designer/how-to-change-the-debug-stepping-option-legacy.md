---
title: "Vorgehensweise: Ändern Sie die Option zum schrittweisen Debuggen (Vorgängerversion) | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- branch stepping
- debugging, stepping options
- debugging workflows, stepping options
- stepping, changing options
- instance stepping
ms.assetid: aedc06af-d58a-44d6-aee4-f397f1f923a0
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: ea687b0a08aa4697ac9f7c7b0aca875af131a561
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-change-the-debug-stepping-option-legacy"></a>Vorgehensweise: Ändern der Option zum schrittweisen Debuggen (Vorgängerversion)
In diesem Thema wird beschrieben, wie so ändern Sie die Option zum schrittweisen Debuggen [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] Anwendungen in älteren Windows Workflow-Designer, die über parallele Aktionen verfügen. Verwenden Sie die Vorgängerversion von [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], wenn Sie entweder auf [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] oder [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] abzielen möchten.

 Beim Debuggen von legacyaktivitäten, die gleichzeitig ausgeführt werden, z. B. auf **ParallelActivity** oder **ConditionedActivityGroup**, können Sie eine der beiden Optionen den Code schrittweise.

 Führen Sie die nachstehenden Schritte aus, um die Option zum schrittweisen Debuggen in Ihrem Legacyworkflowprojekt zu ändern.

## <a name="procedures"></a>Verfahren

#### <a name="to-change-the-debug-stepping-option"></a>So ändern Sie die Option zum schrittweisen Debuggen

1.  Starten Sie Visual Studio.

2.  Öffnen Sie ein vorhandenes Legacyworkflowprojekt, oder erstellen Sie ein neues Projekt, das gleichzeitige Aktivitäten verwendet und auf [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] oder [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] abzielt.

3.  Auf der **Workflow** Menü in der Vorgängerversion [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], zeigen Sie auf **Debuggen**, und zeigen Sie dann auf **Steppingoptionen**.

4.  Wählen Sie entweder **Instanz** oder **Verzweigung**.

## <a name="see-also"></a>Siehe auch

- [Debuggen von Legacyworkflows](../workflow-designer/debugging-legacy-workflows.md)
- [Optionen zum schrittweisen Debuggen (Vorgängerversion)](../workflow-designer/debug-stepping-options-legacy.md)
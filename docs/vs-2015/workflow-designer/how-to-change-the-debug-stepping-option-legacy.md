---
title: 'Vorgehensweise: Ändern der Option zum schrittweise Debuggen (Legacy) | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- branch stepping
- debugging, stepping options
- debugging workflows, stepping options
- stepping, changing options
- instance stepping
ms.assetid: aedc06af-d58a-44d6-aee4-f397f1f923a0
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5126b3dc45d33471080ae154e06f4a327e21fef7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663435"
---
# <a name="how-to-change-the-debug-stepping-option-legacy"></a>Vorgehensweise: Ändern der Option zum schrittweisen Debuggen (Vorgängerversion)
In diesem Thema wird beschrieben, wie die Option zum schrittweisen Debuggen für [!INCLUDE[wf](../includes/wf-md.md)]-Anwendungen in der Vorgängerversion von [!INCLUDE[wfd1](../includes/wfd1-md.md)] ausgeführt wird, die über parallele Aktionen verfügen. Verwenden Sie die Vorgängerversion von [!INCLUDE[wfd2](../includes/wfd2-md.md)], wenn Sie entweder auf [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] oder [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] abzielen möchten.

 Wenn Sie Legacy Aktivitäten Debuggen, die gleichzeitig ausgeführt werden (z. b. **ParallelActivity** oder **ConditionedActivityGroup**), können Sie eine von zwei Optionen verwenden, um den Code schrittweise zu durchlaufen.

 Führen Sie die nachstehenden Schritte aus, um die Option zum schrittweisen Debuggen in Ihrem Legacyworkflowprojekt zu ändern.

## <a name="procedures"></a>Prozeduren

#### <a name="to-change-the-debug-stepping-option"></a>So ändern Sie die Option zum schrittweisen Debuggen

1. Starten Sie Visual Studio.

2. Öffnen Sie ein vorhandenes Legacyworkflowprojekt, oder erstellen Sie ein neues Projekt, das gleichzeitige Aktivitäten verwendet und auf [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] oder [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] abzielt.

3. Zeigen Sie im Menü **Workflow** in der Vorgängerversion auf [!INCLUDE[wfd2](../includes/wfd2-md.md)] **Debuggen**, und zeigen Sie dann auf Schritt-für- **Schritt-Optionen**.

4. Wählen Sie entweder **Instanz** oder **Branch**aus.

## <a name="see-also"></a>Weitere Informationen
 [Debuggen von Legacy Workflows](../workflow-designer/debugging-legacy-workflows.md) [Debug-Schritt Optionen (Legacy)](../workflow-designer/debug-stepping-options-legacy.md)
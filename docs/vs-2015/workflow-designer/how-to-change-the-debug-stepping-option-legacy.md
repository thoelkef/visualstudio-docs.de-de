---
title: 'Vorgehensweise: Ändern Sie die Option zum schrittweisen Debuggen (Vorgängerversion) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- branch stepping
- debugging, stepping options
- debugging workflows, stepping options
- stepping, changing options
- instance stepping
ms.assetid: aedc06af-d58a-44d6-aee4-f397f1f923a0
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: b89ad55fec7b15884acefd5607cfd863a45564b3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49179236"
---
# <a name="how-to-change-the-debug-stepping-option-legacy"></a>Vorgehensweise: Ändern der Option zum schrittweisen Debuggen (Vorgängerversion)
In diesem Thema wird beschrieben, wie die Option zum schrittweisen Debuggen für [!INCLUDE[wf](../includes/wf-md.md)]-Anwendungen in der Vorgängerversion von [!INCLUDE[wfd1](../includes/wfd1-md.md)] ausgeführt wird, die über parallele Aktionen verfügen. Verwenden Sie die Vorgängerversion von [!INCLUDE[wfd2](../includes/wfd2-md.md)], wenn Sie entweder auf [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] oder [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] abzielen möchten.  
  
 Beim Debuggen von legacyaktivitäten, die gleichzeitig ausgeführt werden, z. B. auf **ParallelActivity** oder **ConditionedActivityGroup**, können Sie eine der beiden Optionen den Code schrittweise.  
  
 Führen Sie die nachstehenden Schritte aus, um die Option zum schrittweisen Debuggen in Ihrem Legacyworkflowprojekt zu ändern.  
  
## <a name="procedures"></a>Verfahren  
  
#### <a name="to-change-the-debug-stepping-option"></a>So ändern Sie die Option zum schrittweisen Debuggen  
  
1.  Starten Sie Visual Studio.  
  
2.  Öffnen Sie ein vorhandenes Legacyworkflowprojekt, oder erstellen Sie ein neues Projekt, das gleichzeitige Aktivitäten verwendet und auf [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] oder [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] abzielt.  
  
3.  Auf der **Workflow** Menü in der Vorgängerversion [!INCLUDE[wfd2](../includes/wfd2-md.md)], zeigen Sie auf **Debuggen**, und zeigen Sie dann auf **Steppingoptionen**.  
  
4.  Wählen Sie entweder **Instanz** oder **Branch**.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von Legacyworkflows](../workflow-designer/debugging-legacy-workflows.md)   
 [Optionen zum schrittweisen Debuggen (Vorgängerversion)](../workflow-designer/debug-stepping-options-legacy.md)
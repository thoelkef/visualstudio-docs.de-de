---
title: 'Vorgehensweise: Hinzufügen von Aktivitäten zur Toolbox (Vorgängerversion) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Toolbox, adding activities
- activities, adding to Toolbox
ms.assetid: b66ea29c-120b-40ba-8a61-c1c8240850fa
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 0fafcc260f451c4ead24d7a9dbb72a4db22c0b79
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49249365"
---
# <a name="how-to-add-activities-to-the-toolbox-legacy"></a>Vorgehensweise: Hinzufügen von Aktivitäten zur Toolbox (Vorgängerversion)
Beim Erstellen einer Workflowprojektmappe mit der Vorgängerversion [!INCLUDE[wfd1](../includes/wfd1-md.md)] , das als Ziel der [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] oder [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)], benutzerdefinierte Aktivitäten können dem Workflowprojekt hinzugefügt werden und deren Designer platziert wird, der **Toolbox** für einfache Zugriff. Sie können auch Aktivitäten direkt hinzufügen der **Toolbox** aus einer Dynamic Link Library (DLL).  
  
### <a name="to-add-an-activity-to-the-toolbox-from-a-dll"></a>So fügen Sie eine Aktivität aus einer DLL zur Toolbox hinzu  
  
1.  Mit der rechten Maustaste der toolboxfensteroberfläche unter **Windows Workflow**, und klicken Sie dann auf **Elemente auswählen**.  
  
2.  In der **Toolboxelemente auswählen** Dialogfeld klicken Sie auf die **System.Activities-Komponenten** Registerkarte, und klicken Sie dann auf **Durchsuchen** von der unteren rechten Seite des Fensters.  
  
3.  Wählen Sie die DLL aus dem Verzeichnis, das die Implementierung der benutzerdefinierten Aktivität hinzufügen, enthält die **Toolbox**, und klicken Sie dann auf **öffnen**.  
  
4.  Klicken Sie auf **OK** zum Hinzufügen der Aktivität zur Toolbox abzuschließen.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden des Aktivitätsdesigners der Vorgängerversion](../workflow-designer/using-the-legacy-activity-designer.md)   
 [Legacyworkflowaktivitäten](../workflow-designer/legacy-workflow-activities.md)
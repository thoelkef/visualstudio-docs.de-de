---
title: Debuggen von Workflows von einem Remote Computer aus (Legacy) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, debugging remotely
- debugging workflows, remotely
- remote debugging, workflows
- debugging, remote
ms.assetid: 44eaec8f-9959-4ae7-a374-670946f933c1
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bce98714832042471145bcf7d908a62b15bdb144
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656849"
---
# <a name="debugging-workflows-from-a-remote-computer-legacy"></a>Debuggen von Workflows von einem Remotecomputer (Vorgängerversion)
In diesem Thema wird das Debuggen von [!INCLUDE[wf](../includes/wf-md.md)]-Anwendungen der Vorgängerversion beschrieben, die mit der Vorgängerversion von [!INCLUDE[wfd1](../includes/wfd1-md.md)] erstellt werden. Verwenden Sie die Vorgängerversion von [!INCLUDE[wfd2](../includes/wfd2-md.md)] verwenden, wenn die Anwendung auf [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] oder [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] abzielen muss.

 Wenn Sie [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] installieren, besteht eine der Komponenten Installationsoptionen darin, den [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] Debugger für [!INCLUDE[wf](../includes/wf-md.md)] zu installieren. Hiermit werden die Komponenten zum Remotedebuggen installiert. Diese Komponenten für Remotedebugging müssen auf dem Computer installiert werden, auf dem Remoteworkflow-Debuggen ausgeführt werden soll.

 Zusätzlich muss die Assembly, die die Workflowdefinition des Legacyworkflows enthält, den Sie auf einem Remotecomputer debuggen, im globalen Assemblycache (GAC) des lokalen Computers installiert sein, von dem Sie debuggen. Wird beispielsweise ein Legacyworkflow auf einem Remotecomputer A ausgeführt und debuggen Sie diesen vom lokalen Computer B, muss die Workflowdefinition im GAC von Computer B vorhanden sein. Hiermit wird der Designer für die Deserialisierung und die Anzeige des Workflowmarkups des remote auf Computer A ausgeführten Workflows auf Computer B aktiviert. Weitere Informationen zum globalen Assemblycache finden Sie unter der MSDN Library.

 Das Remotedebugging in [!INCLUDE[wf2](../includes/wf2-md.md)] funktioniert genauso wie das Remotedebugging for andere [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Komponenten. Weitere Informationen finden Sie unter [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] Remote Debuggen in der MSDN Library.

## <a name="see-also"></a>Siehe auch
 [Debuggen von Legacyworkflows](../workflow-designer/debugging-legacy-workflows.md)
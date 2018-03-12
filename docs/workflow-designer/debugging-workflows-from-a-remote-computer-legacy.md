---
title: "Debuggen von Workflows von einem Remotecomputer (Vorgängerversion) | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- workflows, debugging remotely
- debugging workflows, remotely
- remote debugging, workflows
- debugging, remote
ms.assetid: 44eaec8f-9959-4ae7-a374-670946f933c1
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: be8c1f6a049224cc5b79a82dc6bc100840c72fd0
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2018
---
# <a name="debugging-workflows-from-a-remote-computer-legacy"></a>Debuggen von Workflows von einem Remotecomputer (Vorgängerversion)
In diesem Thema wird beschrieben, wie Debuggen Vorgängerversion [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] Anwendungen, die mit der älteren Windows-Workflow-Designer erstellt werden. Verwenden Sie die Vorgängerversion von [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] verwenden, wenn die Anwendung auf [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] oder [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] abzielen muss.

 Bei der Installation [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)], eines der Komponenteninstallation ist zum Installieren der [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] für Debugger [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]. Hiermit werden die Komponenten zum Remotedebuggen installiert. Diese Komponenten für Remotedebugging müssen auf dem Computer installiert werden, auf dem Remoteworkflow-Debuggen ausgeführt werden soll.

 Zusätzlich muss die Assembly, die die Workflowdefinition des Legacyworkflows enthält, den Sie auf einem Remotecomputer debuggen, im globalen Assemblycache (GAC) des lokalen Computers installiert sein, von dem Sie debuggen. Wird beispielsweise ein Legacyworkflow auf einem Remotecomputer A ausgeführt und debuggen Sie diesen vom lokalen Computer B, muss die Workflowdefinition im GAC von Computer B vorhanden sein. Hiermit wird der Designer für die Deserialisierung und die Anzeige des Workflowmarkups des remote auf Computer A ausgeführten Workflows auf Computer B aktiviert. Weitere Informationen zum globalen Assemblycache finden Sie unter der MSDN Library.

 Das Remotedebugging in [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] funktioniert genauso wie das Remotedebugging for andere [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Komponenten. Weitere Informationen finden Sie unter [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] Remotedebuggen in der MSDN Library.

## <a name="see-also"></a>Siehe auch

- [Debuggen von Legacyworkflows](../workflow-designer/debugging-legacy-workflows.md)
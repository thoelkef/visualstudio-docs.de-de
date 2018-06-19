---
title: Workflow-Designer - Debuggen von Workflows von einem Remotecomputer (Vorgängerversion)
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- workflows, debugging remotely
- debugging workflows, remotely
- remote debugging, workflows
- debugging, remote
ms.assetid: 44eaec8f-9959-4ae7-a374-670946f933c1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 391180cd76fe5e0cccca802ba1cbfb78277dabc1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31967907"
---
# <a name="debugging-workflows-from-a-remote-computer-legacy"></a>Debuggen von Workflows von einem Remotecomputer (Vorgängerversion)

Dieses Thema beschreibt, wie remote ältere Windows Workflow Foundation (WF)-Anwendungen zu debuggen, die mit der älteren Windows-Workflow-Designer erstellt wurden. Verwenden Sie die legacy-Workflow-Designer, wenn Ihre Anwendung .NET Framework, Version 3.5 oder die WinFX abzielen muss.

 Bei der Installation von Visual Studio ist eine der Komponenteninstallation die Visual Studio Debugger für Windows Workflow Foundation (WF) installieren. Hiermit werden die Komponenten zum Remotedebuggen installiert. Diese Komponenten für Remotedebugging müssen auf dem Computer installiert werden, auf dem Remoteworkflow-Debuggen ausgeführt werden soll.

 Zusätzlich muss die Assembly, die die Workflowdefinition des Legacyworkflows enthält, den Sie auf einem Remotecomputer debuggen, im globalen Assemblycache (GAC) des lokalen Computers installiert sein, von dem Sie debuggen. Wird beispielsweise ein Legacyworkflow auf einem Remotecomputer A ausgeführt und debuggen Sie diesen vom lokalen Computer B, muss die Workflowdefinition im GAC von Computer B vorhanden sein. Hiermit wird der Designer für die Deserialisierung und die Anzeige des Workflowmarkups des remote auf Computer A ausgeführten Workflows auf Computer B aktiviert. Weitere Informationen zum globalen Assemblycache finden Sie unter der MSDN Library.

 Das Debuggen von Windows Workflow Foundation funktioniert genauso wie das Remotedebuggen für andere Visual Studio-Komponenten. Weitere Informationen finden Sie in der Visual Studio Remotedebuggen in der MSDN Library.

## <a name="see-also"></a>Siehe auch

- [Debuggen von Legacyworkflows](../workflow-designer/debugging-legacy-workflows.md)
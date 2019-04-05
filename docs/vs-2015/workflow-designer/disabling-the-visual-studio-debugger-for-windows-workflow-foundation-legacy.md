---
title: Deaktivieren des Debuggers für Windows Workflow Foundation (Vorgängerversion) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, disabling debugger
- debugging workflows, disabling debugger
- workflow debugger, disabling
ms.assetid: 9da96d0e-f941-4fa9-a1a5-6bab50adfec9
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e5065de4ec0217123f76eb23d32bcb0facd25dcc
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58957512"
---
# <a name="disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>Deaktivieren des Visual Studio-Debuggers für Windows Workflow Foundation (Vorgängerversion)
In diesem Thema wird das Deaktivieren des [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Debuggers mithilfe der Konfigurationsdatei beim Erstellen von [!INCLUDE[wf](../includes/wf-md.md)]-Anwendungen in der Vorgängerversion von [!INCLUDE[wfd1](../includes/wfd1-md.md)] beschrieben. Verwenden Sie die Vorgängerversion von [!INCLUDE[wfd2](../includes/wfd2-md.md)], wenn Sie entweder auf [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] oder [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] abzielen möchten.

 Standardmäßig ist der [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)]-Debugger für [!INCLUDE[wf](../includes/wf-md.md)] für einen Hostprozess aktiviert. Um workflowdebuggen zu deaktivieren, Sie müssen ausdrücklich ausschalten, indem Sie einen Eintrag "DisableWorkflowDebugging" hinzufügen  **\<Switches >** Element in der  **\<system.diagnostics >** Abschnitt der Konfigurationsdatei des Hosts.

 Im folgenden Beispiel wird gezeigt, wie die Hostkonfigurationsdatei geändert wird, um Workflowdebuggen zu deaktivieren.

```
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
   <system.diagnostics>
      <switches>
         <add name="DisableWorkflowDebugging" value="true"/>
      </switches>
   </system.diagnostics>
</configuration>
```

## <a name="see-also"></a>Siehe auch
 [Aufrufen des Visual Studio-Debuggers für Windows Workflow Foundation (Vorgängerversion)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md) [Debuggen von Legacyworkflows](../workflow-designer/debugging-legacy-workflows.md)
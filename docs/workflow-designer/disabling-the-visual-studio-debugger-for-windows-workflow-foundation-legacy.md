---
title: Deaktivieren die Visual Studio-Debugger für Windows Workflow Foundation (Vorgängerversion) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- workflows, disabling debugger
- debugging workflows, disabling debugger
- workflow debugger, disabling
ms.assetid: 9da96d0e-f941-4fa9-a1a5-6bab50adfec9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a609062f3f84538f7c1655cd5ca82971fc608f62
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>Deaktivieren des Visual Studio-Debuggers für Windows Workflow Foundation (Vorgängerversion)

In diesem Thema wird beschrieben, wie zum Deaktivieren der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Debugger mithilfe der Konfigurationsdatei beim Erstellen von [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] Anwendungen in älteren Windows Workflow-Designer. Verwenden Sie die Vorgängerversion von [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], wenn Sie entweder auf [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] oder [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] abzielen möchten.

 Standardmäßig ist der [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)]-Debugger für [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] für einen Hostprozess aktiviert. Um workflowdebuggen zu deaktivieren, Sie müssen ausdrücklich ausschalten, indem Sie ein Eintrag "disableworkflowdebugging zum" ** \<Switches >** Element in der ** \<system.diagnostics >**Abschnitt der Hostkonfigurationsdatei.

 Im folgenden Beispiel wird gezeigt, wie die Hostkonfigurationsdatei geändert wird, um Workflowdebuggen zu deaktivieren.

```xml
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

- [Aufrufen des Visual Studio-Debuggers für Windows Workflow Foundation (Vorgängerversion)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)
- [Debuggen von Legacyworkflows](../workflow-designer/debugging-legacy-workflows.md)
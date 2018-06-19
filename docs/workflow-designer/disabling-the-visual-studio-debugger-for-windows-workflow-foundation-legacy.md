---
title: Workflow-Designer - Deaktivieren von Visual Studio-Debugger für Windows Workflow Foundation (Vorgängerversion)
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
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
ms.openlocfilehash: 473ee507e35f5ec5df902df64ee34326dcf90a2b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31969964"
---
# <a name="disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>Deaktivieren des Visual Studio-Debuggers für Windows Workflow Foundation (Vorgängerversion)

Dieses Thema beschreibt, wie Visual Studio-Debugger, die mithilfe der Konfigurationsdatei beim Erstellen von Windows Workflow Foundation (WF)-Anwendungen in älteren Windows Workflow-Designer deaktivieren. Verwenden Sie die legacy-Workflow-Designer, wenn Sie .NET Framework, Version 3.5 oder die WinFX abzielen möchten.

 Standardmäßig ist der Visual Studio Debugger für Windows Workflow Foundation (WF) für einen Hostprozess aktiviert. Um workflowdebuggen zu deaktivieren, Sie müssen ausdrücklich ausschalten, indem Sie ein Eintrag "disableworkflowdebugging zum"  **\<Switches >** Element in der  **\<system.diagnostics >** Abschnitt der Hostkonfigurationsdatei.

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
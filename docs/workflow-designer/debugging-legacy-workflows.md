---
title: Debuggen von Legacyworkflows | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- workflows, debugging
- debugging, workflows
- debugging workflows
ms.assetid: e6097b47-760a-4b30-a92c-ae70cdbda49f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2710266446e285d9107f4450c09ffe2e8e87e090
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="debugging-legacy-workflows"></a>Debuggen von Legacyworkflows

Bei Verwendung von älteren Windows-Workflow-Designer in [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] erstellen [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] Anwendungen, anfügungen Framework 3.0 oder 3.5, können Sie die Workflows genau wie jedes andere Programm debuggen, durch Festlegen von Haltepunkten, Anfügen an Prozesse und untersuchen Threads und die Aufrufliste. Sie haben auch die Möglichkeit, remote zu debuggen.

> [!NOTE]
> Wenn mehrere Visual Studio-Versionen auf dem Computer installiert und deinstalliert wurden, kann das WF3-Debuggen aus einem der beiden folgenden Gründe fehlschlagen:
>
> -   Die Haltepunkte werden nicht erreicht.
> -   Folgende Meldung wird angezeigt:
>
> **Debuggen kann nicht auf dem Webserver. Der Debugger ist nicht ordnungsgemäß installiert.  Der angeforderte Codetyp kann nicht debuggt werden.  Führen Sie Setup zum Installieren oder reparieren den Debugger an.**
>
> Wenn eines dieser Szenarien beim Debuggen von .NET Framework 3.0- oder 3.5-Workflows auftritt, führen Sie eine Reparatur der Visual Studio-Installation aus.

 [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] kann in die folgenden standardmäßigen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Debugfenster integriert werden:

-   **Haltepunkt**: funktioniert wie erwartet, aber Sie geben eine Aktivität für den Namen der Funktion.

-   **Aufrufliste**: veränderte eine Gliederung der Aktivitäten bereitzustellen, die in einer Workflowinstanz ausgeführt wurden. Die Einträge in der **Aufrufliste** Fenster sind eine Tiefensuche der ausgeführten Aktivitäten. Sie können auf einen Eintrag doppelklicken, um den Fokus auf die ausgewählte Aktivität zu lenken.

-   **Threads**: stellt die Instanz-ID der Workflowinstanz, die gedebuggt wird.

 Die folgenden Debugfunktionen werden von Visual Studio für Windows Workflow Foundation nicht unterstützt.

-   Bedingte Haltepunkte auf der Entwurfsoberfläche

-   Schnellüberwachung

-   Nächste Anweisung festlegen

-   Ausführen bis Cursor

-   Bearbeiten und Fortfahren

-   Just-In-Time-Debuggen

-   Debuggen im gemischten Modus
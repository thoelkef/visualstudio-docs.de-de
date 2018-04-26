---
title: Workflow-Designer - Debuggen von Legacyworkflows
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
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
ms.openlocfilehash: 33a8358c5d62b938fc64d608c9b4546ab1745aaa
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="debugging-legacy-workflows"></a>Debuggen von Legacyworkflows

Wenn Sie die älteren Windows-Workflow-Designer in Visual Studio verwenden, um Windows Workflow Foundation (WF)-Anwendungen, anfügungen Framework 3.0 oder 3.5 zu erstellen, können Sie die Workflows genau wie jedes andere Programm debuggen, durch Festlegen von Haltepunkten, Anfügen an Prozesse werden, und Threads und die Aufrufliste überprüfen. Sie haben auch die Möglichkeit, remote zu debuggen.

> [!NOTE]
> Wenn mehrere Visual Studio-Versionen auf dem Computer installiert und deinstalliert wurden, kann das WF3-Debuggen aus einem der beiden folgenden Gründe fehlschlagen:
>
> -   Die Haltepunkte werden nicht erreicht.
> -   Folgende Meldung wird angezeigt:
>
> **Debuggen kann nicht auf dem Webserver. Der Debugger ist nicht ordnungsgemäß installiert.  Der angeforderte Codetyp kann nicht debuggt werden.  Führen Sie Setup zum Installieren oder reparieren den Debugger an.**
>
> Wenn eines dieser Szenarien beim Debuggen von .NET Framework 3.0- oder 3.5-Workflows auftritt, führen Sie eine Reparatur der Visual Studio-Installation aus.

 In Windows Workflow Foundation sind die folgenden Standard-Visual Studio-Debugfenster integriert:

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
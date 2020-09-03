---
title: 'Vorgehensweise: Festlegen von Haltepunkten in Workflows (Legacy) | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- breakpoints, setting in workflows
- debugging, setting breakpoints in workflows
- debugging workflows, setting breakpoints
- workflows, setting breakpoints
ms.assetid: 78e0be39-3e99-487c-bfef-19db0daf6f42
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 182f28a2b21ae3129ce0d34fae97280ba0a07218
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72603596"
---
# <a name="how-to-set-breakpoints-in-workflows-legacy"></a>Vorgehensweise: Festlegen von Haltepunkten in Workflows (Vorgängerversion)
In diesem Thema wird das Festlegen von Haltepunkten in [!INCLUDE[wf](../includes/wf-md.md)]-Anwendungen mithilfe der Vorgängerversion von [!INCLUDE[wfd1](../includes/wfd1-md.md)] beschrieben. Verwenden Sie die Vorgängerversion von [!INCLUDE[wfd2](../includes/wfd2-md.md)] verwenden, wenn Ihre [!INCLUDE[wf2](../includes/wf2-md.md)]-Anwendungen auf [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] oder [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] abzielen muss.

 Bei der Verwendung der Vorgängerversion von [!INCLUDE[wfd2](../includes/wfd2-md.md)] in [!INCLUDE[vs2010](../includes/vs2010-md.md)] zum Erstellen einer [!INCLUDE[wf2](../includes/wf2-md.md)]-Anwendung können Sie genau wie in Visual Studio Haltepunkte im C#- und Visual Basic-Code festlegen. Wie erwartet, hält die Workflowausführung an jedem festgelegten Haltepunkt an.

 Ein Haltepunkt hat drei Zustände: " *Pending*", " *Bound*" und " *Error*". Wenn Sie einen Haltepunkt festlegen, erhält dieser den Status "Ausstehend". Dieser wird durch ein hohles rotes Symbol dargestellt. Wurde der Workflowtyp von der Laufzeit geladen, erhält dieser den Status "Gebunden", der mit einem ausgefüllten roten Symbol dargestellt wird. Geben Sie ein falsches Format für den Haltepunkt an, erscheint genau wie bei einem ungültigen Aktivitätsnamen eine Fehlermeldung. Der Haltepunkt wird immer noch dem Haltepunktfenster hinzugefügt, er wird jedoch mit einem kleinen "x" markiert.

 Sie können für eine Aktivität auf der Workflowentwurfsoberfläche folgendermaßen Haltepunkte festlegen:

- Klicken Sie mit der rechten Maustaste auf die Aktivität, und wählen Sie halte **Punkt \ Haltepunkt einfügen**.

- Wählen Sie die Aktivität aus, und drücken Sie F9.

- Wählen Sie im Menü **Debuggen** die Option **Neuer Haltepunkt** aus.

     Mit dieser Option können Sie auch während eines Debugvorgangs einen neuen Haltepunkt festlegen, wenn der Debugger an einem Haltepunkt anhält.

    > [!NOTE]
    > Das Festlegen von Haltepunkten für aufgerufene Workflows wird nicht unterstützt.

### <a name="to-set-a-breakpoint-using-the-new-breakpoint-option-on-the-debug-menu"></a>So legen Sie einen Haltepunkt mit der Option "Neuer Haltepunkt" im Menü "Debuggen" fest

1. Wählen Sie im Menü **Debuggen** die Option **Neuer Haltepunkt**aus.

2. Klicken Sie **in der Funktion auf Break**.

     Das Dialogfeld **Neuer Haltepunkt** wird geöffnet.

3. Geben Sie den Namen einer Aktivität im Textfeld **Funktion** an, indem Sie die folgende Syntax verwenden: `QualifiedActivityId[:[FullClassName][:InstanceId]]` .

    > [!NOTE]
    > Anstatt den Aktivitäts Namen im Textfeld **Funktion** zu verwenden, können Sie optional einen Haltepunkt festlegen, indem Sie den absoluten Pfad der Workflow Aktivität angeben. Angenommen, Sie verfügen über eine Workflow Lösung namens **WorkflowConsoleApplication1** und einen Workflow in der Projekt Mappe mit dem Namen **Workflow1** , die eine Aktivität mit dem Namen **Delay1**verwendet. Sie können den Aktivitäts Namen **Delay1** verwenden oder den Pfad als **Delay1: WorkflowConsoleApplication1. Workflow1** oder **Delay1: WorkflowConsoleApplication1. Workflow1: {6614886a-608e-412b-bf98-99ff1559dddf}** angeben.

4. Aktivieren Sie das Kontrollkästchen **IntelliSense verwenden** , um den Funktionsnamen zu überprüfen.

     Ist dieses Kontrollkästchen nicht aktiviert, wird keine Haltepunktnamensüberprüfung durchgeführt.

5. Wählen Sie in der Liste **Sprache** die Option **Workflow** aus.

6. Klicken Sie auf **OK**.

## <a name="see-also"></a>Weitere Informationen
 [Debuggen von Legacy Workflows](../workflow-designer/debugging-legacy-workflows.md) [Aufrufen des Visual Studio-Debuggers für Windows Workflow Foundation (Legacy)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)
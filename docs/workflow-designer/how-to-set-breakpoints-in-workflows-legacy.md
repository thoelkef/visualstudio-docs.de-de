---
title: "Vorgehensweise: Festlegen von Haltepunkten in Workflows (Vorg&#228;ngerversion) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Haltepunkte, Festlegen in Workflows"
  - "Debuggen von Workflows, Festlegen von Haltepunkten"
  - "Debuggen, Festlegen von Haltepunkten in Workflows"
  - "Workflows, Festlegen von Haltepunkten"
ms.assetid: 78e0be39-3e99-487c-bfef-19db0daf6f42
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Vorgehensweise: Festlegen von Haltepunkten in Workflows (Vorg&#228;ngerversion)
In diesem Thema wird das Festlegen von Haltepunkten in [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]\-Anwendungen mithilfe der Vorgängerversion von [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] beschrieben.Verwenden Sie die Vorgängerversion von [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] verwenden, wenn Ihre [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)]\-Anwendungen auf [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] oder [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] abzielen muss.  
  
 Bei der Verwendung der Vorgängerversion von [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] in [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] zum Erstellen einer [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)]\-Anwendung können Sie genau wie in Visual Studio Haltepunkte im C\#\- und Visual Basic\-Code festlegen.Wie erwartet, hält die Workflowausführung an jedem festgelegten Haltepunkt an.  
  
 Ein Haltepunkt verfügt über drei Status: *Ausstehend*, *Gebunden* und *Fehler*.Wenn Sie einen Haltepunkt festlegen, erhält dieser den Status "Ausstehend". Dieser wird durch ein hohles rotes Symbol dargestellt.Wurde der Workflowtyp von der Laufzeit geladen, erhält dieser den Status "Gebunden", der mit einem ausgefüllten roten Symbol dargestellt wird.Geben Sie ein falsches Format für den Haltepunkt an, erscheint genau wie bei einem ungültigen Aktivitätsnamen eine Fehlermeldung.Der Haltepunkt wird immer noch dem Haltepunktfenster hinzugefügt, er wird jedoch mit einem kleinen "x" markiert.  
  
 Sie können für eine Aktivität auf der Workflowentwurfsoberfläche folgendermaßen Haltepunkte festlegen:  
  
-   Klicken Sie mit der rechten Maustaste auf die Aktivität, und wählen Sie **Haltepunkt \\ Haltepunkt einfügen**.  
  
-   Wählen Sie die Aktivität aus, und drücken Sie F9.  
  
-   Wählen Sie im Menü **Debuggen** die Option **Neuer Haltepunkt**.  
  
     Mit dieser Option können Sie auch während eines Debugvorgangs einen neuen Haltepunkt festlegen, wenn der Debugger an einem Haltepunkt anhält.  
  
    > [!NOTE]
    >  Das Festlegen von Haltepunkten für aufgerufene Workflows wird nicht unterstützt.  
  
### So legen Sie einen Haltepunkt mit der Option "Neuer Haltepunkt" im Menü "Debuggen" fest  
  
1.  Klicken Sie im Menü **Debuggen** auf **Neuer Haltepunkt**.  
  
2.  Klicken Sie auf **Halten bei Funktion**.  
  
     Das Dialogfeld **Neuer Haltepunkt** wird angezeigt.  
  
3.  Geben Sie den Namen einer Aktivität mit der folgenden Syntax im Textfeld **Funktion** an: `QualifiedActivityId[:[FullClassName][:InstanceId]]`.  
  
    > [!NOTE]
    >  Alternativ können Sie anstatt den Aktivitätsnamen im Textfeld **Funktion** zu verwenden, einen Haltepunkt festlegen, indem Sie den absoluten Pfad der Workflowaktivität angeben.Angenommen, Sie verfügen beispielsweise über eine Workflowlösung mit dem Namen **WorkflowConsoleApplication1** und in der Projektmappe über eine Lösung mit dem Namen **Workflow1**, die die Aktivität **Delay1** verwendet.Sie können den Aktivitätsnamen **Delay1** verwenden oder den Pfad mit **Delay1:WorkflowConsoleApplication1.Workflow1** oder **Delay1:WorkflowConsoleApplication1.Workflow1: {6614886A\-608E\-412B\-BF98\-99FF1559DDDF}** angeben.  
  
4.  Aktivieren Sie das Kontrollkästchen **IntelliSense verwenden**, um den Funktionsnamen zu überprüfen.  
  
     Ist dieses Kontrollkästchen nicht aktiviert, wird keine Haltepunktnamensüberprüfung durchgeführt.  
  
5.  Wählen Sie aus der Liste **SpracheWorkflow** aus.  
  
6.  Klicken Sie auf **OK**.  
  
## Siehe auch  
 [Debuggen von Legacyworkflows](../workflow-designer/debugging-legacy-workflows.md)   
 [Aufrufen des Visual Studio\-Debuggers für Windows Workflow Foundation \(Vorgängerversion\)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)
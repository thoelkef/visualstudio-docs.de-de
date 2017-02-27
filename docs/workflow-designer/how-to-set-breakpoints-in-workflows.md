---
title: "Vorgehensweise: Festlegen von Haltepunkten in Workflows | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: e41b21c9-c061-4358-8e2f-eb5e412864a8
caps.latest.revision: 10
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# Vorgehensweise: Festlegen von Haltepunkten in Workflows
Wenn Sie [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] verwenden, können Sie Haltepunkte für die grafischen Workflows genauso festlegen, wie Sie es in Visual Basic oder C\#\-Code machen würden.Wie erwartet, hält die Workflowausführung an jedem festgelegten Haltepunkt an.  
  
 Ein Haltepunkt verfügt über drei Status: *Ausstehend*, *Gebunden* und *Fehler*.Wenn Sie einen Haltepunkt festlegen, erhält dieser den Status "Ausstehend". Dieser wird durch ein rot ausgefülltes Symbol dargestellt.Wenn die Laufzeit den Workflowtyp geladen hat, wechselt der Haltepunktstatus zu "Gebunden".Haben Sie ein falsches Format für den Haltepunkt angegeben, etwa einen ungültigen Aktivitätsnamen, dann erscheint eine Fehlermeldung.Der Haltepunkt wird immer noch dem Haltepunktfenster hinzugefügt, er wird jedoch mit einem kleinen "x" markiert.  
  
> [!NOTE]
>  Das Festlegen von Haltepunkten für aufgerufene Workflows wird nicht unterstützt.  
  
> [!WARNING]
>  Stellen Sie sicher, dass Sie die Option **Nur eigenen Code aktivieren \(nur verwaltet\)** im Menü **Tools**, **Optionen**, **Debuggen** auswählen, bevor Sie mit dem Debuggen beginnen.Wenn zwei Sequenzen innerhalb einer anderen Sequenz verschachtelt sind und Sie einen Haltepunkt auf der ersten inneren Sequenz festlegen, wird durch Drücken von **F11** nicht die zweite innere Sequenz debuggt, wenn die Option **Nur eigenen Code aktivieren \(nur verwaltet\)** nicht aktiviert ist.  
  
> [!WARNING]
>  Haltepunkte in einem Workflow werden nicht erreicht, wenn der vollständige Pfad zur XAML\-Dateieigenschaft nicht korrekt ist. Der vollständige Pfad der XAML\-Datei ist nicht korrekt, nachdem das Projekt\/die Projektmappe in einen anderen Ordner oder auf einen anderen Computer verschoben wurde. Wählen Sie STRG\+S, um die vollständige Pfadeigenschaft zu speichern und zu aktualisieren.  
  
### So legen Sie einen Haltepunkt für eine Aktivität in der Entwurfsansicht fest  
  
1.  Wählen Sie die Aktivität aus, bei der der Debugger unterbrechen soll.  
  
2.  Klicken Sie im Menü **Debuggen** auf **Haltepunkte umschalten**.Ein rotes Symbol wird am oberen linken Rand der Aktivität angezeigt.  
  
     Alternativ können Sie auch **F9** drücken, nachdem Sie die Aktivität ausgewählt haben, oder Sie klicken mit der rechten Maustaste auf die Aktivität, zeigen im Kontextmenü auf **Haltepunkt** und wählen dann **Haltepunkt einfügen** aus.  
  
## Siehe auch  
 [Vorgehensweise: Aufrufen des Workflow\-Debuggers](../workflow-designer/how-to-invoke-the-workflow-debugger.md)   
 [Debuggen von Workflows mit dem Workflow\-Designer](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)   
 [Vorgehensweise: Debuggen von XAML mit dem Workflow\-Designer](../workflow-designer/how-to-debug-xaml-with-the-workflow-designer.md)
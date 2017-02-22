---
title: "Vorgehensweise: Debuggen von XAML mit dem Workflow-Designer | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: d9305dbc-af62-4bdd-b03f-c54e3fe9ecc7
caps.latest.revision: 8
caps.handback.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Vorgehensweise: Debuggen von XAML mit dem Workflow-Designer
Workflows werden in XAML definiert.In der Benutzeroberfläche werden Workflows in Form einer XAML\-Struktur dargestellt, die den Workflow definiert.Der Debugprozess gestaltet sich ähnlich dem Debuggen von Workflows in [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)].Während des Debuggens von XAML arbeiten beispielsweise die Fenster "Lokal", "Überwachen" und "Threads" genau wie während des [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Debuggens.Zusätzlich ist während des XAML\-Debuggens die Aufruflistenansicht als zeilenbasierte hierarchische Ansicht des Ausführungsflusses für den Workflow verfügbar.  
  
> [!NOTE]
>  Wenn die XAML für einen Workflow in derselben Assembly wie die Aktivitäten enthalten ist, wird der Assemblyteil der Klassennamen nicht eingeschlossen.Ohne diesen Teil des Klassen\(aktivitäts\)namens kann die XAML zur Laufzeit nicht geladen werden.Es wird davon abgeraten, Aktivitäten im gleichen Namespace wie das Hauptprojekt zu definieren; andernfalls muss die XAML manuell bearbeitet werden, nachdem sie im Designer bearbeitet wurde.  
  
### So debuggen Sie Workflow\-XAML  
  
1.  Öffnen Sie in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ein Workflow\- oder ein Aktivitätsprojekt.  
  
2.  Legen Sie für die Aktivität oder die Aktivitäten, die Sie debuggen möchten, einen Haltepunkt fest, wie in [Vorgehensweise: Festlegen von Haltepunkten in Workflows](../workflow-designer/how-to-set-breakpoints-in-workflows.md) beschrieben.  
  
3.  Klicken Sie mit der rechten Maustaste auf die XAML\-Datei, die die Workflowdefinition enthält, und wählen Sie **Code anzeigen** aus.Der Haltepunkt wird in der gleichen Zeile wie die XAML\-Elementdeklaration der Aktivität angezeigt, für die Sie den Haltepunkt in der Entwurfsansicht festgelegt haben.  
  
4.  Rufen Sie, wie in [Vorgehensweise: Aufrufen des Workflow\-Debuggers](../workflow-designer/how-to-invoke-the-workflow-debugger.md) beschrieben, den Debugger auf.  
  
5.  Wenn die Codeausführung einen der Haltepunkte erreicht, wird das diesem Haltepunkt zugeordnete XAML\-Element hervorgehoben dargestellt.Drücken Sie die Tasten **F10** oder **F11**, um zum nächsten Haltepunkt zu gelangen.  
  
## Siehe auch  
 [Vorgehensweise: Festlegen von Haltepunkten in Workflows](../workflow-designer/how-to-set-breakpoints-in-workflows.md)   
 [Vorgehensweise: Aufrufen des Workflow\-Debuggers](../workflow-designer/how-to-invoke-the-workflow-debugger.md)
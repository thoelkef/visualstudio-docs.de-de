---
title: "WriteLine-Aktivit&#228;tsdesigner | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.WriteLine.UI"
ms.assetid: 1b5f29a8-b7fd-477e-949e-2f689cae3c96
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# WriteLine-Aktivit&#228;tsdesigner
Der **WriteLine**\-Aktivitätsdesigner wird verwendet, um eine <xref:System.Activities.Statements.WriteLine>\-Aktivität zu erstellen und zu konfigurieren.  
  
## Die WriteLine\-Aktivität  
 Die <xref:System.Activities.Statements.Writeline>\-Aktivität schreibt Text in ein angegebenes <xref:System.IO.TextWriter>\-Objekt.Wenn kein <xref:System.IO.TextWriter> angegeben wird, schreibt <xref:System.Activities.Statements.Writeline> den Text in die Konsole.  
  
### Verwenden des WriteLine\-Aktivitätsdesigners  
 Der **WriteLine**\-Aktivitätsdesigner befindet sich in der Kategorie **Primitives** der **Toolbox**, auf die Sie zugreifen können, indem Sie in [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] auf die Registerkarte **Toolbox** klicken \(Sie können auch im Menü **Ansicht** den Befehl **Symbolleiste** auswählen oder STRG\+ALT\+X drücken\).  
  
 Der **WriteLine**\-Aktivitätsdesigner kann aus der **Toolbox** gezogen und auf der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden, etwa innerhalb einer <xref:System.Activities.Statements.Sequence>.Daraufhin wird eine <xref:System.Activities.Statements.WriteLine>\-Aktivität mit dem <xref:System.Activities.Activity.DisplayName%2A>\-Standardwert WriteLine erstellt.Der <xref:System.Activities.Activity.DisplayName%2A>\-Wert kann im Header des **WriteLine**\-Aktivitätsdesigners oder im Feld **DisplayName** des Eigenschaftenrasters bearbeitet werden.  
  
### Die WriteLine\-Eigenschaften  
 In der folgenden Tabelle werden die Eigenschaften von <xref:System.Activities.Statements.WriteLine> aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.Diese Eigenschaften können im Eigenschaftenraster, einige davon auf der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Designeroberfläche bearbeitet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-----------------------|------------------|----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den benutzerfreundlichen Namen der <xref:System.Activities.Statements.WriteLine>\-Aktivität an.Der Standardwert lautet WriteLine.Obwohl der <xref:System.Activities.Activity.DisplayName%2A>\-Wert nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|  
|<xref:System.Activities.Statements.WriteLine.Text%2A>|False|Der zu schreibende Text.Um die Eigenschaft festzulegen, geben Sie einen Visual Basic\-Ausdruck im Feld **Text** im **WriteLine**\-Aktivitätsdesigner oder im Eigenschaftenraster ein.|  
|<xref:System.Activities.Statements.WriteLine.TextWriter%2A>|False|Die <xref:System.IO.TextWriter>\-Instanz, an die die <xref:System.Activities.Statements.WriteLine>\-Aktivität den <xref:System.Activities.Statements.WriteLine.Text%2A>\-Text ausgibt.Der Standardwert ist die Konsole.|  
  
## Siehe auch  
 [Primitive](../workflow-designer/primitives-activity-designers.md)   
 [Assign](../workflow-designer/assign-activity-designer.md)   
 [Delay](../workflow-designer/delay-activity-designer.md)   
 [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
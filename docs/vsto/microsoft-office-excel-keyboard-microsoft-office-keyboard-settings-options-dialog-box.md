---
title: "Microsoft Office Excel-Tastatur, Microsoft Office-Tastatureinstellungen, Dialogfeld &quot;Optionen&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VST.ExcelOptions.KeyboardMappingScheme"
  - "VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Excel_Keyboard"
  - "VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Excel.Keyboard"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Tastenkombinationen, Office-Entwicklung in Visual Studio"
ms.assetid: 2a8b9e70-66fa-4461-8039-b6d8a2fbb963
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# Microsoft Office Excel-Tastatur, Microsoft Office-Tastatureinstellungen, Dialogfeld &quot;Optionen&quot;
  Sowohl in Microsoft Office Excel als auch in Visual Studio werden Tastenkombinationen behandelt.  Dieselbe Tastenkombination kann in Excel und Visual Studio für jeweils unterschiedliche Befehle verwendet werden.  Wenn Excel in einem Projekt auf Dokumentebene in Visual Studio geöffnet ist, erhält nur jeweils eine Anwendung die Befehle der Tastenkombination.  Standardmäßig empfängt Visual Studio alle Tastenkombinationsbefehle. Durch Auswahl der Option **Dynamisches Tastaturschema** können Sie jedoch festlegen, dass Excel alle Befehle empfängt, während das Dokument den Fokus hat.  
  
 Wenn Sie eine Tastenkombination verwenden, für die in der aktuellen Anwendung kein Befehl zugewiesen ist, wird die Tastenkombination an die andere Anwendung übergeben.  
  
 Die ausgewählte Option bleibt für Excel\-Projekte wirksam, bis sie geändert wird.  Die Auswahl hat keine Auswirkungen auf Microsoft Office Word\-Projekte. Änderungen für Word können nur mithilfe der Tastaturoptionen für Microsoft Office Word vorgenommen werden.  
  
## UIElement-Liste  
 **Visual Studio\-Tastaturschema**  
 Visual Studio empfängt alle Tastenkombinationsbefehle, auch wenn Excel den Fokus hat.  Wenn Sie beispielsweise die Funktionstaste F5 drücken, während Excel den Fokus hat, startet Visual Studio das Debuggen der Arbeitsmappe.  
  
 **Dynamisches Tastaturschema**  
 Visual Studio erhält nur dann Tastenkombinationsbefehle, wenn es den Fokus hat.  Wenn Excel den Fokus hat, empfängt Excel alle Tastenkombinationsbefehle.  Wenn Sie beispielsweise die Funktionstaste F5 drücken, während Excel den Fokus hat, wird das Dialogfeld **Gehe zu** in Excel geöffnet.  Wenn Sie F5 drücken, während Visual Studio den Fokus hat, startet Visual Studio das Debuggen der Projektmappe.  
  
## Siehe auch  
 [Microsoft Office Word-Tastatur, Microsoft Office-Tastatureinstellungen, Dialogfeld "Optionen"](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)  
  
  
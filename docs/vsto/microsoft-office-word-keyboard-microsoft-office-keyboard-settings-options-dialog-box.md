---
title: "Microsoft Office Word-Tastatur, Microsoft Office-Tastatureinstellungen, Dialogfeld &quot;Optionen&quot; | Microsoft Docs"
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
  - "VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Word.Keyboard"
  - "VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Word_Keyboard"
  - "VST.WordOptions.KeyboardMappingScheme"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Tastenkombinationen, Office-Entwicklung in Visual Studio"
ms.assetid: d98edaab-846a-4baa-b190-702b1134754c
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Microsoft Office Word-Tastatur, Microsoft Office-Tastatureinstellungen, Dialogfeld &quot;Optionen&quot;
  Sowohl in Microsoft Office Word als auch in Visual Studio werden Tastenkombinationen behandelt.  Die gleiche Tastenkombination kann in Word und Visual Studio für jeweils unterschiedliche Befehle verwendet werden.  Wenn Word in einem Projekt auf Dokumentebene in Visual Studio geöffnet ist, erhält nur jeweils eine Anwendung die Befehle der Tastenkombination.  Standardmäßig erhält Visual Studio alle Tastenkombinationsbefehle. Wenn jedoch das Dokument den Fokus hat, kann durch Auswahl der Option **Dynamisches Tastaturschema** Word die Befehle erhalten.  
  
 Wenn Sie eine Tastenkombination verwenden, für die in der aktuellen Anwendung kein Befehl zugewiesen ist, wird die Tastenkombination an die andere Anwendung übergeben.  
  
 Die ausgewählte Option bleibt für Word\-Projekte wirksam, bis sie geändert wird.  Die Auswahl hat keine Auswirkung auf Microsoft Office Excel\-Projekte. Änderungen für Excel können nur mithilfe der Tastaturoptionen für Microsoft Office Excel vorgenommen werden.  
  
## UIElement-Liste  
 **Visual Studio\-Tastaturschema**  
 Visual Studio erhält alle Tastenkombinationsbefehle, auch wenn das Word\-Dokument den Fokus hat.  Wenn Sie z. B. die Funktionstaste F5 drücken, während das Dokument den Fokus hat, startet Visual Studio den Debugvorgang der Projektmappe.  
  
 **Dynamisches Tastaturschema**  
 Visual Studio erhält nur dann Tastenkombinationsbefehle, wenn es den Fokus hat.  Wenn das Word\-Dokument den Fokus hat, erhält Word alle Tastenkombinationsbefehle.  Wenn Sie z. B. die Funktionstaste F5 drücken, während das Word\-Dokument den Fokus hat, öffnet Word das Dialogfeld **Suchen und Ersetzen** mit der ausgewählten Registerkarte **Gehe zu**.  Wenn Sie F5 drücken, während Visual Studio den Fokus hat, startet Visual Studio das Debuggen der Projektmappe.  
  
## Siehe auch  
 [Microsoft Office Excel-Tastatur, Microsoft Office-Tastatureinstellungen, Dialogfeld "Optionen"](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)  
  
  
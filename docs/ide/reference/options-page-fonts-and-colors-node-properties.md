---
title: "Optionsseite, Eigenschaften des Knotens &quot;Schriftarten und Farben&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Einstellungen unter „Extras“ | „Optionen“, Eigenschaften des Knotens „Schriftarten und Farben“"
  - "Automatisierung [Visual Studio], Steuern mit „Extras“ | „Optionen“"
ms.assetid: 8e1ab784-5f85-4e2b-8ef9-e5d59ca4dbcb
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Optionsseite, Eigenschaften des Knotens &quot;Schriftarten und Farben&quot;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Dieses Dokument beschreibt Schriftart\- und Farbeigenschaften für ein Toolfenster, das für die Anzeige im Dialogfeld **Optionen** in der Kategorie **Umgebung** unter **Schriftarten und Farben** registriert ist.  So kann das dynamische Verhalten von Gruppen kolorierbarer Elemente unterstützt werden, die sich ändern können, wenn VSPackages\-Pakete installiert oder deinstalliert werden.  
  
 Der folgende Abschnitt behandelt als Beispiel einen registrierten Fenstertyp und die für jedes Fenster verfügbaren Eigenschaften.  
  
## Text\-Editor oder Drucker oder Dialogfelder und Toolfenster  
 `DTE.Properties("FontsAndColors", "TextEditor")`  
  
 \- oder \-  
  
 `DTE.Properties("FontsAndColors", "Printer")`  
  
 \- oder \-  
  
 `DTE.Properties("FontsAndColors", "Dialogs and Tool Windows")`  
  
|Eigenschaftenelementname|Wert|Beschreibung|  
|------------------------------|----------|------------------|  
|FontFamily|Get\/Set \(Zeichenfolge\)|Der zu verwendende Schriftartname, z. B. "Courier New".|  
|FontCharacterSet|Get\/Set \(<xref:EnvDTE.vsFontCharSet>\)|Ein <xref:EnvDTE.vsFontCharSet>\-Wert, der den Typ des zu verwendenden Zeichensatzes angibt, z. B. Hebräisch oder Russisch.|  
|FontSize|Get\/Set \(Short\)|Die Größe der zu verwendenden Schriftart in Punkt.  Beispiel:10 oder 12.|  
  
## Siehe auch  
 [Steuern der Einstellungen im Dialogfeld "Optionen" \(Menü "Extras"\)](../Topic/Controlling%20Options%20Settings.md)   
 [Bestimmen der Namen von Eigenschaftenelementen auf Optionsseiten](../Topic/Determining%20the%20Names%20of%20Property%20Items%20on%20Options%20Pages.md)   
 [Optionsseite, Eigenschaften des Knotens "Umgebung"](../../ide/reference/options-page-environment-node-properties.md)   
 [Optionsseite, Eigenschaften des Knotens "Text\-Editor"](../../ide/reference/options-page-text-editor-node-properties.md)
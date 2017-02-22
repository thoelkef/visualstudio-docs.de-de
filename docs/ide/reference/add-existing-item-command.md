---
title: "Befehl &quot;Vorhandenes Element hinzuf&#252;gen&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "project.addexistingitem"
helpviewer_keywords: 
  - "Vorhandenes Element hinzufügen (Befehl)"
  - "File.AddExistingItem-Befehl"
ms.assetid: 41f56131-d4c7-4f81-83b7-bdac713ea870
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Befehl &quot;Vorhandenes Element hinzuf&#252;gen&quot;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Fügt der aktuellen Projektmappe eine vorhandene Datei hinzu und öffnet diese.  
  
## Syntax  
  
```  
File.AddExistingItem filename [/e:editorname]  
```  
  
## Argumente  
 `filename`  
 Erforderlich.  Der vollständige Pfad und Dateiname mit Erweiterung des Elements, das der aktuellen Projektmappe hinzugefügt werden soll.  Wenn der Dateipfad oder \-name Leerzeichen enthält, schließen Sie den gesamten Pfad in Anführungszeichen ein.  
  
## Schalter  
 \/e: `editorname`  
 Optional.  Name des Editors, in dem die Datei geöffnet wird.  Wenn zwar das Argument, aber kein Editorname angegeben wurde, wird das Dialogfeld **Öffnen mit** angezeigt.  
  
 Die Argumentsyntax \/e:`editorname` verwendet die Editornamen wie im **Dialogfeld Öffnen mit** angezeigt, wobei der Name in Anführungszeichen eingeschlossen ist.  Um ein Stylesheet im Quellcode\-Editor zu öffnen, geben Sie für das Argument \/e:`editorname` beispielsweise Folgendes ein:  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## Hinweise  
 Die automatische Vervollständigung versucht, den richtigen Pfad und Dateinamen während der Eingabe zu ermitteln.  
  
## Beispiel  
 In diesem Beispiel wird der aktuellen Projektmappe die Datei Form1.frm hinzugefügt.  
  
```  
>File.AddExistingItem "C:\public\solution files\Form1.frm"  
```  
  
## Siehe auch  
 [Visual Studio\-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Such\/Befehlsfeld](../../ide/find-command-box.md)   
 [Visual Studio\-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)
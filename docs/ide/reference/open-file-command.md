---
title: "Befehl &quot;Datei &#246;ffnen&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "file.openfile"
helpviewer_keywords: 
  - "File.OpenFile-Befehl"
  - "of-Befehl"
  - "Datei öffnen (Befehl)"
ms.assetid: a51a83fc-e3c6-4fa2-8882-8b7b6c0a6406
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Befehl &quot;Datei &#246;ffnen&quot;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Öffnet eine vorhandene Datei und ermöglicht die Angabe eines Editors.  
  
## Syntax  
  
```  
File.OpenFile filename [/e:editorname]  
```  
  
## Argumente  
 `filename`  
 Erforderlich.  Der vollständige oder teilweise Pfad und Dateiname der zu öffnenden Datei.  Pfade, die Leerzeichen enthalten, müssen in Anführungszeichen eingeschlossen sein.  
  
## Schalter  
 \/e:`editorname`  
 Optional.  Name des Editors, in dem die Datei geöffnet wird.  Wenn zwar das Argument, aber kein Editorname angegeben wurde, wird das Dialogfeld **Öffnen mit** angezeigt.  
  
 \/e: Die Argumentsyntax`editorname` der Editor verwendet, während sie im Dialogfeld Öffnen mit angezeigt, wobei der Name in Anführungszeichen eingeschlossen.  
  
 Um eine Datei im Quellcode\-Editor zu öffnen, geben Sie für das Argument \/e:`editorname` beispielsweise Folgendes ein:  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## Hinweise  
 Beim Eingeben eines Pfades versucht die automatische Vervollständigung, den korrekten Pfad und Dateinamen zu finden.  
  
## Beispiel  
 In diesem Beispiel wird die Stildatei "Test1.css" im Quellcode\-Editor geöffnet.  
  
```  
>File.OpenFile "C:\My Projects\project1\Test1.css" /e:"Source Code (text) Editor"  
```  
  
## Siehe auch  
 [Visual Studio\-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Direktfenster](../../ide/reference/immediate-window.md)   
 [Such\/Befehlsfeld](../../ide/find-command-box.md)   
 [Visual Studio\-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)
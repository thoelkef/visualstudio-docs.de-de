---
title: "Befehl &quot;Neues Element hinzuf&#252;gen&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "project.addnewitem"
helpviewer_keywords: 
  - "Neues Element hinzufügen (Befehl)"
  - "File.AddNewItem-Befehl"
ms.assetid: 63b7df32-db83-463b-bbe7-7ff011fe5298
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Befehl &quot;Neues Element hinzuf&#252;gen&quot;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Fügt der aktuellen Projektmappe ein neues Projektmappenelement wie eine HTM\-, CSS\-, TXT\- oder Framesetdatei hinzu und öffnet dieses.  
  
## Syntax  
  
```  
File.AddNewItem [filename] [/t:templatename] [/e:editorname]  
```  
  
## Argumente  
 `filename`  
 Optional.  Der Pfad und Dateiname des Elements, das der Projektmappe hinzugefügt werden soll.  
  
## Schalter  
 \/t: `templatename`  
 Optional.  Gibt den Typ der zu erstellenden Datei an.  Wenn kein Vorlagenname angegeben wird, wird standardmäßig eine Textdatei erstellt.  
  
 Die Argumentsyntax \/t:`templatename` gibt die im Dialogfeld **Neues Projektmappenelement hinzufügen** gefundenen Informationen wieder.  Es muss die vollständige Kategorie, gefolgt vom Dateityp, eingegeben werden; der Name der Kategorie wird mit einem umgekehrten Schrägstrich \(`\`\) vom Dateityp getrennt und die gesamte Zeichenfolge in Anführungszeichen eingeschlossen.  
  
 Um z. B. eine neue Textdatei zu erstellen, geben Sie für das Argument \/t:`templatename` Folgendes ein:  
  
```  
/t:"General\Style Sheet"  
```  
  
 \/e: `editorname`  
 Optional.  Name des Editors, in dem die Datei geöffnet wird.  Wenn zwar das Argument, aber kein Editorname angegeben wurde, wird das Dialogfeld **Öffnen mit** angezeigt.  
  
 Die Argumentsyntax \/e:`editorname` verwendet die Editornamen wie im **Dialogfeld Öffnen mit** angezeigt, wobei der Name in Anführungszeichen eingeschlossen ist.  
  
 Um ein Stylesheet im Quellcode\-Editor zu öffnen, geben Sie für das Argument \/e:`editorname` beispielsweise Folgendes ein:  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## Beispiel  
 In diesem Beispiel wird der aktuellen Projektmappe ein neues Projektmappenelement, MyHTMLpg, hinzugefügt.  
  
```  
>File.AddNewItem MyHTMLpg /t:"General\HTML Page"  
```  
  
## Siehe auch  
 [Visual Studio\-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Such\/Befehlsfeld](../../ide/find-command-box.md)   
 [Visual Studio\-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)
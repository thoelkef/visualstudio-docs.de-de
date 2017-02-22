---
title: "Befehl &quot;Neue Datei&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "file.newfile"
helpviewer_keywords: 
  - "File.NewFile-Befehl"
  - "Neue Datei (Befehl)"
ms.assetid: 767868d6-a525-425b-a43b-2198f636ab6b
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Befehl &quot;Neue Datei&quot;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Erstellt eine neue Datei und öffnet diese.  Die Datei wird im Ordner **Verschiedene Dateien** angezeigt.  
  
## Syntax  
  
```  
File.NewFile [filename] [/t:templatename] [/editor:editorname]  
```  
  
## Argumente  
 `filename`  
 Optional.  Der Name der Datei.  Wenn kein Name angegeben wird, wird ein Standardname verwendet.  Wenn kein Vorlagenname angegeben ist, wird eine Textdatei erstellt.  
  
## Schalter  
 \/t:`templatename`  
 Optional.  Gibt den Typ der zu erstellenden Datei an.  
  
 \/t: Die Argumentsyntax`templatename` die im New File Dialog Box gefunden werden.  Geben Sie den Kategorienamen gefolgt von einem umgekehrten Schrägstrich \(`\`\) und dem Vorlagennamen ein, und schließen Sie die gesamte Zeichenfolge in Anführungszeichen ein.  
  
 Um z. B. eine neue [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]\-Quelldatei zu erstellen, geben Sie für das Argument \/t:`templatename` Folgendes ein:  
  
```  
/t:"Visual C++\C++ File (.cpp)"  
```  
  
 Im Beispiel oben wird angegeben, dass die C\+\+\-Dateivorlage sich im Dialogfeld **Neue Datei** unter der Kategorie Visual C\+\+ befindet.  
  
 \/e:`editorname`  
 Optional.  Name des Editors, in dem die Datei geöffnet wird.  Wenn zwar das Argument, aber kein Editorname angegeben wurde, wird das Dialogfeld **Öffnen mit** angezeigt.  
  
 \/e: Die Argumentsyntax`editorname` der Editor verwendet, während sie im Dialogfeld Öffnen mit angezeigt, wobei der Name in Anführungszeichen eingeschlossen.  
  
 Um eine Datei im Quellcode\-Editor zu öffnen, geben Sie für das Argument \/e:`editorname` beispielsweise Folgendes ein:  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## Beispiel  
 Durch dieses Beispiel wird die neue Webseite "test1.htm" erstellt und im Quellcode\-Editor geöffnet.  
  
```  
>File.NewFile test1 /t:"General\HTML Page" /e:"Source Code (text) Editor"  
```  
  
## Siehe auch  
 [Visual Studio\-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Direktfenster](../../ide/reference/immediate-window.md)   
 [Such\/Befehlsfeld](../../ide/find-command-box.md)   
 [Visual Studio\-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)
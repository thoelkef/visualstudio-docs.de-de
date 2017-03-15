---
title: "Befehl &quot;Befehlsfensterausgaben protokollieren&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "tools.logcommandwindowoutput"
helpviewer_keywords: 
  - "Protokollieren des Befehls 'Befehlsfensterausgaben'"
  - "View.LogCommandWindowOutput-Befehl"
ms.assetid: d4ecec35-5af4-4954-8d60-2cd24583fbb4
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# Befehl &quot;Befehlsfensterausgaben protokollieren&quot;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Kopiert die gesamte Ein\- und Ausgabe aus dem **Befehlsfenster** in eine Datei.  
  
## Syntax  
  
```  
Tools.LogCommandWindowOutput [filename] [/on|/off] [/overwrite]  
```  
  
## Argumente  
 `filename`  
 Optional.  Der Name der Protokolldatei.  Standardmäßig wird die Datei im Profilordner des Benutzers erstellt.  Wenn der Dateiname bereits vorhanden ist, wird das Protokoll an das Ende der vorhandenen Datei angefügt.  Wenn keine Datei angegeben wird, wird die zuletzt angegebene Datei verwendet.  Wenn keine vorherige Datei vorhanden ist, wird eine Standardprotokolldatei mit dem Namen **cmdline.log** erstellt.  
  
> [!TIP]
>  Um den Speicherort der Protokolldatei zu ändern, geben Sie den vollständigen Pfad der Datei ein und schließen diesen in Anführungszeichen ein, sofern er Leerzeichen enthält.  
  
## Schalter  
 \/on  
 Optional.  Startet das Protokoll für das **Befehlsfenster** in der angegebenen Datei und fügt die Datei mit den neuen Informationen an.  
  
 \/off  
 Optional.  Hält die Protokollierung für das **Befehlsfenster** an.  
  
 \/overwrite  
 Optional.  Wenn die im `filename`\-Argument angegebene Datei einer vorhandenen Datei entspricht, wird diese überschrieben.  
  
## Hinweise  
 Wenn keine Datei angegeben wird, wird standardmäßig die Datei **cmdline.log** erstellt.  Standardmäßig lautet der Alias für diesen Befehl `Log`.  
  
## Beispiele  
 In diesem Beispiel wird eine neue Protokolldatei, cmdline.log, erstellt und die Befehlsprotokollierung gestartet.  
  
```  
>Tools.LogCommandWindowOutput cmdlog  
```  
  
 In diesem Beispiel wird die Protokollierung von Befehlen beendet.  
  
```  
>Tools.LogCommandWindowOutput /off  
```  
  
 In diesem Beispiel wird die Protokollierung von Befehlen in der zuvor verwendeten Protokolldatei wieder aufgenommen.  
  
```  
>Tools.LogCommandWindowOutput /on  
```  
  
## Siehe auch  
 [Visual Studio\-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Such\/Befehlsfeld](../../ide/find-command-box.md)   
 [Visual Studio\-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)
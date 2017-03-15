---
title: "Befehl &quot;Vorhandenes Projekt hinzuf&#252;gen&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "file.addexistingproject"
helpviewer_keywords: 
  - "Vorhandenes Projekt hinzufügen (Befehl)"
  - "File.AddExistingProject"
ms.assetid: 71cf3e31-c76b-405b-ad6a-1b1bc654bd40
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Befehl &quot;Vorhandenes Projekt hinzuf&#252;gen&quot;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Fügt der aktuellen Projektmappe ein vorhandenes Projekt hinzu.  
  
## Syntax  
  
```  
File.AddExistingProject filename  
```  
  
## Argumente  
 `filename`  
 Optional.  Der vollständige Pfad und Projektname mit Erweiterung des Projekts, das der aktuellen Projektmappe hinzugefügt werden soll.  
  
 Wenn das `filename`\-Argument Leerzeichen enthält, muss es in Anführungszeichen eingeschlossen werden.  
  
 Wenn kein Dateiname angegeben ist, wird durch den Befehl das Dateidialogfeld geöffnet, damit der Benutzer ein Projekt auswählen kann.  
  
## Hinweise  
 Die automatische Vervollständigung versucht, den richtigen Pfad und Dateinamen während der Eingabe zu ermitteln.  
  
## Beispiel  
 In diesem Beispiel wird der aktuellen Projektmappe das [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]\-Projekt TestProject1 hinzugefügt.  
  
```  
>File.AddExistingProject "c:\visual studio projects\TestProject1.vbproj"  
```  
  
## Siehe auch  
 [Visual Studio\-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Such\/Befehlsfeld](../../ide/find-command-box.md)   
 [Visual Studio\-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)
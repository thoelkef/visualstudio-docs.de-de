---
title: "Befehl &quot;Projekt &#246;ffnen&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "file.openproject"
helpviewer_keywords: 
  - "File.OpenProject-Befehl"
  - "op-Befehl"
  - "Projekt öffnen (Befehl)"
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Befehl &quot;Projekt &#246;ffnen&quot;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Öffnet ein vorhandenes Projekt.  
  
## Syntax  
  
```  
File.OpenProject filename  
```  
  
## Argumente  
 `filename`  
 Erforderlich.  Der vollständige Pfad und Dateiname des zu öffnenden Projekts.  
  
 Die Syntax des `filename`\-Arguments erfordert, dass Pfade, die Leerzeichen enthalten, in Anführungszeichen eingeschlossen werden.  
  
## Hinweise  
 Die automatische Vervollständigung versucht, den richtigen Pfad und Dateinamen während der Eingabe zu ermitteln.  
  
 Dieser Befehl ist nicht verfügbar, während er debuggt.  
  
## Beispiel  
 In diesem Beispiel wird das [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]\-Projekt "Test1" geöffnet.  
  
```  
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"  
```  
  
## Siehe auch  
 [Visual Studio\-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Such\/Befehlsfeld](../../ide/find-command-box.md)   
 [Visual Studio\-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)
---
title: "Befehl &quot;Projektmappe &#246;ffnen&quot; | Microsoft Docs"
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
  - "file.opensolution"
helpviewer_keywords: 
  - "File.OpenSolution-Befehl"
  - "Projektmappe öffnen (Befehl)"
ms.assetid: 61de76c8-69d7-4cdb-b605-e132f45d05d9
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Befehl &quot;Projektmappe &#246;ffnen&quot;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Öffnet eine vorhandene Projektmappe und schließt alle anderen geöffneten Projektmappen.  
  
## Syntax  
  
```  
File.OpenSolution filename  
```  
  
## Argumente  
 `Filename`  
 Erforderlich.  Der vollständige Pfad und Dateiname der zu öffnenden Projektmappe.  
  
 Die Syntax des `filename`\-Arguments erfordert, dass Pfade, die Leerzeichen enthalten, in Anführungszeichen eingeschlossen werden.  
  
## Hinweise  
 Die automatische Vervollständigung versucht, den richtigen Pfad und Dateinamen während der Eingabe zu ermitteln.  
  
## Beispiel  
 In diesem Beispiel wird die Projektmappe Test1.sln geöffnet.  
  
```  
>File.OpenSolution "c:\MySolutions\Test1\Test1.sln"  
```  
  
## Siehe auch  
 [Visual Studio\-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Such\/Befehlsfeld](../../ide/find-command-box.md)   
 [Visual Studio\-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)
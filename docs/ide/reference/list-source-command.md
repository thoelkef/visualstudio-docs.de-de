---
title: "Befehl &quot;Quelle auflisten&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Debug.ListSource"
helpviewer_keywords: 
  - "Debug.ListSource-Befehl"
  - "Quelle auflisten (Befehl)"
  - "ListSource-Befehl"
ms.assetid: e45f08d2-f4a3-49c3-9452-aa60508e2f74
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# Befehl &quot;Quelle auflisten&quot;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Zeigt die angegebenen Quellcodezeilen an.  
  
## Syntax  
  
```  
Debug.ListSource [/Count:number] [/Current] [/File:filename]  
[/Line:number] [/ShowLineNumbers:yes|no]  
```  
  
## Schalter  
 \/Count:`number`  
 Optional.  Gibt die Anzahl der anzuzeigenden Zeilen an.  
  
 \/Current  
 Optional.  Zeigt die aktuelle Zeile an.  
  
 \/File:`filename`  
 Optional.  Der Pfad der anzuzeigenden Datei.  Falls kein Dateiname angegeben wird, zeigt der Befehl den Quellcode für die Zeile der aktuellen Anweisung an.  
  
 \/Line:`number`  
 Optional.  Zeigt eine bestimmte Zeilennummer an.  
  
 \/ShowLineNumbers:`yes|no`  
 Optional.  Gibt an, ob Zeilennummern angezeigt werden sollen.  
  
## Hinweise  
  
## Beispiel  
 In diesem Beispiel wird der Quellcode aus Zeile 4 der Datei Form1.vb mit Zeilennummern angezeigt.  
  
```  
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes  
```  
  
## Siehe auch  
 [Visual Studio\-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)
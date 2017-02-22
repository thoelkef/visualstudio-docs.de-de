---
title: "Befehl &quot;Drucken&quot; | Microsoft Docs"
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
  - "debug.print"
helpviewer_keywords: 
  - "Debug.Print-Befehl"
  - "Drucken (Befehl)"
  - "Print-Methode"
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Befehl &quot;Drucken&quot;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Wertet einen Ausdruck aus oder zeigt den angegebenen Text an.  
  
## Syntax  
  
```  
Debug.Print text  
```  
  
## Argumente  
 `text`  
 Erforderlich.  Der auszuwertende Ausdruck oder anzuzeigende Text.  
  
## Hinweise  
 Sie können das Fragezeichen \(?\) als Alias für diesen Befehl verwenden.  Daher kann der Befehl  
  
```  
>Debug.Print expA  
```  
  
 beispielsweise auch wie folgt geschrieben werden  
  
```  
>? expA  
```  
  
 Beide Versionen dieses Befehls geben den aktuellen Wert des Ausdrucks `expA` zurück.  
  
## Beispiel  
  
```  
>Debug.Print varA  
```  
  
## Siehe auch  
 [Befehl "Anweisung auswerten"](../../ide/reference/evaluate-statement-command.md)   
 [Visual Studio\-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Such\/Befehlsfeld](../../ide/find-command-box.md)   
 [Visual Studio\-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)
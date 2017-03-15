---
title: "Befehl &quot;Anweisung auswerten&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.evaluatestatement"
helpviewer_keywords: 
  - "Debug.EvaluateStatement-Befehl"
  - "Anweisung auswerten (Befehl)"
ms.assetid: 032039bc-9477-4f93-9b9d-66d4be0e90f4
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Befehl &quot;Anweisung auswerten&quot;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Wertet die angegebene Anweisung aus und zeigt sie an.  
  
## Syntax  
  
```  
Debug.EvaluateStatement text   
```  
  
## Argumente  
 `text`  
 Erforderlich.  Die auszuwertende Anweisung.  
  
## Hinweise  
 Abhängig vom Fenster, das zur Eingabe des **EvaluateStatement**\-Befehls verwendet wird, wird ein Gleichheitszeichen \(\=\) als Vergleichsoperator oder als Zuweisungsoperator interpretiert.  
  
 Im **Befehlsfenster** wird ein Gleichheitszeichen \(\=\) als Vergleichsoperator interpretiert.  Wenn die Werte der Variablen `a` und `b` beispielsweise unterschiedlich sind, gibt der Befehl  
  
```  
>Debug.EvaluateStatement(a=b)  
```  
  
 den Wert `false` zurück.  
  
 Im **Direktfenster** wird ein Gleichheitszeichen \(\=\) dagegen als Zuweisungsoperator interpretiert.  Daher kann der Befehl  
  
```  
>Debug.EvaluateStatement(a=b)  
```  
  
 der Variablen `a` z. B. der Wert von Variable `b` zugewiesen.  
  
## Beispiel  
  
```  
>Debug.EvaluateStatement(a+b)  
```  
  
## Siehe auch  
 [Befehl "Drucken"](../../ide/reference/print-command.md)   
 [Visual Studio\-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Such\/Befehlsfeld](../../ide/find-command-box.md)   
 [Visual Studio\-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)
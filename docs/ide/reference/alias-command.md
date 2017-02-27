---
title: "Befehl &quot;Alias&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "tools.alias"
helpviewer_keywords: 
  - "alias-Befehl"
  - "Aliase, Visual Studio-Befehle"
  - "Befehlsaliase"
  - "Befehle, Aliase"
  - "Tools.Alias-Befehl"
ms.assetid: bdf857df-b5d5-450f-8c10-a6fd4dccc130
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Befehl &quot;Alias&quot;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Erstellt einen neuen Alias für einen vollständigen Befehl, einen vollständigen Befehl und seine Argumente oder für einen anderen Alias.  
  
> [!TIP]
>  Bei Eingabe von `>alias` ohne Argumente wird die aktuelle Liste der Aliase mit den jeweiligen Definitionen angezeigt.  
  
## Syntax  
  
```  
Tools.Alias [/delete] [/reset] [aliasname] [aliasstring]  
```  
  
## Argumente  
 `aliasname`  
 Optional.  Der Name für den neuen Alias.  Wenn für `aliasname` kein Wert angegeben wird, wird eine Liste der aktuellen Aliase und ihrer Definitionen angezeigt.  
  
 `aliasstring`  
 Optional.  Der vollständige Befehlsname oder der Name des vorhandenen Alias sowie alle Parameter, für die Sie einen Alias erstellen möchten.  Wenn für `aliasstring` kein Wert angegeben wird, werden der Aliasname und die Aliaszeichenfolge für den angegebenen Alias angezeigt.  
  
## Schalter  
 \/delete oder \/del oder \/d  
 Optional.  Löscht den angegebenen Alias und entfernt ihn aus der automatischen Vervollständigung.  
  
 \/reset  
 Optional.  Setzt die Liste der vordefinierten Aliase auf die ursprünglichen Einstellungen zurück.  Das bedeutet, dass alle vordefinierten Aliase wiederhergestellt und alle benutzerdefinierten Aliase entfernt werden.  
  
## Hinweise  
 Da Aliase Befehle darstellen, müssen sie sich am Anfang der Befehlszeile befinden.  
  
 Wenn Sie diesen Befehl geben, sollten Sie die Schalter unmittelbar nach dem Befehl hinzufügen und nicht erst nach den Aliasen, da der Schalter andernfalls als Teil der Aliaszeichenfolge einbezogen wird.  
  
 Vor der Wiederherstellung der Aliase werden Sie vom `/reset`\-Schalter aufgefordert, den Vorgang zu bestätigen.  Es gibt keine Kurzform für `/reset`.  
  
## Beispiele  
 In diesem Beispiel wird der neue Alias `upper` für den vollständigen Befehl "Edit.MakeUpperCase" erstellt.  
  
```  
>Tools.Alias upper Edit.MakeUpperCase  
```  
  
 In diesem Beispiel wird der Alias `upper` gelöscht.  
  
```  
>Tools.alias /delete upper  
```  
  
 In diesem Beispiel wird eine Liste aller aktuellen Aliase und Definitionen angezeigt.  
  
```  
>Tools.Alias  
```  
  
## Siehe auch  
 [Visual Studio\-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Such\/Befehlsfeld](../../ide/find-command-box.md)   
 [Visual Studio\-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)
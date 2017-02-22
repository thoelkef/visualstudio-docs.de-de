---
title: "Befehl &quot;Arbeitsspeicher auflisten&quot; | Microsoft Docs"
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
  - "debug.listmemory"
helpviewer_keywords: 
  - "Debug.ListMemory-Befehl"
  - "Arbeitsspeicher auflisten (Befehl)"
  - "ListMemory-Befehl"
ms.assetid: a84de361-a6a6-4f6d-96aa-a0d4a424371e
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Befehl &quot;Arbeitsspeicher auflisten&quot;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Zeigt den Inhalt des angegebenen Speicherbereichs an.  
  
## Syntax  
  
```  
Debug.ListMemory [/ANSI|Unicode] [/Count:number] [/Format:formattype]  
[/Hex|Signed|Unsigned] [expression]  
```  
  
## Argumente  
 `expression`  
 Optional.  Die Speicheradresse, an der die Anzeige des Arbeitsspeichers beginnen soll.  
  
## Schalter  
 \/ANSI&#124;Unicode  
 Optional.  Zeigt den Arbeitsspeicher in Form von Zeichen an, die den Bytes des Arbeitsspeichers, entweder ANSI oder Unicode, entsprechen.  
  
 \/Count:`number`  
 Optional.  Bestimmt, wie viele Bytes des Arbeitsspeichers, beginnend mit `expression`, angezeigt werden sollen.  
  
 \/Format:`formattype`  
 Optional.  Formattyp für das Anzeigen von Arbeitsspeicherinformationen im Fenster **Arbeitsspeicher**; kann die Werte OneByte, TwoBytes, FourBytes, EightBytes, Float \(32\-bit\) oder Double \(64\-bit\) annehmen.  Wenn OneByte verwendet wird, steht `/Unicode` nicht zur Verfügung.  
  
 \/Hex&#124;Signed&#124;Unsigned  
 Optional.  Gibt das Format für die Anzeige von Zahlen an: mit Vorzeichen, ohne Vorzeichen oder hexadezimal.  
  
## Hinweise  
 Anstatt einen **Debug.ListMemory**\-Befehl mit allen Schaltern vollständig auszuschreiben, können Sie ihn auch über vordefinierte Aliase aufrufen, die über bestimmte, auf spezifische Werte voreingestellte Schalter verfügen.  Anstelle der folgenden Eingabe:  
  
```  
>Debug.ListMemory /Format:float /Count:30 /Unicode  
```  
  
 können Sie Folgendes schreiben:  
  
```  
>df /Count:30 /Unicode  
```  
  
 Liste der verfügbaren Aliase für den **Debug.ListMemory**\-Befehl:  
  
|Alias|Befehl und Schalter|  
|-----------|-------------------------|  
|**d**|Debug.ListMemory|  
|**da**|Debug.ListMemory \/Ansi|  
|**db**|Debug.ListMemory \/Format:OneByte|  
|**dc**|Debug.ListMemory \/Format:FourBytes \/Ansi|  
|**dd**|Debug.ListMemory \/Format:FourBytes|  
|**df**|Debug.ListMemory\/Format:Float|  
|**dq**|Debug.ListMemory \/Format:EightBytes|  
|**du**|Debug.ListMemory \/Unicode|  
  
## Beispiel  
  
```  
>Debug.ListMemory /Format:float /Count:30 /Unicode  
```  
  
## Siehe auch  
 [Befehl "Aufrufliste auflisten"](../../ide/reference/list-call-stack-command.md)   
 [Befehl "Threads auflisten"](../../ide/reference/list-threads-command.md)   
 [Visual Studio\-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Such\/Befehlsfeld](../../ide/find-command-box.md)   
 [Visual Studio\-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)
---
title: "Unknown argument for &#39;:&#39; operator. Complete Regular Expression required in search string. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.0x800A00BE"
  - "vs.message.VS_E_RE_SPECIALUNKNOWN"
ms.assetid: 8cbc2f7f-7ea1-4803-904c-1f716cd36376
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Unknown argument for &#39;:&#39; operator. Complete Regular Expression required in search string.
Im Allgemeinen tritt dieser Fehler beim Suchen oder Ersetzen auf, wenn in einer Suchzeichenfolge reguläre Ausdrücke oder Platzhalter verwendet werden.  Der Operator Doppelpunkt \(`:`\) wurde eingegeben, das nachfolgende Argument war jedoch kein gültiges Argument.  
  
> [!NOTE]
>  Bei Argumenten für den Operator Doppelpunkt \(`:`\) muss die Groß\- und Kleinschreibung beachtet werden.  
  
### So beheben Sie diesen Fehler  
  
1.  Schlagen Sie die korrekte Syntax für reguläre Ausdrücke im Thema "Reguläre Ausdrücke" nach.  
  
2.  Überprüfen Sie die Groß\- und Kleinschreibung des Arguments.  
  
3.  Wenn Sie einen Eingabemethoden\-Editor \(IME\) verwenden, vergewissern Sie sich, dass das Argument keine normal breiten Zeichen verwendet.  
  
## Siehe auch  
 [Verwenden von regulären Ausdrücken in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md)   
 [NIB: Find and Replace, Quick Find](http://msdn.microsoft.com/de-de/dad03582-4931-4893-83ba-84b37f5b1600)   
 [Suchen in Dateien](../ide/find-in-files.md)
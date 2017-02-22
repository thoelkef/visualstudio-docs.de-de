---
title: "Erweiterte Suchoperatoren in Suchausdr&#252;cken | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Help Viewer 2.0, Suchcode"
  - "Help Viewer 2.0, Suchcode nach Programmiersprache"
  - "Help Viewer 2.0, Schlüsselwortsuche"
  - "Help Viewer 2.0, Titelsuche"
  - "Codesuche [Help Viewer 2.0]"
  - "Titelsuche [Help Viewer 2.0]"
ms.assetid: 0cdc1746-8481-45ec-9c53-d0d89cdcbd5e
caps.latest.revision: 9
caps.handback.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Erweiterte Suchoperatoren in Suchausdr&#252;cken
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Durch Verwendung der erweiterten Suchoperatoren können Sie die Suche nach Inhalten weiter eingrenzen, indem Sie komplexere Suchausdrücke aus einfacheren erstellen.  Wie die folgende Tabelle zeigt, schränken diese Operatoren den Kontext ein, in dem eine Abfrage ausgeführt wird.  
  
> [!WARNING]
>  Sie müssen erweiterte Suchoperatoren mit einem abschließenden Doppelpunkt und ohne Leerzeichen vor dem Doppelpunkt eingeben, damit das Suchmodul diese erkennt.  
  
|So suchen Sie|Verwendung|Beispiel|Ergebnis|  
|-------------------|----------------|--------------|--------------|  
|Ein Begriff im Titel des Themas|Titel:|Titel:BinaryReader|Themen, die "binaryreader" in ihren Titeln enthalten.|  
|Ein Begriff in einem Codebeispiel|Code:|code:readdouble|Themen, die "readdouble" in einem Codebeispiel enthalten.|  
|Ein Begriff in einem Beispiel zu einer bestimmten Programmiersprache|code:vb:|code:vb:string|Themen, die "Zeichenfolge" in einem Visual Basic\-Beispiel enthalten.|  
|Ein Thema, das mit einem bestimmten Schlüsselwort des Indexes verknüpft ist|Schlüsselwort:|keyword:readbyte|Themen, die mit dem "readbyte"\-Indexschlüsselwort verknüpft sind.|  
  
 Sie können den Code\-Operator verwenden, um Inhalte zu einigen Programmiersprachen zu suchen. Ergebnisse werden aber nur für Inhalte zurückgegeben, die mit einer bestimmten Programmiersprache gekennzeichnet sind.  In der folgenden Tabelle werden die Programmiersprachen aufgelistet, die dieser Operator unterstützt:  
  
|Programmiersprache|Verwendung|  
|------------------------|----------------|  
|Visual Basic|code:vb<br /><br /> oder<br /><br /> code:visualbasic|  
|C\#|code:c\#<br /><br /> oder<br /><br /> code:csharp|  
|C\+\+|code:cpp<br /><br /> oder<br /><br /> code:C\+\+<br /><br /> oder<br /><br /> code:cplusplus|  
|F\#|code:f\#<br /><br /> oder<br /><br /> code:fsharp|  
|JavaScript|code:javascript<br /><br /> oder<br /><br /> code:js|  
|XAML|code:xaml|  
  
## Siehe auch  
 [Logische Operatoren in Suchausdrücken](../ide/logical-operators-in-search-expressions.md)   
 [Tipps zur Volltextsuche](../ide/full-text-search-tips.md)
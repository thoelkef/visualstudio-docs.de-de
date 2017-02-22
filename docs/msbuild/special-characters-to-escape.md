---
title: "Special Characters to Escape | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "special characters to escape"
  - "msbuild, special characters to escape"
ms.assetid: 5b5172c3-41e4-4f38-a16f-2aeac831a5fc
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Special Characters to Escape
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sonderzeichen müssen nur dann mit Escapezeichen versehen werden, wenn sie eine besondere Bedeutung in dem Kontext haben, in dem sie verwendet werden.  Beispielsweise ist das Sternchen \(\*\) nur in den "Include"\- und "Exclude"\-Attributen einer Elementdefinition oder in einem Aufruf von <xref:Microsoft.Build.Tasks.CreateItem> ein Sonderzeichen.  In allen anderen Fällen wird das Sternchen als einfaches Sternchen behandelt.  Obwohl sie Sternchen nicht überall in Projektdateien mit Escapezeichen versehen müssen, kann dies auch nicht schaden.  
  
 Verwenden Sie die Notation %*xx* anstelle des Sonderzeichens, wobei *xx* den Hexadezimalwert des ASCII\-Zeichens darstellt.  Wenn Sie ein Sternchen \(\*\) als Literalzeichen verwenden möchten, verwenden Sie z. B. den Wert `%2A`.  
  
 Es folgt die vollständige Liste der Sonderzeichen mit Escapezeichen:  
  
|Zeichen|Beschreibung|  
|-------------|------------------|  
|%|Prozentzeichen, für Verweise auf Metadaten verwendet.|  
|$|Dollarzeichen, für Verweise auf Eigenschaften verwendet.|  
|@|At\-Zeichen, für Verweise auf Elementlisten verwendet.|  
|\(|Öffnende runde Klammer, in Listen verwendet.|  
|\)|Schließende runde Klammer, in Listen verwendet.|  
|\`|Apostroph, in Bedingungen und anderen Ausdrücken verwendet.|  
|;|Semikolon, ein Listentrennzeichen.|  
|?|Fragezeichen, ein Platzhalterzeichen beim Beschreiben einer Dateispezifikation im Include\/Exclude\-Abschnitt eines Elements.|  
|\*|Sternchen, ein Platzhalterzeichen beim Beschreiben einer Dateispezifikation im Include\/Exclude\-Abschnitt eines Elements.|  
  
## Siehe auch  
 [How to: Escape Special Characters in MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md)   
 [MSBuild Reference](../msbuild/msbuild-reference.md)
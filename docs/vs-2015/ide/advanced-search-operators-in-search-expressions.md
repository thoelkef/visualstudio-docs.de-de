---
title: Erweiterte Suchoperatoren in Suchausdrücken | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Help Viewer 2.0, searching for keywords
- Help Viewer 2.0, searching code
- Help Viewer 2.0, searching code by programming language
- Help Viewer 2.0, searching titles
- searching code [Help Viewer 2.0]
- searching titles [Help Viewer 2.0]
ms.assetid: 0cdc1746-8481-45ec-9c53-d0d89cdcbd5e
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9c2b8df3878f67207b22127881722aedd8caae8e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54775573"
---
# <a name="advanced-search-operators-in-search-expressions"></a>Erweiterte Suchoperatoren in Suchausdrücken
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mithilfe von erweiterten Suchoperatoren können Sie Ihre Suche nach Inhalten verfeinern, indem Sie aus einfachen Suchausdrücken komplexere erstellen. Wie die folgende Tabelle zeigt, schränken diese Operatoren den Kontext ein, in dem eine Abfrage ausgeführt wird.  
  
> [!WARNING]
>  Sie müssen erweiterte Suchoperatoren mit einem abschließenden Doppelpunkt eingeben. Es dürfen sich keine Leerzeichen zwischen dem Suchoperator und dem Doppelpunkt befinden, damit die Suchmaschine diesen erkennen kann.  
  
|Suchen nach|Verwendung|Beispiel|Ergebnis|  
|-------------------|---------|-------------|------------|  
|Eine Benennung im Titel des Themas|title:|title:binaryreader|Themen, die „binaryreader“ im Titel enthalten.|  
|Eine Benennung in einem Codebeispiel|code:|code:readdouble|Themen, die „readdouble“ in einem Codebeispiel enthalten.|  
|Eine Benennung in einem Beispiel einer spezifischen Programmiersprache|code:vb:|code:vb:string|Themen, die „string“ in einem Visual Basic-Beispiel enthalten.|  
|Ein Thema, das einem bestimmten Index-Schlüsselwort zugeordnet ist|Schlüsselwort:|Schlüsselwort: readbyte|Themen, die dem Indexschlüsselwort „readbyte“ zugeordnet sind.|  
  
 Sie können den Operator code: verwenden, um Inhalt zu einer beliebigen Programmiersprache zu suchen. Es werden allerdings nur Ergebnisse für Inhalt zurückgegeben, der mit einer spezifischen Programmiersprache markiert ist. Die folgende Tabelle enthält die Programmiersprachen, die dieser Operator unterstützt:  
  
|Programmiersprache|Verwendung|  
|--------------------------|---------|  
|Visual Basic|code:vb<br /><br /> oder<br /><br /> code:visualbasic|  
|C#|code:c#<br /><br /> oder<br /><br /> code:csharp|  
|C++|code:cpp<br /><br /> oder<br /><br /> code:c++<br /><br /> oder<br /><br /> code:cplusplus|  
|F#|code:f#<br /><br /> oder<br /><br /> code:fsharp|  
|JavaScript|code:javascript<br /><br /> oder<br /><br /> code:js|  
|XAML|code:xaml|  
  
## <a name="see-also"></a>Siehe auch  
 [Logische Operatoren in Suchausdrücken](../ide/logical-operators-in-search-expressions.md)   
 [Tipps zur Volltextsuche](../ide/full-text-search-tips.md)

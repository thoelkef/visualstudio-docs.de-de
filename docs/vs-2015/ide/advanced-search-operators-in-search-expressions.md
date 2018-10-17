---
title: Erweiterte Suchoperatoren in Suchausdrücken | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 706d6d89d46a1e5db4f94c2e7d5e35ace73e1bac
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49177986"
---
# <a name="advanced-search-operators-in-search-expressions"></a>Erweiterte Suchoperatoren in Suchausdrücken
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mithilfe von erweiterten Suchoperatoren können Sie Ihre Suche nach Inhalten verfeinern, indem Sie aus einfachen Suchausdrücken komplexere erstellen. Wie die folgende Tabelle zeigt, schränken diese Operatoren den Kontext ein, in dem eine Abfrage ausgeführt wird.  
  
> [!WARNING]
>  Sie müssen erweiterte Suchoperatoren mit einem abschließenden Doppelpunkt eingeben. Es dürfen sich keine Leerzeichen zwischen dem Suchoperator und dem Doppelpunkt befinden, damit die Suchmaschine diesen erkennen kann.  
  
|Suchen nach|Mit|Beispiel|Ergebnis|  
|-------------------|---------|-------------|------------|  
|Eine Benennung im Titel des Themas|title:|title:binaryreader|Themen, die "Binaryreader" im Titel enthalten.|  
|Eine Benennung in einem Codebeispiel|code:|code:readdouble|Themen, die „readdouble“ in einem Codebeispiel enthalten.|  
|Eine Benennung in einem Beispiel einer spezifischen Programmiersprache|code:vb:|code:vb:string|Themen, "String" in Visual Basic-Beispiel enthalten.|  
|Ein Thema, das einem bestimmten Index-Schlüsselwort zugeordnet ist|Schlüsselwort:|Schlüsselwort: readbyte|Themen, die den Index-Schlüsselwort "Readbyte" zugeordnet sind.|  
  
 Sie können den Operator code: verwenden, um Inhalt zu einer beliebigen Programmiersprache zu suchen. Es werden allerdings nur Ergebnisse für Inhalt zurückgegeben, der mit einer spezifischen Programmiersprache markiert ist. Die folgende Tabelle enthält die Programmiersprachen, die dieser Operator unterstützt:  
  
|Programmiersprache|Mit|  
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




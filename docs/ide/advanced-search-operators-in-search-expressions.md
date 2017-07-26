---
title: "Erweiterte Suchoperatoren in Suchausdrücken | Microsoft-Dokumentation"
ms.custom: 
ms.date: 06/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Help Viewer 2.0, searching for keywords
- Help Viewer 2.0, searching code
- Help Viewer 2.0, searching code by programming language
- Help Viewer 2.0, searching titles
- searching code [Help Viewer 2.0]
- searching titles [Help Viewer 2.0]
ms.assetid: 0cdc1746-8481-45ec-9c53-d0d89cdcbd5e
caps.latest.revision: 9
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 07ff2413503209d6ade252ac89dbfbe2589e7e85
ms.openlocfilehash: 7ad9c78134c337445a3e9180ad27234b7bcb07cc
ms.contentlocale: de-de
ms.lasthandoff: 06/02/2017

---
# <a name="advanced-search-operators-in-search-expressions"></a>Erweiterte Suchoperatoren in Suchausdrücken
Mithilfe von erweiterten Suchoperatoren in Help Viewer können Sie Ihre Suche nach Inhalten eingrenzen, indem Sie aus einfachen Suchausdrücken komplexere erstellen. Wie die folgende Tabelle zeigt, schränken diese Operatoren den Kontext ein, in dem eine Abfrage ausgeführt wird.  

> [!WARNING]
>  Sie müssen erweiterte Suchoperatoren mit einem abschließenden Doppelpunkt eingeben. Es dürfen sich keine Leerzeichen zwischen dem Suchoperator und dem Doppelpunkt befinden, damit die Suchmaschine diesen erkennen kann.  

|Suchen nach|Verwendung|Beispiel|Ergebnis|  
|-------------------|---------|-------------|------------|  
|Eine Benennung im Titel des Themas|title:|title:binaryreader|Themen, die „Binaryreader“ im Titel enthalten.|  
|Eine Benennung in einem Codebeispiel|code:|code:readdouble|Themen, die „readdouble“ in einem Codebeispiel enthalten.|  
|Eine Benennung in einem Beispiel einer spezifischen Programmiersprache|code:vb:|code:vb:string|Themen, die „string“ in einem Visual Basic-Beispiel enthalten.|  
|Ein Thema, das einem bestimmten Index-Schlüsselwort zugeordnet ist|Schlüsselwort:|Schlüsselwort: readbyte|Themen, die dem Index-Schlüsselwort „readbyte“ zugeordnet sind.|  

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


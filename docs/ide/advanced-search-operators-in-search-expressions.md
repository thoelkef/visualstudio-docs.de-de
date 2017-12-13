---
redirect_url: /visualstudio/ide/logical-operators-in-search-expressions
ms.openlocfilehash: fe896af873197c95a4b226396e0b6333fdc40cfa
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2017
---
Title: "Erweiterte Suchoperationen in Suchausdrücken | Microsoft-Dokumentation" ms.custom: "" ms.date: "2.6.2017" ms.reviewer: "" ms.suite: "" ms.technology: 
  - "vs-help-viewer" ms.tgt_pltfrm: "" ms.topic: "Artikel" helpviewer_keywords: 
  - „Help Viewer, Schlüsselwortsuche“
  - „Help Viewer, Codesuche“
  - „Help Viewer, Suchcode nach Programmiersprache“
  - „Help Viewer, Titelsuche“
  - „Codesuche [Help Viewer]“
  - „Titelsuche [Help Viewer]“ ms.assetid: 0cdc1746-8481-45ec-9c53-d0d89cdcbd5e caps.latest.revision: 9 author: "gewarren" ms.author: "gewarren" manager: ghogen
---
# <a name="advanced-search-operators-in-search-expressions"></a>Erweiterte Suchoperatoren in Suchausdrücken
Mit erweiterten Suchoperatoren im Help Viewer können Sie Ihre Suche nach Inhalt optimieren, indem Sie festlegen, in welchem Bereich des Themas nach dem Suchbegriff gesucht werden soll. In der folgenden Tabelle werden die vier verfügbaren erweiterten Suchoperatoren veranschaulicht.

|Suchen nach|Verwendung|Beispiel|Ergebnis|  
|-------------------|---------|-------------|------------|  
|Eine Benennung im Titel des Themas|title:|title:binaryreader|Themen, die „Binaryreader“ im Titel enthalten.|  
|Eine Benennung in einem Codebeispiel|code:|code:readdouble|Themen, die „readdouble“ in einem Codebeispiel enthalten.|  
|Eine Benennung in einem Beispiel einer spezifischen Programmiersprache|code:vb:|code:vb:string|Themen, die „string“ in einem Visual Basic-Codebeispiel enthalten.|  
|Ein Thema, das einem bestimmten Index-Schlüsselwort zugeordnet ist|Schlüsselwort:|Schlüsselwort: readbyte|Themen, die dem Index-Schlüsselwort „readbyte“ zugeordnet sind.|  

> [!WARNING]
>  Sie müssen erweiterte Suchoperatoren mit einem abschließenden Doppelpunkt eingeben. Es dürfen sich keine Leerzeichen zwischen dem Suchoperator und dem Doppelpunkt befinden, damit die Suchmaschine diesen erkennen kann.    

## <a name="programming-languages-for-code-examples"></a>Programmiersprachen für Codebeispiele
Sie können den Codeoperator verwenden, um Inhalt zu einer beliebigen Programmiersprache zu suchen. Es werden allerdings nur Ergebnisse für Inhalt zurückgegeben, der mit einer spezifischen Programmiersprachenbezeichnung markiert ist. Verwenden Sie einen der folgenden Programmiersprachenwerte, um Beispiele für eine bestimmte Programmiersprache zurückzugeben:  

|Programmiersprache|Suchoperatorsyntax|  
|--------------------|---------|  
|Visual Basic|code:vb<br/>code:visualbasic|  
|C#|code:c#<br/>code:csharp|  
|C++|code:cpp<br/>code:c++<br/>code:cplusplus|  
|F#|code:f#<br/>code:fsharp|  
|JavaScript|code:javascript<br/>code:js|  
|XAML|code:xaml|

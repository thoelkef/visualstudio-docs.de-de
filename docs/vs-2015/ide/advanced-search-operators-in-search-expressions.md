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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c5088fc04f4440260bdb9d3f040d99061c05d243
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72620337"
---
# <a name="advanced-search-operators-in-search-expressions"></a>Erweiterte Suchoperatoren in Suchausdrücken
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mit erweiterten Such Operatoren können Sie Ihre Suche nach Inhalten verfeinern, indem Sie kompliziertere Such Ausdrücke aus einfacheren Such Ausdrücken erstellen. Wie die folgende Tabelle zeigt, schränken diese Operatoren den Kontext ein, in dem eine Abfrage ausgeführt wird.

> [!WARNING]
> Sie müssen erweiterte Suchoperatoren mit einem abschließenden Doppelpunkt eingeben. Es dürfen sich keine Leerzeichen zwischen dem Suchoperator und dem Doppelpunkt befinden, damit die Suchmaschine diesen erkennen kann.

|Suchen nach|Mit|Beispiel|Ergebnis|
|-------------------|---------|-------------|------------|
|Eine Benennung im Titel des Themas|title:|title:binaryreader|Themen, die „binaryreader“ im Titel enthalten.|
|Eine Benennung in einem Codebeispiel|code:|code:readdouble|Themen, die „readdouble“ in einem Codebeispiel enthalten.|
|Eine Benennung in einem Beispiel einer spezifischen Programmiersprache|code:vb:|code:vb:string|Themen, die „string“ in einem Visual Basic-Beispiel enthalten.|
|Ein Thema, das einem bestimmten Index-Schlüsselwort zugeordnet ist|Schlüsselwort:|Schlüsselwort: readbyte|Themen, die dem Indexschlüsselwort „readbyte“ zugeordnet sind.|

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
 [Logische Operatoren in Such Ausdrücken](../ide/logical-operators-in-search-expressions.md) [Volltext-Such Tipps](../ide/full-text-search-tips.md)

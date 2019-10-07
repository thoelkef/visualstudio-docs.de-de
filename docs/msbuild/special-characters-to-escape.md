---
title: Sonderzeichen mit Escapezeichen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- special characters to escape
- msbuild, special characters to escape
ms.assetid: 5b5172c3-41e4-4f38-a16f-2aeac831a5fc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ca7df1c087e35fd188461382e4f44de6ab703964
ms.sourcegitcommit: 16175e0cea6af528e9ec76f0b94690faaf1bed30
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2019
ms.locfileid: "71481955"
---
# <a name="special-characters-to-escape"></a>Sonderzeichen mit Escapezeichen
Sonderzeichen müssen nur dann mit Escapezeichen versehen werden, wenn sie eine besondere Bedeutung in dem Kontext haben, in dem sie verwendet werden. Beispielsweise ist das Sternchen (*) nur in den "Include"- und "Exclude"-Attributen einer Elementdefinition oder in einem Aufruf von <xref:Microsoft.Build.Tasks.CreateItem> ein Sonderzeichen. In allen anderen Fällen wird das Sternchen als einfaches Sternchen behandelt. Obwohl sie Sternchen nicht überall in Projektdateien mit Escapezeichen versehen müssen, kann dies auch nicht schaden.

 Verwenden Sie die Notation %\<xx> anstelle des Sonderzeichens, wobei \<xx> den Hexadezimalwert des ASCII-Zeichens darstellt. Wenn Sie ein Sternchen (*) als Literalzeichen verwenden möchten, verwenden Sie z. B. den Wert `%2A`.

 Es folgt die vollständige Liste der Sonderzeichen mit Escapezeichen:

|Zeichen|BESCHREIBUNG|
|---------------|-----------------|
|%|Prozentzeichen, für Verweise auf Metadaten verwendet.|
|$|Dollarzeichen, für Verweise auf Eigenschaften verwendet.|
|@|At-Zeichen, für Verweise auf Elementlisten verwendet.|
|(|Öffnende runde Klammer, in Listen verwendet.|
|)|Schließende runde Klammer, in Listen verwendet.|
|;|Semikolon, ein Listentrennzeichen.|
|?|Fragezeichen, ein Platzhalterzeichen beim Beschreiben einer Dateispezifikation im Include/Exclude-Abschnitt eines Elements.|
|*|Sternchen, ein Platzhalterzeichen beim Beschreiben einer Dateispezifikation im Include/Exclude-Abschnitt eines Elements.|

> [!NOTE]
> In einigen Szenarios müssen Sie doppelte gerade Anführungszeichen (") möglicherweise mit Escapezeichen versehen, beispielsweise bei der Verwendung solcher Zeichen innerhalb eines `Exec`-Tasks.

## <a name="see-also"></a>Siehe auch
- [Vorgehensweise: Escapesonderzeichen in MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md)
- [MSBuild-Referenz](../msbuild/msbuild-reference.md)

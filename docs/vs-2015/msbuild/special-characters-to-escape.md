---
title: Sonderzeichen mit Escapezeichen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- special characters to escape
- msbuild, special characters to escape
ms.assetid: 5b5172c3-41e4-4f38-a16f-2aeac831a5fc
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e2701c698d795f1af1f888e677362bb2cf248111
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54782461"
---
# <a name="special-characters-to-escape"></a>Sonderzeichen mit Escapezeichen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Sonderzeichen müssen nur dann mit Escapezeichen versehen werden, wenn sie eine besondere Bedeutung in dem Kontext haben, in dem sie verwendet werden. Beispielsweise ist das Sternchen (*) nur in den "Include"- und "Exclude"-Attributen einer Elementdefinition oder in einem Aufruf von <xref:Microsoft.Build.Tasks.CreateItem> ein Sonderzeichen. In allen anderen Fällen wird das Sternchen als einfaches Sternchen behandelt. Obwohl sie Sternchen nicht überall in Projektdateien mit Escapezeichen versehen müssen, kann dies auch nicht schaden.  
  
 Verwenden Sie die Notation %*xx* anstelle des Sonderzeichens, wobei *xx* den Hexadezimalwert des ASCII-Zeichens darstellt. Wenn Sie ein Sternchen (*) als Literalzeichen verwenden möchten, verwenden Sie z. B. den Wert `%2A`.  
  
 Es folgt die vollständige Liste der Sonderzeichen mit Escapezeichen:  
  
|Zeichen|Beschreibung|  
|---------------|-----------------|  
|%|Prozentzeichen, für Verweise auf Metadaten verwendet.|  
|$|Dollarzeichen, für Verweise auf Eigenschaften verwendet.|  
|@|At-Zeichen, für Verweise auf Elementlisten verwendet.|  
|(|Öffnende runde Klammer, in Listen verwendet.|  
|)|Schließende runde Klammer, in Listen verwendet.|  
|`|Apostroph, in Bedingungen und anderen Ausdrücken verwendet.|  
|;|Semikolon, ein Listentrennzeichen.|  
|?|Fragezeichen, ein Platzhalterzeichen beim Beschreiben einer Dateispezifikation im Include/Exclude-Abschnitt eines Elements.|  
|*|Sternchen, ein Platzhalterzeichen beim Beschreiben einer Dateispezifikation im Include/Exclude-Abschnitt eines Elements.|  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Escapesonderzeichen in MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md)   
 [MSBuild-Referenz](../msbuild/msbuild-reference.md)

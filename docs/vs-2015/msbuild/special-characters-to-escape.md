---
title: Sonderzeichen mit Escapezeichen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: c851c6968418356626a69830ea89a918edc2cadf
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49251224"
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




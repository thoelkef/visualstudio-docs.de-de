---
title: FxCopCmd-Fehler | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- FxCopCmd errors
ms.assetid: bb614ed0-1b7c-4b56-99ae-da50ef6cfef9
caps.latest.revision: 12
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b5c7b62ce9e117b348daaa54da3d397346b6eab0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58956947"
---
# <a name="fxcopcmd-errors"></a>FxCopCmd-Fehler
FxCopCmd werden alle schwerwiegenden Fehler nicht berücksichtigt. Wenn FxCopCmd genügend Informationen zum Ausführen einer partiellen Analysis hat, führt es die Analyse- und Berichten aufgetretenen. Der Fehlercode, der eine 32-Bit-Ganzzahl ist, enthält eine bitweise Kombination von numerischen Werten, die Fehlern entsprechen.  
  
 Die folgende Tabelle beschreibt die Fehlercodes von FxCopCmd zurückgegeben:  
  
|Fehler|Numerischer Wert|  
|-----------|-------------------|  
|Keine Fehler|0x0|  
|Analysefehler.|0x1|  
|Ausnahmen von Netzwerkregeln|0x2|  
|Fehler beim Laden des Projekts|0x4|  
|Fehler beim Laden der Assembly|0x8|  
|Fehler beim Laden von Regel-Bibliothek|0x10|  
|Fehler beim Laden von Import-Bericht|0x20|  
|Ausgabefehler|0x40|  
|Befehlszeilenfehler switch|0x80|  
|Initialisierungsfehler|0x100|  
|Assembly-Verweise-Fehler|0x200|  
|BuildBreakingMessage|0x400|  
|Unbekannter Fehler|0x1000000|  
  
 Der Analysis-Fehler wird für schwerwiegende Fehler zurückgegeben. Er gibt an, dass die Analyse nicht abgeschlossen werden konnte. Der Fehlercode enthält ggf. auch die zugrunde liegende Ursache des schwerwiegenden Fehlers. Die folgenden Bedingungen schwerwiegende Fehler zu generieren:  
  
-   Die Analyse konnte nicht als Eingabedaten reichen ausgeführt werden.  
  
-   Die Analyse ausgelöst hat, eine Ausnahme, die nicht von FxCopCmd behandelt wird.  
  
-   Die angegebene Projektdatei wurde nicht gefunden oder ist beschädigt.  
  
-   Die Output-Option wurde nicht angegeben oder die Datei konnte nicht geschrieben werden.  
  
    > [!NOTE]
    >  Die FxCopCmd Rückgabecode "Fehler" 0 x 200 allein ist eher eine Warnung als Fehler. Dieser Rückgabecode gibt an, dass fehlende indirekte Verweise gefunden wurden jedoch, dass FxCopCmd diese behandeln konnte. Es ist eine Warnung, dass es besteht die Möglichkeit, dass einige Analyseergebnisse gefährdet sein könnte. Betrachten Sie die Rückgabecode "Verweist auf Fehler der Assembly" als Fehler, zusammen mit anderen Rückgabecode.  
  
## <a name="see-also"></a>Siehe auch  
 [Anwendungsfehler bei der Codeanalyse](../code-quality/code-analysis-application-errors.md)
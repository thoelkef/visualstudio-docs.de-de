---
title: FxCopCmd-Fehler | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- FxCopCmd errors
ms.assetid: bb614ed0-1b7c-4b56-99ae-da50ef6cfef9
caps.latest.revision: 12
ms.author: mikejo
manager: douge
ms.openlocfilehash: 828805e0746fb985ea310b755cdaaa252e215a07
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51751722"
---
# <a name="fxcopcmd-errors"></a>FxCopCmd-Fehler
FxCopCmd werden alle schwerwiegenden Fehler nicht berücksichtigt. Wenn FxCopCmd genügend Informationen zum Ausführen einer partiellen Analysis hat, führt es die Analyse- und Berichten aufgetretenen. Der Fehlercode, der eine 32-Bit-Ganzzahl ist, enthält eine bitweise Kombination von numerischen Werten, die Fehlern entsprechen.  
  
 Die folgende Tabelle beschreibt die Fehlercodes von FxCopCmd zurückgegeben:  
  
|Fehler|Numerischer Wert|  
|-----------|-------------------|  
|Keine Fehler|0x0|  
|Analysefehler.|0x1|  
|Ausnahmen von Netzwerkregeln|0x2|  
|Fehler beim Laden des Projekts|0 x 4|  
|Fehler beim Laden der Assembly|0x8|  
|Fehler beim Laden von Regel-Bibliothek|0x10|  
|Fehler beim Laden von Import-Bericht|0x20|  
|Ausgabefehler|0 x 40|  
|Befehlszeilenfehler switch|0x80|  
|Initialisierungsfehler|0 x 100|  
|Assembly-Verweise-Fehler|0 x 200|  
|BuildBreakingMessage|0 x 400|  
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
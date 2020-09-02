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
ms.openlocfilehash: 3e0770654f564c57cf576666dcd9575f47d9ce1c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "64787277"
---
# <a name="fxcopcmd-errors"></a>FxCopCmd-Fehler
"FxCopCmd" berücksichtigt nicht alle Fehler als schwerwiegend. Wenn FxCopCmd über ausreichende Informationen zum Ausführen einer partiellen Analyse verfügt, führt es die Analyse durch und meldet Fehler, die aufgetreten sind. Der Fehlercode, bei dem es sich um eine 32-Bit-Ganzzahl handelt, enthält eine bitweise Kombination numerischer Werte, die Fehlern entsprechen.  
  
 In der folgenden Tabelle werden die von FxCopCmd zurückgegebenen Fehlercodes beschrieben:  
  
|Fehler|Numerischer Wert|  
|-----------|-------------------|  
|Keine Fehler|0x0|  
|Analysefehler|0x1|  
|Regelausnahmen|0x2|  
|Fehler beim Laden des Projekts|0x4|  
|Fehler beim Laden der Assembly|0x8|  
|Fehler beim Laden der Regel Bibliothek.|0x10|  
|Fehler beim Laden des Berichts|0x20|  
|Ausgabefehler|0x40|  
|Fehler beim Wechseln der Befehlszeile.|0x80|  
|Initialisierungsfehler|0x100|  
|Assemblyverweifehler|0x200|  
|Buildbreakingmessage|0x400|  
|Unbekannter Fehler.|0x1000000|  
  
 Der Analysefehler wird für schwerwiegende Fehler zurückgegeben. Gibt an, dass die Analyse nicht abgeschlossen werden konnte. Der Fehlercode enthält ggf. auch die zugrunde liegende Ursache des schwerwiegenden Fehlers. Die folgenden Bedingungen generieren schwerwiegende Fehler:  
  
- Die Analyse konnte aufgrund unzureichender Eingaben nicht durchgeführt werden.  
  
- Die Analyse hat eine Ausnahme ausgelöst, die von FxCopCmd nicht behandelt wird.  
  
- Die angegebene Projektdatei wurde nicht gefunden oder ist beschädigt.  
  
- Die Output-Option wurde nicht angegeben, oder die Datei konnte nicht geschrieben werden.  
  
    > [!NOTE]
    > Der FxCopCmd-Rückgabecode "Assemblyverweisfehler" 0x200 allein ist eine Warnung und kein Fehler. Dieser Rückgabecode gibt an, dass fehlende indirekte Verweise gefunden wurden, aber von FxCopCmd verarbeitet werden konnte. Es ist eine Warnung, dass es möglich ist, dass einige Analyseergebnisse kompromittiert wurden. Beachten Sie, dass der Rückgabecode "Assemblyverweise Fehler" als Fehler angezeigt wird, wenn er mit einem anderen Rückgabecode kombiniert wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anwendungsfehler bei der Codeanalyse](../code-quality/code-analysis-application-errors.md)
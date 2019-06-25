---
title: FxCopCmd-Fehler
ms.date: 10/19/2016
ms.topic: reference
helpviewer_keywords:
- FxCopCmd errors
ms.assetid: bb614ed0-1b7c-4b56-99ae-da50ef6cfef9
ms.author: gewarren
author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a40d4b7baa3d994ca41213a100881e5f509a5167
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62816487"
---
# <a name="fxcopcmd-tool-errors"></a>FxCopCmd-Tool-Fehler

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

**Analysefehler** für schwerwiegende Fehler zurückgegeben wird. Er gibt an, dass die Analyse nicht abgeschlossen werden konnte. Der Fehlercode enthält ggf. auch die zugrunde liegende Ursache des schwerwiegenden Fehlers. Die folgenden Bedingungen schwerwiegende Fehler zu generieren:

- Die Analyse konnte aufgrund unzureichender Eingabe nicht ausgeführt werden.

- Die Analyse ausgelöst hat, eine Ausnahme, die nicht von FxCopCmd behandelt wird.

- Die angegebene Projektdatei wurde nicht gefunden oder ist beschädigt.

- Die Output-Option wurde nicht angegeben oder die Datei konnte nicht geschrieben werden.

> [!NOTE]
> Die FxCopCmd Rückgabecode **Assemblyverweise Fehler** 0 x 200 allein ist eher eine Warnung als Fehler. Dieser Rückgabecode gibt an, dass, die es indirekte Verweise fehlen jedoch, dass FxCopCmd sie verarbeiten können. Die Warnung bedeutet, dass es besteht die Möglichkeit, dass einige Analyseergebnisse gefährdet sein könnte. Behandeln **Assemblyverweise Fehler** als einen Fehler, wenn es mit einem anderen Rückgabecode kombiniert wird.

## <a name="see-also"></a>Siehe auch

- [Anwendungsfehler bei der Codeanalyse](../code-quality/code-analysis-application-errors.md)
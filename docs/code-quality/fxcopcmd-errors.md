---
title: FxCopCmd-Fehler | Microsoft Docs
ms.date: 10/19/2016
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- FxCopCmd errors
ms.assetid: bb614ed0-1b7c-4b56-99ae-da50ef6cfef9
ms.author: gewarren
author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7a53f8810331a678cb84958e1a1269767064b478
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="fxcopcmd-tool-errors"></a>FxCopCmd-Tool-Fehler

Alle schwerwiegenden Fehler berücksichtigt FxCopCmd nicht. Wenn FxCopCmd ausreichende Informationen, um eine partielle Analysen verfügt, führt es aufgetretenen Fehler Analysen und Berichte. Der Fehlercode, der eine 32-Bit-Ganzzahl ist, enthält eine bitweise Kombination von numerischen Werten, die Fehlern entsprechen.

Die folgende Tabelle beschreibt die Fehlercodes von FxCopCmd zurückgegeben:

|Fehler|Numerischer Wert|
|-----------|-------------------|
|Keine Fehler|0x0|
|Analysefehler|0x1|
|Regelausnahmen|0x2|
|Fehler beim Laden des Projekts|0 x 4|
|Fehler beim Laden der Assembly|0x8|
|Fehler beim Laden des Regel-Bibliothek|0x10|
|Fehler beim Laden des Berichts importieren|0x20|
|Ausgabefehler|0 x 40|
|Befehlszeilenfehler switch|0x80|
|Initialisierungsfehler|0 x 100|
|Assembly-Verweise-Fehler|0 x 200|
|BuildBreakingMessage|0 x 400|
|Unbekannter Fehler|0 x 1000000|

**Analysefehler** für schwerwiegende Fehler zurückgegeben wird. Er gibt an, dass die Analyse nicht abgeschlossen werden konnte. Sofern zutreffend, enthält den Fehlercode auch die zugrunde liegende Ursache des schwerwiegenden Fehlers an. Die folgenden Bedingungen generieren, bei denen schwerwiegende Fehler:

- Die Analyse konnte aufgrund unzureichender Eingabe nicht ausgeführt werden.

- Die Analyse ausgelöst hat, eine Ausnahme, die nicht von FxCopCmd behandelt wird.

- Die angegebene Projektdatei konnte nicht gefunden oder ist beschädigt.

- Die Output-Option wurde nicht angegeben oder die Datei konnte nicht geschrieben werden.

> [!NOTE]
> Der FxCopCmd-Rückgabecode **Assemblyverweise Fehler** 0 x 200 allein ist eher eine Warnung als Fehler. Diesen Rückgabecode gibt an, die es indirekte Verweise fehlen jedoch, dass FxCopCmd, zu deren Behandlung konnte. Die Warnung bedeutet, dass es besteht die Möglichkeit, dass einige Analyseergebnisse gefährdet sein könnte. Behandeln **Assemblyverweise Fehler** als einen Fehler, wenn es mit anderen Rückgabecode kombiniert wird.

## <a name="see-also"></a>Siehe auch

- [Anwendungsfehler bei der Codeanalyse](../code-quality/code-analysis-application-errors.md)
---
title: FxCopCmd-Fehler | Microsoft Docs
ms.date: 10/19/2016
ms.technology: vs-ide-code-analysis
ms.topic: article
helpviewer_keywords:
- FxCopCmd errors
ms.assetid: bb614ed0-1b7c-4b56-99ae-da50ef6cfef9
ms.author: gewarren
author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b407167a772a82b56c39ba222dc3c1f563f5c012
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/03/2018
---
# <a name="fxcopcmd-tool-errors"></a>FxCopCmd-Tool-Fehler

Alle schwerwiegenden Fehler berücksichtigt FxCopCmd nicht. Wenn FxCopCmd ausreichende Informationen, um eine partielle Analysen verfügt, führt es aufgetretenen Fehler Analysen und Berichte. Der Fehlercode, der eine 32-Bit-Ganzzahl ist, enthält eine bitweise Kombination von numerischen Werten, die Fehlern entsprechen.

Die folgende Tabelle beschreibt die Fehlercodes von FxCopCmd zurückgegeben:

|Fehler|Numerischer Wert|
|-----------|-------------------|
|Keine Fehler|0x0|
|Analysefehler|0x1|
|Regelausnahmen|0x2|
|Fehler beim Laden des Projekts|0x4|
|Fehler beim Laden der Assembly|0x8|
|Fehler beim Laden des Regel-Bibliothek|0x10|
|Fehler beim Laden des Berichts importieren|0x20|
|Ausgabefehler|0x40|
|Befehlszeilenfehler switch|0x80|
|Initialisierungsfehler|0x100|
|Assembly-Verweise-Fehler|0x200|
|BuildBreakingMessage|0x400|
|Unbekannter Fehler|0x1000000|

**Analysefehler** für schwerwiegende Fehler zurückgegeben wird. Er gibt an, dass die Analyse nicht abgeschlossen werden konnte. Sofern zutreffend, enthält den Fehlercode auch die zugrunde liegende Ursache des schwerwiegenden Fehlers an. Die folgenden Bedingungen generieren, bei denen schwerwiegende Fehler:

- Die Analyse konnte aufgrund unzureichender Eingabe nicht ausgeführt werden.

- Die Analyse ausgelöst hat, eine Ausnahme, die nicht von FxCopCmd behandelt wird.

- Die angegebene Projektdatei konnte nicht gefunden oder ist beschädigt.

- Die Output-Option wurde nicht angegeben oder die Datei konnte nicht geschrieben werden.

> [!NOTE]
> Der FxCopCmd-Rückgabecode **Assemblyverweise Fehler** 0 x 200 allein ist eher eine Warnung als Fehler. Diesen Rückgabecode gibt an, die es indirekte Verweise fehlen jedoch, dass FxCopCmd, zu deren Behandlung konnte. Die Warnung bedeutet, dass es besteht die Möglichkeit, dass einige Analyseergebnisse gefährdet sein könnte. Behandeln **Assemblyverweise Fehler** als einen Fehler, wenn es mit anderen Rückgabecode kombiniert wird.

## <a name="see-also"></a>Siehe auch

- [Anwendungsfehler bei der Codeanalyse](../code-quality/code-analysis-application-errors.md)
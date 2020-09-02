---
title: Tipps zur Volltextsuche | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- hv_search
helpviewer_keywords:
- Help Viewer 2.0, full-text search tips
- full-text search tips [Help Viewer 2.0]
ms.assetid: bcaad23d-2ca7-4bec-8b54-b884bc34e70b
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ac683ff6e7079478d5b4e642918df4e281a53f0b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72645654"
---
# <a name="full-text-search-tips"></a>Tipps zur Volltextsuche
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eins der besonders nützlichen Verfahren zum Finden von Informationen in der Hilfe ist das Ausführen einer Volltextsuche. Um Ihre Ergebnisse einzugrenzen und anzupassen, müssen Sie verstehen, welchen Einfluss Syntax auf Ihre Abfrage hat. Dieses Thema stellt Tipps, Vorgehensweisen und detaillierte Syntaxinformationen vor, mit denen Sie bessere Abfragen erstellen können.

## <a name="full-text-search-tips"></a>Tipps zur Volltextsuche
 Sie können zielgerichtetere Suchen erstellen, die nur die für Sie interessanten Themen zurückgeben, wenn Sie wissen, wie die Hilfe die Formatierung interpretiert, die Sie in Abfragen verwenden. Zu diesen Formaten zählen Sonderzeichen, reservierte Wörter und Filter.

### <a name="general-guidelines"></a>Allgemeine Richtlinien
 Die folgende Tabelle enthält einige einfache Regeln und Richtlinien für das Entwickeln von Suchabfragen in der Hilfe.

|Syntax|BESCHREIBUNG|
|------------|-----------------|
|Groß- und Kleinschreibung|Groß-/Kleinschreibung wird bei Suchvorgängen nicht beachtet. Entwickeln Sie Ihre Suchkriterien mit Groß-oder Kleinbuchstaben. Beispielsweise werden für „OLE“ und „ole“ die gleichen Ergebnisse zurückgegeben.|
|Zeichenkombinationen|Sie können nicht nur nach einzelnen Buchstaben (a–z) oder Ziffern (0–9) suchen. Wenn Sie versuchen, nach bestimmten reservierten Wörtern zu suchen, wie etwa „und“, „von“ und „mit“, werden diese ignoriert. Weitere Informationen finden Sie unter „Bei der Suche ignorierte Wörter (Stoppwörter)“ weiter unten in diesem Thema.|
|Auswertungsreihenfolge|Suchabfragen werden von links nach rechts ausgewertet.|

### <a name="search-syntax"></a>Suchsyntax
 Wenn Sie eine Suchzeichenfolge angeben, die mehrere Wörter umfasst, wie etwa „Wort1 Wort2“, ist diese Zeichenfolge äquivalent zu der Eingabe „Wort1 UND Wort2“, die nur Themen zurückgibt, die alle einzelnen Wörter in der Suchzeichenfolge enthalten.

> [!IMPORTANT]
> 1. Die Suche nach Ausdrücken wird nicht unterstützt. Wenn Sie in einer Suchzeichenfolge mehr als ein Wort angeben, enthalten die zurückgegebenen Themen alle angegebenen Wörter, aber nicht unbedingt genau den Ausdruck, den Sie angegeben haben.
>    2. Verwenden Sie logische Operatoren, um die Beziehung zwischen den Wörtern in Ihrem Suchausdruck anzugeben. Sie können logische Operatoren, wie etwa UND, ODER, NICHT und NAH eingeben, um Ihre Suche weiter einzugrenzen. Wenn Sie beispielsweise nach „Deklarieren NAH Vereinigungsmenge“ suchen, enthalten die Suchergebnisse Themen, die die Wörter „Deklarieren“ und „Vereinigungsmenge“ durch nicht mehr als ein paar Wörter getrennt enthalten. Weitere Informationen finden Sie unter [logische Operatoren in Such Ausdrücken](../ide/logical-operators-in-search-expressions.md).

### <a name="filters"></a>Filter
 Sie können die Suchergebnisse weiter eingrenzen, indem Sie erweiterte Suchoperatoren verwenden. Die Hilfe enthält drei Kategorien, die Sie zum Filtern von Ergebnissen einer Volltextsuche verwenden können: Titel, Code und Schlüsselwort. Weitere Informationen finden sie unter [Erweiterte Suchoperatoren in Suchausdrücken](../ide/advanced-search-operators-in-search-expressions.md).

### <a name="ranking-of-search-results"></a>Rangfolge von Suchergebnissen
 Der Suchalgorithmus wendet bestimmte Kriterien an, um einen höheren oder niedrigeren Rang von Suchergebnissen in der Ergebnisliste auszuweisen. Im Allgemeinen:

1. Inhalte, die Suchwörter im Titel enthalten, haben einen höheren Rang als Inhalte, auf die das nicht zutrifft.

2. Inhalte die Suchwörter in großer Nähe zueinander enthalten, erhalten einen höheren Rang als Inhalte, auf die das nicht zugrifft.

3. Inhalte, die eine höhere Dichte der Suchwörter aufweisen, erhalten einen höheren Rang als Inhalte mit einer geringeren Dichte der Suchwörter.

### <a name="words-ignored-in-searches-stop-words"></a>Bei der Suche ignorierte Wörter (Stoppwörter)
 Häufig auftretende Wörter oder Ziffern, die manchmal als Stoppwörter bezeichnet werden, werden bei der Volltextsuche automatisch ignoriert. Wenn Sie beispielsweise nach dem Ausdruck „übergeben durch“ suchen, zeigen die Suchergebnisse Themen an, die das Wort „übergeben“ enthalten, ignorieren aber das Wort „durch“.

## <a name="see-also"></a>Weitere Informationen
 Suchen von logischen [Informations](../ide/locate-information.md) [Operatoren in Such Ausdrücken](../ide/logical-operators-in-search-expressions.md)

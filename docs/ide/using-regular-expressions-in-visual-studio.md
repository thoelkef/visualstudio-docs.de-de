---
title: Reguläre Ausdrücke verwenden
ms.date: 03/26/2018
ms.topic: conceptual
f1_keywords:
- vsregularexpressionhelp
- vs.regularexpressionhelp
- vs.wildcardsbuilder
- vs.netregularexpressionhelp
- vs.wildcards
helpviewer_keywords:
- regular expressions [Visual Studio]
- regular expressions
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5fc2e1afa95c56dda79296a24f027fb93d62c585
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747742"
---
# <a name="use-regular-expressions-in-visual-studio"></a>Verwenden von regulären Ausdrücken in Visual Studio

Visual Studio verwendet [reguläre Ausdrücke von .NET](/dotnet/standard/base-types/regular-expressions) zum Suchen und Ersetzen von Text.

## <a name="replacement-patterns"></a>Ersetzungsmuster

Umschließen Sie die Gruppe mit Klammern im Muster für reguläre Ausdrücke, um eine nummerierte Erfassungsgruppe zu verwenden. Verwenden Sie `$number`, wenn `number` eine ganze Zahl ist, beginnend mit 1, um eine bestimmte nummerierte Gruppe in einem Ersetzungsmuster anzugeben. Der gruppierte reguläre Ausdruck `(\d)([a-z])` definiert beispielsweise zwei Gruppen: die erste Gruppe enthält eine einzelne Dezimalstelle, und die zweite Gruppe enthält ein einzelnes Zeichen zwischen **a** und **z**. Der Ausdruck findet vier Übereinstimmungen in der folgenden Zeichenfolge: **1a 2b 3c 4d**. Die Ersatzzeichenfolge `z$1` verweist nur auf die erste Gruppe und konvertiert die Zeichenfolge in **z1 z2 z3 z4**.

Weitere Informationen zu regulären Ausdrücken, die in Ersetzungsmustern verwendet werden, finden Sie unter [Ersetzungen in regulären Ausdrücken (Leitfaden für .NET)](/dotnet/standard/base-types/substitutions-in-regular-expressions).

## <a name="regular-expression-examples"></a>Beispiele für reguläre Ausdrücke

Hier einige Beispiele:

|Zweck|Ausdruck|Beispiel|
|-------------|----------------|-------------|
|Übereinstimmung mit beliebigem Zeichen (mit Ausnahme des Zeilenumbruchs)|sein.|`a.o` findet „aro“ in „around“ und „abo“ in „about“, jedoch nicht „acro“ in „across“.|
|Übereinstimmung mit keinem oder mehreren Vorkommen des vorhergehenden Ausdrucks (wobei die Übereinstimmung möglichst viele Zeichen umfasst).|*|`a*r` findet „r“ in „rack“, „ar“ in „ark“ und „aar“ in „aardvark“.|
|Keine oder häufigere Übereinstimmung mit beliebigem Zeichen (Platzhalter *)|.*|`c.*e` findet „cke“ in „racket“, „comme“ in „comment“ und „code“ in „code“.|
|Übereinstimmung mit einem oder mehreren Vorkommen des vorhergehenden Ausdrucks (wobei die Übereinstimmung möglichst viele Zeichen umfasst).|+|`e.+d` findet „eed“ in „feeder“, jedoch nicht „ed“.|
|Ein- oder mehrmalige Übereinstimmung mit beliebigem Zeichen (Platzhalter ?)|.+|`e.+e` findet „eede“ in „feeder“, jedoch nicht „ee“.|
|Übereinstimmung mit keinem oder mehreren Vorkommen des vorhergehenden Ausdrucks (wobei die Übereinstimmung möglichst wenig Zeichen umfasst).|*?|`e.*?e` findet „ee“ in „feeder“, jedoch nicht „eede“.|
|Übereinstimmung mit einem oder mehreren Vorkommen des vorhergehenden Ausdrucks (wobei die Übereinstimmung möglichst wenig Zeichen umfasst).|+?|`e.+?e` findet „ente“ und „erprise“ in „enterprise“, jedoch nicht das vollständige Wort „enterprise“.|
|Verankert die übereinstimmende Zeichenfolge am Anfang einer Zeile oder Zeichenfolge.|^|`^car` findet das Wort „car“ nur, wenn es am Anfang einer Zeile angezeigt wird.|
|Verankert die übereinstimmende Zeichenfolge am Ende einer Zeile|\r?$|`end\r?$` findet „end“ nur, wenn es am Ende einer Zeile angezeigt wird.|
|Verankern der übereinstimmende Zeichenfolge am Ende der Datei|$|`end$` findet „end“ nur, wenn es am Ende der Datei vorkommt.|
|Übereinstimmung mit beliebigem Zeichen in einem Satz|[abc]|`b[abc]` findet „ba“, „bb“ und „bc“.|
|Übereinstimmung mit beliebigem Zeichen in einem Bereich von Zeichen|[a-f]|`be[n-t]` findet „bet“ in „between“, „ben“ in „beneath“ und „bes“ in „beside“, jedoch nicht „bel“ in „below“.|
|Erfassung und implizite Nummerierung des in Klammern befindlichen Ausdrucks|()|`([a-z])X\1` findet „aXa“ und „bXb“, jedoch nicht „aXb“. „\1“ bezieht sich auf die erste Ausdrucksgruppe „[a-z]“.|
|Aufheben der Gültigkeit einer Übereinstimmung|(?!abc)|`real(?!ity)` findet „real“ in „realty“ und „really“, jedoch nicht in „reality“. Findet außerdem das zweite "real" (jedoch nicht das erste "real") in "realityreal".|
|Übereinstimmung mit beliebigem Zeichen, das sich nicht in einem angegebenen Satz von Zeichen befindet|[^abc]|`be[^n-t]` findet „bef“ in „before“, „beh“ in „behind“ und „bel“ in „below“, jedoch nicht „beneath“.|
|Übereinstimmung mit dem Ausdruck vor oder nach dem Symbol.|&#124;|`(sponge\|mud) bath` findet „sponge bath“ und „mud bath“.|
|Versehen des Zeichens hinter dem umgekehrten Schrägstrich mit Escapezeichen| \\ |`\^` findet das Zeichen „^“.|
|Angeben der Anzahl von Vorkommen des vorherigen Zeichens oder der Gruppe|{x}, wobei x die Anzahl von Vorkommen ist|`x(ab){2}x` findet „xababx“ und `x(ab){2,3}x` findet „xababx“ und „xabababx“, jedoch nicht „xababababx“.|
|Übereinstimmung mit Text in einer Unicode-Zeichenklasse. Weitere Informationen zu Unicode-Zeichenklassen finden Sie unter<br /><br /> [Unicode Standard 5.2 Character Properties (Unicode-Standard 5.2-Zeicheneigenschaften)](http://www.unicode.org/versions/Unicode5.2.0/ch04.pdf).|\p{X}, wobei "X" die Unicode-Nummer angibt.|`\p{Lu}` findet „T“ und „D“ in „Thomas Doe“.|
|Übereinstimmung mit einer Wortgrenze|\b (Außerhalb einer Zeichenklasse gibt `\b` eine Wortgrenze, innerhalb einer Zeichenklasse gibt `\b` eine Rücktaste an.)|`\bin` findet „in“ in „inside“, jedoch nicht „pinto“.|
|Übereinstimmung mit Zeilenumbruch (d.h. ein Wagenrücklaufzeichen gefolgt von einer neuen Zeile).|\r?\n|`End\r?\nBegin` findet „End“ und „Begin“ nur, wenn „End“ als letzte Zeichenfolge in einer Zeile vorkommt und „Begin“ als erste Zeichenfolge in der nächsten Zeile.|
|Übereinstimmung mit beliebigem alphanumerischen Zeichen|\w|`a\wd` findet „add“ und „a1d“, jedoch nicht „a d“.|
|Übereinstimmung mit beliebigem Leerzeichen.|\s|`Public\sInterface` findet den Begriff „Public Interface“.|
|Übereinstimmung mit beliebigem numerischen Zeichen|\d|`\d` findet „3“ in „3456“, „2“ in „23“ und „1“ in „1“.|
|Übereinstimmung mit einem Unicode-Zeichen|"\uXXXX", wobei "XXXX"den Unicode-Zeichenwert angibt.|`\u0065` findet das Zeichen „e“.|
|Übereinstimmung mit einem Bezeichner|\b[\_\w-[0-9]][\_\w]*\b|Findet „type1“, jedoch nicht „&type1“ oder „#define“.|
|Übereinstimmung mit einer Zeichenfolge in Anführungszeichen|((\\".+?\\")&#124;('.+?'))|Übereinstimmung mit einer beliebigen Zeichenfolge in einfachen oder doppelten Anführungszeichen|
|Übereinstimmung mit einer Hexadezimalzahl|\b0[xX]([0-9a-fA-F]+\)\b|Entspricht „0xc67f“, jedoch nicht „0xc67g“.|
|Übereinstimmung mit ganzen Zahlen und Dezimalzahlen|\b[0-9]*\\.\*[0-9]+\b|Findet "1.333".|

> [!TIP]
> In Windows-Betriebssystemen enden die meisten Zeilen auf „\r\n“ (ein Wagenrücklaufzeichen gefolgt von einer neuen Zeile). Diese Zeichen sind nicht sichtbar, aber im Editor vorhanden und werden an den .NET-Dienst regulärer Ausdrücke übergeben.

## <a name="see-also"></a>Siehe auch

- [Suchen und Ersetzen von Text](../ide/finding-and-replacing-text.md)

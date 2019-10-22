---
title: 'CA1806: Methoden Ergebnisse nicht ignorieren | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1806
- DoNotIgnoreMethodResults
helpviewer_keywords:
- CA1806
- DoNotIgnoreMethodResults
ms.assetid: fd805687-0817-481e-804e-b62cfb3b1076
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f68ab71d9ce4fab1b0612f15d866c58e302a317e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671504"
---
# <a name="ca1806-do-not-ignore-method-results"></a>CA1806: Methodenergebnisse nicht ignorieren
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotIgnoreMethodResults|
|CheckId|CA1806|
|Kategorie|Microsoft. Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Für diese Warnung gibt es mehrere mögliche Gründe:

- Ein neues-Objekt wird erstellt, aber nie verwendet.

- Eine Methode, die eine neue Zeichenfolge erstellt und zurückgibt, wird aufgerufen, und die neue Zeichenfolge wird nie verwendet.

- Eine com-oder P/aufrufen-Methode, die ein HRESULT oder einen Fehlercode zurückgibt, der niemals verwendet wird. Regelbeschreibung

  Unnötige Objekt Erstellung und zugeordnete Garbage Collection der Leistungsfähigkeit des nicht verwendeten Objekts.

  Zeichen folgen sind unveränderlich, und Methoden wie String. touppergibt eine neue Instanz einer Zeichenfolge zurück, anstatt die Instanz der Zeichenfolge in der aufrufenden Methode zu ändern.

  Das Ignorieren von HRESULT oder Fehlercode kann zu unerwartetem Verhalten bei Fehlerbedingungen oder zu Ressourcenmangel führen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Wenn Methode a eine neue Instanz eines B-Objekts erstellt, das nie verwendet wird, übergeben Sie die Instanz als Argument an eine andere Methode, oder weisen Sie die Instanz einer Variablen zu. Wenn das Erstellen eines Objekts unnötig ist, entfernen Sie es.-oder-

 Wenn method a die Methode b aufruft, verwendet jedoch nicht die neue Zeichen folgen Instanz, die von der Methode b zurückgegeben wird. Übergeben Sie die Instanz als Argument an eine andere Methode, weisen Sie die Instanz einer Variablen zu. Oder entfernen Sie den-Befehl, wenn dies unnötig ist.

 - oder -

 Wenn method a die Methode B aufruft, jedoch nicht das HRESULT oder den Fehlercode verwendet, das von der Methode zurückgegeben wird. Verwenden Sie das Ergebnis in einer Bedingungs Anweisung, weisen Sie das Ergebnis einer Variablen zu, oder übergeben Sie es als Argument an eine andere Methode.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel, es sei denn, das Erstellen des Objekts dient einem bestimmten Zweck.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Klasse, die das Ergebnis des Aufruf von String. Trim ignoriert.

<!-- TODO: review snippet reference  [!CODE [FxCop.Usage.DoNotIgnoreMethodResults#1](FxCop.Usage.DoNotIgnoreMethodResults#1)]  -->

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird der vorherige Verstoß korrigiert, indem das Ergebnis von String. Trim der Variablen zugewiesen wird, für die es aufgerufen wurde.

<!-- TODO: review snippet reference  [!CODE [FxCop.Usage.DoNotIgnoreMethodResults2#1](FxCop.Usage.DoNotIgnoreMethodResults2#1)]  -->

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Methode, die kein Objekt verwendet, das Sie erstellt.

> [!NOTE]
> Diese Verletzung kann in Visual Basic nicht reproduziert werden.

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/cpp/FxCop.Usage.DoNotIgnoreMethodResults3.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/cs/FxCop.Usage.DoNotIgnoreMethodResults3.cs#1)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/vb/FxCop.Usage.DoNotIgnoreMethodResults3.vb#1)]

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird der vorherige Verstoß behoben, indem die unnötige Erstellung eines Objekts entfernt wird.

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/cpp/FxCop.Usage.DoNotIgnoreMethodResults4.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/cs/FxCop.Usage.DoNotIgnoreMethodResults4.cs#1)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/vb/FxCop.Usage.DoNotIgnoreMethodResults4.vb#1)]

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Methode, die den Fehlercode ignoriert, den die native Methode GetShortPathName zurückgibt.

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults5/cpp/FxCop.Usage.DoNotIgnoreMethodResults5.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults5/cs/FxCop.Usage.DoNotIgnoreMethodResults5.cs#1)]

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird der vorherige Verstoß behoben, indem der Fehlercode überprüft und eine Ausnahme ausgelöst wird, wenn der-Befehl fehlschlägt.

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults6/cpp/FxCop.Usage.DoNotIgnoreMethodResults6.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults6/cs/FxCop.Usage.DoNotIgnoreMethodResults6.cs#1)]
---
title: 'CA1806: Methodenergebnisse nicht ignorieren'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1806
- DoNotIgnoreMethodResults
helpviewer_keywords:
- CA1806
- DoNotIgnoreMethodResults
ms.assetid: fd805687-0817-481e-804e-b62cfb3b1076
author: gewarren
ms.author: gewarren
dev_langs:
- CPP
- CSharp
- VB
manager: douge
ms.openlocfilehash: ebbad9eb48a448aa756f580ade794ba70eb25611
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/13/2018
ms.locfileid: "45546836"
---
# <a name="ca1806-do-not-ignore-method-results"></a>CA1806: Methodenergebnisse nicht ignorieren

|||
|-|-|
|TypeName|DoNotIgnoreMethodResults|
|CheckId|CA1806|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Es gibt mehrere mögliche Gründe für diese Warnung aus:

- Ist ein neues Objekt erstellt, aber nie verwendet.

- Eine Methode, die erstellt und gibt eine neue Zeichenfolge aufgerufen wird, und die neue Zeichenfolge wird nie verwendet.

- Eine COM- oder P/Invoke-Methode, die einen HRESULT oder den Fehlercode Code zurückgibt, der nie verwendet wird. Regelbeschreibung

Unnötige objekterstellung und die zugeordneten Garbagecollection des nicht verwendeten Objekts wird Leistung beeinträchtigt.

Zeichenfolgen sind unveränderlich, und Methoden, z. B. String.ToUpper gibt eine neue Instanz der eine Zeichenfolge anstatt in der Instanz der Zeichenfolge in der aufrufenden Methode ändern.

Wird ignoriert. HRESULT oder den Fehlercode kann zu unerwartetem Verhalten in fehlerbedingungen oder Ressourcenmangel Bedingungen führen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Wenn eine-Methode eine neue Instanz der B-Objekt, die nie verwendet wird erstellt, übergeben Sie die Instanz als Argument an eine andere Methode oder weisen Sie die Instanz einer Variablen zu. Wenn die objekterstellung nicht erforderlich ist, entfernt werden die.- oder -

 Wenn die Methode A Methode B aufruft, aber verwendet nicht die neue Zeichenfolgeninstanz, die die B-Methode zurückgibt. Übergeben Sie die Instanz als Argument an eine andere Methode, weisen Sie die Instanz einer Variablen zu. Ein, oder entfernen Sie den Aufruf aus, wenn es nicht erforderlich ist.

 - oder - 

 Wenn die Methode A Methode B aufruft, jedoch nicht den HRESULT-Wert verwendet, oder Fehlercode, die zurückgegeben der Methode. Verwenden Sie das Ergebnis in einer bedingungsanweisung, weisen Sie das Ergebnis einer Variablen oder als Argument an eine andere Methode übergeben.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie eine Warnung dieser Regel nicht, es sei denn, der Vorgang der Erstellung des Objekts einige Zweck dient.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Klasse, die das Ergebnis des Aufrufs von String.Trim ignoriert.

 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_1.cs)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/VisualBasic/ca1806-do-not-ignore-method-results_1.vb)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_1.cpp)]

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird der vorherige Verstoß korrigiert, indem das Ergebnis der String.Trim an die Variable, die, der es aufgerufen wurde.

 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_2.cs)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/VisualBasic/ca1806-do-not-ignore-method-results_2.vb)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_2.cpp)]

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Methode, die kein Objekt, das erstellt wird.

> [!NOTE]
> Diese Verletzung kann nicht in Visual Basic nicht reproduziert werden.

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_3.cpp)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_3.cs)]

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird der vorherige Verstoß korrigiert, durch das Entfernen der Erstellung eines Objekts nicht erforderlichen.

 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_4.cs)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_4.cpp)]

<!-- Examples don't exist for the below... -->
<!--
## Example
 The following example shows a method that ignores the error code that the native method GetShortPathName returns.

## Example
 The following example fixes the previous violation by checking the error code and throwing an exception when the call fails.
-->
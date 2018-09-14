---
title: 'CA1500: Variablennamen sollten nicht mit Feldnamen übereinstimmen'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- VariableNamesShouldNotMatchFieldNames
- CA1500
helpviewer_keywords:
- VariableNamesShouldNotMatchFieldNames
- CA1500
ms.assetid: fa0e5029-79e9-4a33-8576-787ac3c26c39
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 74f9cfadc4bc413c3b176d5f37f1017074547435
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548259"
---
# <a name="ca1500-variable-names-should-not-match-field-names"></a>CA1500: Variablennamen sollten nicht mit Feldnamen übereinstimmen

|||
|-|-|
|TypeName|VariableNamesShouldNotMatchFieldNames|
|CheckId|CA1500|
|Kategorie|Microsoft.Maintainability|
|Unterbrechende Änderung|Wenn für einen Parameter ausgelöst, die den gleichen Namen wie ein Feld hat folgende Aufgaben ausführen:<br /><br /> Nicht-unterbrechend – Wenn das Feld und die Methode, die den Parameter deklariert außerhalb der Assembly, unabhängig von der Änderung nicht sichtbar ist, die Sie vornehmen.<br />Unterbrechend – Wenn Sie den Namen des Felds ändern und außerhalb der Assembly angezeigt werden können.<br />-Unterbrechend – Wenn Sie den Namen des Parameters ändern und die Methode, die es deklariert außerhalb der Assembly angezeigt werden kann.<br /><br /> Wenn für eine lokale Variable ausgelöst, die den gleichen Namen wie ein Feld hat folgende Aufgaben ausführen:<br /><br /> Nicht-unterbrechend – Wenn das Feld kann nicht außerhalb der Assembly, unabhängig von der Änderung angezeigt werden, die Sie vornehmen.<br />Geringfügiger – Wenn Sie den Namen der lokalen Variablen ändern, und ändern Sie den Namen des Felds nicht.<br />-Unterbrechend – Wenn Sie den Namen des Felds ändern und ihn außerhalb der Assembly angezeigt werden kann.|

## <a name="cause"></a>Ursache

Eine Instanzmethode deklariert einen Parameter oder eine lokale Variable, deren Name eines Instanzenfelds des deklarierenden Typs übereinstimmt. Zum Abfangen von lokaler Variablen, die die Regel verletzen, muss der getestete Assembly mit Debuginformationen erstellt werden, und die zugehörigen Programmdatenbankdatei (.pdb) muss verfügbar sein.

## <a name="rule-description"></a>Regelbeschreibung

Wenn der Name eines Instanzenfelds einen Parameter oder einer lokalen Variablen übereinstimmt, erfolgt mithilfe des Instanzfelds der `this` (`Me` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)])-Schlüsselwort innerhalb des Methodentexts. Wenn Code zu verwalten, ist es einfach vergessen dieser Differenz. dabei wird vorausgesetzt, dass der Parameter/lokale Variablen auf das Instanzenfeld bezieht, was zu Fehlern führt. Dies gilt insbesondere bei langen Text.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, benennen Sie entweder die Parametervariable oder das Feld ein.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt zwei Verstöße gegen die Regel an.

[!code-vb[FxCop.Maintainability.VarMatchesField#1](../code-quality/codesnippet/VisualBasic/ca1500-variable-names-should-not-match-field-names_1.vb)]
[!code-csharp[FxCop.Maintainability.VarMatchesField#1](../code-quality/codesnippet/CSharp/ca1500-variable-names-should-not-match-field-names_1.cs)]
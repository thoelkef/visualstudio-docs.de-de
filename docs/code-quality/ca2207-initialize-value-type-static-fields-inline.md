---
title: 'CA2207: Statische Felder Werttyp Inline initialisieren'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- InitializeValueTypeStaticFieldsInline
- CA2207
helpviewer_keywords:
- CA2207
- InitializeValueTypeStaticFieldsInline
ms.assetid: d1ea9d8b-ecc2-46ca-86e2-c41dd0e76658
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ee4ffd51eef5b8a4f0523dd2356d4e0bdb29b945
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53869156"
---
# <a name="ca2207-initialize-value-type-static-fields-inline"></a>CA2207: Statische Felder Werttyp Inline initialisieren

|||
|-|-|
|TypeName|InitializeValueTypeStaticFieldsInline|
|CheckId|CA2207|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Ein Werttyp deklariert einen expliziten statischen Konstruktor.

## <a name="rule-description"></a>Regelbeschreibung
 Wenn ein Werttyp deklariert wird, durchläuft er standardmäßig initialisiert, wenn alle Felder für Werttyp auf 0 (null) festgelegt werden, und alle Verweistypfelder festgelegt sind `null` (`Nothing` in Visual Basic). Ein expliziter statischer Konstruktor ist nur garantiert vor einem Instanzenkonstruktor ausgeführt werden, oder statische Member des Typs aufgerufen wird. Aus diesem Grund, wenn der Typ erstellt wird, ohne einen Instanzkonstruktor aufrufen, wird der statische Konstruktor Ausführung nicht garantiert.

 Wenn alle statische Daten Inline initialisiert und keine expliziter statischer Konstruktor deklariert ist, fügen die C#- und Visual Basic-Compiler die `beforefieldinit` Flag, um die Definition der MSIL-Klasse. Der Compiler fügen auch einen privaten, statischen Konstruktor mit dem statischen Initialisierungscode hinzu. Diese private statische Konstruktor ist garantiert ausgeführt werden, bevor ein statisches Feld des Typs zugegriffen werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Zur Behebung wird ein Verstoß gegen diese Regel alle statische Daten initialisieren, wenn sie deklariert ist, und entfernen den statischen Konstruktor.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1810: Statische Felder von Verweistypen Inline initialisieren](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)
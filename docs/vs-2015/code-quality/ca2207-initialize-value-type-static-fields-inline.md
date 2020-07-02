---
title: 'CA2207: statische Felder für Werttyp Inline initialisieren | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- InitializeValueTypeStaticFieldsInline
- CA2207
helpviewer_keywords:
- CA2207
- InitializeValueTypeStaticFieldsInline
ms.assetid: d1ea9d8b-ecc2-46ca-86e2-c41dd0e76658
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 792fe18a4f472d0b8a4fd62c652f2ae34fcf6864
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546301"
---
# <a name="ca2207-initialize-value-type-static-fields-inline"></a>CA2207: Statische Felder für Werttyp inline initialisieren.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|InitializeValueTypeStaticFieldsInline|
|CheckId|CA2207|
|Kategorie|Microsoft. Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Ein Werttyp deklariert einen expliziten statischen Konstruktor.

## <a name="rule-description"></a>Beschreibung der Regel
 Wenn ein Werttyp deklariert wird, wird eine Standard Initialisierung durchgeführt, bei der alle Werttyp Felder auf 0 (null) und alle Verweistyp Felder auf `null` ( `Nothing` in Visual Basic) festgelegt sind. Es ist nur garantiert, dass ein expliziter statischer Konstruktor ausgeführt wird, bevor ein Instanzkonstruktor oder ein statischer Member des Typs aufgerufen wird. Wenn der Typ ohne Aufruf eines Instanzkonstruktors erstellt wird, wird der statische Konstruktor daher nicht garantiert ausgeführt.

 Wenn alle statischen Daten inline initialisiert werden und kein expliziter statischer Konstruktor deklariert wird, fügen die c#-und Visual Basic Compiler das `beforefieldinit` Flag zur MSIL-Klassendefinition hinzu. Die Compiler fügen außerdem einen privaten statischen Konstruktor hinzu, der den statischen Initialisierungs Code enthält. Dieser private statische Konstruktor wird garantiert ausgeführt, bevor auf statische Felder des Typs zugegriffen wird.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, initialisieren Sie alle statischen Daten, wenn Sie deklariert werden, und entfernen Sie den statischen Konstruktor.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1810: Statische Felder von Referenztypen inline initialisieren.](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)

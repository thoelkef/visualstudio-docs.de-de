---
title: 'CA1810: Initialisieren von statischen Feldern des Verweis Typs Inline | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
helpviewer_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
ms.assetid: e9693118-a914-4efb-9550-ec659d8d97d2
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 9032ac105477370477b13554afe4ee65bd7cd733
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72609019"
---
# <a name="ca1810-initialize-reference-type-static-fields-inline"></a>CA1810: Statische Felder von Verweistypen inline initialisieren
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|InitializeReferenceTypeStaticFieldsInline|
|CheckId|CA1810|
|Kategorie|Microsoft. Performance|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein Verweistyp deklariert einen expliziten statischen Konstruktor.

## <a name="rule-description"></a>Regelbeschreibung
 Wenn ein Typ einen expliziten statischen Konstruktor deklariert, überprüft der JIT-Compiler (Just in Time) jede statische Methode und jeden Instanzenkonstruktor des Typs. Dadurch wird sichergestellt, dass der statische Konstruktor zuvor aufgerufen wurde. Die statische Initialisierung wird ausgelöst, wenn auf einen statischen Member zugegriffen wird oder wenn eine Instanz des Typs erstellt wird. Die statische Initialisierung wird jedoch nicht ausgelöst, wenn Sie eine Variable des Typs deklarieren, aber nicht verwenden. Dies kann wichtig sein, wenn die Initialisierung den globalen Zustand ändert.

 Wenn alle statischen Daten inline initialisiert werden und ein expliziter statischer Konstruktor nicht deklariert ist, fügen Microsoft Intermediate Language (MSIL)-Compiler das `beforefieldinit`-Flag und einen impliziten statischen Konstruktor, der die statischen Daten initialisiert, mit dem MSIL-Typ hinzu. Definition. Wenn der JIT-Compiler auf das `beforefieldinit`-Flag trifft, werden die statischen Konstruktorüberprüfungen meistens nicht hinzugefügt. Die statische Initialisierung wird garantiert zu einem bestimmten Zeitpunkt ausgeführt, bevor auf statische Felder zugegriffen wird, jedoch nicht, bevor eine statische Methode oder ein Instanzkonstruktor aufgerufen wird. Beachten Sie, dass die statische Initialisierung jederzeit erfolgen kann, nachdem eine Variable vom Typ deklariert wurde.

 Durch die Überprüfung statischer Konstruktoren kann die Leistung herabgesetzt werden. Häufig wird ein statischer Konstruktor nur zum Initialisieren statischer Felder verwendet. in diesem Fall müssen Sie nur sicherstellen, dass die statische Initialisierung vor dem ersten Zugriff eines statischen Felds erfolgt. Das Verhalten von `beforefieldinit` ist für diese und die meisten anderen Typen geeignet. Sie ist nur ungeeignet, wenn die statische Initialisierung den globalen Zustand beeinflusst und eine der folgenden Punkte zutrifft:

- Die Auswirkung auf den globalen Status ist aufwendig und ist nicht erforderlich, wenn der Typ nicht verwendet wird.

- Auf die globalen Zustands Effekte kann ohne Zugriff auf statische Felder des Typs zugegriffen werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, initialisieren Sie alle statischen Daten nach deren Deklaration und entfernen den statischen Konstruktor.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn die Leistung nicht relevant ist. oder, wenn globale Zustandsänderungen, die durch die statische Initialisierung verursacht werden, aufwendig sind oder garantiert werden müssen, bevor eine statische Methode des Typs aufgerufen oder eine Instanz des Typs erstellt wird.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ, `StaticConstructor`, der gegen die Regel verstößt, und einen Typ, `NoStaticConstructor`, der den statischen Konstruktor durch Inline Initialisierung ersetzt, um die Regel zu erfüllen.

 [!code-csharp[FxCop.Performance.RefTypeStaticCtor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.RefTypeStaticCtor/cs/FxCop.Performance.RefTypeStaticCtor.cs#1)]
 [!code-vb[FxCop.Performance.RefTypeStaticCtor#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.RefTypeStaticCtor/vb/FxCop.Performance.RefTypeStaticCtor.vb#1)]

 Beachten Sie, dass das `beforefieldinit`-Flag für die MSIL-Definition für die `NoStaticConstructor`-Klasse hinzugefügt wurde.

 **. Class Public Auto ANSI StaticConstructor** **erweitert [mscorlib] System. Object** 
 **{** 
 **}//Ende der Klasse StaticConstructor** 
 **. Class Public Auto ANSI beforefieldinit NoStaticConstructor** ** erweitert [mscorlib] System. Object** 
 **{** 1 **}//Ende der Klasse NoStaticConstructor**
## <a name="related-rules"></a>Verwandte Regeln
 [CA2207: Statische Felder für Werttyp inline initialisieren](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)

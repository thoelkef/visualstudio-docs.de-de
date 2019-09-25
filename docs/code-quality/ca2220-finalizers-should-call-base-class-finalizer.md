---
title: 'CA2220: Finalizer sollten Basisklassen-Finalizer aufrufen.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
helpviewer_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e5af6b7872f0fa05183334e6acd2bc4922f84990
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231160"
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220: Finalizer sollten Basisklassen-Finalizer aufrufen.

|||
|-|-|
|TypeName|FinalizersShouldCallBaseClassFinalizer|
|CheckId|CA2220|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Ein Typ, der über <xref:System.Object.Finalize%2A?displayProperty=fullName> schreibt, ruft nicht <xref:System.Object.Finalize%2A> die-Methode in der Basisklasse auf.

## <a name="rule-description"></a>Regelbeschreibung

Der Abschluss muss durch die Vererbungshierarchie weitergegeben werden. Um dies zu gewährleisten, müssen-Typen Ihre <xref:System.Object.Finalize%2A> Basisklassen Methode in Ihrer <xref:System.Object.Finalize%2A> eigenen-Methode abrufen. Der C# Compiler fügt den-Befehl dem Basisklassen-Finalizer automatisch hinzu.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, müssen Sie die- <xref:System.Object.Finalize%2A> Methode des Basistyps von Ihrer <xref:System.Object.Finalize%2A> -Methode abrufen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Unterdrücken Sie keine Warnung dieser Regel. Einige Compiler, die auf abzielen, Common Language Runtime einen-Befehl an den Finalizer des Basistyps in die Microsoft Intermediate Language (MSIL) einfügen. Wenn eine Warnung aus dieser Regel gemeldet wird, fügt der Compiler den-Befehl nicht ein, und Sie müssen ihn dem Code hinzufügen.

## <a name="example"></a>Beispiel

Im folgenden Visual Basic Beispiel wird ein Typ `TypeB` gezeigt, der die <xref:System.Object.Finalize%2A> -Methode in der-Basisklasse ordnungsgemäß aufruft.

[!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2220-finalizers-should-call-base-class-finalizer_1.vb)]

## <a name="see-also"></a>Siehe auch

- [Dispose-Muster](/dotnet/standard/design-guidelines/dispose-pattern)
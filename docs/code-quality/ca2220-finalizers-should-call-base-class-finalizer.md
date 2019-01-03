---
title: 'CA2220: Finalizer sollten Basisklassen-Finalizer aufrufen.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4befae0ca3095994c3d48d20647045d4825154e4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53825395"
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220: Finalizer sollten Basisklassen-Finalizer aufrufen.

|||
|-|-|
|TypeName|FinalizersShouldCallBaseClassFinalizer|
|CheckId|CA2220|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Ein Typ, überschreibt <xref:System.Object.Finalize%2A?displayProperty=fullName> ruft nicht die <xref:System.Object.Finalize%2A> -Methode in der Basisklasse.

## <a name="rule-description"></a>Regelbeschreibung

Der Abschluss muss durch die Vererbungshierarchie weitergegeben werden. Um dies zu gewährleisten, müssen Typen ihrer Basisklasse aufrufen <xref:System.Object.Finalize%2A> innerhalb ihrer eigenen <xref:System.Object.Finalize%2A> Methode. Den Aufruf von den Basisklassen-Finalizer wird von der C#-Compiler automatisch hinzugefügt.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, rufen Sie des Basistyps <xref:System.Object.Finalize%2A> aus Ihrem <xref:System.Object.Finalize%2A> Methode.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Unterdrücken Sie keine Warnung dieser Regel. Einige Compiler, die die common Language Runtime als Ziel legen Sie einen Aufruf der Basistyp des Finalizers in die Microsoft intermediate Language (MSIL). Wenn eine Warnung dieser Regel gemeldet wird, wird der Compiler kein Aufruf eingefügt, und müssen Sie es an Ihrem Code hinzufügen.

## <a name="example"></a>Beispiel

Das folgende Visual Basic-Beispiel zeigt ein `TypeB` ordnungsgemäß aufruft, die <xref:System.Object.Finalize%2A> -Methode in der Basisklasse.

[!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2220-finalizers-should-call-base-class-finalizer_1.vb)]

## <a name="see-also"></a>Siehe auch

- [Dispose-Muster](/dotnet/standard/design-guidelines/dispose-pattern)
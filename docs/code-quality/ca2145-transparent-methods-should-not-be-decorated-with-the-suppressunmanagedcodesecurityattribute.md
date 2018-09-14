---
title: 'CA2145: Transparente Methoden dürfen nicht mit dem SuppressUnmanagedCodeSecurity-Attribut versehen werden'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2145
ms.assetid: 81970700-b438-4b3b-9239-16887e16f7b7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9299cb67b8c08b9179375e0ce2e709f2554883b1
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547408"
---
# <a name="ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute"></a>CA2145: Transparente Methoden dürfen nicht mit dem SuppressUnmanagedCodeSecurity-Attribut versehen werden

|||
|-|-|
|TypeName|TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity|
|CheckId|CA2145|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Eine transparente Methode, eine Methode, die mit der <xref:System.Security.SecuritySafeCriticalAttribute> -Methode oder ein Typ, der eine Methode enthält, ist markiert, mit der <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> Attribut.

## <a name="rule-description"></a>Regelbeschreibung

Methoden mit ergänzt die <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> Attribut haben einen impliziten LinkDemand auf einer beliebigen Methode, die ihn aufruft. Dieser LinkDemand erfordert, dass der aufrufende Code sicherheitskritisch ist. Das Markieren der Methode, die SuppressUnmanagedCodeSecurity mit verwendet die <xref:System.Security.SecurityCriticalAttribute> Attribut macht diese Anforderung für Aufrufer der Methode leichter ersichtlich.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, markieren Sie die Methode bzw. kein Entitätstyp mit dem <xref:System.Security.SecurityCriticalAttribute> Attribut.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Unterdrücken Sie keine Warnung dieser Regel.

### <a name="code"></a>Code

[!code-csharp[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../code-quality/codesnippet/CSharp/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute_1.cs)]
---
title: 'CA1411: COM-Registrierungsmethoden dürfen nicht sichtbar sein | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1411
- ComRegistrationMethodsShouldNotBeVisible
helpviewer_keywords:
- ComRegistrationMethodsShouldNotBeVisible
- CA1411
ms.assetid: a59f96f1-1f38-4596-b656-947df5c55311
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f001a2bb4920ebfb3f5cff3745639bd346a0a920
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85540140"
---
# <a name="ca1411-com-registration-methods-should-not-be-visible"></a>CA1411: Die COM-Registrierungsmethoden dürfen nicht sichtbar sein.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|ComRegistrationMethodsShouldNotBeVisible|
|CheckId|CA1411|
|Kategorie|Microsoft. Interoperabilität|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine Methode, die mit dem- <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> Attribut oder dem-Attribut markiert ist, <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> ist extern sichtbar.

## <a name="rule-description"></a>Beschreibung der Regel
 Wenn eine Assembly mit Component Object Model (com) registriert wird, werden der Registrierung für jeden COM-sichtbaren Typ in der Assembly Einträge hinzugefügt. Methoden, die mit dem <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> -Attribut und dem-Attribut markiert sind, <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> werden während der Registrierungs-bzw. der Aufhebung der Registrierung aufgerufen, um Benutzercode auszuführen, der für die Registrierung/Aufhebung der Registrierung dieser Typen spezifisch ist. Dieser Code sollte nicht außerhalb dieser Prozesse aufgerufen werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Zugriff der-Methode in `private` oder `internal` ( `Friend` in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ).

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt zwei Methoden, die gegen die Regel verstoßen.

 [!code-csharp[FxCop.Interoperability.ComRegistration2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration2/cs/FxCop.Interoperability.ComRegistration2.cs#1)]
 [!code-vb[FxCop.Interoperability.ComRegistration2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration2/vb/FxCop.Interoperability.ComRegistration2.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1410: Die COM-Registrierungsmethoden müssen übereinstimmen.](../code-quality/ca1410-com-registration-methods-should-be-matched.md)

## <a name="see-also"></a>Weitere Informationen
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>[Registrieren von](https://msdn.microsoft.com/library/87925795-a3ae-4833-b138-125413478551) Assemblys mit com- [Regasm.exe (Assembly Registration Tool)](https://msdn.microsoft.com/library/e190e342-36ef-4651-a0b4-0e8c2c0281cb)

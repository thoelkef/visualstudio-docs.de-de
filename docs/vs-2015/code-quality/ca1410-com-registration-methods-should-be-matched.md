---
title: 'CA1410: COM-Registrierungsmethoden müssen abgeglichen werden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
helpviewer_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
ms.assetid: f3b2e62d-fd66-4093-9f0c-dba01ad995fd
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 30f507f07de858dc222b4824ac6da633c76812ab
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652742"
---
# <a name="ca1410-com-registration-methods-should-be-matched"></a>CA1410: Die COM-Registrierungsmethoden müssen übereinstimmen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ComRegistrationMethodsShouldBeMatched|
|CheckId|CA1410|
|Kategorie|Microsoft. Interoperabilität|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein Typ deklariert eine Methode, die mit dem <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName>-Attribut markiert ist, deklariert jedoch keine Methode, die mit dem <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>-Attribut markiert ist, oder umgekehrt.

## <a name="rule-description"></a>Regelbeschreibung
 Damit Component Object Model (com)-Clients einen [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]-Typ erstellen können, muss der Typ zuerst registriert werden. Wenn Sie verfügbar ist, wird eine Methode, die mit dem <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>-Attribut markiert ist, während des Registrierungsvorgangs aufgerufen, um benutzerdefinierten Code auszuführen. Eine entsprechende-Methode, die mit dem <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>-Attribut markiert ist, wird während der Aufhebung der Registrierung aufgerufen, um die Vorgänge der Registrierungsmethode umzukehren.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie die entsprechende Registrierung oder Aufhebung der Registrierung hinzu.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ, der gegen die Regel verstößt. Der kommentierte Code zeigt die Korrektur des Verstoßes.

 [!code-csharp[FxCop.Interoperability.ComRegistration#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration/cs/FxCop.Interoperability.ComRegistration.cs#1)]
 [!code-vb[FxCop.Interoperability.ComRegistration#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration/vb/FxCop.Interoperability.ComRegistration.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1411: Die COM-Registrierungsmethoden dürfen nicht sichtbar sein](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)

## <a name="see-also"></a>Siehe auch
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName> [Registrieren von Assemblys mit com](https://msdn.microsoft.com/library/87925795-a3ae-4833-b138-125413478551) [Regasm. exe (Assembly Registration Tool)](https://msdn.microsoft.com/library/e190e342-36ef-4651-a0b4-0e8c2c0281cb)

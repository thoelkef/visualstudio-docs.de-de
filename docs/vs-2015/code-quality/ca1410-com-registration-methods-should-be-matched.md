---
title: 'CA1410: die COM-Registrierungsmethoden verglichen werden soll | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
helpviewer_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
ms.assetid: f3b2e62d-fd66-4093-9f0c-dba01ad995fd
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 228c5faffc2cf3ceb48cc8c88c6cefa88f63b2cf
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49273623"
---
# <a name="ca1410-com-registration-methods-should-be-matched"></a>CA1410: Die COM-Registrierungsmethoden müssen übereinstimmen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|ComRegistrationMethodsShouldBeMatched|
|CheckId|CA1410|
|Kategorie|Microsoft.Interoperability|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein Typ deklariert eine Methode, die mit der <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> Attribut deklariert jedoch keine Methode, die mit der <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> -Attribut, oder umgekehrt.

## <a name="rule-description"></a>Regelbeschreibung
 Für Clients von Component Object Model (COM) zum Erstellen einer [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Typ, der Typ muss zuerst registriert werden. Wenn sie verfügbar ist, eine Methode, die mit der <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> -Attribut während der Registrierung zum Ausführen benutzerdefinierter Code aufgerufen wird. Eine entsprechende Methode, die mit der <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> -Attribut aufgerufen wird, bei der Aufhebung der Registrierung, der die Vorgänge von der Registrierungsmethode umzukehren.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie die entsprechende Registrierung oder das Aufheben der Registrierung-Methode.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ, der gegen die Regel verstößt. Kommentierte Code zeigt das Update für die Verletzung.

 [!code-csharp[FxCop.Interoperability.ComRegistration#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration/cs/FxCop.Interoperability.ComRegistration.cs#1)]
 [!code-vb[FxCop.Interoperability.ComRegistration#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration/vb/FxCop.Interoperability.ComRegistration.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1411: Die COM-Registrierungsmethoden dürfen nicht sichtbar sein](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)

## <a name="see-also"></a>Siehe auch
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName> [Registrieren von Assemblys bei COM](http://msdn.microsoft.com/library/87925795-a3ae-4833-b138-125413478551) [Regasm.exe (Assembly Registration-Tool)](http://msdn.microsoft.com/library/e190e342-36ef-4651-a0b4-0e8c2c0281cb)




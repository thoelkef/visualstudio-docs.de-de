---
title: 'CA2149: Transparente Methoden dürfen keine Aufrufe in nativen Code durchführen.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2149
ms.assetid: 28951bd7-f3db-4871-99aa-bad68d1ead80
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 725bf599d8d13d345767f5af4d38db619263c23d
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920383"
---
# <a name="ca2149-transparent-methods-must-not-call-into-native-code"></a>CA2149: Transparente Methoden dürfen keine Aufrufe in nativen Code durchführen.

|||
|-|-|
|TypeName|Transparentmethodsmustnotcallnativecode|
|CheckId|CA2149|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
Eine Methode ruft eine native Funktion durch einen Methodenstub wie z. b. P/Aufruf auf.

## <a name="rule-description"></a>Regelbeschreibung
Diese Regel wird für jede transparente Methode ausgelöst, die direkt in nativem Code aufruft, z. b. über einen P/-Aufruf. Verstöße gegen diese Regel führen im Transparenz <xref:System.MethodAccessException> Modell der Ebene 2 zu einer und <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> im Transparenz Modell der Ebene 1 zu einer vollständigen Anforderung.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, markieren Sie die Methode, die den nativen <xref:System.Security.SecurityCriticalAttribute> Code <xref:System.Security.SecuritySafeCriticalAttribute> mit dem-Attribut oder dem-Attribut aufruft.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
[!code-csharp[FxCop.Security.CA2149.TransparentMethodsMustNotCallNativeCode#1](../code-quality/codesnippet/CSharp/ca2149-transparent-methods-must-not-call-into-native-code_1.cs)]
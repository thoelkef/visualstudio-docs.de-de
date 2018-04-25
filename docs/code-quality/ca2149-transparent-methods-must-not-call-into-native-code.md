---
title: 'CA2149: Transparente Methoden dürfen keine Aufrufe in systemeigenen Code durchführen'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2149
ms.assetid: 28951bd7-f3db-4871-99aa-bad68d1ead80
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: c14cfff80836ebaeb8b2d0dda2298f91e913083f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="ca2149-transparent-methods-must-not-call-into-native-code"></a>CA2149: Transparente Methoden dürfen keine Aufrufe in systemeigenen Code durchführen
|||
|-|-|
|TypeName|TransparentMethodsMustNotCallNativeCode|
|CheckId|CA2149|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine Methode ruft eine systemeigene Funktion durch einen Methodenstub, z. B. P/Invoke.

## <a name="rule-description"></a>Regelbeschreibung
 Diese Regel wird für jede transparente Methode ausgelöst, die einen direkten Aufruf in systemeigenem Code ausführt, z. B. mit P/Invoke. Verstöße gegen diese Regel führen zu einem <xref:System.MethodAccessException> im Transparenzmodell der Ebene 2 zu einer vollständigen Anforderung für <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> im Transparenzmodell Ebene 1.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, markieren Sie die Methode, die Aufrufe von systemeigenem Code mit der <xref:System.Security.SecurityCriticalAttribute> oder <xref:System.Security.SecuritySafeCriticalAttribute> Attribut.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 [!code-csharp[FxCop.Security.CA2149.TransparentMethodsMustNotCallNativeCode#1](../code-quality/codesnippet/CSharp/ca2149-transparent-methods-must-not-call-into-native-code_1.cs)]
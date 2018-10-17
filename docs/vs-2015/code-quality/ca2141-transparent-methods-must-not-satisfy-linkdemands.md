---
title: 'CA2141: Transparente Methoden dürfen keine LinkDemands erfüllen | Microsoft-Dokumentation'
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
- CA2141
ms.assetid: 2957f5f7-c511-4180-ba80-752034f10a77
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8b43c907870149d3b54ed3e129d0974f2417d387
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49295801"
---
# <a name="ca2141transparent-methods-must-not-satisfy-linkdemands"></a>CA2141: Transparente Methoden dürfen keine LinkDemands erfüllen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|TransparentMethodsMustNotSatisfyLinkDemands|
|CheckId|CA2141|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine sicherheitstransparente Methode ruft eine Methode in einer Assembly, die nicht mit der <xref:System.Security.AllowPartiallyTrustedCallersAttribute> -Attribut (APTCA) oder eine sicherheitstransparente Methode erfüllt einen <xref:System.Security.Permissions.SecurityAction> `.LinkDemand` für einen Typ oder eine Methode.

## <a name="rule-description"></a>Regelbeschreibung
 Erfüllt einen LinkDemand ist einen sicherheitsrelevanten Vorgang, der unbeabsichtigten Ausweitung von Berechtigungen führen kann. Sicherheitstransparenter Code dürfen keine LinkDemands, erfüllen, da er nicht gelten die gleichen sicherheitsanforderungen für die Überwachung als sicherheitskritischem Code ist. Transparente Methoden in Sicherheit Regel Satz Assemblys der Ebene 1 führt alle LinkDemands sie erfüllen, um die in vollständige Anforderungen zur Laufzeit konvertiert werden, was zu Leistungsproblemen führen kann. In Assemblys mit Sicherheit Regel Satz Ebene 2 können transparente Methoden nicht in der just-in-Time-Compiler (JIT) kompiliert werden soll, wenn sie versuchen, einen LinkDemand zu erfüllen.

 In Assemblys, mit Sicherheit auf Ebene 2 versuchen, eine sicherheitstransparente Methode erfüllt einen LinkDemand oder Aufrufen einer Methode in einer nicht-APTCA-Assembly löst eine <xref:System.MethodAccessException>; in Assemblys der Ebene 1 die LinkDemand-Anweisung wird eine vollständige Anforderung.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, markieren Sie die Zugriffsmethode mit der <xref:System.Security.SecurityCriticalAttribute> oder <xref:System.Security.SecuritySafeCriticalAttribute> Attribut, oder entfernen Sie die LinkDemand-Anweisung aus der verwendete Methode.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 In diesem Beispiel versucht, eine transparente Methode zum Aufrufen einer Methode, die einen LinkDemand aufweist. Mit dieser Regel wird ausgelöst, in diesem Code.

 [!code-csharp[FxCop.Security.CA2141.TransparentMethodsMustNotSatisfyLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2141.transparentmethodsmustnotsatisfylinkdemands/cs/ca2141 - transparentmethodsmustnotsatisfylinkdemands.cs#1)]




---
title: 'CA2141: transparente Methoden dürfen keine LinkDemand-Anforderungen erfüllen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2141
ms.assetid: 2957f5f7-c511-4180-ba80-752034f10a77
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: bee810ed938d316e92095ad47062ed5ad9cd456f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546444"
---
# <a name="ca2141transparent-methods-must-not-satisfy-linkdemands"></a>CA2141: Transparente Methoden dürfen keine LinkDemands erfüllen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|Transparentmethodsmustnostatisfylinkdemand|
|CheckId|CA2141|
|Category|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine Sicherheits transparente Methode ruft eine Methode in einer Assembly auf, die nicht mit dem- <xref:System.Security.AllowPartiallyTrustedCallersAttribute> Attribut (APTCA) markiert ist, oder eine Sicherheits transparente Methode erfüllt einen <xref:System.Security.Permissions.SecurityAction> `.LinkDemand` für einen Typ oder eine Methode.

## <a name="rule-description"></a>Beschreibung der Regel
 Das erfüllen von LinkDemand ist ein sicherheitssensibler Vorgang, der eine unbeabsichtigte Erhöhung von Berechtigungen verursachen kann. Sicherheits transparenter Code muss linkrequirements nicht erfüllen, da er nicht denselben Sicherheits Überwachungsanforderungen unterliegt wie der sicherheitskritische Code. Transparente Methoden in Assemblys für sicherheitsregelsatz der Ebene 1 bewirken, dass alle verknüpften linkanforderungen zur Laufzeit in vollständige Anforderungen konvertiert werden. Dies kann zu Leistungsproblemen führen. In Assemblys der sicherheitsregelsatz-Ebene 2 können transparente Methoden im JIT-Compiler (Just-in-Time) nicht kompiliert werden, wenn Sie versuchen, einen LinkDemand zu erfüllen.

 In Assemblys, in denen Sicherheit der Ebene 2 angezeigt wird, löst der Versuch einer Sicherheits transparenten Methode, einen LinkDemand-oder eine Methode in einer nicht-APTCA-Assembly zu erfüllen, eine <xref:System.MethodAccessException> aus; in Assemblys der Ebene 1 wird der LinkDemand zu einer vollständigen Anforderung

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, markieren Sie die Zugriffsmethode mit dem- <xref:System.Security.SecurityCriticalAttribute> Attribut oder- <xref:System.Security.SecuritySafeCriticalAttribute> Attribut, oder entfernen Sie LinkDemand aus der Methode, auf die zugegriffen wird.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 In diesem Beispiel versucht eine transparente Methode, eine Methode aufzurufen, die über einen LinkDemand verfügt. Diese Regel wird in diesem Code ausgelöst.

 [!code-csharp[FxCop.Security.CA2141.TransparentMethodsMustNotSatisfyLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2141.transparentmethodsmustnotsatisfylinkdemands/cs/ca2141 - transparentmethodsmustnotsatisfylinkdemands.cs#1)]

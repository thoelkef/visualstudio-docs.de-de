---
title: 'CA2146: Typen müssen mindestens so kritisch sein wie ihre Basis Typen und Schnittstellen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2146
ms.assetid: 241fb784-1f6b-46e5-8ceb-c438e341d38e
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ab621ade120a257508eddbf9527f674b5fda8748
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610189"
---
# <a name="ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces"></a>CA2146: Typen müssen mindestens genauso kritisch sein wie ihre Basistypen und Schnittstellen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|Typesmustbeatleastascriticalasbasetypes|
|CheckId|CA2146|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein transparenter Typ wird von einem Typ abgeleitet, der mit dem <xref:System.Security.SecuritySafeCriticalAttribute> oder dem <xref:System.Security.SecurityCriticalAttribute> gekennzeichnet ist, oder ein Typ, der mit dem <xref:System.Security.SecuritySafeCriticalAttribute>-Attribut markiert ist, wird von einem Typ abgeleitet, der mit dem <xref:System.Security.SecurityCriticalAttribute>-Attribut markiert ist.

## <a name="rule-description"></a>Regelbeschreibung
 Diese Regel wird ausgelöst, wenn ein abgeleiteter Typ über ein Sicherheitstransparenzattribut verfügt, das nicht so wichtig wie der Basistyp oder die implementierte Schnittstelle ist. Nur wichtige Typen können von wichtigen Basistypen abgeleitet werden oder kritische Schnittstellen implementieren, und nur kritische oder sicherheitskritische Typen können von sicherheitskritischen Basistypen abgeleitet werden oder sicherheitskritische Schnittstellen implementieren. Verstöße gegen diese Regel in der Transparenz der Ebene 2 führen zu einer <xref:System.TypeLoadException> für den abgeleiteten Typ.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um diese Verletzung zu beheben, markieren Sie den abgeleiteten oder implementierenden Typ mit einem Transparenz Attribut, das mindestens so kritisch ist wie der Basistyp oder die Schnittstelle.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 [!code-csharp[FxCop.Security.CA2146.TypesMustBeAtLeastAsCriticalAsBaseTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2146.typesmustbeatleastascriticalasbasetypes/cs/ca2146 - typesmustbeatleastascriticalasbasetypes.cs#1)]

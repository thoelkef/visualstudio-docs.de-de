---
title: 'CA2144: Transparenter Code darf keine Assemblys aus Bytearrays laden'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2144
ms.assetid: 777b1310-6e16-4413-b4ee-5f3136304f82
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0ea3149d2fb01b447bd2c539f7de0d440a36fe91
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53825762"
---
# <a name="ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays"></a>CA2144: Transparenter Code darf keine Assemblys aus Bytearrays laden

|||
|-|-|
|TypeName|TransparentMethodsShouldNotLoadAssembliesFromByteArrays|
|CheckId|CA2144|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine transparente Methode lädt eine Assembly aus einem Bytearray, das mit einem der folgenden Methoden:

- <xref:System.Reflection.Assembly.Load%2A>

- <xref:System.Reflection.Assembly.Load%2A>

- <xref:System.Reflection.Assembly.Load%2A>

## <a name="rule-description"></a>Regelbeschreibung
 Die Sicherheitsüberprüfung für transparenten Code ist nicht so umfassend wie die Sicherheitsüberprüfung für wichtigen Code, da in transparentem Code keine sicherheitsrelevanten Aktionen ausgeführt werden können. Aus einem Bytearray geladene Assemblys werden in transparentem Code eventuell nicht erkannt, und dieses Bytearray könnte wichtigen oder sicherheitsgeschützten Code enthalten, der überwacht werden muss. Transparenter Code darf daher keine Assemblys aus einem Bytearray laden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Markieren Sie die Methode, die die Assembly geladen wird, um einen Verstoß gegen diese Regel zu beheben, die <xref:System.Security.SecurityCriticalAttribute> oder <xref:System.Security.SecuritySafeCriticalAttribute> Attribut.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Die Regel wird für den folgenden Code ausgelöst, da eine transparente Methode eine Assembly aus einem Bytearray geladen.

 [!code-csharp[FxCop.Security.CA2144.TransparentMethodsShouldNotLoadAssembliesFromByteArrays#1](../code-quality/codesnippet/CSharp/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays_1.cs)]
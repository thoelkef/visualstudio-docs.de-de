---
title: 'CA2151: Felder mit kritischen Typen sollten sicherheitskritisch sein | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 09db9d25-7d58-4725-a252-4a07baadf046
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c2ce99a404dacdbcc82c628f8f682c53883948ff
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/13/2018
ms.locfileid: "47590981"
---
# <a name="ca2151-fields-with-critical-types-should-be-security-critical"></a>CA2151: Felder mit kritischen Typen sollten sicherheitskritisch sein
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [CA2151: Felder mit kritischen Typen sollten sicherheitskritisch sein](https://docs.microsoft.com/visualstudio/code-quality/ca2151-fields-with-critical-types-should-be-security-critical).

|||
|-|-|
|TypeName||
|CheckId|CA2151|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein sicherheitstransparentes Feld oder ein sicherungskritisches Feld wird deklariert. Sein Typ wird als sicherheitskritisch angegeben. Zum Beispiel:

```csharp
[assembly: AllowPartiallyTrustedCallers]

   [SecurityCritical]
   class Type1 { } // Security Critical type

   class Type2 // Security transparent type
   {
      Type1 m_field; // CA2151, transparent field of critical type
   }

```

 In diesem Beispiel ist `m_field` ein sicherheitstransparentes Feld eines Typs, der sicherheitskritisch ist.

## <a name="rule-description"></a>Regelbeschreibung
 Um sicherheitskritische Typen zu verwenden, muss der Code, der auf den Typ verweist, entweder sicherheitskritisch oder sicherungskritisch sein. Dies gilt auch, wenn der Verweis indirekt ist. Wenn Sie beispielsweise auf ein transparentes Feld verweisen, das über einen kritischen Typ verfügt, muss der Code entweder sicherheitskritisch oder sicherungskritisch sein. Daher kann ein sicherheitstransparentes oder sicherungskritisches Feld irreführend sein, denn transparenter Code kann trotzdem nicht auf das Feld zugreifen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, markieren Sie das Feld mit dem <xref:System.Security.SecurityCriticalAttribute>-Attribut, oder ändern Sie den Typ, auf den durch das Feld verwiesen wird, in sicherheitstransparent oder sicherungskritisch.

```csharp
// Fix 1: Make the referencing field security critical
[assembly: AllowPartiallyTrustedCallers]

   [SecurityCritical]
   class Type1 { } // Security Critical type

   class Type2 // Security transparent type
   {
      [SecurityCritical]
      Type1 m_field; // Fixed: critical type, critical field
   }

// Fix 2: Make the referencing field security critical
[assembly: AllowPartiallyTrustedCallers]

   class Type1 { } // Type1 is now transparent

   class Type2 // Security transparent type
   {
      [SecurityCritical]
      Type1 m_field; // Fixed: critical type, critical field
   }

```

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2145.transparentmethodsshouldnotusesuppressunmanagedcodesecurity/cs/ca2145.cs#1)]

### <a name="comments"></a>Kommentare




---
title: 'CA2126: Typlinkaufrufe erfordern vererbungsanforderungen | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
helpviewer_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
ms.assetid: 07b604e5-5579-4df9-a578-dadd0d8370a7
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 254fd15f97afe69f927bb8a1aae1954105776641
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ca2126-type-link-demands-require-inheritance-demands"></a>CA2126: Typlinkaufrufe erfordern Vererbungsanforderungen
|||  
|-|-|  
|TypeName|TypeLinkDemandsRequireInheritanceDemands|  
|CheckId|CA2126|  
|Kategorie|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Ein öffentlicher unversiegelter Typ wird geschützt durch einen Linkaufruf verfügt über eine überschreibbare Methode und weder der Typ noch die Methode mit einer vererbungsanforderung geschützt ist.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Ein Linkaufruf auf eine Methode oder der deklarierende Typ erfordert den unmittelbaren Aufrufer der Methode, die angegebene Berechtigung. Eine vererbungsanforderung für eine Methode erfordert eine überschreibende Methode über die angegebene Berechtigung verfügen. Für einen Typ eine vererbungsanforderung erfordert eine abgeleitete Klasse die angegebene Berechtigung.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, Sichern Sie den Typ oder die Methode mit einer vererbungsanforderung für die gleichen Berechtigungen wie der Linkaufruf aus.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt einen Typ, der die Regel verletzt.  
  
 [!code-cpp[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/CPP/ca2126-type-link-demands-require-inheritance-demands_1.cpp)]
 [!code-vb[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/VisualBasic/ca2126-type-link-demands-require-inheritance-demands_1.vb)]
 [!code-csharp[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2126-type-link-demands-require-inheritance-demands_1.cs)]  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA2108: Deklarative Sicherheit auf Werttypen überprüfen](../code-quality/ca2108-review-declarative-security-on-value-types.md)  
  
 [CA2112: Gesicherte Typen sollten keine Felder verfügbar machen](../code-quality/ca2112-secured-types-should-not-expose-fields.md)  
  
 [CA2122: Methoden mit Linkaufrufen nicht indirekt verfügbar machen](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)  
  
 [CA2123: Überschreibungslinkaufrufe sollten mit der Basis identisch sein](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Schreiben von sicherem Richtlinien](/dotnet/standard/security/secure-coding-guidelines)   
 [Vererbungsanforderungen](http://msdn.microsoft.com/en-us/28b9adbb-8f08-4f10-b856-dbf59eb932d9)   
 [Verknüpfungsaufrufe](/dotnet/framework/misc/link-demands)   
 [Forderungen](http://msdn.microsoft.com/en-us/e5283e28-2366-4519-b27d-ef5c1ddc1f48)
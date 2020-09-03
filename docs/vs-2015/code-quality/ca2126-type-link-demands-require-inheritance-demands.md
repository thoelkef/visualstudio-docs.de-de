---
title: 'CA2126: typverknüpfungs Anforderungen erfordern Vererbungs Anforderungen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
helpviewer_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
ms.assetid: 07b604e5-5579-4df9-a578-dadd0d8370a7
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 051a041c245fae55e3d4759130c145c662734aa8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544273"
---
# <a name="ca2126-type-link-demands-require-inheritance-demands"></a>CA2126: Typlinkaufrufe erfordern Vererbungsanforderungen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|TypeLinkDemandsRequireInheritanceDemands|
|CheckId|CA2126|
|Category|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein öffentlicher unversiegelter Typ wird durch einen Link Aufruf geschützt, verfügt über eine über schreibbare Methode, und weder der Typ noch die Methode wird mit einer Vererbungs Anforderung geschützt.

## <a name="rule-description"></a>Beschreibung der Regel
 Ein Link Aufruf für eine Methode oder Ihren deklarierenden Typ erfordert, dass der unmittelbare Aufrufer der Methode über die angegebene Berechtigung verfügt. Ein Vererbungs Bedarf für eine Methode erfordert, dass eine über schreibende Methode über die angegebene Berechtigung verfügt. Ein Vererbungs Bedarf für einen Typ erfordert, dass eine abgeleitete Klasse über die angegebene Berechtigung verfügt.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, sichern Sie den Typ oder die Methode mit einer Vererbungs Anforderung für dieselbe Berechtigung wie der Link Aufruf.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ, der gegen die Regel verstößt.

 [!code-cpp[FxCop.Security.TypesWithLinkDemands#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.TypesWithLinkDemands/cpp/FxCop.Security.TypesWithLinkDemands.cpp#1)]
 [!code-csharp[FxCop.Security.TypesWithLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TypesWithLinkDemands/cs/FxCop.Security.TypesWithLinkDemands.cs#1)]
 [!code-vb[FxCop.Security.TypesWithLinkDemands#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.TypesWithLinkDemands/vb/FxCop.Security.TypesWithLinkDemands.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA2108: Deklarative Sicherheit auf Werttypen überprüfen.](../code-quality/ca2108-review-declarative-security-on-value-types.md)

 [CA2112: Gesicherte Typen sollten keine Felder verfügbar machen.](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

 [CA2122: Methoden mit Linkaufrufen nicht indirekt verfügbar machen.](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)

 [CA2123: Überschreibungslinkaufrufe sollten mit der Basis identisch sein.](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)

## <a name="see-also"></a>Weitere Informationen
 [Sichere Codierungs Richtlinien](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [Vererbung Anforderungen](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9) [Link Anforderungen](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [Anforderungen](https://msdn.microsoft.com/e5283e28-2366-4519-b27d-ef5c1ddc1f48)

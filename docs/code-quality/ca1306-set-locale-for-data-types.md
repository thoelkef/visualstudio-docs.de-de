---
title: "CA1306: Gebietsschema für Datentypen festlegen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1306
- SetLocaleForDataTypes
helpviewer_keywords:
- CA1306
- SetLocaleForDataTypes
ms.assetid: 104297b2-5806-4de0-a8d9-c589380a796c
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2a8760aa983cdd798e5ea46fa4161375f0eab7fc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ca1306-set-locale-for-data-types"></a>CA1306: Gebietsschema für Datentypen festlegen
|||  
|-|-|  
|TypeName|SetLocaleForDataTypes|  
|CheckId|CA1306|  
|Kategorie|Microsoft.Globalization|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## <a name="cause"></a>Ursache  
 Eine Methode oder ein Konstruktor erstellt eine oder mehrere <xref:System.Data.DataTable?displayProperty=fullName> oder <xref:System.Data.DataSet?displayProperty=fullName> Instanzen und die Gebietsschemaeigenschaft nicht explizit festgelegt (<xref:System.Data.DataTable.Locale%2A?displayProperty=fullName> oder <xref:System.Data.DataSet.Locale%2A?displayProperty=fullName>).  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Das Gebietsschema bestimmt kulturspezifische Darstellungselemente für Daten, z. B. für Zahlenwerte, Währungssymbole und Sortierreihenfolge verwendete Formatierung. Beim Erstellen einer <xref:System.Data.DataTable> oder <xref:System.Data.DataSet>, sollten Sie das Gebietsschema explizit festlegen. Standardmäßig ist das Gebietsschema für diese Art der aktuellen Kultur. Für Daten, die in einer Datenbank oder Datei gespeichert und Global gemeinsam genutzt wird, sollte das Gebietsschema in der Regel auf die invariante Kultur festgelegt werden (<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>). Wenn Daten über Kulturen hinweg gemeinsam verwendet werden, verwenden das Standardgebietsschema kann dazu führen, dass der Inhalt des der <xref:System.Data.DataTable> oder <xref:System.Data.DataSet> dargestellt oder falsch interpretiert werden.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, legen Sie explizit das Gebietsschema für die <xref:System.Data.DataTable> oder <xref:System.Data.DataSet>.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Sie können ruhig auf eine Warnung dieser Regel zu unterdrücken, wenn die Bibliothek oder Anwendung für eine begrenzte lokale Zielgruppe ist, die Daten nicht freigegeben werden oder die Standardeinstellung das gewünschte Verhalten in allen unterstützten Szenarien ergibt.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel erstellt zwei <xref:System.Data.DataTable> Instanzen.  
  
 [!code-csharp[FxCop.Globalization.DataTable#1](../code-quality/codesnippet/CSharp/ca1306-set-locale-for-data-types_1.cs)]  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Data.DataTable?displayProperty=fullName>   
 <xref:System.Data.DataSet?displayProperty=fullName>   
 <xref:System.Globalization.CultureInfo?displayProperty=fullName>   
 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>   
 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>
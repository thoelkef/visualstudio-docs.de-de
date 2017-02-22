---
title: "CA1306: Gebietsschema f&#252;r Datentypen festlegen | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1306"
  - "SetLocaleForDataTypes"
helpviewer_keywords: 
  - "CA1306"
  - "SetLocaleForDataTypes"
ms.assetid: 104297b2-5806-4de0-a8d9-c589380a796c
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1306: Gebietsschema f&#252;r Datentypen festlegen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SetLocaleForDataTypes|  
|CheckId|CA1306|  
|Kategorie \(Category\)|Microsoft.Globalization|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Durch eine Methode oder einen Konstruktor wurden eine oder mehrere <xref:System.Data.DataTable?displayProperty=fullName>\-Instanzen oder <xref:System.Data.DataSet?displayProperty=fullName>\-Instanzen erstellt, und die Gebietsschemaeigenschaft \(<xref:System.Data.DataTable.Locale%2A?displayProperty=fullName> oder <xref:System.Data.DataSet.Locale%2A?displayProperty=fullName>\) wurde nicht explizit festgelegt.  
  
## Regelbeschreibung  
 Das Gebietsschema bestimmt kulturspezifische Darstellungselemente für Daten wie die für Zahlenwerte, Währungssymbole und Sortierreihenfolge verwendete Formatierung.  Wenn Sie eine <xref:System.Data.DataTable> oder ein <xref:System.Data.DataSet> erstellen, sollten Sie das Gebietsschema explizit festlegen.  Standardmäßig wird die aktuelle Kultur als Gebietsschema für diese Typen verwendet.  Für Daten, die in einer Datenbank oder Datei gespeichert sind und global freigegeben werden, sollte das Gebietsschema in der Regel auf die unveränderliche Kultur \(<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>\) festgelegt werden.  Wenn Daten in verschiedenen Kulturen freigegeben werden, wird der Inhalt der <xref:System.Data.DataTable> oder des <xref:System.Data.DataSet> bei Verwendung des Standardgebietsschemas unter Umständen falsch dargestellt oder interpretiert.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, legen Sie das Gebietsschema für die <xref:System.Data.DataTable> oder das <xref:System.Data.DataSet> explizit fest.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos unterdrückt werden, wenn die Bibliothek oder Anwendung für eine begrenzte lokale Zielgruppe bestimmt ist, wenn die Daten nicht freigegeben werden oder wenn die Standardeinstellung in allen unterstützten Szenarien das gewünschte Verhalten zeigt.  
  
## Beispiel  
 Im folgenden Beispiel werden zwei <xref:System.Data.DataTable>\-Instanzen erstellt.  
  
 [!code-cs[FxCop.Globalization.DataTable#1](../code-quality/codesnippet/CSharp/ca1306-set-locale-for-data-types_1.cs)]  
  
## Siehe auch  
 <xref:System.Data.DataTable?displayProperty=fullName>   
 <xref:System.Data.DataSet?displayProperty=fullName>   
 <xref:System.Globalization.CultureInfo?displayProperty=fullName>   
 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>   
 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>
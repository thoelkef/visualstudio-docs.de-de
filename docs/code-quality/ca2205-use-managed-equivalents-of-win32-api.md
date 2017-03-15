---
title: "CA2205: Verwaltete Entsprechungen der Win32 API verwenden | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UseManagedEquivalentsOfWin32Api"
  - "CA2205"
helpviewer_keywords: 
  - "CA2205"
  - "UseManagedEquivalentsOfWin32Api"
ms.assetid: 1c65ab59-3e50-4488-a727-3969c7f6cbe4
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# CA2205: Verwaltete Entsprechungen der Win32 API verwenden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseManagedEquivalentsOfWin32Api|  
|CheckId|CA2205|  
|Kategorie \(Category\)|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Eine Plattformaufrufmethode ist definiert, und in der [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Klassenbibliothek existiert eine Methode mit der entsprechenden Funktionalität.  
  
## Regelbeschreibung  
 Mit einer Plattformaufrufmethode wird eine nicht verwaltete DLL\-Funktion aufgerufen. Die Aufrufmethode wird mit dem <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>\-Attribut bzw. in Visual Basic mit dem `Declare`\-Schlüsselwort definiert.  Eine fehlerhaft definierte Plattformaufrufmethode kann zu Laufzeitausnahmen führen. Mögliche Gründe hierfür sind Probleme wie falsch benannte Funktionen, eine fehlerhafte Zuordnung von Datentypen für Parameter und Rückgabewerte sowie fehlerhafte Feldspezifikationen, beispielsweise eine falsche Aufrufkonvention und ein falscher Zeichensatz.  Falls die entsprechende verwaltete Methode verfügbar ist, ist ein Aufruf dieser Methode im Allgemeinen einfacher und weniger fehleranfällig als eine Definition oder ein direkter Aufruf der nicht verwalteten Methode.  Der Aufruf einer Plattformaufrufmethode kann außerdem zu zusätzlichen Sicherheitsproblemen führen, die behandelt werden müssen.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, ersetzen Sie den Aufruf der nicht verwalteten Funktion durch einen Aufruf der entsprechenden verwalteten Funktion.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie eine Warnung dieser Regel, wenn die benötigte Funktionalität durch die vorgeschlagene Ersetzungsmethode nicht bereitgestellt wird.  
  
## Beispiel  
 Im folgenden Beispiel wird eine Plattformaufrufmethodendefinition veranschaulicht, die gegen die Regel verstößt.  Darüber hinaus werden die Aufrufe der Plattformaufrufmethode und der entsprechenden verwalteten Methode dargestellt.  
  
 [!code-cs[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/CSharp/ca2205-use-managed-equivalents-of-win32-api_1.cs)]
 [!code-vb[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/VisualBasic/ca2205-use-managed-equivalents-of-win32-api_1.vb)]  
  
## Verwandte Regeln  
 [CA1404: GetLastError unmittelbar nach P\/Invoke aufrufen](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)  
  
 [CA1060: P\/Invokes in NativeMethods\-Klasse verschieben](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)  
  
 [CA1400: Für P\/Invoke müssen Einstiegspunkte vorhanden sein](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)  
  
 [CA1401: P\/Invokes dürfen nicht sichtbar sein](../code-quality/ca1401-p-invokes-should-not-be-visible.md)  
  
 [CA2101: Marshalling für P\/Invoke\-Zeichenfolgenargumente festlegen](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)
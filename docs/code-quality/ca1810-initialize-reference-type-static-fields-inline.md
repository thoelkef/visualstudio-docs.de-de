---
title: 'CA1810: Statische Felder Initialisieren von Verweistypen Inline | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
helpviewer_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
ms.assetid: e9693118-a914-4efb-9550-ec659d8d97d2
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 113d5206d2b4827902cf83827efd5b8738387755
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ca1810-initialize-reference-type-static-fields-inline"></a>CA1810: Statische Felder von Verweistypen inline initialisieren
|||  
|-|-|  
|TypeName|InitializeReferenceTypeStaticFieldsInline|  
|CheckId|CA1810|  
|Kategorie|Microsoft.Performance|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## <a name="cause"></a>Ursache  
 Ein Verweistyp deklariert einen expliziten statischen Konstruktor.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Wenn ein Typ einen expliziten statischen Konstruktor deklariert, überprüft der JIT-Compiler (Just in Time) jede statische Methode und jeden Instanzenkonstruktor des Typs. Dadurch wird sichergestellt, dass der statische Konstruktor zuvor aufgerufen wurde. Statischen Initialisierung wird ausgelöst, wenn auf ein statischer Member zugegriffen wird, oder wenn eine Instanz des Typs erstellt wird. Statischen Initialisierung wird jedoch nicht ausgelöst, wenn Sie eine Variable des Typs deklarieren, aber nicht verwenden, was wichtig, wenn die Initialisierung globalen Zustand ändert sein kann.  
  
 Wenn alle statische Daten Inline initialisiert und ein expliziter statischer Konstruktor nicht deklariert ist, Hinzufügen von Microsoft intermediate Language (MSIL)-Compiler die `beforefieldinit` Flag und einen impliziten statischen Konstruktor, der initialisiert die statischen Daten, die in den MSIL-Typ Definition. Wenn der JIT-Compiler erkennt die `beforefieldinit` kennzeichnen, in den meisten Fällen die Überprüfung statischer Konstruktoren nicht hinzugefügt werden. Statischen Initialisierung ist garantiert, einige Zeit stattfinden, bevor statische Felder zugegriffen werden, aber nicht, bevor ein statische Methode oder die Instanz-Konstruktor aufgerufen wird. Beachten Sie, dass die statische Initialisierung zu einem beliebigen Zeitpunkt nach dem Deklarieren einer Variablen des Typs auftreten kann.  
  
 Durch die Überprüfung statischer Konstruktoren kann die Leistung herabgesetzt werden. Ein statischer Konstruktor wird häufig verwendet, nur für statische Felder zu initialisieren, in dem Fall Sie nur sicherstellen, dass die statische Initialisierung, müssen vor dem ersten Zugriff eines statischen Felds tritt auf. Die `beforefieldinit` Verhalten eignet sich für diese und die meisten anderen Projekttypen. Es ist nur dann ungeeignet, bei der statischen Initialisierung wirkt sich auf die globalen Status und eine der folgenden ist "true":  
  
-   Die Auswirkung auf den globalen Zustand ist teuer und ist nicht erforderlich, wenn der Typ nicht verwendet wird.  
  
-   Die Auswirkungen des globalen Status können zugegriffen werden, ohne den Zugriff auf statische Felder des Typs.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, initialisieren Sie alle statischen Daten nach deren Deklaration und entfernen den statischen Konstruktor.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Sie können ruhig auf eine Warnung dieser Regel zu unterdrücken, sofern die Leistung nicht relevant ist; oder wenn der globale Status für Änderungen, die von der statischen Initialisierung verursacht werden aufwendig oder müssen sichergestellt werden, um auftreten, bevor eine statische Methode des Typs aufgerufen wird, oder es wird eine Instanz des Typs erstellt haben.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt einen Typ `StaticConstructor`, die die Regel und einen Typ verletzt `NoStaticConstructor`, die den statischen Konstruktor mit Inline-Initialisierung die Regel erfüllen ersetzt.  
  
 [!code-csharp[FxCop.Performance.RefTypeStaticCtor#1](../code-quality/codesnippet/CSharp/ca1810-initialize-reference-type-static-fields-inline_1.cs)]
 [!code-vb[FxCop.Performance.RefTypeStaticCtor#1](../code-quality/codesnippet/VisualBasic/ca1810-initialize-reference-type-static-fields-inline_1.vb)]  
  
 Beachten Sie das Hinzufügen der `beforefieldinit` -Flag auf der MSIL-Definition für die `NoStaticConstructor` Klasse.  
  
 **auto-.class öffentlich Ansi StaticConstructor**  
 **[mscorlib erweitert**  
**{**  
**} / / Ende der Klasse StaticConstructor**  
**.Class automatisch öffentlich Ansi Beforefieldinit NoStaticConstructor**  
 **[mscorlib erweitert**  
**{**  
**} / / Ende der Klasse NoStaticConstructor**   
## <a name="related-rules"></a>Verwandte Regeln  
 [CA2207: Statische Felder für Werttyp inline initialisieren](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)
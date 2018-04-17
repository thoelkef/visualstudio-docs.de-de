---
title: 'CA2207: Statische Felder Typ Inline initialisieren | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- InitializeValueTypeStaticFieldsInline
- CA2207
helpviewer_keywords:
- CA2207
- InitializeValueTypeStaticFieldsInline
ms.assetid: d1ea9d8b-ecc2-46ca-86e2-c41dd0e76658
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f5d063cda94451feef28aba9715033234d9adaa1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ca2207-initialize-value-type-static-fields-inline"></a>CA2207: Statische Felder für Werttyp inline initialisieren
|||  
|-|-|  
|TypeName|InitializeValueTypeStaticFieldsInline|  
|CheckId|CA2207|  
|Kategorie|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechende Änderung|  
  
## <a name="cause"></a>Ursache  
 Ein Werttyp deklariert einen expliziten statischen Konstruktor.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Wenn ein Werttyp deklariert wurde, unterliegt es standardmäßig initialisiert, wenn alle Werttyp-Feld auf 0 (null) festgelegt werden, und alle Felder von Verweistypen festgelegt sind `null` (`Nothing` in Visual Basic). Ein expliziter statischer Konstruktor ist nur garantiert, bevor ein Instanzkonstruktor oder statischer Member des Typs aufgerufen wird. Aus diesem Grund Wenn der Typ erstellt wurde, ohne einen Instanzkonstruktor und aufrufen, wird der statische Konstruktor möglicherweise nicht ausgeführt.  
  
 Wenn alle statische Daten Inline initialisiert und keine expliziter statischer Konstruktor deklariert, die C#- und Visual Basic-Compiler Hinzufügen der `beforefieldinit` Flag für die Definition der MSIL-Klasse. Der Compiler belaufen sich auch einen privaten statischen Konstruktor, der den statischen Initialisierungscode enthält. Dieser private statische Konstruktor ist garantiert, ausführen, damit alle statischen Felder des Typs zugegriffen werden.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Zur Behebung ein Verstoß gegen diese Regel initialisieren alle statischen Daten nach wird deklariert, und entfernen den statischen Konstruktor.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA1810: Statische Felder von Verweistypen inline initialisieren](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)
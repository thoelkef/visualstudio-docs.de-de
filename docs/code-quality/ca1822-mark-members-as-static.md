---
title: 'CA1822: Member als statisch markieren | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MarkMembersAsStatic
- CA1822
helpviewer_keywords:
- MarkMembersAsStatic
- CA1822
ms.assetid: 743f0af7-41d1-4852-8d97-af0688b31118
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d1f3c20f39fe863925d46c1f86f2f6a821e8489a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ca1822-mark-members-as-static"></a>CA1822: Member als statisch markieren
|||  
|-|-|  
|TypeName|MarkMethodsAsStatic|  
|CheckId|CA1822|  
|Kategorie|Microsoft.Performance|  
|Unterbrechende Änderung|Nicht unterbrechend – Wenn der Member nicht außerhalb der Assembly sichtbar ist müssen unabhängig von der Änderung. Nicht unterbrechend – Wenn Sie nur das Element auf ein Instanzmember mit ändern die `this` Schlüsselwort.<br /><br /> Unterbrechend – Wenn Sie das Element über einen Instanzmember in ein statisches Element ändern, und er außerhalb der Assembly sichtbar ist.|  
  
## <a name="cause"></a>Ursache  
 Ein Element, das nicht auf Instanzdaten zugreift, ist nicht als static markiert (Shared in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Member, die nicht auf Instanzdaten zugreifen oder keine Instanzmethoden aufrufen, können als static markiert werden (Shared in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Danach gibt der Compiler nicht virtuelle Aufrufsites an diese Member aus. Ausgeben von Aufrufsites verhindert eine Überprüfung zur Laufzeit für jeden Aufruf, der sicherstellt, dass der aktuelle Objektzeiger ungleich Null ist. Dies kann zu eine messbaren Leistungssteigerung für leistungsabhängigen Code erreichen. In einigen Fällen stellt der Fehler auf die aktuelle Objektinstanz ein Problem auf Richtigkeit.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Markieren Sie den Member als statisch (oder im freigegebenen [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) oder verwenden Sie "this" / "Me" in der Methode Anforderungstext, falls zutreffend.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Sie können ruhig zum Unterdrücken einer Warnung dieser Regel für zuvor gelieferten Code, für den die Lösung eine unterbrechende Änderung wäre.  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA1811: Nicht aufgerufenen privaten Code vermeiden](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1812: Nicht instanziierte interne Klassen vermeiden](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1804: Nicht verwendete lokale Variablen entfernen](../code-quality/ca1804-remove-unused-locals.md)
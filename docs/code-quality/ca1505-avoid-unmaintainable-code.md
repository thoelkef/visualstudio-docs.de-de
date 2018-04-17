---
title: 'CA1505: Nicht wartbaren Code vermeiden | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- AvoidUnmaintainableCode
- CA1505
helpviewer_keywords:
- AvoidUnmaintainableCode
- CA1505
ms.assetid: 8292b268-5929-4221-b699-f9c414bcec5d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4338b73aab38b1d63f4d4015c3a1fe1e1d292932
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ca1505-avoid-unmaintainable-code"></a>CA1505: Nicht wartbaren Code vermeiden
|||  
|-|-|  
|TypeName|AvoidUnmantainableCode|  
|CheckId|CA1505|  
|Kategorie|Microsoft.Maintainability|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## <a name="cause"></a>Ursache  
 Ein Typ oder eine Methode verfügt über einen niedrigen Wartbarkeitsindexwert.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Der Wartbarkeitsindex wird berechnet, indem Sie die folgenden Metriken: Codezeilen, Programm Volume und zyklomatische Komplexität. Programm-Volume ist ein Maß für die Schwierigkeit Kenntnisstand eines Typs oder einer Methode, die basierend auf der Anzahl von Operatoren und Operanden in den Code. Zyklomatische Komplexität ist ein Maß der strukturellen Komplexität des Typs oder der Methode. Weitere Informationen finden Sie Informationen zu Codemetrik am [Messen von Komplexität und verwaltbarkeit von verwaltetem Code](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md).  
  
 Ein niedriger Wartbarkeitsindex zeigt an, dass ein Typ oder eine Methode wahrscheinlich schwer zu verwalten und Umgestalten geeignet wäre.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um diese Verstoß zu beheben, gestalten Sie den Typ oder die Methode aus, und versuchen Sie es verkleinern und genauer spezifizieren Typen oder Methoden aufgeteilt.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Schließen Sie diese Warnung, wenn ein Typ oder eine Methode weiterhin als verwaltbar angesehen wird trotz seiner Größe oder wenn der Typ oder Methode unterteilt werden kann.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwaltbarkeitswarnungen](../code-quality/maintainability-warnings.md)   
 [Messen von Komplexität und Verwaltbarkeit verwalteten Codes](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
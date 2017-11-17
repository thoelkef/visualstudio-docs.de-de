---
title: "CA1506: Übermäßige Klassenkopplungen vermeiden | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AvoidExcessiveClassCoupling
- CA1506
helpviewer_keywords:
- AvoidExcessiveClassCoupling
- CA1506
ms.assetid: 9f0943c0-e802-4e3f-8798-2ab8653ddc80
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8192868aa7c5d79039a5e94a2aa13c47ada5d47c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ca1506-avoid-excessive-class-coupling"></a>CA1506: Übermäßige Klassenkopplungen vermeiden
|||  
|-|-|  
|TypeName|AvoidExcessiveClassCoupling|  
|CheckId|CA1506|  
|Kategorie|Microsoft.Maintainability|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Ein Typ oder eine Methode ist mit vielen anderen Knotentypen gekoppelt.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Durch diese Regel wird die Klassenkopplung gemessen, indem die eindeutigen Typverweise, die ein Typ oder eine Methode enthält, gezählt werden.  
  
 Typen und Methoden, die einen hohen Grad an Klassenkopplungen aufweisen können schwierig zu verwalten sein. Es wird empfohlen, Typen und Methoden, die lose Kopplung und hohe Kohäsion aufweisen.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um diese Verstoß zu beheben, versuchen Sie, gestalten Sie den Typ oder eine Methode zum Verringern der Anzahl von Typen, mit denen er verknüpft ist.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Schließen Sie diese Warnung, wenn der Typ oder Methode noch verwaltbar trotz der großen Anzahl von Abhängigkeiten von anderen Typen betrachtet wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwaltbarkeitswarnungen](../code-quality/maintainability-warnings.md)   
 [Messen von Komplexität und Verwaltbarkeit verwalteten Codes](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
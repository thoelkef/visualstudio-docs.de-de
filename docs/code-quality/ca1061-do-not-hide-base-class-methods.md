---
title: 'CA1061: Basisklassenmethoden nicht ausblenden | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1061
- DoNotHideBaseClassMethods
helpviewer_keywords:
- DoNotHideBaseClassMethods
- CA1061
ms.assetid: 0bda9dc8-87b4-4038-ab9d-563298387466
caps.latest.revision: "9"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d7eb4db46697e7f4cbb54d9ee11e4289b5a2ba2c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ca1061-do-not-hide-base-class-methods"></a>CA1061: Basisklassenmethoden nicht ausblenden
|||  
|-|-|  
|TypeName|DoNotHideBaseClassMethods|  
|CheckId|CA1061|  
|Kategorie|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Ein abgeleiteter Typ deklariert eine Methode mit dem gleichen Namen und die gleiche Anzahl von Parametern als eines seiner Basismethoden; mindestens einer der Parameter ist ein Basistyp des entsprechenden Parameters in der Basismethode. und alle übrigen Parameter über die Typen, die mit den entsprechenden Parametern in der Basismethode identisch sind.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Eine Methode in einem Basistyp wird durch eine Methode mit identischem Namen in einem abgeleiteten Typ verdeckt, wenn die Parametersignatur der abgeleiteten Methode nur hinsichtlich der Typen unterscheidet, die schwächer abgeleitet als die entsprechenden Typen in der Parametersignatur der Basismethode sind.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie oder benennen Sie die Methode, oder ändern Sie die Parametersignatur, sodass die Methode die Basismethode nicht ausgeblendet wird.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt eine Methode, die die Regel verletzt.  
  
 [!code-csharp[FxCop.Design.HideBaseMethod#1](../code-quality/codesnippet/CSharp/ca1061-do-not-hide-base-class-methods_1.cs)]
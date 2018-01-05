---
title: 'CA1040: Leere Schnittstellen vermeiden | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1040
- AvoidEmptyInterfaces
helpviewer_keywords:
- AvoidEmptyInterfaces
- CA1040
ms.assetid: 120a741b-5fd1-4836-8453-7857e0cd0380
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 1b2dd61f70328ed4aa8ca08c518cebf8d6abbedb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ca1040-avoid-empty-interfaces"></a>CA1040: Leere Schnittstellen vermeiden
|||  
|-|-|  
|TypeName|AvoidEmptyInterfaces|  
|CheckId|CA1040|  
|Kategorie|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Die Schnittstelle keine Member deklarieren oder zwei oder mehr Schnittstellen implementieren.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Schnittstellen definieren Member, die ein Verhalten oder einen Verwendungsvertrag bereitstellen. Die durch die Schnittstelle beschriebene Funktionalität kann von jedem Typ übernommen werden, unabhängig davon, an welcher Stelle der Typ in der Vererbungshierarchie steht. Ein Typ implementiert eine Schnittstelle, indem er Implementierungen für die Member der Schnittstelle bereitstellt. Eine leere Schnittstelle definiert keine Member. Aus diesem Grund ist es keinen Vertrag zu definieren, der implementiert werden können.  
  
 Wenn Ihr Design leere umfasst voraussichtlich Schnittstellen, die Typen implementieren, verwenden Sie wahrscheinlich eine Schnittstelle als Marker oder zur Identifizierung einer Gruppenstatus von Datentypen. Wenn diese Identifikation zur Laufzeit erfolgt, ist die richtige Vorgehensweise, um dies zu erreichen, verwenden Sie ein benutzerdefiniertes Attribut. Verwenden Sie das Vorhandensein oder fehlen des Attributs oder die Eigenschaften des Attributs, um den Zieltypen zu identifizieren. Wenn die Kennung zum Zeitpunkt der Kompilierung auftreten muss, ist es zulässig, eine leere Schnittstelle verwenden.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Entfernen Sie die Schnittstelle, oder fügen Sie Mitglieder hinzu. Wenn die leere Schnittstelle zum Bezeichnen eines Satz von Typen verwendet wird, ersetzen Sie die Schnittstelle mit einem benutzerdefinierten Attribut ein.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Sie können ruhig auf eine Warnung dieser Regel zu unterdrücken, wenn die Schnittstelle verwendet wird, um einen Satz von Typen zur Kompilierzeit zu identifizieren.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt eine leere Schnittstelle.  
  
 [!code-csharp[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/CSharp/ca1040-avoid-empty-interfaces_1.cs)]
 [!code-cpp[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/CPP/ca1040-avoid-empty-interfaces_1.cpp)]
 [!code-vb[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/VisualBasic/ca1040-avoid-empty-interfaces_1.vb)]
---
title: 'CA1033: Schnittstellenmethoden sollten von untergeordneten Typen aufgerufen werden | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- InterfaceMethodsShouldBeCallableByChildTypes
- CA1033
helpviewer_keywords:
- CA1033
- InterfaceMethodsShouldBeCallableByChildTypes
ms.assetid: 9f171497-a5e3-4769-a77b-7aed755b2662
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4a9596a147ab16961d6c1396c0d367f87c6182e4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ca1033-interface-methods-should-be-callable-by-child-types"></a>CA1033: Schnittstellenmethoden sollten von untergeordneten Typen aufgerufen werden können
|||  
|-|-|  
|TypeName|InterfaceMethodsShouldBeCallableByChildTypes|  
|CheckId|CA1033|  
|Kategorie|Microsoft.Design|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## <a name="cause"></a>Ursache  
 Ein unversiegelter, extern sichtbarer Typ gibt eine explizite Methodenimplementierung einer öffentlichen Schnittstelle an und gibt keine alternative extern sichtbare Methode mit dem gleichen Namen an.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Erwägen Sie einen Basistyp an, der eine Methode für die öffentliche Schnittstelle explizit implementiert. Ein Typ, der von diesem Basistyp abgeleitet ist, kann geerbte Schnittstellenmethode zugreifen, nur über einen Verweis auf die aktuelle Instanz (`this` in c#), das die-Schnittstelle umgewandelt wird. Wenn der abgeleitete Typ (explizit) die geerbten Schnittstellenmethode erneut implementiert, kann die grundlegende Implementierung nicht mehr zugegriffen werden. Der Aufruf über die aktuelle Instanz Referenz wird die abgeleitete Implementierung aufgerufen wird. Dies bewirkt, dass Rekursion und schließlich zu einem Stapelüberlauf.  
  
 Diese Regel meldet keinen Verstoß für eine explizite Implementierung der <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> Wenn eine extern sichtbare `Close()` oder `System.IDisposable.Dispose(Boolean)` Methode wird bereitgestellt.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, implementieren Sie eine neue Methode, die die gleiche Funktionen verfügbar macht und für abgeleitete Typen sichtbar ist, oder ändern Sie in einer Implementierung verwenden. Wenn eine unterbrechende Änderung zulässig ist, ist eine Alternative zu den Typ versiegelt.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Sie können ruhig zum Unterdrücken einer Warnung dieser Regel, wenn eine extern sichtbare Methode angegeben wird, die die gleiche Funktionalität aber einen anderen Namen als die explizit implementierte Methode.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt einen Typ `ViolatingBase`, die die Regel und einen Typ verletzt `FixedBase`, zeigt, dass eine Lösung für die Verletzung.  
  
 [!code-csharp[FxCop.Design.ExplicitMethodImplementations#1](../code-quality/codesnippet/CSharp/ca1033-interface-methods-should-be-callable-by-child-types_1.cs)]  
  
## <a name="see-also"></a>Siehe auch  
 [Schnittstellen](/dotnet/csharp/programming-guide/interfaces/index)
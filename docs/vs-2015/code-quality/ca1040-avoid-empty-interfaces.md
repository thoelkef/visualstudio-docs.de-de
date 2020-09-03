---
title: 'CA1040: leere Schnittstellen vermeiden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1040
- AvoidEmptyInterfaces
helpviewer_keywords:
- AvoidEmptyInterfaces
- CA1040
ms.assetid: 120a741b-5fd1-4836-8453-7857e0cd0380
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0ef6dc666cbc3c26d58358c9b59264f93a7bf184
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548251"
---
# <a name="ca1040-avoid-empty-interfaces"></a>CA1040: Leere Schnittstellen vermeiden.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|AvoidEmptyInterfaces|
|CheckId|CA1040|
|Category|Microsoft. Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Die-Schnittstelle deklariert keine Member oder implementiert mindestens zwei andere Schnittstellen.

## <a name="rule-description"></a>Beschreibung der Regel
 Schnittstellen definieren Member, die ein Verhalten oder einen Verwendungsvertrag bereitstellen. Die durch die Schnittstelle beschriebene Funktionalität kann von jedem Typ übernommen werden, unabhängig davon, an welcher Stelle der Typ in der Vererbungshierarchie steht. Ein Typ implementiert eine Schnittstelle, indem er Implementierungen für die Member der Schnittstelle bereitstellt. Eine leere Schnittstelle definiert keine Member. Daher wird kein Vertrag definiert, der implementiert werden kann.

 Wenn Ihr Entwurf leere Schnittstellen enthält, die von Typen implementiert werden sollen, verwenden Sie wahrscheinlich eine Schnittstelle als Marker oder eine Möglichkeit zum Identifizieren einer Gruppe von Typen. Wenn diese Identifikation zur Laufzeit erfolgt, ist die korrekte Vorgehensweise die Verwendung eines benutzerdefinierten Attributs. Verwenden Sie das vorhanden sein oder Fehlen des-Attributs oder der Eigenschaften des-Attributs, um die Zieltypen zu identifizieren. Wenn die Identifikation zur Kompilierzeit erfolgen muss, ist es akzeptabel, eine leere Schnittstelle zu verwenden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Entfernen Sie die-Schnittstelle, oder fügen Sie Ihr Member hinzu. Wenn die leere Schnittstelle verwendet wird, um einen Satz von Typen zu bezeichnen, ersetzen Sie die-Schnittstelle durch ein benutzerdefiniertes Attribut.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn die-Schnittstelle verwendet wird, um einen Satz von Typen zur Kompilierzeit zu identifizieren.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine leere-Schnittstelle.

 [!code-cpp[FxCop.Design.InterfacesNotEmpty#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.InterfacesNotEmpty/cpp/FxCop.Design.InterfacesNotEmpty.cpp#1)]
 [!code-csharp[FxCop.Design.InterfacesNotEmpty#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.InterfacesNotEmpty/cs/FxCop.Design.InterfacesNotEmpty.cs#1)]
 [!code-vb[FxCop.Design.InterfacesNotEmpty#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.InterfacesNotEmpty/vb/FxCop.Design.InterfacesNotEmpty.vb#1)]

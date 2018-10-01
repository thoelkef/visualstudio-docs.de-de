---
title: Verwaltbarkeitswarnungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.codeanalysis.maintainabilityrules
helpviewer_keywords:
- warnings, maintainability
- managed code analysis warnings, maintainability warnings
- maintainability warnings
ms.assetid: 537e70ca-a88c-49df-bfc7-0ee63bbe4f16
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 53e4763ecc4e9f36dd402f33bfad30e5795c1814
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47512662"
---
# <a name="maintainability-warnings"></a>Verwaltbarkeitswarnungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Verwaltbarkeitswarnungen](https://docs.microsoft.com/visualstudio/code-quality/maintainability-warnings).  
  
Verwaltbarkeitswarnungen zu Bibliotheks- und Anwendungswartung unterstützen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Regel|Beschreibung|  
|----------|-----------------|  
|[CA1500: Variablennamen sollten nicht mit Feldnamen übereinstimmen](../code-quality/ca1500-variable-names-should-not-match-field-names.md)|Eine Instanzmethode deklariert einen Parameter oder eine lokale Variable, deren Name ein Instanzenfelds des deklarierenden Typs übereinstimmt, was zu Fehlern führt.|  
|[CA1501: Übermäßige Vererbung vermeiden](../code-quality/ca1501-avoid-excessive-inheritance.md)|Ein Typ ist in seiner Vererbungshierarchie mehr als vier Ebenen tief. Tief verschachtelte Typenhierarchien können schwer zu verfolgen, verstehen und verwalten sein.|  
|[CA1502: Übermäßige Komplexität vermeiden](../code-quality/ca1502-avoid-excessive-complexity.md)|Diese Regel ermöglicht Aussagen über die Anzahl linear unabhängiger Pfade in einer Methode, wobei die Anzahl der Pfade durch die Anzahl und Komplexität bedingter Branches bestimmt wird.|  
|[CA1504: Irreführende Feldnamen überprüfen](../code-quality/ca1504-review-misleading-field-names.md)|Der Name eines Instanzenfelds beginnt mit "S_" oder den Namen eines statischen (freigegeben [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) Feld beginnt mit "M_".|  
|[CA1505: Nicht wartbaren Code vermeiden](../code-quality/ca1505-avoid-unmaintainable-code.md)|Ein Typ oder eine Methode verfügt über einen niedrigen Wartbarkeitsindexwert. Ein niedriger Wartbarkeitsindex zeigt an, dass ein Typ oder eine Methode wahrscheinlich schwer zu verwalten ist und geeignet für einen Neuentwurf wäre.|  
|[CA1506: Übermäßige Klassenkopplungen vermeiden](../code-quality/ca1506-avoid-excessive-class-coupling.md)|Durch diese Regel wird die Klassenkopplung gemessen, indem die eindeutigen Typverweise, die ein Typ oder eine Methode enthält, gezählt werden.|  
  
## <a name="see-also"></a>Siehe auch  
 [Messen von Komplexität und Verwaltbarkeit verwalteten Codes](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)




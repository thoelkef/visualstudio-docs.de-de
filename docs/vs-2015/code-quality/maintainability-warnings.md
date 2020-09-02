---
title: Wart barkeits Warnungen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.maintainabilityrules
helpviewer_keywords:
- warnings, maintainability
- managed code analysis warnings, maintainability warnings
- maintainability warnings
ms.assetid: 537e70ca-a88c-49df-bfc7-0ee63bbe4f16
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e448a72e2ff92b3e3028829d4b1e7658c304ee3c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667894"
---
# <a name="maintainability-warnings"></a>Verwaltbarkeitswarnungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wart barkeits Warnungen unterstützen die Verwaltung von Bibliotheken und Anwendungen.

## <a name="in-this-section"></a>In diesem Abschnitt

|Regel|Beschreibung|
|----------|-----------------|
|[CA1500: Variablennamen sollten nicht mit Feldnamen übereinstimmen.](../code-quality/ca1500-variable-names-should-not-match-field-names.md)|Eine Instanzmethode deklariert einen Parameter oder eine lokale Variable, deren Name mit einem Instanzfeld des deklarierenden Typs übereinstimmt, was zu Fehlern führt.|
|[CA1501: Übermäßige Vererbung vermeiden.](../code-quality/ca1501-avoid-excessive-inheritance.md)|Ein Typ ist in seiner Vererbungshierarchie mehr als vier Ebenen tief. Tief verschachtelte Typenhierarchien können schwer zu verfolgen, verstehen und verwalten sein.|
|[CA1502: Übermäßige Komplexität vermeiden.](../code-quality/ca1502-avoid-excessive-complexity.md)|Diese Regel ermöglicht Aussagen über die Anzahl linear unabhängiger Pfade in einer Methode, wobei die Anzahl der Pfade durch die Anzahl und Komplexität bedingter Branches bestimmt wird.|
|[CA1504: Irreführende Feldnamen überprüfen.](../code-quality/ca1504-review-misleading-field-names.md)|Der Name eines Instanzfelds beginnt mit "S_", oder der Name eines statischen Felds (Shared in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ) beginnt mit "M_".|
|[CA1505: Nicht wartbaren Code vermeiden.](../code-quality/ca1505-avoid-unmaintainable-code.md)|Ein Typ oder eine Methode verfügt über einen niedrigen Wartbarkeitsindexwert. Ein niedriger Wartbarkeitsindex zeigt an, dass ein Typ oder eine Methode wahrscheinlich schwer zu verwalten ist und geeignet für einen Neuentwurf wäre.|
|[CA1506: Übermäßige Klassenkopplungen vermeiden.](../code-quality/ca1506-avoid-excessive-class-coupling.md)|Durch diese Regel wird die Klassenkopplung gemessen, indem die eindeutigen Typverweise, die ein Typ oder eine Methode enthält, gezählt werden.|

## <a name="see-also"></a>Weitere Informationen
 [Messen von Komplexität und Verwaltbarkeit verwalteten Codes](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)

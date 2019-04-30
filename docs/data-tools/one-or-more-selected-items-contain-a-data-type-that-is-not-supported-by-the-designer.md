---
title: Mindestens eines der ausgewählten Elemente enthält einen Datentyp, der nicht vom Designer unterstützt wird.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 71dcd4f9-2946-42c5-9ce4-99c819ea2785
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 12ec2ed7dc2a12556fcb6eeeddbe2d0745ae7f72
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62566367"
---
# <a name="one-or-more-selected-items-contain-a-data-type-that-is-not-supported-by-the-designer"></a>Mindestens eines der ausgewählten Elemente enthält einen Datentyp, der nicht vom Designer unterstützt wird.

Eine oder mehrere Elemente aus gezogen **Server-Explorer** oder **Datenbank-Explorer** auf die **O/R Designer** enthält einen Datentyp, der von nicht unterstützt wird die **O / R Designer**, z. B. [CLR-benutzerdefinierte Typen](/dotnet/framework/data/adonet/sql/clr-user-defined-types).

## <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

1. Erstellen Sie eine auf der gewünschten Tabelle basierende Ansicht, in der der nicht unterstützte Datentyp nicht enthalten ist.

2. Ziehen Sie die Ansicht von **Server-Explorer** oder **Datenbank-Explorer** in den Designer.

## <a name="see-also"></a>Siehe auch

- [O/R-Designer-Meldungen](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
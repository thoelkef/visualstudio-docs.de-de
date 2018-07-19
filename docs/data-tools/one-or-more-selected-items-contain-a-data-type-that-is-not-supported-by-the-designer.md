---
title: Mindestens eines der ausgewählten Elemente enthält einen Datentyp, der nicht vom Designer unterstützt wird.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 71dcd4f9-2946-42c5-9ce4-99c819ea2785
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 68d8675df54e37b9a6122b853e742addc0d8060c
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089489"
---
# <a name="one-or-more-selected-items-contain-a-data-type-that-is-not-supported-by-the-designer"></a>Mindestens eines der ausgewählten Elemente enthält einen Datentyp, der nicht vom Designer unterstützt wird.

Eine oder mehrere Elemente aus gezogen **Server-Explorer** oder **Datenbank-Explorer** auf die **O/R Designer** enthält einen Datentyp, der von nicht unterstützt wird die **O / R Designer**, z. B. [CLR-benutzerdefinierte Typen](/dotnet/framework/data/adonet/sql/clr-user-defined-types).

## <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

1. Erstellen Sie eine auf der gewünschten Tabelle basierende Ansicht, in der der nicht unterstützte Datentyp nicht enthalten ist.

2. Ziehen Sie die Ansicht von **Server-Explorer** oder **Datenbank-Explorer** in den Designer.

## <a name="see-also"></a>Siehe auch

- [O/R-Designer-Meldungen](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
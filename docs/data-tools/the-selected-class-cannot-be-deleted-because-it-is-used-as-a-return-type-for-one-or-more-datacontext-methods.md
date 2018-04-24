---
title: Die ausgewählte Klasse kann nicht gelöscht werden, da sie als Rückgabetyp für mindestens eine DataContext-Methode verwendet wird.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: c1460f8e3484633643d5b7bc9c7df181989b83ff
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>Die ausgewählte Klasse kann nicht gelöscht werden, da sie als Rückgabetyp für mindestens eine DataContext-Methode verwendet wird.

Der Rückgabetyp mindestens einer <xref:System.Data.Linq.DataContext>-Methode ist die ausgewählte Entitätsklasse. Durch das Löschen einer Entitätsklasse, die als Rückgabetyp für eine <xref:System.Data.Linq.DataContext>-Methode verwendet wird, tritt bei der Kompilierung des Projekts ein Fehler auf. Zum Löschen der ausgewählten Entitätsklasse identifizieren Sie die <xref:System.Data.Linq.DataContext>-Methoden, die sie verwenden, und legen Sie deren Rückgabetypen auf eine andere Entitätsklasse fest.

Zum Zurücksetzen der Rückgabetypen von <xref:System.Data.Linq.DataContext> -Methoden auf ihre ursprünglichen automatisch generierten Typen löschen zunächst die <xref:System.Data.Linq.DataContext> Methode aus dem Methodenbereich und ziehen anschließend das Objekt aus **Server-Explorer** / **Datenbank-Explorer** erneut in den O/R-Designer.

## <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

1. Identifizieren <xref:System.Data.Linq.DataContext> Methoden, mit denen die Entitätsklasse als Rückgabetyp dazu eine <xref:System.Data.Linq.DataContext> Methode in den Methoden Bereich und Überprüfen der **Rückgabetyp** Eigenschaft in der **Eigenschaften** Fenster .

2. Legen Sie die **Rückgabetyp** auf eine andere Entitätsklasse oder Entfernen der <xref:System.Data.Linq.DataContext> Methode aus dem Methodenbereich.

## <a name="see-also"></a>Siehe auch

- [O/R-Designer-Meldungen](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL-tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
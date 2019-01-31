---
title: Die ausgewählte Klasse kann nicht gelöscht werden, da sie als Rückgabetyp für mindestens eine DataContext-Methode verwendet wird.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 00fc4ee0be84cc4937fddc083633324cc8ab41d3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2019
ms.locfileid: "55070863"
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>Die ausgewählte Klasse kann nicht gelöscht werden, da sie als Rückgabetyp für mindestens eine DataContext-Methode verwendet wird.

Der Rückgabetyp mindestens einer <xref:System.Data.Linq.DataContext>-Methode ist die ausgewählte Entitätsklasse. Löschen einer Entitätsklasse, die verwendet wird, als der Rückgabetyp für eine <xref:System.Data.Linq.DataContext> Methode bewirkt, dass die Kompilierung des Projekts fehlschlagen. Zum Löschen der ausgewählten Entitätsklasse identifizieren Sie die <xref:System.Data.Linq.DataContext>-Methoden, die sie verwenden, und legen Sie deren Rückgabetypen auf eine andere Entitätsklasse fest.

Für das Zurücksetzen der Rückgabetypen von <xref:System.Data.Linq.DataContext>-Methoden auf ihre ursprünglichen, automatisch erstellten Typen löschen Sie zunächst die <xref:System.Data.Linq.DataContext>-Methode aus dem Bereich **Methoden** und ziehen anschließend das Objekt aus dem **Server-Explorer**/**Datenbank-Explorer** erneut in den **O/R-Designer**.

## <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

1. Identifizieren Sie die <xref:System.Data.Linq.DataContext>-Methoden, die diese Entitätsklasse als Rückgabetyp verwenden, indem Sie im Bereich **Methoden** eine <xref:System.Data.Linq.DataContext>-Methode auswählen und im Fenster **Eigenschaften** die Eigenschaft **Rückgabetyp** überprüfen.

2. Legen Sie den **Rückgabetyp** auf eine andere Entitätsklasse fest, oder entfernen Sie die <xref:System.Data.Linq.DataContext>-Methode aus dem Methodenbereich.

## <a name="see-also"></a>Siehe auch

- [O/R-Designer-Meldungen](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
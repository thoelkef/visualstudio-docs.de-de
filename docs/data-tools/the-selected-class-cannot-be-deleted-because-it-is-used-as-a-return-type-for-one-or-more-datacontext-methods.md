---
title: Die ausgewählte Klasse kann nicht gelöscht werden.
description: Die ausgewählte Klasse kann nicht gelöscht werden, da sie als Rückgabetyp für mindestens eine DataContext-Methode verwendet wird.
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 84fabc7f0f1efdf06006597aec9bb813578589a8
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2020
ms.locfileid: "89743256"
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>Die ausgewählte Klasse kann nicht gelöscht werden, da sie als Rückgabetyp für mindestens eine DataContext-Methode verwendet wird.

Der Rückgabetyp mindestens einer <xref:System.Data.Linq.DataContext>-Methode ist die ausgewählte Entitätsklasse. Wenn Sie eine Entitäts Klasse löschen, die als Rückgabetyp für eine Methode verwendet wird, tritt <xref:System.Data.Linq.DataContext> bei der Kompilierung des Projekts ein Fehler auf. Zum Löschen der ausgewählten Entitätsklasse identifizieren Sie die <xref:System.Data.Linq.DataContext>-Methoden, die sie verwenden, und legen Sie deren Rückgabetypen auf eine andere Entitätsklasse fest.

Für das Zurücksetzen der Rückgabetypen von <xref:System.Data.Linq.DataContext>-Methoden auf ihre ursprünglichen, automatisch erstellten Typen löschen Sie zunächst die <xref:System.Data.Linq.DataContext>-Methode aus dem Bereich **Methoden** und ziehen anschließend das Objekt aus dem **Server-Explorer**/**Datenbank-Explorer** erneut in den **O/R-Designer**.

## <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

1. Identifizieren Sie die <xref:System.Data.Linq.DataContext>-Methoden, die diese Entitätsklasse als Rückgabetyp verwenden, indem Sie im Bereich **Methoden** eine <xref:System.Data.Linq.DataContext>-Methode auswählen und im Fenster **Eigenschaften** die Eigenschaft **Rückgabetyp** überprüfen.

2. Legen Sie den **Rückgabetyp** auf eine andere Entitätsklasse fest, oder entfernen Sie die <xref:System.Data.Linq.DataContext>-Methode aus dem Methodenbereich.

## <a name="see-also"></a>Siehe auch

- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)

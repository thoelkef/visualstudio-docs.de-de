---
title: Die ausgewählte Klasse kann nicht gelöscht werden, da Sie als Rückgabetyp für mindestens eine DataContext-Methode verwendet wird. Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cf16fe7453388e19308ed603ee9dbbac207cec41
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667259"
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>Die ausgewählte Klasse kann nicht gelöscht werden, da sie als Rückgabetyp für mindestens eine DataContext-Methode verwendet wird.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der Rückgabetyp mindestens einer <xref:System.Data.Linq.DataContext>-Methode ist die ausgewählte Entitätsklasse. Durch das Löschen einer Entitätsklasse, die als Rückgabetyp für eine <xref:System.Data.Linq.DataContext>-Methode verwendet wird, tritt bei der Kompilierung des Projekts ein Fehler auf. Zum Löschen der ausgewählten Entitätsklasse identifizieren Sie die <xref:System.Data.Linq.DataContext>-Methoden, die sie verwenden, und legen Sie deren Rückgabetypen auf eine andere Entitätsklasse fest.

 Wenn Sie die Rückgabe Typen von <xref:System.Data.Linq.DataContext> Methoden auf ihre ursprünglichen automatisch generierten Typen zurücksetzen möchten, löschen Sie zuerst die <xref:System.Data.Linq.DataContext>-Methode aus dem Methoden Bereich, und ziehen Sie dann das Objekt aus **Server-Explorer** /**Datenbank-Explorer** erneut auf den O/R-Designer.

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

1. Identifizieren Sie <xref:System.Data.Linq.DataContext> Methoden, die die Entitäts Klasse als Rückgabetyp verwenden, indem Sie im Methoden Bereich eine <xref:System.Data.Linq.DataContext> Methode auswählen und im **Eigenschaften** Fenster die Eigenschaft **Rückgabetyp** überprüfen.

2. Legen Sie den **Rückgabetyp** auf eine andere Entitätsklasse fest, oder entfernen Sie die <xref:System.Data.Linq.DataContext>-Methode aus dem Methodenbereich.

## <a name="see-also"></a>Siehe auch
 [LINQ to SQL Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) Exemplarische Vorgehensweise [: Erstellen von LINQ to SQL Klassen (o-r-Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [DataContext-Methoden (o/r-Designer)](../data-tools/datacontext-methods-o-r-designer.md) Gewusst [wie: Ändern des Rückgabe Typs einer DataContext-Methode (o/r-Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)

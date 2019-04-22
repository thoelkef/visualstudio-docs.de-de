---
title: Die ausgewählte Klasse kann nicht gelöscht werden, da sie als Rückgabetyp für mindestens eine DataContext-Methode verwendet wird | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 02454e308a97f043caa6e85e1c4308c2d2a2402e
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2019
ms.locfileid: "59649042"
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>Die ausgewählte Klasse kann nicht gelöscht werden, da sie als Rückgabetyp für mindestens eine DataContext-Methode verwendet wird.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der Rückgabetyp mindestens einer <xref:System.Data.Linq.DataContext>-Methode ist die ausgewählte Entitätsklasse. Durch das Löschen einer Entitätsklasse, die als Rückgabetyp für eine <xref:System.Data.Linq.DataContext>-Methode verwendet wird, tritt bei der Kompilierung des Projekts ein Fehler auf. Zum Löschen der ausgewählten Entitätsklasse identifizieren Sie die <xref:System.Data.Linq.DataContext>-Methoden, die sie verwenden, und legen Sie deren Rückgabetypen auf eine andere Entitätsklasse fest.  
  
 Die Rückgabetypen der wiederherstellen <xref:System.Data.Linq.DataContext> zuerst löschen, Methoden, um ihre ursprüngliche automatisch generierten Typen, die <xref:System.Data.Linq.DataContext> Methode aus dem Methodenbereich und ziehen Sie dann auf das Objekt aus **Server-Explorer** / **Datenbank-Explorer** in den O/R-Designer erneut.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
1.  Identifizieren <xref:System.Data.Linq.DataContext> Methoden, mit denen die Entitätsklasse als Rückgabetyp durch Auswahl einer <xref:System.Data.Linq.DataContext> -Methode in der die Methoden Bereich, und Überprüfen der **Rückgabetyp** -Eigenschaft in der **Eigenschaften** Fenster .  
  
2.  Legen Sie den **Rückgabetyp** auf eine andere Entitätsklasse fest, oder entfernen Sie die <xref:System.Data.Linq.DataContext>-Methode aus dem Methodenbereich.  
  
## <a name="see-also"></a>Siehe auch  
 [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen (O / R-Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [DataContext-Methoden (O/R-Designer)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Vorgehensweise: Ändern des Rückgabetyps für eine DataContext-Methode (O/R-Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)

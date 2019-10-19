---
title: Das Ändern des Rückgabe Typs einer DataContext-Methode kann nicht rückgängig gemacht werden | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 76b161fc-5075-4192-8d94-f15b02e199e9
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f020aed4c1213d3db008862386704c0f63b86bde
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662466"
---
# <a name="changing-the-return-type-of-a-datacontext-method-cannot-be-undone"></a>Das Ändern des Rückgabetyps einer DataContext-Methode kann nicht rückgängig gemacht werden.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eine Änderung des Rückgabetyps einer DataContext-Methode kann nicht rückgängig gemacht werden. Wenn Sie den Typ auf den automatisch generierten Typ zurücksetzen möchten, müssen Sie das Element wieder aus dem Server-Explorer/Datenbank-Explorer in den O/R-Designer ziehen. Möchten Sie den Rückgabetyp wirklich ändern?

 Der Rückgabetyp einer <xref:System.Data.Linq.DataContext>-Methode ist je nachdem, wo Sie das Element im [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] ablegen, unterschiedlich. Wenn Sie ein Element direkt auf einer existierenden Entitätsklasse ablegen, wird eine <xref:System.Data.Linq.DataContext>-Methode erzeugt, die den Rückgabetyp dieser Entitätsklasse hat. Wenn Sie ein Element in einem leeren Bereich von [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] ablegen, wird eine <xref:System.Data.Linq.DataContext>-Methode erstellt, die einen automatisch erstellten Typ zurückgibt. Sie können den Rückgabetyp einer <xref:System.Data.Linq.DataContext>-Methode ändern, wenn Sie sie dem Methodenbereich hinzugefügt haben. Um den Rückgabetyp einer <xref:System.Data.Linq.DataContext>-Methode zu überprüfen oder zu ändern, markieren Sie sie und klicken im Fenster **Eigenschaften** auf die Eigenschaft **Rückgabetyp**.

### <a name="to-change-the-return-type-of-a-datacontext"></a>So ändern Sie den Rückgabetyp eines DataContext

- Klicken Sie auf **Ja**.

### <a name="to-exit-the-message-box-and-leave-the-return-type-unchanged"></a>So schließen Sie das Meldungsfeld, ohne den Rückgabetyp zu ändern

- Klicken Sie auf **Nein**.

### <a name="to-revert-to-the-original-return-type-after-changing-the-return-type"></a>So setzen Sie den Typ auf den ursprünglichen Rückgabetyp zurück, nachdem der Rückgabetyp geändert wurde

1. Wählen Sie die <xref:System.Data.Linq.DataContext>-Methode im [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] aus, und löschen Sie sie.

2. Suchen Sie das Element im **Server-Explorer/Datenbank-Explorer**, und ziehen Sie es auf den [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

     Eine <xref:System.Data.Linq.DataContext>-Methode mit dem ursprünglichen Standardrückgabetyp wird erstellt.

## <a name="see-also"></a>Siehe auch
 [LINQ to SQL Tools in den Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [DataContext-Methoden (o/r-Designer)](../data-tools/datacontext-methods-o-r-designer.md) Gewusst [wie: Erstellen von DataContext-Methoden, die gespeicherten Prozeduren und Funktionen zugeordnet sind (o/r-Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)

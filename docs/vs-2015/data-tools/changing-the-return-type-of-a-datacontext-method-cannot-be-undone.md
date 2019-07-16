---
title: Ändern des Rückgabetyps einer DataContext-Methode kann nicht rückgängig gemacht | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 76b161fc-5075-4192-8d94-f15b02e199e9
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: fb8389d3be96f190941e06ef4a822eaf081f281b
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65705554"
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
 [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [DataContext-Methoden (O/R-Designer)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Vorgehensweise: Erstellen Sie DataContext-Methoden zugeordnet wird, um gespeicherte Prozeduren und Funktionen (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)   
 [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)

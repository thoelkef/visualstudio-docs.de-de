---
title: Ändern des Rückgabetyps einer DataContext-Methode kann nicht rückgängig gemacht | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76b161fc-5075-4192-8d94-f15b02e199e9
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2adc93f6426c39d26395bdeb88fb8c37112a1a98
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47522400"
---
# <a name="changing-the-return-type-of-a-datacontext-method-cannot-be-undone"></a>Das Ändern des Rückgabetyps einer DataContext-Methode kann nicht rückgängig gemacht werden.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Ändern des Rückgabetyps einer DataContext-Methode kann nicht rückgängig gemacht](https://docs.microsoft.com/visualstudio/data-tools/changing-the-return-type-of-a-datacontext-method-cannot-be-undone).  
  
  
Eine Änderung des Rückgabetyps einer DataContext-Methode kann nicht rückgängig gemacht werden. Wenn Sie den Typ auf den automatisch generierten Typ zurücksetzen möchten, müssen Sie das Element wieder aus dem Server-Explorer/Datenbank-Explorer in den O/R-Designer ziehen. Möchten Sie den Rückgabetyp wirklich ändern?  
  
 Der Rückgabetyp einer <xref:System.Data.Linq.DataContext>-Methode ist je nachdem, wo Sie das Element im [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] ablegen, unterschiedlich. Wenn Sie ein Element direkt auf einer existierenden Entitätsklasse ablegen, wird eine <xref:System.Data.Linq.DataContext>-Methode erzeugt, die den Rückgabetyp dieser Entitätsklasse hat. Wenn Sie ein Element in einem leeren Bereich von [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] ablegen, wird eine <xref:System.Data.Linq.DataContext>-Methode erstellt, die einen automatisch erstellten Typ zurückgibt. Sie können den Rückgabetyp einer <xref:System.Data.Linq.DataContext>-Methode ändern, wenn Sie sie dem Methodenbereich hinzugefügt haben. Um zu überprüfen oder Ändern des Rückgabetyps von einer <xref:System.Data.Linq.DataContext> -Methode, wählen Sie ihn, und klicken Sie auf die **Rückgabetyp** -Eigenschaft in der **Eigenschaften** Fenster.  
  
### <a name="to-change-the-return-type-of-a-datacontext"></a>So ändern Sie den Rückgabetyp eines DataContexts  
  
-   Klicken Sie auf **Ja**.  
  
### <a name="to-exit-the-message-box-and-leave-the-return-type-unchanged"></a>So schließen Sie das Meldungsfeld, ohne den Rückgabetyp zu ändern  
  
-   Klicken Sie auf **keine**.  
  
### <a name="to-revert-to-the-original-return-type-after-changing-the-return-type"></a>So setzen Sie den Typ auf den ursprünglichen Rückgabetyp zurück, nachdem der Rückgabetyp geändert wurde  
  
1.  Wählen Sie die <xref:System.Data.Linq.DataContext> Methode für die [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] und löschen Sie sie.  
  
2.  Suchen Sie das Element im **Server Explorer/Datenbank-Explorer** und ziehen Sie es auf die [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
     Eine <xref:System.Data.Linq.DataContext>-Methode mit dem ursprünglichen Standardrückgabetyp wird erstellt.  
  
## <a name="see-also"></a>Siehe auch  
 [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [DataContext-Methoden (O/R-Designer)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Gewusst wie: Erstellen von DataContext-Methoden zugeordnet wird, um gespeicherte Prozeduren und Funktionen (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)


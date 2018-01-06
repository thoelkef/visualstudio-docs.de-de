---
title: "Ändern des Rückgabetyps einer DataContext-Methode kann nicht rückgängig gemacht werden | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76b161fc-5075-4192-8d94-f15b02e199e9
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: e28cf13486e21564c4acdf62e3edc89321a4f1b5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="changing-the-return-type-of-a-datacontext-method-cannot-be-undone"></a>Das Ändern des Rückgabetyps einer DataContext-Methode kann nicht rückgängig gemacht werden.
Eine Änderung des Rückgabetyps einer DataContext-Methode kann nicht rückgängig gemacht werden. Wenn Sie den Typ auf den automatisch generierten Typ zurücksetzen möchten, müssen Sie das Element wieder aus dem Server-Explorer/Datenbank-Explorer in den O/R-Designer ziehen. Möchten Sie den Rückgabetyp wirklich ändern?  
  
Der Rückgabetyp einer <xref:System.Data.Linq.DataContext>-Methode ist je nachdem, wo Sie das Element im [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] ablegen, unterschiedlich. Wenn Sie ein Element direkt auf einer existierenden Entitätsklasse ablegen, wird eine <xref:System.Data.Linq.DataContext>-Methode erzeugt, die den Rückgabetyp dieser Entitätsklasse hat. Wenn Sie ein Element in einem leeren Bereich von [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] ablegen, wird eine <xref:System.Data.Linq.DataContext>-Methode erstellt, die einen automatisch erstellten Typ zurückgibt. Sie können den Rückgabetyp einer <xref:System.Data.Linq.DataContext>-Methode ändern, wenn Sie sie dem Methodenbereich hinzugefügt haben. Um zu überprüfen oder ändern den Rückgabetyp der eine <xref:System.Data.Linq.DataContext> Methode auszuwählen, und klicken Sie auf die **Rückgabetyp** Eigenschaft in der **Eigenschaften** Fenster.  
  
### <a name="to-change-the-return-type-of-a-datacontext"></a>So ändern Sie den Rückgabetyp eines DataContexts  
  
-   Klicken Sie auf **Ja**.  
  
### <a name="to-exit-the-message-box-and-leave-the-return-type-unchanged"></a>So schließen Sie das Meldungsfeld, ohne den Rückgabetyp zu ändern  
  
-   Click **No**.  
  
### <a name="to-revert-to-the-original-return-type-after-changing-the-return-type"></a>So setzen Sie den Typ auf den ursprünglichen Rückgabetyp zurück, nachdem der Rückgabetyp geändert wurde  
  
1.  Wählen Sie die <xref:System.Data.Linq.DataContext> Methode für die [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] und löschen Sie ihn.  
  
2.  Suchen Sie das Element im **Server-Explorer/Datenbank-Explorer** und ziehen Sie es auf die [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
    Eine <xref:System.Data.Linq.DataContext>-Methode mit dem ursprünglichen Standardrückgabetyp wird erstellt.  
  
## <a name="see-also"></a>Siehe auch
[O/R-Designer-Meldungen](../data-tools/o-r-designer-messages.md)  
[LINQ to SQL-tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
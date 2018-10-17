---
title: DataContext-Methoden (O / R-Designer) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2ccf32d4af0bd16032c4601b054be6407071753f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49200459"
---
# <a name="datacontext-methods-or-designer"></a>DataContext-Methoden (O/R-Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
DataContext] (assetId:///T:System.Data.Linq.DataContext?qualifyHint=False & AutoUpgrade = True) Methoden (im Rahmen der [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)) sind Methoden der <xref:System.Data.Linq.DataContext> -Klasse, die Ausführung der gespeicherten Prozeduren und Funktionen in einer Datenbank.  
  
 Die <xref:System.Data.Linq.DataContext>-Klasse ist eine [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]-Klasse, die als Verbindung zwischen einer SQL Server-Datenbank und den [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]-Entitätsklassen dient, die dieser Datenbank zugeordnet sind. Die <xref:System.Data.Linq.DataContext>-Klasse enthält die Verbindungszeichenfolgeninformationen und die Methoden zum Herstellen einer Verbindung mit einer Datenbank und zum Ändern der Daten in der Datenbank. Standardmäßig enthält die <xref:System.Data.Linq.DataContext>-Klasse mehrere Methoden, die Sie aufrufen können, z. B. die <xref:System.Data.Linq.DataContext.SubmitChanges%2A>-Methode, die aktualisierte Daten aus [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]-Klassen an die Datenbank sendet. Sie können auch zusätzliche erstellen <xref:System.Data.Linq.DataContext> Methoden, die gespeicherten Prozeduren und Funktionen zugeordnet. Mit anderen Worten: Durch das Aufrufen dieser benutzerdefinierten Methoden wird in der Datenbank die gespeicherte Prozedur oder die Funktion ausgeführt, der die <xref:System.Data.Linq.DataContext>-Methode zugeordnet ist. Sie können der <xref:System.Data.Linq.DataContext>-Klasse neue Methoden hinzufügen, wie Sie auch anderen Klassen Methoden hinzufügen würden, um diese zu erweitern. Aber in Diskussionen zu <xref:System.Data.Linq.DataContext> Methoden im Rahmen der [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], ist die <xref:System.Data.Linq.DataContext> Methoden, die gespeicherten Prozeduren und Funktionen, die besprochen werden zugeordnet.  
  
## <a name="methods-pane"></a>Methodenbereich  
 Die gespeicherten Prozeduren und Funktionen zugeordneten <xref:System.Data.Linq.DataContext>-Methoden werden im Methodenbereich von [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] angezeigt. Der Methodenbereich ist der Bereich am Rand der **Entitäten** Bereich (der Hauptentwurfsoberfläche). Der Methodenbereich Listet alle <xref:System.Data.Linq.DataContext> Methoden, die Sie erstellt haben die [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Standardmäßig ist der Methodenbereich leer. Ziehen Sie gespeicherte Prozeduren oder Funktionen aus **Server-Explorer**/**Datenbank-Explorer** auf die [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] erstellen <xref:System.Data.Linq.DataContext> Methoden und den Methodenbereich zu füllen. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen Sie DataContext-Methoden zugeordnet wird, um gespeicherte Prozeduren und Funktionen (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md).  
  
> [!NOTE]
>  Öffnen und schließen Sie den Methodenbereich, mit der rechten Maustaste die [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] , und klicken Sie dann auf **Methodenbereich ausblenden** oder **Methodenbereich anzeigen**, oder verwenden Sie die Tastenkombination STRG + 1.  
  
## <a name="two-types-of-datacontext-methods"></a>Zwei Typen von DataContext-Methoden  
 DataContext-Methoden sind Methoden, die gespeicherten Prozeduren und Funktionen in der Datenbank zugeordnet werden. DataContext-Methoden können im Methodenbereich des [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] erstellt und hinzugefügt werden. Es gibt zwei unterschiedliche Arten von <xref:System.Data.Linq.DataContext> Methoden, die, die eine oder mehrere Resultsets zurückgeben und solche, die nicht der Fall ist:  
  
-   <xref:System.Data.Linq.DataContext>-Methoden, die ein oder mehrere Resultsets zurückgeben:  
  
     Erstellen Sie diese Art von <xref:System.Data.Linq.DataContext>-Methode, wenn eine Anwendung nur gespeicherte Prozeduren und Funktionen in der Datenbank ausführen und die Ergebnisse zurückgeben muss. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen Sie DataContext-Methoden zugeordnet wird, um gespeicherte Prozeduren und Funktionen (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md), System.Data.Linq.ISingleResult\<T >, und <xref:System.Data.Linq.IMultipleResults>.  
  
-   <xref:System.Data.Linq.DataContext>-Methoden, die keine Resultsets zurückgeben, wie Einfüge-, Update- und Löschvorgänge für eine bestimmte Entitätsklasse.  
  
     Erstellen Sie diese Art von <xref:System.Data.Linq.DataContext> Methode, wenn die Anwendung, zum Ausführen von gespeicherter Prozeduren verfügt statt das [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] -Standardverhalten zum Speichern geänderter Daten zwischen einer Entitätsklasse und der Datenbank. Weitere Informationen finden Sie unter [Vorgehensweise: Zuweisen von gespeicherten Prozeduren zum Ausführen von Updates, einfügungen und löschen (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
## <a name="return-types-of-datacontext-methods"></a>Rückgabetypen von DataContext-Methoden  
 Beim Ziehen von gespeicherten Prozeduren und Funktionen von **Server-Explorer**/**Datenbank-Explorer** auf die [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], der Rückgabetyp der generierten <xref:System.Data.Linq.DataContext> Methode unterscheidet sich abhängig davon, wo Sie das Element ablegen. Die Elemente direkt auf einer existierenden Entitätsklasse ablegen, wird erstellt eine <xref:System.Data.Linq.DataContext> -Methode mit dem Rückgabetyp der Entitätsklasse; durch Ablegen von Elementen in einem leeren Bereich des der [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] (in beiden Bereichen) erstellt eine <xref:System.Data.Linq.DataContext> -Methode, die zurückgegeben ein automatisch generierten Typ. Der automatisch generierte Typ erhält einen Namen, der dem der gespeicherten Prozedur oder Funktion entspricht, und Eigenschaften, die den von der gespeicherten Prozedur oder Funktion zurückgegebenen Feldern entsprechen.  
  
> [!NOTE]
>  Sie können den Rückgabetyp einer <xref:System.Data.Linq.DataContext>-Methode ändern, wenn Sie sie dem Methodenbereich hinzugefügt haben. Um zu überprüfen oder Ändern des Rückgabetyps des eine <xref:System.Data.Linq.DataContext> -Methode, wählen Sie ihn, und überprüfen Sie die **Rückgabetyp** -Eigenschaft in der **Eigenschaften** Fenster. Weitere Informationen finden Sie unter [Vorgehensweise: Ändern des Rückgabetyps einer DataContext-Methode (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
 Objekte, die von der Datenbank auf die Oberfläche des O/R-Designers gezogen werden, werden nach den Namen der Objekte in der Datenbank automatisch benannt. Wenn dasselbe Objekt mehrfach auf die Oberfläche gezogen wird, wird an das Ende des neuen Namens eine Nummer angehängt, damit die Namen unterschieden werden können. Wenn Namen von Datenbankobjekten Leerzeichen oder in Visual Basic oder C# nicht unterstützte Zeichen enthalten, wird das entsprechende Zeichen durch einen Unterstrich ersetzt.  
  
## <a name="see-also"></a>Siehe auch  
 [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Gespeicherte Prozeduren](http://msdn.microsoft.com/library/4d23dd7a-a85f-44ff-a717-af7d0950c0fc)   
 [Gewusst wie: Erstellen von DataContext-Methoden zugeordnet wird, um gespeicherte Prozeduren und Funktionen (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)   
 [Gewusst wie: Zuweisen von gespeicherten Prozeduren zum Ausführen von Updates, einfügungen und löschen (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [Exemplarische Vorgehensweise: Anpassen des Einfüge-, Update- und delete-Verhalten von Entitätsklassen](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)   
 [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen (O / R-Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)


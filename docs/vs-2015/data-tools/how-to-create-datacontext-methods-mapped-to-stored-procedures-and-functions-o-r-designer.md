---
title: 'Gewusst wie: Erstellen von DataContext-Methoden zugeordnet wird, um gespeicherte Prozeduren und Funktionen (O / R-Designer) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 62d250946e634627c16dbd3b56fce370c11e1f3f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47514245"
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>Gewusst wie: Erstellen von DataContext-Methoden zugeordnet wird, um gespeicherte Prozeduren und Funktionen (O/R Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Vorgehensweise: Erstellen Sie DataContext-Methoden zugeordnet wird, um gespeicherte Prozeduren und Funktionen (O / R-Designer)](https://docs.microsoft.com/visualstudio/data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer).  
  
  
Gespeicherte Prozeduren und Funktionen können hinzugefügt werden die [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] als <xref:System.Data.Linq.DataContext> Methoden. Aufrufen der Methode und die erforderlichen Parameter übergeben, führt die gespeicherte Prozedur oder Funktion für die Datenbank, und gibt die Daten in den Rückgabetyp der <xref:System.Data.Linq.DataContext> Methode. Ausführliche Informationen zu <xref:System.Data.Linq.DataContext> Methoden finden Sie unter [DataContext-Methoden (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).  
  
> [!NOTE]
>  Mit gespeicherten Prozeduren kann auch das [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]-Standardlaufzeitverhalten überschrieben werden, das beim Speichern von Änderungen von Entitätsklassen in einer Datenbank Einfüge-, Update- und Löschvorgänge durchführt. Weitere Informationen finden Sie unter [Vorgehensweise: Zuweisen von gespeicherten Prozeduren zum Ausführen von Updates, einfügungen und löschen (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
## <a name="creating-datacontext-methods"></a>Erstellen von DataContext-Methoden  
 Sie können erstellen <xref:System.Data.Linq.DataContext> Methoden durch Ziehen von gespeicherten Prozeduren oder Funktionen aus **Server Explorer/Datenbank-Explorer** auf die [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
> [!NOTE]
>  Der Rückgabetyp einer generierten <xref:System.Data.Linq.DataContext>-Methode ist davon abhängig, wo Sie die gespeicherte Prozedur oder Funktion im [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] ablegen. Wenn Sie Elemente direkt auf einer existierenden Entitätsklasse ablegen, wird eine <xref:System.Data.Linq.DataContext>-Methode mit dem Rückgabewert dieser Entitätsklasse erstellt. Wenn Sie Elemente in einem leeren Bereich von [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] ablegen, wird eine <xref:System.Data.Linq.DataContext>-Methode erstellt, die einen automatisch generierten Typ zurückgibt. Sie können den Rückgabetyp ändern eine <xref:System.Data.Linq.DataContext> Methode nach dem Methodenbereich hinzugefügt. Um zu überprüfen oder Ändern des Rückgabetyps des eine <xref:System.Data.Linq.DataContext> -Methode, wählen Sie ihn, und überprüfen Sie die **Rückgabetyp** -Eigenschaft in der **Eigenschaften** Fenster. Weitere Informationen finden Sie unter [Vorgehensweise: Ändern des Rückgabetyps einer DataContext-Methode (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>So erstellen Sie DataContext-Methoden, die automatisch generierte Typen zurückgeben  
  
1.  In **Server-Explorer**/**Datenbank-Explorer**, erweitern Sie die **gespeicherte Prozeduren** Knoten der Datenbank mit dem Sie arbeiten.  
  
2.  Suchen Sie die gewünschte gespeicherte Prozedur, und ziehen Sie diese auf einen leeren Bereich des [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
     Die <xref:System.Data.Linq.DataContext> Methode wird mit einem automatisch generierten Rückgabetyp erstellt und wird in der **Methoden** Bereich.  
  
#### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>So erstellen Sie DataContext-Methoden, die über den Rückgabetyp einer Entitätsklasse verfügen  
  
1.  In **Server-Explorer**/**Datenbank-Explorer**, erweitern Sie die **gespeicherte Prozeduren** Knoten der Datenbank mit dem Sie arbeiten.  
  
2.  Suchen Sie die gewünschte gespeicherte Prozedur, und ziehen Sie diese im [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] auf eine vorhandene Entitätsklasse.  
  
     Die <xref:System.Data.Linq.DataContext> Methode wird mit dem Rückgabetyp der ausgewählten Entitätsklasse erstellt und wird in der **Methoden** Bereich.  
  
> [!NOTE]
>  Informationen zum Ändern des Rückgabetyps vorhandener <xref:System.Data.Linq.DataContext> Methoden finden Sie unter [Vorgehensweise: Ändern des Rückgabetyps einer DataContext-Methode (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
## <a name="see-also"></a>Siehe auch  
 [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [DataContext-Methoden (O/R-Designer)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen (O / R-Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Einführung in LINQ in Visual Basic](http://msdn.microsoft.com/library/3047d86e-0d49-40e2-928b-dc02e46c7984)   
 [Gewusst wie: Schreiben von LINQ-Abfragen in C#](http://msdn.microsoft.com/library/45e47fcc-cfa1-4b72-b161-d038ae87bd23)


---
title: 'Vorgehensweise: Erstellen Sie DataContext-Methoden zugeordnet wird, um gespeicherte Prozeduren und Funktionen (O / R-Designer) | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 25542f9179917c5675eb56753f79db895f5d2ddf
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58956246"
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>Vorgehensweise: Erstellen von DataContext-Methoden, die gespeicherten Prozeduren und Funktionen zugeordnet sind (O/R-Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Gespeicherte Prozeduren und Funktionen können hinzugefügt werden die [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] als <xref:System.Data.Linq.DataContext> Methoden. Durch Aufrufen der Methode und Übergeben der erforderlichen Parameter wird die gespeicherte Prozedur oder Funktion in der Datenbank ausgeführt und gibt die Daten im Rückgabetyp der <xref:System.Data.Linq.DataContext>-Methode zurück. Ausführliche Informationen zu <xref:System.Data.Linq.DataContext> Methoden finden Sie unter [DataContext-Methoden (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).  
  
> [!NOTE]
>  Mit gespeicherten Prozeduren kann auch das [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]-Standardlaufzeitverhalten überschrieben werden, das beim Speichern von Änderungen von Entitätsklassen in einer Datenbank Einfüge-, Update- und Löschvorgänge durchführt. Weitere Informationen finden Sie unter [Vorgehensweise: Zuweisen von gespeicherten Prozeduren zum Durchführen von Aktionen zum Aktualisieren, Einfügen und Löschen (O/R-Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
## <a name="creating-datacontext-methods"></a>Erstellen von DataContext-Methoden  
 Sie können erstellen <xref:System.Data.Linq.DataContext> Methoden durch Ziehen von gespeicherten Prozeduren oder Funktionen aus **Server Explorer/Datenbank-Explorer** auf die [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
> [!NOTE]
>  Der Rückgabetyp einer generierten <xref:System.Data.Linq.DataContext>-Methode ist davon abhängig, wo Sie die gespeicherte Prozedur oder Funktion im [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] ablegen. Wenn Sie Elemente direkt auf einer existierenden Entitätsklasse ablegen, wird eine <xref:System.Data.Linq.DataContext>-Methode mit dem Rückgabetyp dieser Entitätsklasse erstellt. Wenn Sie Elemente in einem leeren Bereich von [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] ablegen, wird eine <xref:System.Data.Linq.DataContext>-Methode erstellt, die einen automatisch generierten Typ zurückgibt. Sie können den Rückgabetyp ändern eine <xref:System.Data.Linq.DataContext> Methode nach dem Methodenbereich hinzugefügt. Um den Rückgabetyp einer <xref:System.Data.Linq.DataContext>-Methode zu überprüfen oder zu ändern, markieren Sie sie, und überprüfen Sie die Eigenschaft **Rückgabetyp** im Fenster **Eigenschaften**. Weitere Informationen finden Sie unter [Vorgehensweise: Ändern des Rückgabetyps für eine DataContext-Methode (O/R-Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>So erstellen Sie DataContext-Methoden, die automatisch generierte Typen zurückgeben  
  
1.  In **Server-Explorer**/**Datenbank-Explorer**, erweitern Sie die **gespeicherte Prozeduren** Knoten der Datenbank mit dem Sie arbeiten.  
  
2.  Suchen Sie die gewünschte gespeicherte Prozedur, und ziehen Sie diese auf einen leeren Bereich des [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
     Die <xref:System.Data.Linq.DataContext>-Methode wird mit einem automatisch generierten Rückgabetyp erstellt und im Bereich **Methoden** angezeigt.  
  
#### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>So erstellen Sie DataContext-Methoden, die über den Rückgabetyp einer Entitätsklasse verfügen  
  
1.  In **Server-Explorer**/**Datenbank-Explorer**, erweitern Sie die **gespeicherte Prozeduren** Knoten der Datenbank mit dem Sie arbeiten.  
  
2.  Suchen Sie die gewünschte gespeicherte Prozedur, und ziehen Sie diese im [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] auf eine vorhandene Entitätsklasse.  
  
     Die <xref:System.Data.Linq.DataContext>-Methode wird mit dem Rückgabetyp der ausgewählten Entitätsklasse erstellt und im Bereich **Methoden** angezeigt.  
  
> [!NOTE]
>  Informationen zum Ändern des Rückgabetyps vorhandener <xref:System.Data.Linq.DataContext> Methoden finden Sie unter [Vorgehensweise: Ändern des Rückgabetyps für eine DataContext-Methode (O/R-Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
## <a name="see-also"></a>Siehe auch  
 [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [DataContext-Methoden (O/R-Designer)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen (O / R-Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Einführung in LINQ in Visual Basic](http://msdn.microsoft.com/library/3047d86e-0d49-40e2-928b-dc02e46c7984)   
 [Vorgehensweise: Schreiben von LINQ-Abfragen inC#](http://msdn.microsoft.com/library/45e47fcc-cfa1-4b72-b161-d038ae87bd23)

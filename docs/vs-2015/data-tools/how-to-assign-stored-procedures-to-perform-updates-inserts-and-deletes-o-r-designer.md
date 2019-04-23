---
title: 'Vorgehensweise: Zuweisen von gespeicherten Prozeduren zum Ausführen von Updates, einfügungen und löschen (O / R Designer) | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: e88224ab-ff61-4a3a-b6b8-6f3694546cac
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 247e1720a21c88f15a766fb948156e93ec55e308
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2019
ms.locfileid: "59656322"
---
# <a name="how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-or-designer"></a>Vorgehensweise: Zuweisen von gespeicherten Prozeduren zum Durchführen von Aktionen zum Aktualisieren, Einfügen und Löschen (O/R-Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gespeicherte Prozeduren können dem O/R-Designer hinzugefügt und als typische <xref:System.Data.Linq.DataContext>-Methoden ausgeführt werden. Sie können auch zum Überschreiben des Standardwerts verwendet [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] Laufzeitverhalten führen konnte, die Einfüge-, Update- und Löschvorgänge ausführt, wenn Änderungen von Entitätsklassen in einer Datenbank gespeichert werden (z. B. beim Aufrufen der <xref:System.Data.Linq.DataContext.SubmitChanges%2A> Methode).  
  
> [!NOTE]
>  Wenn Ihre gespeicherte Prozedur Werte zurückgibt, die an den Client zurückgesendet werden müssen (beispielsweise Werte, die in der gespeicherten Prozedur berechnet werden), sollten Sie Ausgabeparameter in Ihrer gespeicherten Prozedur erstellen. Wenn Sie keine Ausgabeparameter verwenden können, sollten Sie eine partielle Methodenimplementierung schreiben und sich nicht auf vom O/R-Designer erzeugte Überschreibungen verlassen. Member, die datenbankgenerierten Werten zugeordnet werden, müssen nach erfolgreicher Beendigung von INSERT- oder UPDATE-Vorgängen auf entsprechende Werte festgelegt werden. Weitere Informationen finden Sie unter [Verantwortlichkeiten der Entwickler In Überschreiben von Standardverhalten](http://msdn.microsoft.com/library/c6909ddd-e053-46a8-980c-0e12a9797be1).  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] behandelt datenbankgenerierte Werte für die Identitätsspalte (automatisch inkrementiert), die ROWGUID-Spalte (datenbankgenerierte GUID) und Timestamp-Spalte automatisch. Datenbankgenerierte Werte in anderen Spaltentypen führen unerwartet zu einem NULL-Wert. Um die datenbankgenerierten Werte zurückzugeben, sollte manuell <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> auf `true` und <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> auf eine der folgenden Einstellungen festgelegt werden: <xref:System.Data.Linq.Mapping.AutoSync>, <xref:System.Data.Linq.Mapping.AutoSync> oder <xref:System.Data.Linq.Mapping.AutoSync>.  
  
## <a name="configuring-the-update-behavior-of-an-entity-class"></a>Konfigurieren des Updateverhaltens einer Entitätsklasse  
 Standardmäßig wird die Updatelogik einer Datenbank (Einfüge-, Update- und Löschvorgänge) mit Änderungen, die von [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]-Entitätsklassen an Daten vorgenommen wurden, von der [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]-Laufzeit bereitgestellt. Die Laufzeit erstellt INSERT-, Update- und Delete-Befehle, die für das Schema der Tabelle (Spalte und Primärschlüsselinformationen) basieren. Wenn das Standardverhalten nicht erwünscht ist, kann das Updateverhalten konfiguriert werden, indem spezielle gespeicherte Prozeduren zur Durchführung der erforderlichen Einfüge-, Update- und Löschvorgänge für die Bearbeitung der Daten in der Tabelle zugewiesen werden. Diese Vorgehensweise ist auch dann sinnvoll, wenn kein Standardverhalten erzeugt wird, z. B. wenn die Entitätsklassen Ansichten zugeordnet sind. Schließlich kann das standardmäßige Updateverhalten auch dann überschrieben werden, wenn die Datenbank den Zugriff auf Tabellen über gespeicherte Prozeduren erfordert.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-assign-stored-procedures-to-override-the-default-behavior-of-an-entity-class"></a>So weisen Sie gespeicherte Prozeduren zu, um das Standardverhalten einer Entitätsklasse zu überschreiben  
  
1.  Öffnen Sie die **LINQ to SQL**-Datei im Designer. (Doppelklicken Sie auf die DBML-Datei in **Projektmappen-Explorer**.)  
  
2.  In **Server-Explorer**/**Datenbank-Explorer**, erweitern Sie **gespeicherte Prozeduren** und suchen Sie die gespeicherten Prozeduren, die für die INSERT-, Update-, verwendet werden sollen. und/oder Löschbefehle der Entitätsklasse.  
  
3.  Ziehen Sie die gespeicherte Prozedur in den O/R-Designer.  
  
     Die gespeicherte Prozedur wird dem Methodenbereich als <xref:System.Data.Linq.DataContext>-Methode hinzugefügt. Weitere Informationen finden Sie unter [DataContext-Methoden (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).  
  
4.  Wählen Sie die Entitätsklasse aus, für die die gespeicherte Prozedur zur Durchführung von Updates verwendet werden soll.  
  
5.  Wählen Sie im Fenster **Eigenschaften** den Befehl aus, der überschrieben werden soll (**Einfügen**, **Aktualisieren** oder **Löschen**).  
  
6.  Klicken Sie auf die Auslassungszeichen (...) neben den Wörtern **Laufzeit verwenden**, um das Dialogfeld **Verhalten konfigurieren** zu öffnen.  
  
7.  Wählen Sie **Anpassen** aus.  
  
8.  Wählen Sie die gewünschte gespeicherte Prozedur in der Liste **Anpassen** aus.  
  
9. Untersuchen Sie die Listen **Methodenargumente** und **Klasseneigenschaften**, um zu überprüfen, ob die **Methodenargumente** den entsprechenden **Klasseneigenschaften** zugeordnet sind. Ordnen Sie die ursprünglichen Methodenargumente (Original_*ArgumentName*) den ursprünglichen Eigenschaften (*PropertyName* (Original)) für Update- und Delete-Befehle.  
  
    > [!NOTE]
    >  Standardmäßig werden Methodenargumente Klasseneigenschaften zugeordnet, wenn die Namen übereinstimmen. Wenn geänderte Eigenschaftennamen von Tabelle und Entitätsklasse nicht mehr übereinstimmen, kann es notwendig sein, die entsprechende Klasseneigenschaft für die Zuordnung auszuwählen, wenn der Designer die korrekte Zuordnung nicht ermitteln kann.  
  
10. Klicken Sie auf **OK** oder auf **Anwenden**.  
  
    > [!NOTE]
    >  Sie können mit der Konfiguration des Verhaltens jeder Klasse/Verhalten-Kombination fortfahren, solange Sie nach jeder Änderung auf **Anwenden** klicken. Wenn Sie die Klasse oder das Verhalten ändern, bevor Sie auf **übernehmen**, ein Warnungsdialogfeld eine Möglichkeit zum Anwenden von Änderungen wird angezeigt.  
  
     Um zur Verwendung der standardlaufzeitlogik für Updates zurückzukehren, klicken Sie auf die Auslassungspunkte neben dem Einfüge-, Update- oder Delete-Befehl in der **Eigenschaften** Fenster und wählen Sie dann **-Laufzeitumgebung verwenden** in die  **Konfigurieren des Verhaltens** Dialogfeld.  
  
## <a name="see-also"></a>Siehe auch  
 [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [DataContext-Methoden (O/R-Designer)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen (O / R-Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Insert-, Update- und Delete-Operationen](http://msdn.microsoft.com/library/26a43a4f-83c9-4732-806d-bb23aad0ff6b)

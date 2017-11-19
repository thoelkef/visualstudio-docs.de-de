---
title: "Verwenden Sie gespeicherte Prozeduren zum Ausführen von Update-, insert und delete in Linq to SQL-O/R-Designer | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e88224ab-ff61-4a3a-b6b8-6f3694546cac
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: f0d6910d2bf449172bac86a3ecd18be8169ef244
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2017
---
# <a name="how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-or-designer"></a>Vorgehensweise: Zuweisen von gespeicherten Prozeduren zum Ausführen von Updates, einfügungen und löschen (O/R-Designer)
Gespeicherte Prozeduren können dem O/R-Designer hinzugefügt und als typische <xref:System.Data.Linq.DataContext>-Methoden ausgeführt werden. Sie können auch zum Überschreiben der standardmäßigen verwendet [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] Laufzeitverhalten, die Einfüge-, Update- und Löschvorgänge durchführt, wenn Änderungen von Entitätsklassen in einer Datenbank gespeichert sind (z. B. beim Aufrufen der <xref:System.Data.Linq.DataContext.SubmitChanges%2A> Methode).  
  
> [!NOTE]
>  Wenn Ihre gespeicherte Prozedur Werte zurückgibt, die an den Client zurückgesendet werden müssen (beispielsweise Werte, die in der gespeicherten Prozedur berechnet werden), sollten Sie Ausgabeparameter in Ihrer gespeicherten Prozedur erstellen. Wenn Sie keine Ausgabeparameter verwenden können, sollten Sie eine partielle Methodenimplementierung schreiben und sich nicht auf vom O/R-Designer erzeugte Überschreibungen verlassen. Member, die datenbankgenerierten Werten zugeordnet werden, müssen nach erfolgreicher Beendigung von INSERT- oder UPDATE-Vorgängen auf entsprechende Werte festgelegt werden. Weitere Informationen finden Sie unter [Aufgaben der Entwickler beim Überschreiben von Standardverhalten](/dotnet/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior).  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] behandelt datenbankgenerierte Werte für die Identitätsspalte (automatisch inkrementiert), die ROWGUID-Spalte (datenbankgenerierte GUID) und Timestamp-Spalte automatisch. Datenbankgenerierte Werte in anderen Spaltentypen führen unerwartet zu einem NULL-Wert. Um die datenbankgenerierten Werte zurückzugeben, sollte manuell <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> auf `true` und <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> auf eine der folgenden Einstellungen festgelegt werden: <xref:System.Data.Linq.Mapping.AutoSync>, <xref:System.Data.Linq.Mapping.AutoSync> oder <xref:System.Data.Linq.Mapping.AutoSync>.  
  
## <a name="configuring-the-update-behavior-of-an-entity-class"></a>Konfigurieren des Updateverhaltens einer Entitätsklasse  
 Standardmäßig ist die Logik für eine Datenbank (einfügungen, Updates und löschungen) mit Änderungen zu aktualisieren, die auf die Daten in vorgenommen wurden [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] Entitätsklassen wird bereitgestellt, indem Sie die [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] Common Language Runtime. Erstellt die Laufzeit standardmäßig INSERT-, Update- und DELETE-Befehle, die abhängig von der das Schema der Tabelle (Spalte und Primärschlüsselinformationen). Wenn das Standardverhalten nicht erwünscht ist, können Sie das Updateverhalten konfigurieren, indem spezielle gespeicherte Prozeduren zum Ausführen der erforderlichen einfügungen, Updates und Löschvorgänge erforderlich, um die Daten in der Tabelle bearbeiten zuweisen. Diese Vorgehensweise ist auch dann sinnvoll, wenn kein Standardverhalten erzeugt wird, z. B. wenn die Entitätsklassen Ansichten zugeordnet sind. Schließlich kann das standardmäßige Updateverhalten auch dann überschrieben werden, wenn die Datenbank den Zugriff auf Tabellen über gespeicherte Prozeduren erfordert.  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-assign-stored-procedures-to-override-the-default-behavior-of-an-entity-class"></a>So weisen Sie gespeicherte Prozeduren zu, um das Standardverhalten einer Entitätsklasse zu überschreiben  
  
1.  Öffnen der **LINQ to SQL** Datei im Designer. (Doppelklicken Sie auf die DBML-Datei in **Projektmappen-Explorer**.)  
  
2.  In **Server-Explorer**/**Datenbank-Explorer**, erweitern Sie **gespeicherte Prozeduren** und suchen Sie die gespeicherten Prozeduren, die für die INSERT-, Update-, verwendet werden sollen. und/oder Löschbefehle der Entitätsklasse.  
  
3.  Ziehen Sie die gespeicherte Prozedur in den O/R-Designer.  
  
     Die gespeicherte Prozedur wird dem Methodenbereich als <xref:System.Data.Linq.DataContext>-Methode hinzugefügt. Weitere Informationen finden Sie unter [DataContext-Methoden (O/R-Designer)](../data-tools/datacontext-methods-o-r-designer.md).  
  
4.  Wählen Sie die Entitätsklasse aus, für die die gespeicherte Prozedur zur Durchführung von Updates verwendet werden soll.  
  
5.  In der **Eigenschaften** Fenster, wählen Sie den Befehl zum Überschreiben (**einfügen**, **Update**, oder **löschen**).  
  
6.  Klicken Sie auf die Auslassungspunkte (...) neben den Wörtern **Laufzeit** So öffnen die **Verhalten konfigurieren** (Dialogfeld).  
  
7.  Wählen Sie **anpassen**.  
  
8.  Wählen Sie die gewünschte gespeicherte Prozedur in der **anpassen** Liste.  
  
9. Überprüfen Sie die Liste der **Methodenargumente** und **Klasseneigenschaften** zu überprüfen, ob die **Methodenargumente** Zuordnung an die entsprechende **Klasseneigenschaften**. Ordnen Sie die ursprünglichen Methodenargumente (Original_*ArgumentName*) den ursprünglichen Eigenschaften (*PropertyName* (Original)) für Update- und Delete-Befehle.  
  
    > [!NOTE]
    >  Standardmäßig werden Methodenargumente Klasseneigenschaften zugeordnet, wenn die Namen übereinstimmen. Wenn geänderte Eigenschaftennamen von Tabelle und Entitätsklasse nicht mehr übereinstimmen, kann es notwendig sein, die entsprechende Klasseneigenschaft für die Zuordnung auszuwählen, wenn der Designer die korrekte Zuordnung nicht ermitteln kann.  
  
10. Klicken Sie auf **OK** oder **gelten**.  
  
    > [!NOTE]
    >  Sie können die Konfiguration des Verhaltens jeder Klasse/Verhalten-Kombination, solange Sie klicken Sie auf Weiter **übernehmen** nach jeder Änderung. Wenn Sie die Klasse oder das Verhalten ändern, bevor Sie auf **übernehmen**, ein Warnungsdialogfeld Gelegenheit bietet, alle Änderungen zu übernehmen, wird angezeigt.  
  
Um zur Verwendung der standardlaufzeitlogik für Updates zurückzukehren, klicken Sie auf das Auslassungszeichen neben der INSERT-, Update- oder Delete-Befehl in der **Eigenschaften** Fenster und wählen Sie dann **verwenden Common Language Runtime** in der  **Konfigurieren Sie das Verhalten** (Dialogfeld).  
  
## <a name="see-also"></a>Siehe auch
[LINQ to SQL-tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
[DataContext-Methoden](../data-tools/datacontext-methods-o-r-designer.md)   
[LINQ to SQL ((.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)   
[INSERT-, Update- und Delete-Operationen ((.NET Framework)](/dotnet/framework/data/adonet/sql/linq/insert-update-and-delete-operations)
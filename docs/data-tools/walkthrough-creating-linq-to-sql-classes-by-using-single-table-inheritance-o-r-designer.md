---
title: 'Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen mithilfe der Vererbung einer einzelnen Tabelle (O / R-Designer)'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 63bc6328-e0df-4655-9ce3-5ff74dbf69a4
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 943b75c9c5f9c0c32ab02b5e73c07282728e0beb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49864726"
---
# <a name="walkthrough-create-linq-to-sql-classes-by-using-single-table-inheritance-or-designer"></a>Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen mithilfe der Vererbung einer einzelnen Tabelle (O/R Designer)
Die [LINQ to SQL-tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) unterstützt Vererbung einer einzelnen Tabelle aus, wie sie in der Regel in relationalen Systemen implementiert ist. Diese exemplarische Vorgehensweise baut auf den allgemeinen Schritten der [Vorgehensweise: Konfigurieren der Vererbung mit dem O/R-Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) Thema und stellt realen Daten zur Veranschaulichung der Verwendung von Vererbung in der [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].

 Im Verlauf dieser exemplarischen Vorgehensweise führen Sie die folgenden Aufgaben aus:

- Erstellen einer Datenbanktabelle und Hinzufügen von Daten.

- Erstellen einer Windows Forms-Anwendung.

- Hinzufügen einer [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]-Datei zu einem Projekt.

- Erstellen neuer Entitätsklassen.

- Konfigurieren der Entitätsklassen zur Verwendung von Vererbung.

- Abfragen der geerbten Klasse.

- Anzeigen der Daten in einem Windows Form.

## <a name="create-a-table-to-inherit-from"></a>Erstellen einer Tabelle, die von erben
 Um die Funktionsweise der Vererbung angezeigt wird, erstellen Sie eine kleine `Person` Tabellen, verwenden Sie diese als eine Basisklasse und erstellen dann eine `Employee` -Objekt, das von ihr erbt.

### <a name="to-create-a-base-table-to-demonstrate-inheritance"></a>So erstellen Sie eine Basistabelle zur Veranschaulichung der Vererbung

1.  In **Server-Explorer** oder **Datenbank-Explorer**, mit der rechten Maustaste die **Tabellen** Knoten, und klicken Sie auf **neue Tabelle hinzufügen**.

    > [!NOTE]
    >  Sie können die Northwind-Datenbank oder eine andere Datenbank verwenden, der Sie eine Tabelle hinzufügen können.

2.  In der **Tabellen-Designer**, fügen Sie die folgenden Spalten der Tabelle:

    |Spaltenname|Datentyp|NULL zulassen|
    |-----------------|---------------|-----------------|
    |**ID**|**int**|**False**|
    |**Type**|**int**|**True**|
    |**Vorname**|**nvarchar(200)**|**False**|
    |**"LastName"**|**nvarchar(200)**|**False**|
    |**Manager**|**int**|**True**|

3.  Legen Sie die ID-Spalte als Primärschlüssel fest.

4.  Speichern Sie die Tabelle, und nennen Sie sie **Person**.

## <a name="add-data-to-the-table"></a>Hinzufügen von Daten in die Tabelle
 Um sicherstellen zu können, dass die Vererbung ordnungsgemäß konfiguriert ist, muss die Tabelle Daten für jede Klasse in der Vererbung einer einzelnen Tabelle enthalten.

### <a name="to-add-data-to-the-table"></a>So fügen Sie der Tabelle Daten hinzu

1.  Öffnen Sie die Tabelle in der Datenansicht. (Mit der rechten Maustaste die **Person** -Tabelle **Server-Explorer** oder **Datenbank-Explorer** , und klicken Sie auf **Tabellendaten anzeigen**.)

2.  Kopieren Sie die folgenden Daten in die Tabelle. (Sie kopieren und fügen Sie ihn in die Tabelle durch Auswahl der gesamten Zeile in der **Ergebnisse** Bereich.)

    ||||||
    |-|-|-|-|-|
    |**ID**|**Type**|**Vorname**|**"LastName"**|**Manager**|
    |**1**|**1**|**Anne**|**Wallace**|**NULL**|
    |**2**|**1**|**Carlos**|**Grilo**|**NULL**|
    |**3**|**1**|**Yael**|**Peled**|**NULL**|
    |**4**|**2**|**Gatis**|**Ozolins**|**1**|
    |**5**|**2**|**Andreas**|**Hauser**|**1**|
    |**6**|**2**|**Tiffany**|**Phuvasate**|**1**|
    |**7**|**2**|**Alexey**|**Orekhov**|**2**|
    |**8**|**2**|**Michał**|**Poliszkiewicz**|**2**|
    |**9**|**2**|**Tai**|**Yee**|**2**|
    |**10**|**2**|**Fabricio**|**Noriega**|**3**|
    |**11**|**2**|**Mindy**|**Martin**|**3**|
    |**12**|**2**|**Ken**|**Kwok**|**3**|

## <a name="create-a-new-project"></a>Erstellt ein neues Projekt
 Nachdem Sie die Tabelle erstellt haben, erstellen Sie ein neues Projekt zur Darstellung der Konfiguration von Vererbung.

### <a name="to-create-the-new-windows-forms-application"></a>Um die neue Windows Forms-Anwendung zu erstellen.

1. In Visual Studio auf die **Datei** , wählen Sie im Menü **neu** > **Projekt**.

2. Erweitern Sie entweder **Visual C#-** oder **Visual Basic** wählen Sie im linken Bereich **Windows Desktop**.

3. Wählen Sie im mittleren Bereich die **Windows Forms-App** Projekttyp.

4. Nennen Sie das Projekt **InheritanceWalkthrough**, und wählen Sie dann **OK**.

     Die **InheritanceWalkthrough** Projekt wird erstellt und hinzugefügt **Projektmappen-Explorer**.

## <a name="add-a-linq-to-sql-classes-file-to-the-project"></a>Hinzufügen einer LINQ to SQL-Klassendatei zum Projekt

### <a name="to-add-a-linq-to-sql-file-to-the-project"></a>Um eine LINQ to SQL-Datei zum Projekt hinzufügen

1.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.

2.  Klicken Sie auf die **LINQ to SQL-Klassen** -Vorlage, und klicken Sie dann auf **hinzufügen**.

     Die *dbml* Datei wird dem Projekt hinzugefügt und die **O/R Designer** wird geöffnet.

## <a name="create-the-inheritance-by-using-the-or-designer"></a>Erstellen der Vererbung mit dem O/R-Designer
 Konfigurieren Sie die Vererbung durch Ziehen einer **Vererbung** -Objekt aus der **Toolbox** auf die Entwurfsoberfläche.

### <a name="to-create-the-inheritance"></a>So erstellen Sie die Vererbung

1.  In **Server-Explorer** oder **Datenbank-Explorer**, navigieren Sie zu der **Person** Tabelle, die Sie zuvor erstellt haben.

2.  Ziehen Sie die **Person** die Tabelle auf die **O/R Designer** Entwurfsoberfläche.

3.  Ziehen Sie eine zweite **Person** die Tabelle auf die **O/R Designer** und ändern Sie den Namen **Mitarbeiter**.

4.  Löschen der **Manager** Eigenschaft aus der **Person** Objekt.

5.  Löschen der **Typ**, **ID**, **FirstName**, und **"LastName"** Eigenschaften aus der **Mitarbeiter** Objekt. (Das heißt, löschen Sie alle Eigenschaften außer **Manager**.)

6.  Aus der **Object Relational Designer** auf der Registerkarte die **Toolbox**, erstellen Sie eine **Vererbung** zwischen der **Person** und  **Mitarbeiter** Objekte. Zu diesem Zweck klicken Sie auf die **Vererbung** Element in der **Toolbox** und die Maustaste los. Klicken Sie anschließend die **Mitarbeiter** Objekt und klicken Sie dann die **Person** -Objekt in der **O/R Designer**. Klicken Sie dann der Pfeil der Vererbungslinie zeigt, auf die **Person** Objekt.

7.  Klicken Sie auf die **Vererbung** Zeile auf der Entwurfsoberfläche angezeigt.

8.  Legen Sie die **Unterscheidungseigenschaft** Eigenschaft **Typ**.

9. Legen Sie die **abgeleiteter Klassendiskriminatorwert** Eigenschaft **2**.

10. Legen Sie die **Basisklassen-Diskriminatorwert** Eigenschaft **1**.

11. Legen Sie die **Vererbungsstandard** Eigenschaft **Person**.

12. Erstellen Sie das Projekt.

## <a name="query-the-inherited-class-and-display-the-data-on-the-form"></a>Abfragen der geerbten Klasse aus, und zeigen Sie die Daten auf dem Formular
 Code wird jetzt auf das Formular, das für eine bestimmte Klasse im Objektmodell Abfragen hinzufügen.

### <a name="to-create-a-linq-query-and-display-the-results-on-the-form"></a>So erstellen Sie eine LINQ-Abfrage und zeigen die Ergebnisse im Formular an

1.  Ziehen Sie eine **ListBox** auf **Form1**.

2.  Doppelklicken Sie auf das Formular, um einen `Form1_Load`-Ereignishandler zu erstellen.

3.  Fügen Sie dem `Form1_Load` -Ereignishandler folgenden Code hinzu:

    ```vb
    Dim dc As New DataClasses1DataContext
    Dim results = From emp In dc.Persons _
        Where TypeOf emp Is Employee _
        Select emp

    For Each Emp As Employee In results
        ListBox1.Items.Add(Emp.LastName)
    Next
    ```

    ```csharp
    NorthwindDataContext dc = new DataClasses1DataContext();
    var results = from emp in dc.Persons
                  where emp is Employee
                  select emp;

    foreach(Employee Emp in results)
    {
        listBox1.Items.Add(Emp.LastName)
    }
    ```

## <a name="test-the-application"></a>Testen der Anwendung
 Führen Sie die Anwendung, und stellen Sie sicher, dass die im Listenfeld angezeigten Datensätze Mitarbeiter sind (Datensätze, bei denen der Wert 2 in ihre **Typ** Spalte).

### <a name="to-test-the-application"></a>So testen Sie die Anwendung

1.  Drücken Sie **F5**.

2.  Stellen Sie sicher, die nur aufzeichnet, die den Wert 2 in ihre **Typ** Spalte angezeigt werden.

3.  Schließen Sie das Formular. (Auf der **Debuggen** Menü klicken Sie auf **Debuggen beenden**.)

## <a name="see-also"></a>Siehe auch

- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen (O / R-Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Vorgehensweise: Zuweisen von gespeicherten Prozeduren zum Durchführen von Aktionen zum Aktualisieren, Einfügen und Löschen (O/R-Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Gewusst wie: Generieren des Objektmodells in Visual Basic oder c#](/dotnet/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp)
---
title: 'Exemplarische Vorgehensweise: Erstellen von LINQ to SQL Klassen mithilfe einer Vererbung für eine einzelne Tabelle (O-R-Designer) | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 63bc6328-e0df-4655-9ce3-5ff74dbf69a4
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9cf95bd2095d9713d498ddccf68fd1e81e1b1e64
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85535706"
---
# <a name="walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-or-designer"></a>Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen mit einer Vererbung für eine einzelne Tabelle (O/R-Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) unterstützen die Vererbung einer einzelnen Tabelle, da Sie in der Regel in relationalen Systemen implementiert ist. In dieser exemplarischen Vorgehensweise werden die allgemeinen Schritte beschrieben, die im Thema Gewusst [wie: Konfigurieren der Vererbung mit dem O/R-Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) erläutert werden, und es werden echte Daten bereitgestellt, um die Verwendung der Vererbung in zu veranschaulichen [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

 Im Verlauf dieser exemplarischen Vorgehensweise führen Sie folgende Aufgaben aus:

- Erstellen einer Datenbanktabelle und Hinzufügen von Daten.

- Erstellen einer Windows Forms-Anwendung.

- Hinzufügen einer [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]-Datei zu einem Projekt.

- Erstellen neuer Entitätsklassen.

- Konfigurieren der Entitätsklassen zur Verwendung von Vererbung.

- Abfragen der geerbten Klasse.

- Anzeigen der Daten in einem Windows Form.

## <a name="create-a-table-to-inherit-from"></a>Erstellen einer Tabelle, von der geerbt werden soll
 Um die Funktionsweise der Vererbung kennen zu lernen, erstellen Sie eine kleine Person-Tabelle, verwenden sie als Basisklasse und erstellen anschließend ein Employee-Objekt, das von ihr erbt.

#### <a name="to-create-a-base-table-to-demonstrate-inheritance"></a>So erstellen Sie eine Basistabelle zur Veranschaulichung der Vererbung

1. Klicken Sie in **Server-Explorer** / **Datenbank-Explorer**mit der rechten Maustaste auf den Knoten **Tabellen** , und klicken Sie auf **neue Tabelle hinzufügen**.

    > [!NOTE]
    > Sie können die Northwind-Datenbank oder eine andere Datenbank verwenden, der Sie eine Tabelle hinzufügen können.

2. Fügen Sie der Tabelle im Tabellen-Designer die folgenden Spalten hinzu:

    |Spaltenname|Datentyp|NULL-Werte zulassen|
    |-----------------|---------------|-----------------|
    |**ID**|**int**|**Alarm**|
    |**Typ**|**int**|**True**|
    |**Vorname**|**nvarchar(200)**|**Alarm**|
    |**Nachname**|**nvarchar(200)**|**Alarm**|
    |**Manager**|**int**|**True**|

3. Legen Sie die ID-Spalte als Primärschlüssel fest.

4. Speichern Sie die Tabelle unter dem Namen **Person**.

## <a name="add-data-to-the-table"></a>Hinzufügen von Daten zur Tabelle
 Um sicherstellen zu können, dass die Vererbung ordnungsgemäß konfiguriert ist, muss die Tabelle Daten für jede Klasse in der Vererbung einer einzelnen Tabelle enthalten.

#### <a name="to-add-data-to-the-table"></a>So fügen Sie der Tabelle Daten hinzu

1. Öffnen Sie die Tabelle in der Datenansicht. (Klicken Sie mit der rechten Maustaste auf die Tabelle **Person** in **Server-Explorer** / Klicken Sie **Datenbank-Explorer** und klicken Sie auf **Tabellendaten anzeigen**.)

2. Kopieren Sie die folgenden Daten in die Tabelle. (Sie können Sie kopieren und in die Tabelle einfügen, indem Sie im Ergebnisbereich die gesamte Zeile auswählen.)

    |**ID**|**Typ**|**Vorname**|**Nachname**|**Manager**|
    |-|-|-|-|-|
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

## <a name="create-a-new-project"></a>Erstellen eines neues Projekts
 Nachdem Sie die Tabelle erstellt haben, erstellen Sie ein neues Projekt zur Darstellung der Konfiguration von Vererbung.

#### <a name="to-create-the-new-windows-application"></a>So erstellen Sie die neue Windows-Anwendung

1. Erstellen Sie im Menü **Datei** ein neues Projekt.

2. Nennen Sie das Projekt " **vererancewalkthrough**".

    > [!NOTE]
    > Der [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] wird von Visual Basic- und C#-Projekten unterstützt. Erstellen Sie das neue Projekt in einer der beiden Sprachen.

3. Klicken Sie auf die **Windows Forms Anwendungs** Vorlage, und klicken Sie dann auf **OK**. Weitere Informationen finden Sie unter [Client Anwendungen](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

4. Das Projekt "vererancewalkthrough" wird erstellt und **Projektmappen-Explorer**hinzugefügt.

## <a name="add-a-linq-to-sql-classes-file-to-the-project"></a>Hinzufügen einer LINQ to SQL-Klassendatei zum Projekt

#### <a name="to-add-a-linq-to-sql-file-to-the-project"></a>So fügen Sie dem Projekt eine LINQ to SQL-Datei hinzu

1. Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.

2. Klicken Sie auf die Vorlage **LINQ to SQL-Klassen** und dann auf **Hinzufügen**.

     Dem Projekt wird die DBML-Datei hinzugefügt, und der [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] wird geöffnet.

## <a name="create-the-inheritance-by-using-the-or-designer"></a>Erstellen der Vererbung mithilfe des O/R-Designers
 Konfigurieren Sie die Vererbung, indem Sie aus der **Toolbox** ein Objekt aus dem Bereich **Vererbung** auf die Entwurfsoberfläche ziehen.

#### <a name="to-create-the-inheritance"></a>So erstellen Sie die Vererbung

1. Navigieren Sie in **Server-Explorer** / **Datenbank-Explorer**zu der Tabelle **Person** , die Sie zuvor erstellt haben.

2. Ziehen Sie die **Person** -Tabelle auf die [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] Entwurfs Oberfläche.

3. Ziehen Sie eine zweite **Person** -Tabelle auf den [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] , und ändern Sie den Namen in **Employee**.

4. Löschen Sie die **Manager**-Eigenschaft aus dem Objekt **Person**.

5. Löschen Sie die Eigenschaften **Type**, **ID**, **FirstName** und **LastName** aus dem Objekt **Employee**. (Mit anderen Worten: Entfernen Sie alle Eigenschaften außer **Manager**.)

6. Erstellen Sie von der Registerkarte **Objektrelationaler Designer** der **Toolbox** eine **Vererbung** zwischen dem **Person**-Objekt und dem **Employee**-Objekt. Klicken Sie dazu in der **Toolbox** auf das Element **Vererbung**, und lassen Sie die Maustaste los. Klicken Sie als nächstes auf das **Employee** -Objekt und dann auf das **Person** -Objekt in [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . Der Pfeil in der Vererbungs Zeile verweist auf das **Person** -Objekt.

7. Klicken Sie auf die Linie der **Vererbung** auf der Entwurfsoberfläche.

8. Legen Sie die Eigenschaft **Diskriminatoreigenschaft** auf **Type** fest.

9. Legen Sie die Eigenschaft **Diskrimatorwert der abgeleiteten Klasse** auf **2** fest.

10. Legen Sie die Eigenschaft **Basisklassen-Diskrimatorwert** auf **1** fest.

11. Legen Sie die **Vererbungsstandard**-Eigenschaft auf **Person** fest.

12. Erstellen Sie das Projekt.

## <a name="query-the-inherited-class-and-display-the-data-on-the-form"></a>Abfragen der geerbten Klasse und Anzeigen der Daten im Formular
 Im Folgenden fügen Sie dem Formular Code zur Abfrage einer bestimmten Klasse im Objektmodell hinzu.

#### <a name="to-create-a-linq-query-and-display-the-results-on-the-form"></a>So erstellen Sie eine LINQ-Abfrage und zeigen die Ergebnisse im Formular an

1. Ziehen Sie ein **ListBox** -Steuerfeld auf Form1.

2. Doppelklicken Sie auf das Formular, um einen `Form1_Load`-Ereignishandler zu erstellen.

3. Fügen Sie dem `Form1_Load` -Ereignishandler folgenden Code hinzu:

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
 Führen Sie die Anwendung aus, und überprüfen Sie, ob alle im Listenfeld angezeigten Datensätze Mitarbeiter sind (Datensätze, die den Wert 2 in der Type-Spalte haben).

#### <a name="to-test-the-application"></a>So testen Sie die Anwendung

1. Drücken Sie F5.

2. Stellen Sie sicher, dass nur Datensätze angezeigt werden, die den Wert 2 in ihrer Type-Spalte haben.

3. Schließen Sie das Formular. (Klicken Sie im Menü **Debuggen** auf **Debugging Debuggen**.)

## <a name="see-also"></a>Weitere Informationen
 [LINQ to SQL Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) Gewusst [wie: Hinzufügen von LINQ to SQL Klassen zu einem Projekt (o-r-Designer)](https://msdn.microsoft.com/library/7bb184ab-ec54-4cda-b706-604b2b4a3ed6) Exemplarische Vorgehensweise: [Erstellen von LINQ to SQL Klassen (o-r-Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) Gewusst [wie: Zuweisen von gespeicherten Prozeduren zum Ausführen von Aktualisierungen, Einfügungen und Löschungen (o/r-Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) Gewusst [wie: Generieren des Objektmodells in Visual Basic oder c#](https://msdn.microsoft.com/library/a0c73b33-5650-420c-b9dc-f49310c201ee)

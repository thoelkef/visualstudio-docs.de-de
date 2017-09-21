---
title: "Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen mithilfe von Vererbung einer einzelnen Tabelle (O/R-Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 63bc6328-e0df-4655-9ce3-5ff74dbf69a4
caps.latest.revision: 4
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen mithilfe von Vererbung einer einzelnen Tabelle (O/R-Designer)
Der [Object Relational Designer \(O\/R\-Designer\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md) unterstützt Vererbung einer einzelnen Tabelle, wie sie typischerweise in relationalen Systemen implementiert ist.Diese exemplarische Vorgehensweise baut auf den in [Vorgehensweise: Konfigurieren von Vererbung mit dem O\/R\-Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) dargestellten allgemeinen Schritten auf und stellt reale Daten zur Veranschaulichung der Verwendung von Vererbung in [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] bereit.  
  
 Im Verlauf dieser exemplarischen Vorgehensweise führen Sie folgende Aufgaben aus:  
  
-   Erstellen einer Datenbanktabelle und Hinzufügen von Daten.  
  
-   Erstellen einer Windows Forms\-Anwendung.  
  
-   Hinzufügen einer [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]\-Datei zu einem Projekt.  
  
-   Erstellen neuer Entitätsklassen.  
  
-   Konfigurieren der Entitätsklassen zur Verwendung von Vererbung.  
  
-   Abfragen der geerbten Klasse.  
  
-   Anzeigen der Daten in einem Windows Form.  
  
## Erstellen einer Tabelle, von der geerbt werden soll  
 Um die Funktionsweise der Vererbung kennen zu lernen, erstellen Sie eine kleine Person\-Tabelle, verwenden sie als Basisklasse und erstellen anschließend ein Employee\-Objekt, das von ihr erbt.  
  
#### So erstellen Sie eine Basistabelle zur Veranschaulichung der Vererbung  
  
1.  Klicken Sie in **Server\-Explorer**\/**Datenbank\-Explorer** mit der rechten Maustaste auf den Knoten **Tabellen**, und klicken Sie auf **Neue Tabelle hinzufügen**.  
  
    > [!NOTE]
    >  Sie können die Northwind\-Datenbank oder eine andere Datenbank verwenden, der Sie eine Tabelle hinzufügen können.  
  
2.  Fügen Sie der Tabelle im Tabellen\-Designer die folgenden Spalten hinzu:  
  
    |Spaltenname|Datentyp|NULL zulassen|  
    |-----------------|--------------|-------------------|  
    |ID|int|False|  
    |Typ|int|True|  
    |FirstName|nvarchar\(200\)|False|  
    |LastName|nvarchar\(200\)|False|  
    |Manager|int|True|  
  
3.  Legen Sie die ID\-Spalte als Primärschlüssel fest.  
  
4.  Speichern Sie die Tabelle unter dem Namen "Person".  
  
## Hinzufügen von Daten zur Tabelle  
 Um sicherstellen zu können, dass die Vererbung ordnungsgemäß konfiguriert ist, muss die Tabelle Daten für jede Klasse in der Vererbung einer einzelnen Tabelle enthalten.  
  
#### So fügen Sie der Tabelle Daten hinzu  
  
1.  Öffnen Sie die Tabelle in der Datenansicht.\(Klicken Sie in **Server\-Explorer**\/**Datenbank\-Explorer** mit der rechten Maustaste auf die Tabelle **Person**, und klicken Sie auf **Tabellendaten anzeigen**.\)  
  
2.  Kopieren Sie die folgenden Daten in die Tabelle.\(Sie können sie kopieren und dann in die Tabelle einfügen, indem Sie im [Results Pane](http://msdn.microsoft.com/de-de/3c712f20-7c9f-4021-b1ac-fdc6f534c95a) die ganze Zeile markieren.\)  
  
    ||||||  
    |-|-|-|-|-|  
    |ID|Typ|FirstName|LastName|Manager|  
    |1|1|Anne|Wallace|NULL|  
    |2|1|Carlos|Grilo|NULL|  
    |3|1|Yael|Peled|NULL|  
    |4|2|Gatis|Ozolins|1|  
    |5|2|Andreas|Hauser|1|  
    |6|2|Tiffany|Phuvasate|1|  
    |7|2|Alexey|Orekhov|2|  
    |8|2|Michał|Poliszkiewicz|2|  
    |9|2|Tai|Yee|2|  
    |10|2|Fabricio|Noriega|3|  
    |11|2|Mindy|Martin|3|  
    |12|2|Ken|Kwok|3|  
  
## Erstellen eines neues Projekts  
 Nachdem Sie die Tabelle erstellt haben, erstellen Sie ein neues Projekt zur Darstellung der Konfiguration von Vererbung.  
  
#### So erstellen Sie die neue Windows\-Anwendung  
  
1.  Erstellen Sie im Menü **Datei** ein neues Projekt.  
  
2.  Nennen Sie das Projekt InheritanceWalkthrough.  
  
    > [!NOTE]
    >  Der [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] wird von Visual Basic\- und C\#\-Projekten unterstützt.Erstellen Sie das neue Projekt in einer der beiden Sprachen.  
  
3.  Klicken Sie auf die Vorlage **Windows Forms\-Anwendung** und anschließend auf **OK**.Weitere Informationen finden Sie unter [Clientanwendungen](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
4.  Das InheritanceWalkthrough\-Projekt wird erstellt und dem **Projektmappen\-Explorer** hinzugefügt.  
  
## Hinzufügen einer LINQ to SQL\-Klassendatei zum Projekt  
  
#### So fügen Sie dem Projekt eine LINQ to SQL\-Datei hinzu  
  
1.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.  
  
2.  Klicken Sie auf die Vorlage **LINQ to SQL\-Klassen** und dann auf **Hinzufügen**.  
  
     Dem Projekt wird die DBML\-Datei hinzugefügt, und der [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] wird geöffnet.  
  
## Erstellen der Vererbung mithilfe des O\/R\-Designers  
 Konfigurieren Sie die Vererbung, indem Sie aus der **Toolbox** ein Objekt aus dem Bereich **Vererbung** auf die Entwurfsoberfläche ziehen.  
  
#### So erstellen Sie die Vererbung  
  
1.  Navigieren Sie in **Server\-Explorer**\/**Datenbank\-Explorer** zu der zuvor von Ihnen erstellten Tabelle **Person**.  
  
2.  Ziehen Sie die Tabelle **Person** auf die [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]\-Entwurfsoberfläche.  
  
3.  Ziehen Sie eine zweite Tabelle **Person** auf den [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], und ändern Sie ihren Namen in "Employee".  
  
4.  Löschen Sie die **Manager**\-Eigenschaft aus dem Objekt **Person**.  
  
5.  Löschen Sie die Eigenschaften **Type**, **ID**, **FirstName** und **LastName** aus dem Objekt **Employee**.\(Mit anderen Worten: Entfernen Sie alle Eigenschaften außer **Manager**.\)  
  
6.  Erstellen Sie von der Registerkarte **O\/R\-Designer** der **Toolbox** eine **Vererbung** zwischen dem **Person**\-Objekt und dem **Employee**\-Objekt.Klicken Sie dazu in der **Toolbox** auf das Element **Vererbung**, und lassen Sie die Maustaste los.Klicken Sie anschließend im [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] zuerst auf das **Employee**\-Objekt und dann auf das **Person**\-Objekt.Der Pfeil der Vererbungslinie zeigt auf das **Person**\-Objekt.  
  
7.  Klicken Sie auf die Linie der **Vererbung** auf der Entwurfsoberfläche.  
  
8.  Legen Sie die Eigenschaft **Unterscheidungseigenschaft** auf **Type** fest.  
  
9. Legen Sie die Eigenschaft **Diskrimatorwert der abgeleiteten Klasse** auf **2** fest.  
  
10. Legen Sie die Eigenschaft **Basisklassen\-Diskrimatorwert** auf **1** fest.  
  
11. Legen Sie die **Vererbungsstandard**\-Eigenschaft auf **Person** fest.  
  
12. Erstellen Sie das Projekt.  
  
## Abfragen der geerbten Klasse und Anzeigen der Daten im Formular  
 Im Folgenden fügen Sie dem Formular Code zur Abfrage einer bestimmten Klasse im Objektmodell hinzu.  
  
#### So erstellen Sie eine LINQ\-Abfrage und zeigen die Ergebnisse im Formular an  
  
1.  Ziehen Sie eine **ListBox** auf Form1.  
  
2.  Doppelklicken Sie auf das Formular, um einen `Form1_Load`\-Ereignishandler zu erstellen.  
  
3.  Fügen Sie dem `Form1_Load`\-Ereignishandler den folgenden Code hinzu:  
  
    ```vb#  
    Dim dc As New DataClasses1DataContext  
    Dim results = From emp In dc.Persons _  
        Where TypeOf emp Is Employee _  
        Select emp  
  
    For Each Emp As Employee In results  
        ListBox1.Items.Add(Emp.LastName)  
    Next  
    ```  
  
    ```c#  
    NorthwindDataContext dc = new DataClasses1DataContext();  
    var results = from emp in dc.Persons  
                  where emp is Employee  
                  select emp;  
  
    foreach(Employee Emp in results)  
    {  
        listBox1.Items.Add(Emp.LastName)  
    }  
    ```  
  
## Testen der Anwendung  
 Führen Sie die Anwendung aus, und überprüfen Sie, ob alle im Listenfeld angezeigten Datensätze Mitarbeiter sind \(Datensätze, die den Wert 2 in der Spalte "Type" haben\).  
  
#### So testen Sie die Anwendung  
  
1.  Drücken Sie F5.  
  
2.  Stellen Sie sicher, dass nur Datensätze angezeigt werden, die den Wert 2 in ihrer Type\-Spalte haben.  
  
3.  Schließen Sie das Formular.\(Klicken Sie im Menü **Debuggen** auf **Debuggen beenden**.\)  
  
## Siehe auch  
 [Übersicht über den O\/R\-Designer](../Topic/LINQ%20to%20SQL%20Tools%20in%20Visual%20Studio1.md)   
 [Vorgehensweise: Hinzufügen von LINQ to SQL\-Klassen zu einem Projekt \(O\/R\-Designer\)](../Topic/How%20to:%20Add%20LINQ%20to%20SQL%20Classes%20to%20a%20Project%20\(O-R%20Designer\).md)   
 [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL\-Klassen \(O\/R\-Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [Vorgehensweise: Zuweisen von gespeicherten Prozeduren zur Durchführung von Update\-, Einfüge\- und Löschvorgängen \(O\/R\-Designer\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Vorgehensweise: Generieren des Objektmodells in Visual Basic oder C\#](../Topic/How%20to:%20Generate%20the%20Object%20Model%20in%20Visual%20Basic%20or%20C%23.md)
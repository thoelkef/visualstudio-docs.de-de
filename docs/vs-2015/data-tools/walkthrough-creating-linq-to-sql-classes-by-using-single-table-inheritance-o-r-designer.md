---
title: 'Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen mithilfe der Vererbung einer einzelnen Tabelle (O / R-Designer) | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 63bc6328-e0df-4655-9ce3-5ff74dbf69a4
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a7dfd293f5b2219eab6c3a2896c800a1337f2c8c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60111973"
---
# <a name="walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-or-designer"></a>Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen mithilfe der Vererbung einer einzelnen Tabelle (O/R-Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) unterstützt Vererbung einer einzelnen Tabelle aus, wie sie in der Regel in relationalen Systemen implementiert ist. Diese exemplarische Vorgehensweise baut auf den allgemeinen Schritten der [Vorgehensweise: Konfigurieren der Vererbung mit dem O/R-Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) Thema und stellt realen Daten zur Veranschaulichung der Verwendung von Vererbung in der [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
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
  
1. In **Server-Explorer**/**Datenbank-Explorer**, mit der rechten Maustaste die **Tabellen** Knoten, und klicken Sie auf **neue Tabelle hinzufügen**.  
  
    > [!NOTE]
    >  Sie können die Northwind-Datenbank oder eine andere Datenbank verwenden, der Sie eine Tabelle hinzufügen können.  
  
2. Fügen Sie der Tabelle im Tabellen-Designer die folgenden Spalten hinzu:  
  
    |Spaltenname|Datentyp|NULL zulassen|  
    |-----------------|---------------|-----------------|  
    |**ID**|**int**|**False**|  
    |**Type**|**int**|**True**|  
    |**FirstName**|**nvarchar(200)**|**False**|  
    |**LastName**|**nvarchar(200)**|**False**|  
    |**Manager**|**int**|**True**|  
  
3. Legen Sie die ID-Spalte als Primärschlüssel fest.  
  
4. Speichern Sie die Tabelle unter dem Namen **Person**.  
  
## <a name="add-data-to-the-table"></a>Hinzufügen von Daten zur Tabelle  
 Um sicherstellen zu können, dass die Vererbung ordnungsgemäß konfiguriert ist, muss die Tabelle Daten für jede Klasse in der Vererbung einer einzelnen Tabelle enthalten.  
  
#### <a name="to-add-data-to-the-table"></a>So fügen Sie der Tabelle Daten hinzu  
  
1. Öffnen Sie die Tabelle in der Datenansicht. (Mit der rechten Maustaste die **Person** -Tabelle **Server-Explorer**/**Datenbank-Explorer** , und klicken Sie auf **Tabellendaten anzeigen**.)  
  
2. Kopieren Sie die folgenden Daten in die Tabelle. (Sie können kopieren und fügen Sie ihn in die Tabelle durch die gesamte Zeile in den Bereich "Ergebnisse" auswählen.)  
  
    ||||||  
    |-|-|-|-|-|  
    |**ID**|**Type**|**FirstName**|**LastName**|**Manager**|  
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
  
1. Von der **Datei** Menü ein neues Projekt erstellen.  
  
2. Nennen Sie das Projekt **InheritanceWalkthrough**.  
  
    > [!NOTE]
    >  Der [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] wird von Visual Basic- und C#-Projekten unterstützt. Erstellen Sie das neue Projekt in einer der beiden Sprachen.  
  
3. Klicken Sie auf die **Windows Forms-Anwendung** -Vorlage, und klicken Sie dann auf **OK**. Weitere Informationen finden Sie unter [Clientanwendungen](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
4. Das InheritanceWalkthrough-Projekt wird erstellt und hinzugefügt **Projektmappen-Explorer**.  
  
## <a name="add-a-linq-to-sql-classes-file-to-the-project"></a>Hinzufügen einer LINQ to SQL-Klassendatei zum Projekt  
  
#### <a name="to-add-a-linq-to-sql-file-to-the-project"></a>So fügen Sie dem Projekt eine LINQ to SQL-Datei hinzu  
  
1. Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.  
  
2. Klicken Sie auf die Vorlage **LINQ to SQL-Klassen** und dann auf **Hinzufügen**.  
  
     Dem Projekt wird die DBML-Datei hinzugefügt, und der [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] wird geöffnet.  
  
## <a name="create-the-inheritance-by-using-the-or-designer"></a>Erstellen der Vererbung mithilfe des O/R-Designers  
 Konfigurieren Sie die Vererbung, indem Sie aus der **Toolbox** ein Objekt aus dem Bereich **Vererbung** auf die Entwurfsoberfläche ziehen.  
  
#### <a name="to-create-the-inheritance"></a>So erstellen Sie die Vererbung  
  
1. In **Server-Explorer**/**Datenbank-Explorer**, navigieren Sie zu der **Person** Tabelle, die Sie zuvor erstellt haben.  
  
2. Ziehen Sie die **Person** die Tabelle auf die [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] Entwurfsoberfläche.  
  
3. Ziehen Sie eine zweite **Person** die Tabelle auf die [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] und ändern Sie den Namen **Mitarbeiter**.  
  
4. Löschen Sie die **Manager**-Eigenschaft aus dem Objekt **Person**.  
  
5. Löschen Sie die Eigenschaften **Type**, **ID**, **FirstName** und **LastName** aus dem Objekt **Employee**. (Mit anderen Worten: Entfernen Sie alle Eigenschaften außer **Manager**.)  
  
6. Erstellen Sie von der Registerkarte **Objektrelationaler Designer** der **Toolbox** eine **Vererbung** zwischen dem **Person**-Objekt und dem **Employee**-Objekt. Klicken Sie dazu in der **Toolbox** auf das Element **Vererbung**, und lassen Sie die Maustaste los. Klicken Sie anschließend die **Mitarbeiter** Objekt und klicken Sie dann die **Person** -Objekt in der [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Der Pfeil der Vererbungslinie zeigt auf die **Person** Objekt.  
  
7. Klicken Sie auf die Linie der **Vererbung** auf der Entwurfsoberfläche.  
  
8. Legen Sie die Eigenschaft **Diskriminatoreigenschaft** auf **Type** fest.  
  
9. Legen Sie die Eigenschaft **Diskrimatorwert der abgeleiteten Klasse** auf **2** fest.  
  
10. Legen Sie die Eigenschaft **Basisklassen-Diskrimatorwert** auf **1** fest.  
  
11. Legen Sie die **Vererbungsstandard**-Eigenschaft auf **Person** fest.  
  
12. Erstellen Sie das Projekt.  
  
## <a name="query-the-inherited-class-and-display-the-data-on-the-form"></a>Abfragen der geerbten Klasse und Anzeigen der Daten im Formular  
 Im Folgenden fügen Sie dem Formular Code zur Abfrage einer bestimmten Klasse im Objektmodell hinzu.  
  
#### <a name="to-create-a-linq-query-and-display-the-results-on-the-form"></a>So erstellen Sie eine LINQ-Abfrage und zeigen die Ergebnisse im Formular an  
  
1. Ziehen Sie eine **ListBox** auf Form1.  
  
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
  
3. Schließen Sie das Formular. (Klicken Sie im Menü **Debuggen** auf **Debuggen beenden**.)  
  
## <a name="see-also"></a>Siehe auch  
 [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Vorgehensweise: Hinzufügen von LINQ to SQL-Klassen zu einem Projekt (O / R-Designer)](http://msdn.microsoft.com/library/7bb184ab-ec54-4cda-b706-604b2b4a3ed6)   
 [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen (O / R-Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [Vorgehensweise: Zuweisen von gespeicherten Prozeduren zum Ausführen von Updates, einfügungen und löschen (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Vorgehensweise: (Vorgehensweise: Generieren des Objektmodells in Visual Basic oder C#)](http://msdn.microsoft.com/library/a0c73b33-5650-420c-b9dc-f49310c201ee)

---
title: Erstellen von Windows Forms zum Suchen von Daten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- Windows Forms, searching data
- Windows Forms, displaying data
- parameters, displaying filtered data
- data [Visual Studio], parameterizing queries
- data [Visual Studio], searching
ms.assetid: 65ca79a9-7458-466c-af55-978cd24c549e
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e42c86cf94115d317eb20df66f4cef005e05eba9
ms.sourcegitcommit: c9a01c599ce19a5845605b3b28c0229fd0abb93f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2018
ms.locfileid: "52281796"
---
# <a name="create-a-windows-form-to-search-data"></a>Erstellen eines Windows Forms zum Suchen von Daten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Es kommt häufig vor, dass ausgewählte Daten auf einem Formular angezeigt werden, Angenommen, Sie möchten die Bestellungen für einen bestimmten Kunden oder die Details für eine bestimmte Bestellung anzeigen. In diesem Szenario gibt der Benutzer zunächst Informationen in ein Formular ein. Anschließend wird eine Abfrage mit der Eingabe des Benutzers als Parameter ausgeführt, d. h. die Daten werden auf der Grundlage einer parametrisierten Abfrage ausgewählt. Die Abfrage gibt nur die Daten zurück, die den vom Benutzer eingegebenen Kriterien entsprechen. Diese exemplarische Vorgehensweise veranschaulicht das Erstellen einer Abfrage, die Kunden in einer bestimmten Stadt zurückgibt, sowie das Anpassen der Benutzeroberfläche, damit Benutzer eine Stadt eingeben und zum Ausführen der Abfrage auf eine Schaltfläche klicken können.  
  
 Durch die Verwendung parametrisierter Abfragen wird die Effizienz der Anwendung erhöht, weil die Datenbank die Arbeit ausführt, für die sie optimiert ist, nämlich die schnelle Filterung von Datensätzen. Im Gegensatz dazu, wenn Sie eine ganze Datenbanktabelle anfordern, über das Netzwerk übertragen, und klicken Sie dann mit der Anwendungslogik, die gewünschten Datensätze suchen, kann Ihre Anwendung langsam und ineffizient werden.  
  
 Sie können alle TableAdapter (und Steuerelemente Parameterwerte annehmen und Ausführen der Abfrage), mit parametrisierte Abfragen hinzufügen der **Suchkriterien-Generator** Dialogfeld. Öffnen Sie das Dialogfeld durch Auswählen der **Abfrage hinzufügen** Befehl die **Daten** Menü (oder in einem TableAdapter-Smarttag).  
  
 In dieser exemplarischen Vorgehensweise werden u. a. folgende Aufgaben veranschaulicht:  
  
-   Erstellen ein neues Windows Forms-Anwendungsprojekt.  
  
-   Erstellen und konfigurieren die Datenquelle in Ihrer Anwendung mit der **Datenquellenkonfiguration** Assistenten.  
  
-   Festlegen des Ablagetyps der Elemente in der **Datenquellen** Fenster.  
  
-   Erstellen von Steuerelementen, die Daten anzeigen, indem das Ziehen von Elementen aus der **Datenquellen** auf das Formular.  
  
-   Hinzufügen von Steuerelementen zum Anzeigen der Daten auf dem Formular.  
  
-   Abschließen der **Suchkriterien-Generator** Dialogfeld.  
  
-   Eingeben von Parametern in das Formular und Ausführen der parametrisierten Abfrage.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Für die Durchführung dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:  
  
-   Zugriff auf die Beispieldatenbank Northwind.  
  
## <a name="create-the-windows-application"></a>Erstellen Sie die Windows-Anwendung  
 Der erste Schritt ist die Erstellung einer **Windows-Anwendung**. Zuweisen eines Namens für das Projekt an dieser Stelle optional ist, aber Sie erhalten sie hier einen Namen ein, da Sie es später noch Mal speichern.  
  
#### <a name="to-create-the-new-windows-application-project"></a>So erstellen Sie das neue Windows-Anwendungsprojekt  
  
1.  Von der **Datei** Menü ein neues Projekt erstellen.  
  
2.  Benennen Sie das Projekt mit `WindowsSearchForm`.  
  
3.  Wählen Sie **Windows-Anwendung** , und klicken Sie auf **OK**.  
  
     Die **WindowsSearchForm** Projekt wird erstellt und hinzugefügt **Projektmappen-Explorer**.  
  
## <a name="create-the-data-source"></a>Erstellen der Datenquelle  
 Dieser Schritt wird eine Datenquelle erstellt, aus einer Datenbank mithilfe der **Datenquellenkonfiguration** Assistenten. Sie benötigen Zugriff auf die Beispieldatenbank Northwind, um die Verbindung herstellen zu können. Informationen zum Einrichten der Beispieldatenbank Northwind finden Sie unter [Installieren von SQL Server-Beispieldatenbanken](../data-tools/install-sql-server-sample-databases.md).  
  
#### <a name="to-create-the-data-source"></a>So erstellen Sie die Datenquelle  
  
1.  Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.  
  
2.  In der **Datenquellen** wählen Sie im Fenster **neue Datenquelle hinzufügen** zum Starten der **Datenquellenkonfiguration** Assistenten.  
  
3.  Wählen Sie auf der Seite **Datenquellentyp auswählen** die Option **Datenbank** aus, und klicken Sie auf **Weiter**.  
  
4.  Auf der **wählen Sie Ihre Datenverbindung** Seite führen Sie einen der folgenden:  
  
    -   Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank „Northwind“ verfügbar ist, wählen Sie diese aus.  
  
    -   Wählen Sie **neue Verbindung** zum Starten der **Verbindung hinzufügen/ändern** Dialogfeld.  
  
5.  Wenn Ihre Datenbank ein Kennwort erfordert, wählen Sie die Option Einbeziehung vertraulicher Daten, und klicken Sie dann auf **Weiter**.  
  
6.  Auf der **Verbindungszeichenfolge in der Programmkonfigurationsdatei speichern** auf **Weiter**.  
  
7.  Auf der **Datenbankobjekte auswählen** Seite, erweitern Sie die **Tabellen** Knoten.  
  
8.  Wählen Sie die **Kunden** Tabelle, und klicken Sie dann auf **Fertig stellen**.  
  
     Die **NorthwindDataSet** wird Ihrem Projekt hinzugefügt und die **Kunden** Tabelle angezeigt wird, der **Datenquellen** Fenster.  
  
## <a name="create-the-form"></a>Erstellen Sie das Formular  
 Sie können die datengebundenen Steuerelemente erstellen, durch Ziehen von Elementen aus der **Datenquellen** auf das Formular.  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>So erstellen Sie datengebundene Steuerelemente auf dem Formular  
  
1.  Erweitern Sie die **Kunden** Knoten in der **Datenquellen** Fenster.  
  
2.  Ziehen Sie die **Kunden** Knoten aus der **Datenquellen** auf das Formular.  
  
     Auf dem Formular werden <xref:System.Windows.Forms.DataGridView> und ein ToolStrip-Element (<xref:System.Windows.Forms.BindingNavigator>) angezeigt, mit denen Sie durch die Datensätze auf dem Formular navigieren können. Ein [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, und <xref:System.Windows.Forms.BindingNavigator> werden in der Komponentenleiste angezeigt.  
  
## <a name="addparameterization-search-functionality-to-the-query"></a>Addparameterization (Suchfunktionen) zur Abfrage  
 Sie können eine WHERE-Klausel hinzufügen, um die ursprüngliche Abfrage mithilfe der **Suchkriterien-Generator** Dialogfeld.  
  
#### <a name="to-create-a-parameterized-query-and-controls-to-enter-the-parameters"></a>So erstellen Sie eine parametrisierte Abfrage sowie Steuerelemente zur Eingabe der Parameter  
  
1.  Wählen Sie die <xref:System.Windows.Forms.DataGridView> steuern, und wählen Sie dann **Abfrage hinzufügen** auf die **Daten** Menü.  
  
2.  Typ `FillByCity` in die **Neuer Abfragename** Bereich auf die **Suchkriterien-Generator** Dialogfeld.  
  
3.  Hinzufügen `WHERE City = @City` für Abfragen in der **Abfragetext** Bereich.  
  
     Die Abfrage müsste ungefähr wie folgt aussehen:  
  
     `SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax`  
  
     `FROM Customers`  
  
     `WHERE City = @City`  
  
    > [!NOTE]
    >  Zugriff und OLE DB-Datenquellen verwenden das Fragezeichen ("?") zur Angabe von Parametern, sodass die WHERE-Klausel wie folgt aussehen würde: `WHERE City = ?`.  
  
4.  Klicken Sie auf **OK** schließen die **Suchkriterien-Generator** Dialogfeld.  
  
     Ein **FillByCityToolStrip** zum Formular hinzugefügt wird.  
  
## <a name="testing-the-application"></a>Testen der Anwendung  
 Beim Ausführen der Anwendung wird das Formular geöffnet, das zur Übernahme der Parametereingabe bereit ist.  
  
#### <a name="to-test-the-application"></a>So testen Sie die Anwendung  
  
1.  Drücken Sie F5, um die Anwendung auszuführen.  
  
2.  Typ **London** in die **City** Textfeld, und klicken Sie dann auf **FillByCity**.  
  
     Das Datenraster wird mit den Kunden gefüllt, die die Kriterien erfüllen. In diesem Beispiel zeigt das Datenraster nur Kunden, deren Wert der **London** in ihre **City** Spalte.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Je nach den Anforderungen der Anwendung können nach dem Erstellen eines parametrisierten Formulars weitere Schritte sinnvoll sein. Sie können an dieser exemplarischen Vorgehensweise beispielsweise folgende Verbesserungen vornehmen:  
  
-   Hinzufügen von Steuerelementen, die verknüpfte Daten anzeigen. Weitere Informationen finden Sie unter [Vorgehensweise: Anzeigen von verknüpften Daten in einer Windows Forms-Anwendung](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md).  
  
-   Hinzufügen oder Entfernen von Datenbankobjekten aus dem Dataset durch Bearbeiten. Weitere Informationen finden Sie unter [Erstellen und Konfigurieren von Datasets in Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)


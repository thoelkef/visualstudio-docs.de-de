---
title: Erstellen eines Windows Forms-Benutzersteuerelements, die Bindung an Nachschlagedaten unterstützt | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data binding, user controls
- LookupBindingPropertiesAttribute class, examples
- user controls [Visual Basic], creating
ms.assetid: c48b4d75-ccfc-4950-8b14-ff8adbfe4208
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7c0514d29d3c8e87b277115f8e1307dc0a5fb0c4
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2019
ms.locfileid: "59662711"
---
# <a name="create-a-windows-forms-user-control-that-supports-lookup-data-binding"></a>Erstellen eines Windows Forms-Benutzersteuerelements, das Nachschlagedatenbindung unterstützt
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zum Anzeigen von Daten in Windows Forms können Sie die in der **Toolbox** vorhandenen Steuerelemente verwenden oder, falls die gewünschte Funktionalität in den Standardsteuerelementen nicht verfügbar ist, benutzerdefinierte Steuerelemente erstellen. Diese exemplarische Vorgehensweise erläutert, wie Sie ein Steuerelement erstellen, das <xref:System.ComponentModel.LookupBindingPropertiesAttribute> implementiert. Steuerelemente, die <xref:System.ComponentModel.LookupBindingPropertiesAttribute> implementieren, können drei Eigenschaften enthalten, die an Daten gebunden werden können. Solche Steuerelemente ähneln einem <xref:System.Windows.Forms.ComboBox>-Steuerelement.  
  
 Weitere Informationen über das Erstellen von Steuerelementen, finden Sie unter [Entwickeln von Windows Forms-Steuerelementen zur Entwurfszeit](http://msdn.microsoft.com/library/e5a8e088-7ec8-4fd9-bcb3-9078fd134829).  
  
 Beim Erstellen von Steuerelementen, die in Datenbindungsszenarios verwendet werden sollen, müssen Sie eines der folgenden Datenbindungsattribute implementieren:  
  
|Die Datenbindung Attributverwendung|  
|-----------------------------------|  
|Implementieren Sie <xref:System.ComponentModel.DefaultBindingPropertyAttribute> für einfache Steuerelemente, die eine einzige Spalte (oder Eigenschaft) von Daten anzeigen, wie das <xref:System.Windows.Forms.TextBox>-Steuerelement. Weitere Informationen finden Sie unter [Erstellen eines Windows Forms-Benutzersteuerelements, die einfache Datenbindung unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|  
|Implementieren Sie <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> für Steuerelemente, die Listen (oder Tabellen) von Daten anzeigen, wie das <xref:System.Windows.Forms.DataGridView>-Steuerelement. Weitere Informationen finden Sie unter [Erstellen eines Windows Forms-Benutzersteuerelements, das komplexe Datenbindung unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|  
|Implementieren Sie <xref:System.ComponentModel.LookupBindingPropertiesAttribute> für Steuerelemente, die Listen (oder Tabellen) von Daten anzeigen, aber auch eine einzelne Spalte oder Eigenschaft darstellen müssen, wie das <xref:System.Windows.Forms.ComboBox>-Steuerelement. (Dieser Prozess wird in dieser exemplarischen Vorgehensweise beschrieben.)|  
  
 In dieser exemplarischen Vorgehensweise wird ein Nachschlagesteuerelement erstellt, das an Daten aus zwei Tabellen gebunden ist. In diesem Beispiel werden die Tabellen `Customers` und `Orders` aus der Beispieldatenbank Northwind verwendet. Das Nachschlagesteuerelement wird an das Feld `CustomerID` der Tabelle `Orders` gebunden. Das Steuerelement verwendet diesen Wert, um in der Tabelle `CompanyName` den entsprechenden Wert von `Customers` nachzuschlagen.  
  
 Bei dieser exemplarischen Vorgehensweise lernen Sie Folgendes:  
  
-   Erstellen Sie ein neues **Windows-Anwendung**.  
  
-   Ihrem Projekt ein neues **Benutzersteuerelement** hinzufügen.  
  
-   Entwerfen des Benutzersteuerelements im visuellen Designer.  
  
-   Implementieren des `LookupBindingProperty`-Attributs.  
  
-   Erstellen eines Datasets mit dem **Datenquellenkonfiguration** Assistenten.  
  
-   Die Spalte **CustomerID** in der Tabelle **Orders** im **Datenquellenfenster** festlegen, um das neue Steuerelement zu verwenden.  
  
-   Erstellen eines Formulars, um Daten in dem neuen Steuerelement anzuzeigen.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Für die Durchführung dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:  
  
-   Zugriff auf die Beispieldatenbank Northwind.  
  
## <a name="create-a-windows-application"></a>Erstellen Sie eine Windows-Anwendung  
 Der erste Schritt ist die Erstellung einer **Windows-Anwendung**.  
  
#### <a name="to-create-the-new-windows-project"></a>So erstellen Sie ein neues Windows-Projekt  
  
1.  In Visual Studio aus der **Datei** im Menü Erstellen Sie ein neues **Projekt**.  
  
2.  Nennen Sie das Projekt **LookupControlWalkthrough**.  
  
3.  Wählen Sie **Windows Forms-Anwendung**, und klicken Sie auf **OK**.  
  
     Das Projekt **LookupControlWalkthrough** wird erstellt und dem **Projektmappen-Explorer** hinzugefügt.  
  
## <a name="add-a-user-control-to-the-project"></a>Hinzufügen eines Benutzersteuerelements zum Projekt  
 In dieser exemplarischen Vorgehensweise wird aus einem **Benutzersteuerelement** ein Nachschlagesteuerelement erstellt. Fügen Sie dem Projekt **LookupControlWalkthrough** zunächst also ein **Benutzersteuerelement** hinzu.  
  
#### <a name="to-add-a-user-control-to-the-project"></a>So fügen Sie dem Projekt ein Benutzersteuerelement hinzu  
  
1.  Klicken Sie im Menü **Projekt** auf **Benutzersteuerelement hinzufügen**.  
  
2.  Typ `LookupBox` in die **Namen** Bereich, und klicken Sie dann auf **hinzufügen**.  
  
     Das **LookupBox**-Steuerelement wird dem **Projektmappen-Explorer** hinzugefügt und im Designer geöffnet.  
  
## <a name="design-the-lookupbox-control"></a>Entwerfen des LookupBox-Steuerelements  
  
#### <a name="to-design-the-lookupbox-control"></a>So entwerfen Sie das LookupBox-Steuerelement  
  
-   Ziehen Sie ein <xref:System.Windows.Forms.ComboBox> aus der **Toolbox** auf die Entwurfsoberfläche des Benutzersteuerelements.  
  
## <a name="add-the-required-data-binding-attribute"></a>Fügen Sie das erforderliche Attribut für die Datenbindung hinzu  
 Implementieren Sie für Nachschlagesteuerelemente, die Datenbindung unterstützen, das <xref:System.ComponentModel.LookupBindingPropertiesAttribute>.  
  
#### <a name="to-implement-the-lookupbindingproperties-attribute"></a>So implementieren Sie das LookupBindingProperties-Attribut  
  
1.  Wechseln Sie für das **LookupBox**-Steuerelement zur Codeansicht. (Wählen Sie im Menü **Ansicht** den Befehl **Code** aus.)  
  
2.  Ersetzen Sie den Code in `LookupBox` durch folgenden Code:  
  
     [!code-csharp[VbRaddataDisplaying#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/LookupBox.cs#5)]
     [!code-vb[VbRaddataDisplaying#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/LookupBox.vb#5)]  
  
3.  Wählen Sie im Menü **Erstellen** die Option **Projektmappe erstellen**aus.  
  
## <a name="create-a-data-source-from-your-database"></a>Erstellen Sie eine Datenquelle aus der Datenbank  
 In diesem Schritt wird mit dem **Assistenten zum Konfigurieren von Datenquellen** eine Datenquelle erstellt, die auf den Tabellen `Customers` und `Orders` der Beispieldatenbank Northwind basiert. Sie benötigen Zugriff auf die Beispieldatenbank Northwind, um die Verbindung herstellen zu können. Informationen zum Einrichten der Beispieldatenbank Northwind finden Sie unter [Installieren von SQL Server-Beispieldatenbanken](../data-tools/install-sql-server-sample-databases.md).  
  
#### <a name="to-create-the-data-source"></a>So erstellen Sie die Datenquelle  
  
1.  Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.  
  
2.  Klicken Sie im **Datenquellenfenster** auf **Neue Datenquelle hinzufügen**, um den **Assistenten zum Konfigurieren von Datenquellen** zu starten.  
  
3.  Wählen Sie auf der Seite **Datenquellentyp auswählen** die Option **Datenbank** aus, und klicken Sie auf **Weiter**.  
  
4.  Führen Sie auf der Seite **Wählen Sie Ihre Datenverbindung** einen der folgenden Schritte aus:  
  
    -   Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank „Northwind“ verfügbar ist, wählen Sie diese aus.  
  
    -   Klicken Sie auf **Neue Verbindung**, um das Dialogfeld **Add/Modify Connection** (Verbindung hinzufügen/ändern) zu öffnen.  
  
5.  Falls die Datenbank ein Kennwort erfordern sollte, aktivieren Sie die Option für die Einbeziehung vertraulicher Daten, und klicken Sie dann auf **Weiter**.  
  
6.  Klicken Sie auf der Seite **Save connection string to the Application Configuration file** (Verbindungszeichenfolge in der Programmkonfigurationsdatei speichern) auf **Weiter**.  
  
7.  Erweitern Sie auf der Seite **Datenbankobjekte auswählen** den Knoten **Tabellen**.  
  
8.  Wählen Sie die Tabellen `Customers` und `Orders` aus, und klicken Sie dann auf **Fertig stellen**.  
  
     Das **NorthwindDataSet** wird Ihrem Projekt hinzugefügt, und die Tabellen `Customers` und `Orders` werden im **Datenquellenfenster** angezeigt.  
  
## <a name="set-the-customerid-column-of-the-orders-table-to-use-the-lookupbox-control"></a>Legen Sie die CustomerID-Spalte der Tabelle Orders, verwenden Sie das LookupBox-Steuerelement  
 Im **Datenquellenfenster** können Sie vor dem Ziehen von Elementen auf das Formular festlegen, welches Steuerelement erstellt werden soll.  
  
#### <a name="to-set-the-customerid-column-to-bind-to-the-lookupbox-control"></a>So legen Sie die Bindung der Spalte "CustomerID" an das LookupBox-Steuerelement fest  
  
1.  Öffnen Sie **Form1** im Designer.  
  
2.  Erweitern Sie im **Datenquellenfenster** den Knoten **Customers**.  
  
3.  Erweitern Sie den Knoten **Orders** (denjenigen, der sich im Knoten **Customers** unterhalb der Spalte **Fax** befindet).  
  
4.  Klicken Sie im Knoten **Orders** auf den Dropdownpfeil, und wählen Sie in der Steuerelementliste die Option **Details** aus.  
  
5.  Klicken Sie in der Spalte **CustomerID** (im Knoten **Orders**) auf den Dropdownpfeil, und wählen Sie **Anpassen** aus.  
  
6.  Wählen Sie im Dialogfeld **Data UI Customization Options** (Optionen für die Anpassung der Datenbenutzeroberfläche) in der Liste **Zugeordnete Steuerelemente** den Eintrag **LookupBox** aus.  
  
7.  Klicken Sie auf **OK**.  
  
8.  Klicken Sie in der Spalte **CustomerID** auf den Dropdownpfeil, und wählen Sie **LookupBox** aus.  
  
## <a name="addcontrols-to-the-form"></a>Addcontrols zum Formular  
 Sie können die datengebundenen Steuerelemente erstellen, indem Sie Elemente aus dem **Datenquellenfenster** auf **Form1** ziehen.  
  
#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>So erstellen Sie datengebundene Steuerelemente auf dem Windows Form  
  
-   Ziehen Sie die **Bestellungen** Knoten aus der **Datenquellen** auf das Windows-Formular, und überprüfen Sie, ob die **LookupBox** Steuerelement wird verwendet, um die Anzeige der Daten in die `CustomerID` die Spalte.  
  
## <a name="bind-the-control-to-look-up-companyname-from-the-customers-table"></a>Binden des Steuerelements zum Nachschlagen von CompanyName in der Customers-Tabelle  
  
#### <a name="to-setup-the-lookup-bindings"></a>So richten Sie die Nachschlagebindungen ein  
  
-   Wählen Sie im **Kunden** Knoten in der **Datenquellen** angezeigt, und ziehen Sie es auf das Kombinationsfeld für den Sie im Dialogfeld die **CustomerIDLookupBox** auf **Form1** .  
  
     Damit wird die Datenbindung so eingerichtet, dass der Wert für `CompanyName` aus der Tabelle `Customers` angezeigt und gleichzeitig der Wert für `CustomerID` aus der Tabelle `Orders` beibehalten wird.  
  
## <a name="running-the-application"></a>Ausführen der Anwendung  
  
#### <a name="to-run-the-application"></a>So führen Sie die Anwendung aus  
  
-   Drücken Sie F5, um die Anwendung auszuführen.  
  
-   Navigieren Sie durch einige Datensätze, und prüfen Sie, ob im `LookupBox`-Steuerelement der Wert von `CompanyName` angezeigt wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)

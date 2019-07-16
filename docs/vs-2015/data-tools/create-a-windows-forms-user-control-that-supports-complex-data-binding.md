---
title: Erstellen eines Windows Forms-Benutzersteuerelements, das komplexe Datenbindung unterstützt | Microsoft-Dokumentation
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
- data binding, complex
- user controls [Visual Studio], complex data binding
ms.assetid: c8f29c2b-b49b-4618-88aa-33b6105880b5
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0c27ec5be48b37f95068a2be6c8605a97d122d21
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65705004"
---
# <a name="create-a-windows-forms-user-control-that-supports-complex-data-binding"></a>Erstellen eines Windows Forms-Benutzersteuerelements, das komplexe Datenbindung unterstützt
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zum Anzeigen von Daten in Formularen in Windows-Anwendungen können Sie die in der **Toolbox** vorhandenen Steuerelemente verwenden oder, falls die gewünschte Funktionalität in den Standardsteuerelementen nicht verfügbar ist, benutzerdefinierte Steuerelemente erstellen. Diese exemplarische Vorgehensweise erläutert, wie Sie ein Steuerelement erstellen, das <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> implementiert. Steuerelemente, die <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> implementieren, enthalten eine Eigenschaft `DataSource` und `DataMember`, die an Daten gebunden werden kann. Solche Steuerelemente sind vergleichbar mit <xref:System.Windows.Forms.DataGridView> oder <xref:System.Windows.Forms.ListBox>.  
  
 Weitere Informationen über das Erstellen von Steuerelementen, finden Sie unter [Entwickeln von Windows Forms-Steuerelementen zur Entwurfszeit](https://msdn.microsoft.com/library/e5a8e088-7ec8-4fd9-bcb3-9078fd134829).  
  
 Beim Erstellen von Steuerelementen, die in Datenbindungsszenarios verwendet werden sollen, müssen Sie eines der folgenden Datenbindungsattribute implementieren:  
  
|Die Datenbindung Attributverwendung|  
|-----------------------------------|  
|Implementieren Sie <xref:System.ComponentModel.DefaultBindingPropertyAttribute> für einfache Steuerelemente, die eine einzige Spalte (oder Eigenschaft) von Daten anzeigen, wie das <xref:System.Windows.Forms.TextBox>-Steuerelement. Weitere Informationen finden Sie unter [Erstellen eines Windows Forms-Benutzersteuerelements, die einfache Datenbindung unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|  
|Implementieren Sie <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> für Steuerelemente, die Listen (oder Tabellen) von Daten anzeigen, wie das <xref:System.Windows.Forms.DataGridView>-Steuerelement. (Dieser Prozess wird in dieser exemplarischen Vorgehensweise beschrieben.)|  
|Implementieren Sie die <xref:System.ComponentModel.LookupBindingPropertiesAttribute> auf Steuerelementen wie einem <xref:System.Windows.Forms.ComboBox>,das Listen (oder Tabellen) von Daten anzeigt, aber auch in einer einzelnen Spalte oder Eigenschaft vorhanden sein muss. Weitere Informationen finden Sie unter [Erstellen eines Windows Forms-Benutzersteuerelements, die Bindung an Nachschlagedaten unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|  
  
 In dieser exemplarischen Vorgehensweise wird ein Steuerelement erstellt, das Datenzeilen aus einer Tabelle darstellt. In diesem Beispiel wird die Tabelle `Customers` der Beispieldatenbank Northwind verwendet. Das komplexe Benutzersteuerelement stellt die Tabelle Customers in einer <xref:System.Windows.Forms.DataGridView> im benutzerdefinierten Steuerelement dar.  
  
 Bei dieser exemplarischen Vorgehensweise lernen Sie Folgendes:  
  
- Erstellen Sie ein neues **Windows-Anwendung**.  
  
- Ihrem Projekt ein neues **Benutzersteuerelement** hinzufügen.  
  
- Entwerfen des Benutzersteuerelements im visuellen Designer.  
  
- Implementieren des `ComplexBindingProperty`-Attributs.  
  
- Erstellen eines Datasets mit dem [Assistenten zur Datenquellenkonfiguration](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).  
  
- Legen Sie die **Kunden** -Tabelle in der [Fensters "Datenquellen"](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) auf das neue, komplexe Steuerelement verwendet.  
  
- Fügen Sie das neue Steuerelement durch Ziehen aus dem **Fensters "Datenquellen"** auf **Form1**.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Für die Durchführung dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:  
  
- Zugriff auf die Beispieldatenbank Northwind.
  
## <a name="create-a-windows-application"></a>Erstellen Sie eine Windows-Anwendung  
 Der erste Schritt ist die Erstellung einer **Windows-Anwendung**.  
  
#### <a name="to-create-the-new-windows-project"></a>So erstellen Sie ein neues Windows-Projekt  
  
1. In Visual Studio aus der **Datei** im Menü Erstellen Sie ein neues **Projekt**.  
  
2. Geben Sie dem Projekt den Namen **ComplexControlWalkthrough**.  
  
3. Wählen Sie **Windows-Anwendung**, und klicken Sie auf **OK**. Weitere Informationen finden Sie unter [Clientanwendungen](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     Das Projekt **ComplexControlWalkthrough** wird erstellt und dem **Projektmappen-Explorer** hinzugefügt.  
  
## <a name="add-a-user-control-to-the-project"></a>Hinzufügen eines Benutzersteuerelements zum Projekt  
 Da in dieser exemplarischen Vorgehensweise ein komplexes, datenbindbares Steuerelement aus erstellt eine **Benutzersteuerelement**, müssen Sie hinzufügen, eine **Benutzersteuerelement** Elements zum Projekt.  
  
#### <a name="to-add-a-user-control-to-the-project"></a>So fügen Sie dem Projekt ein Benutzersteuerelement hinzu  
  
1. Klicken Sie im Menü **Projekt** auf **Benutzersteuerelement hinzufügen**.  
  
2. Geben Sie **ComplexDataGridView** in den Bereich **Name** ein, und klicken Sie anschließend auf **Hinzufügen**.  
  
     Das **ComplexDataGridView**-Steuerelement wird dem **Projektmappen-Explorer** hinzugefügt und im Designer geöffnet.  
  
## <a name="design-the-complexdatagridview-control"></a>Entwerfen des ComplexDataGridView-Steuerelements  
 Dieser Schritt fügt dem Benutzersteuerelement eine <xref:System.Windows.Forms.DataGridView> hinzu.  
  
#### <a name="to-design-the-complexdatagridview-control"></a>So entwerfen Sie das ComplexDataGridView-Steuerelement  
  
- Ziehen Sie ein <xref:System.Windows.Forms.DataGridView> aus der **Toolbox** auf die Entwurfsoberfläche des Benutzersteuerelements.  
  
## <a name="add-the-required-data-binding-attribute"></a>Fügen Sie das erforderliche Attribut für die Datenbindung hinzu  
 Für komplexe Steuerelemente, die Datenbindung unterstützen, können Sie das <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> implementieren.  
  
#### <a name="to-implement-the-complexbindingproperties-attribute"></a>So implementieren Sie das ComplexBindingProperties-Attribut  
  
1. Wechseln Sie für das **ComplexDataGridView**-Steuerelement zur Codeansicht. (Wählen Sie im Menü **Ansicht** die Option **Code** aus.)  
  
2. Ersetzen Sie den Code in `ComplexDataGridView` durch folgenden Code:  
  
     [!code-csharp[VbRaddataDisplaying#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/ComplexDataGridView.cs#4)]
     [!code-vb[VbRaddataDisplaying#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/ComplexDataGridView.vb#4)]  
  
3. Wählen Sie im Menü **Erstellen** die Option **Projektmappe erstellen**aus.  
  
## <a name="creating-a-data-source-from-your-database"></a>Erstellen eine Datenquelle aus einer Datenbank  
 In diesem Schritt wird der **Assistent zum Konfigurieren von Datenquellen** verwendet, um eine Datenquelle anhand der `Customers`-Tabelle in der Beispieldatenbank Northwind zu erstellen. Sie benötigen Zugriff auf die Beispieldatenbank Northwind, um die Verbindung herstellen zu können. Informationen zum Einrichten der Beispieldatenbank Northwind finden Sie unter [Installieren von SQL Server-Beispieldatenbanken](../data-tools/install-sql-server-sample-databases.md).  
  
#### <a name="to-create-the-data-source"></a>So erstellen Sie die Datenquelle  
  
1. Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.  
  
2. Klicken Sie im **Datenquellenfenster** auf **Neue Datenquelle hinzufügen**, um den **Assistenten zum Konfigurieren von Datenquellen** zu starten.  
  
3. Wählen Sie auf der Seite **Datenquellentyp auswählen** die Option **Datenbank** aus, und klicken Sie auf **Weiter**.  
  
4. Führen Sie auf der Seite **Wählen Sie Ihre Datenverbindung** einen der folgenden Schritte aus:  
  
    - Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank „Northwind“ verfügbar ist, wählen Sie diese aus.  
  
    - Klicken Sie auf **Neue Verbindung**, um das Dialogfeld **Add/Modify Connection** (Verbindung hinzufügen/ändern) zu öffnen.  
  
5. Falls die Datenbank ein Kennwort erfordern sollte, aktivieren Sie die Option für die Einbeziehung vertraulicher Daten, und klicken Sie dann auf **Weiter**.  
  
6. Klicken Sie auf der Seite **Save connection string to the Application Configuration file** (Verbindungszeichenfolge in der Programmkonfigurationsdatei speichern) auf **Weiter**.  
  
7. Erweitern Sie auf der Seite **Datenbankobjekte auswählen** den Knoten **Tabellen**.  
  
8. Wählen Sie die `Customers`-Tabelle aus, und klicken Sie anschließend auf **Fertig stellen**.  
  
     Das **NorthwindDataSet** wird dem Projekt hinzugefügt, und die Tabelle `Customers` wird im **Datenquellenfenster** angezeigt.  
  
## <a name="set-the-customers-table-to-use-the-complexdatagridview-control"></a>Festlegen der Tabelle Customers das Steuerelement ComplexDataGridView verwendet  
 Im **Datenquellenfenster** können Sie vor dem Ziehen von Elementen auf das Formular festlegen, welches Steuerelement erstellt werden soll.  
  
#### <a name="to-set-the-customers-table-to-bind-to-the-complexdatagridview-control"></a>So legen Sie die Bindung der Spalte Customers an das ComplexDataGridView-Steuerelement fest  
  
1. Öffnen Sie **Form1** im Designer.  
  
2. Erweitern Sie im **Datenquellenfenster** den Knoten **Customers**.  
  
3. Klicken Sie auf den Dropdownpfeil für den Knoten **Customers**, und wählen Sie **Anpassen**.  
  
4. Wählen Sie im Dialogfeld **Optionen für die Anpassung der Datenbenutzeroberfläche** in der Liste **Zugeordnete Steuerelemente** den Eintrag **ComplexDataGridView** aus.  
  
5. Klicken Sie auf den Dropdownpfeil für die `Customers`-Tabelle, und wählen Sie **ComplexDataGridView** aus der Steuerungsliste aus.  
  
## <a name="addcontrols-to-the-form"></a>Addcontrols zum Formular  
 Sie können die datengebundenen Steuerelemente erstellen, indem Sie Elemente aus dem Fenster **Datenquellen** auf das Formular ziehen.  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>So erstellen Sie datengebundene Steuerelemente auf dem Formular  
  
- Ziehen Sie den Hauptknoten **Kunden** Knoten aus der **Datenquellen** auf das Formular. Überprüfen Sie, ob die **ComplexDataGridView** Steuerelement wird verwendet, um die Daten der Tabelle angezeigt.  
  
## <a name="running-the-application"></a>Ausführen der Anwendung  
  
#### <a name="to-run-the-application"></a>So führen Sie die Anwendung aus  
  
- Drücken Sie F5, um die Anwendung auszuführen.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Entsprechend den Anforderungen an Ihre Anwendung können Sie nach der Erstellung eines Steuerelements, das Datenbindung unterstützt, noch weitere Schritte ausführen. Zu den typischen nächsten Schritten gehören Folgende:  
  
- Platzieren der benutzerdefinierten Steuerelemente in eine Steuerelementbibliothek, sodass Sie sie in anderen Anwendungen wiederverwenden können.  
  
- Erstellen von Steuerelementen, die Nachschlageszenarien unterstützen. Weitere Informationen finden Sie unter [Erstellen eines Windows Forms-Benutzersteuerelements, die Bindung an Nachschlagedaten unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Festlegen des Steuerelements, das beim Ziehen aus dem Datenquellenfenster erstellt werden](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)   
 [Windows Forms-Steuerelemente](https://msdn.microsoft.com/library/f050de8f-4ebd-4042-94b8-edf9a1dbd52a)

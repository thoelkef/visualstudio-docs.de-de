---
title: Erstellen eines Windows Forms-Benutzersteuerelements, das komplexe Datenbindung unterstützt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
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
- data binding, user controls
- data binding, complex
- user controls [Visual Studio], complex data binding
ms.assetid: c8f29c2b-b49b-4618-88aa-33b6105880b5
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 27f8a0e7fca0f14ee784eddaeb30f4d734994dc9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47520538"
---
# <a name="create-a-windows-forms-user-control-that-supports-complex-data-binding"></a>Erstellen eines Windows Forms-Benutzersteuerelements, das komplexe Datenbindung unterstützt
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [erstellen Sie ein Windows Forms-Benutzersteuerelement mit Datenbindung](https://docs.microsoft.com/visualstudio/data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding).  
  
  
Anzeigen von Daten in Formularen in Windows-Anwendungen können Sie vorhandenen Steuerelemente aus der **Toolbox**, oder Sie können benutzerdefinierte Steuerelemente erstellen, wenn Ihre Anwendung Funktionen erfordert, die in den Standardsteuerelementen nicht verfügbar ist. Diese exemplarische Vorgehensweise erläutert, wie Sie ein Steuerelement erstellen, das <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> implementiert. Steuerelemente, die <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> implementieren, enthalten eine Eigenschaft `DataSource` und `DataMember`, die an Daten gebunden werden kann. Solche Steuerelemente sind vergleichbar mit <xref:System.Windows.Forms.DataGridView> oder <xref:System.Windows.Forms.ListBox>.  
  
 Weitere Informationen über das Erstellen von Steuerelementen, finden Sie unter [Entwickeln von Windows Forms-Steuerelementen zur Entwurfszeit](http://msdn.microsoft.com/library/e5a8e088-7ec8-4fd9-bcb3-9078fd134829).  
  
 Beim Erstellen von Steuerelementen für die Verwendung in Szenarios mit Datenbindung müssen Sie eine der folgenden Datenbindungsattribute implementieren:  
  
|Die Datenbindung Attributverwendung|  
|-----------------------------------|  
|Implementieren Sie <xref:System.ComponentModel.DefaultBindingPropertyAttribute> für einfache Steuerelemente, die eine einzige Spalte (oder Eigenschaft) von Daten anzeigen, wie das <xref:System.Windows.Forms.TextBox>-Steuerelement. Weitere Informationen finden Sie unter [Erstellen eines Windows Forms-Benutzersteuerelements, die einfache Datenbindung unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|  
|Implementieren Sie <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> für Steuerelemente, die Listen (oder Tabellen) von Daten anzeigen, wie das <xref:System.Windows.Forms.DataGridView>-Steuerelement. (Dieser Prozess wird in dieser exemplarischen Vorgehensweise beschrieben.)|  
|Implementieren Sie die <xref:System.ComponentModel.LookupBindingPropertiesAttribute> auf Steuerelementen wie einem <xref:System.Windows.Forms.ComboBox>,das Listen (oder Tabellen) von Daten anzeigt, aber auch in einer einzelnen Spalte oder Eigenschaft vorhanden sein muss. Weitere Informationen finden Sie unter [Erstellen eines Windows Forms-Benutzersteuerelements, die Bindung an Nachschlagedaten unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|  
  
 In dieser exemplarischen Vorgehensweise wird ein Steuerelement erstellt, das Datenzeilen aus einer Tabelle darstellt. In diesem Beispiel wird die Tabelle `Customers` der Beispieldatenbank Northwind verwendet. Das komplexe Benutzersteuerelement stellt die Tabelle Customers in einer <xref:System.Windows.Forms.DataGridView> im benutzerdefinierten Steuerelement dar.  
  
 Bei dieser exemplarischen Vorgehensweise lernen Sie Folgendes:  
  
-   Erstellen Sie ein neues **Windows-Anwendung**.  
  
-   Fügen Sie einen neuen **Benutzersteuerelement** zu Ihrem Projekt.  
  
-   Entwerfen des Benutzersteuerelements im visuellen Designer.  
  
-   Implementieren des `ComplexBindingProperty`-Attributs.  
  
-   Erstellen eines Datasets mit dem [Assistenten zur Datenquellenkonfiguration](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).  
  
-   Legen Sie die **Kunden** -Tabelle in der [Fensters "Datenquellen"](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) auf das neue, komplexe Steuerelement verwendet.  
  
-   Fügen Sie das neue Steuerelement durch Ziehen aus dem **Fensters "Datenquellen"** auf **Form1**.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Für die Durchführung dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:  
  
-   Zugriff auf die Beispieldatenbank Northwind. Weitere Informationen finden Sie unter [Vorgehensweise: Installieren von Beispieldatenbanken](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="create-a-windows-application"></a>Erstellen Sie eine Windows-Anwendung  
 Der erste Schritt ist die Erstellung einer **Windows-Anwendung**.  
  
#### <a name="to-create-the-new-windows-project"></a>So erstellen Sie ein neues Windows-Projekt  
  
1.  In Visual Studio aus der **Datei** im Menü Erstellen Sie ein neues **Projekt**.  
  
2.  Nennen Sie das Projekt **ComplexControlWalkthrough**.  
  
3.  Wählen Sie **Windows-Anwendung**, und klicken Sie auf **OK**. Weitere Informationen finden Sie unter [Clientanwendungen](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     Die **ComplexControlWalkthrough** Projekt wird erstellt und hinzugefügt **Projektmappen-Explorer**.  
  
## <a name="add-a-user-control-to-the-project"></a>Fügen Sie dem Projekt ein Benutzersteuerelement  
 Da in dieser exemplarischen Vorgehensweise ein komplexes, datenbindbares Steuerelement aus erstellt eine **Benutzersteuerelement**, müssen Sie hinzufügen, eine **Benutzersteuerelement** Elements zum Projekt.  
  
#### <a name="to-add-a-user-control-to-the-project"></a>So fügen Sie dem Projekt ein Benutzersteuerelement hinzu  
  
1.  Von der **Projekt** Menü wählen **Benutzersteuerelement hinzufügen**.  
  
2.  Typ **ComplexDataGridView** in die **Namen** Bereich, und klicken Sie dann auf **hinzufügen**.  
  
     Die **ComplexDataGridView** -Steuerelement hinzugefügt **Projektmappen-Explorer**, und im Designer geöffnet.  
  
## <a name="design-the-complexdatagridview-control"></a>Entwerfen des ComplexDataGridView-Steuerelements  
 Dieser Schritt fügt dem Benutzersteuerelement eine <xref:System.Windows.Forms.DataGridView> hinzu.  
  
#### <a name="to-design-the-complexdatagridview-control"></a>So entwerfen Sie das ComplexDataGridView-Steuerelement  
  
-   Ziehen Sie eine <xref:System.Windows.Forms.DataGridView> aus der **Toolbox** auf der Entwurfsoberfläche des Benutzersteuerelements.  
  
## <a name="add-the-required-data-binding-attribute"></a>Fügen Sie das erforderliche Attribut für die Datenbindung hinzu  
 Für komplexe Steuerelemente, die Datenbindung unterstützen, können Sie das <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> implementieren.  
  
#### <a name="to-implement-the-complexbindingproperties-attribute"></a>So implementieren Sie das ComplexBindingProperties-Attribut  
  
1.  Wechseln der **ComplexDataGridView** -Steuerelement zur Codeansicht. (Auf der **Ansicht** , wählen Sie im Menü **Code**.)  
  
2.  Ersetzen Sie den Code in `ComplexDataGridView` durch folgenden Code:  
  
     [!code-csharp[VbRaddataDisplaying#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/ComplexDataGridView.cs#4)]
     [!code-vb[VbRaddataDisplaying#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/ComplexDataGridView.vb#4)]  
  
3.  Wählen Sie im Menü **Erstellen** die Option **Projektmappe erstellen**aus.  
  
## <a name="creating-a-data-source-from-your-database"></a>Erstellen eine Datenquelle aus einer Datenbank  
 Dieser Schritt verwendet den **Datenquellenkonfiguration** Assistenten zum Erstellen einer Datenquelle basierend auf den `Customers` -Tabelle in der Beispieldatenbank Northwind. Sie benötigen Zugriff auf die Beispieldatenbank Northwind, um die Verbindung herstellen zu können. Informationen zum Einrichten der Beispieldatenbank Northwind finden Sie unter [Installieren von SQL Server-Beispieldatenbanken](../data-tools/install-sql-server-sample-databases.md).  
  
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
  
8.  Wählen Sie die `Customers` Tabelle, und klicken Sie dann auf **Fertig stellen**.  
  
     Die **NorthwindDataSet** wird Ihrem Projekt hinzugefügt und die `Customers` Tabelle angezeigt wird, der **Datenquellen** Fenster.  
  
## <a name="set-the-customers-table-to-use-the-complexdatagridview-control"></a>Festlegen der Tabelle Customers das Steuerelement ComplexDataGridView verwendet  
 In der **Datenquellen** Fenster können Sie das Steuerelement erstellt werden, vor dem Ziehen von Elementen auf das Formular festlegen.  
  
#### <a name="to-set-the-customers-table-to-bind-to-the-complexdatagridview-control"></a>So legen Sie die Bindung der Spalte Customers an das ComplexDataGridView-Steuerelement fest  
  
1.  Open **Form1** im Designer.  
  
2.  Erweitern Sie die **Kunden** Knoten in der **Datenquellen** Fenster.  
  
3.  Klicken Sie auf die Dropdown-Pfeil der **Kunden** Knoten, und wählen Sie **anpassen**.  
  
4.  Wählen Sie die **ComplexDataGridView** aus der Liste der **zugeordnete Steuerelemente** in die **Optionen für die Anpassung** Dialogfeld.  
  
5.  Klicken Sie auf die Dropdown-Pfeil der `Customers` Tabelle, und wählen Sie **ComplexDataGridView** aus der Steuerungsliste.  
  
## <a name="addcontrols-to-the-form"></a>Addcontrols zum Formular  
 Sie können die datengebundenen Steuerelemente erstellen, durch Ziehen von Elementen aus der **Datenquellen** auf das Formular.  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>So erstellen Sie datengebundene Steuerelemente auf dem Formular  
  
-   Ziehen Sie den Hauptknoten **Kunden** Knoten aus der **Datenquellen** auf das Formular. Überprüfen Sie, ob die **ComplexDataGridView** Steuerelement wird verwendet, um die Daten der Tabelle angezeigt.  
  
## <a name="running-the-application"></a>Ausführen der Anwendung  
  
#### <a name="to-run-the-application"></a>So führen Sie die Anwendung aus  
  
-   Drücken Sie F5, um die Anwendung auszuführen.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Entsprechend den Anforderungen an Ihre Anwendung können Sie nach der Erstellung eines Steuerelements, das Datenbindung unterstützt, noch weitere Schritte ausführen. Zu den typischen nächsten Schritten gehören Folgende:  
  
-   Platzieren der benutzerdefinierten Steuerelemente in eine Steuerelementbibliothek, sodass Sie sie in anderen Anwendungen wiederverwenden können.  
  
-   Erstellen von Steuerelementen, die Nachschlageszenarien unterstützen. Weitere Informationen finden Sie unter [Erstellen eines Windows Forms-Benutzersteuerelements, die Bindung an Nachschlagedaten unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Festlegen des Steuerelements, das beim Ziehen aus dem Datenquellenfenster erstellt werden](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)   
 [Windows Forms-Steuerelemente](http://msdn.microsoft.com/library/f050de8f-4ebd-4042-94b8-edf9a1dbd52a)


---
title: Erstellen eines Windows Forms-Benutzersteuerelements, die einfache Datenbindung unterstützt | Microsoft-Dokumentation
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
- custom controls [Visual Studio], Data Sources Window
- Data Sources Window, controls
ms.assetid: b1488366-6dfb-454e-9751-f42fd3f3ddfb
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0ac931dfcf7b56619707a2bd42a32f5a369b04d9
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65704994"
---
# <a name="create-a-windows-forms-user-control-that-supports-simple-data-binding"></a>Erstellen eines Windows Forms-Benutzersteuerelements, das die einfache Datenbindung unterstützt
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zum Anzeigen von Daten in Formularen in Windows-Anwendungen können Sie die in der **Toolbox** vorhandenen Steuerelemente verwenden oder, falls die gewünschte Funktionalität in den Standardsteuerelementen nicht verfügbar ist, benutzerdefinierte Steuerelemente erstellen. Diese exemplarische Vorgehensweise erläutert, wie Sie ein Steuerelement erstellen, das <xref:System.ComponentModel.DefaultBindingPropertyAttribute> implementiert. Steuerelemente, die <xref:System.ComponentModel.DefaultBindingPropertyAttribute> implementieren, können eine Eigenschaft enthalten, die an Daten gebunden werden kann. Solche Steuerelemente sind vergleichbar mit <xref:System.Windows.Forms.TextBox> oder <xref:System.Windows.Forms.CheckBox>.  
  
 Weitere Informationen über das Erstellen von Steuerelementen, finden Sie unter [Entwickeln von Windows Forms-Steuerelementen zur Entwurfszeit](https://msdn.microsoft.com/library/e5a8e088-7ec8-4fd9-bcb3-9078fd134829).  
  
 Bei der Erstellung von Steuerelementen für die Verwendung in Szenarios mit Datenbindung müssen Sie eine der folgenden Datenbindungsattribute implementieren:  
  
|Die Datenbindung Attributverwendung|  
|-----------------------------------|  
|Implementieren Sie <xref:System.ComponentModel.DefaultBindingPropertyAttribute> für einfache Steuerelemente, die eine einzige Spalte (oder Eigenschaft) von Daten anzeigen, wie das <xref:System.Windows.Forms.TextBox>-Steuerelement. (Dieser Prozess wird in dieser exemplarischen Vorgehensweise beschrieben.)|  
|Implementieren Sie <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> für Steuerelemente, die Listen (oder Tabellen) von Daten anzeigen, wie das <xref:System.Windows.Forms.DataGridView>-Steuerelement. Weitere Informationen finden Sie unter [Erstellen eines Windows Forms-Benutzersteuerelements, das komplexe Datenbindung unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|  
|Implementieren Sie die <xref:System.ComponentModel.LookupBindingPropertiesAttribute> auf Steuerelementen wie einem <xref:System.Windows.Forms.ComboBox>,das Listen (oder Tabellen) von Daten anzeigt, aber auch in einer einzelnen Spalte oder Eigenschaft vorhanden sein muss. Weitere Informationen finden Sie unter [Erstellen eines Windows Forms-Benutzersteuerelements, die Bindung an Nachschlagedaten unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|  
  
 In dieser exemplarischen Vorgehensweise wird ein einfaches Steuerelement erstellt, das Daten aus einer einzelnen Spalte in einer Tabelle anzeigt. In diesem Beispiel wird die Spalte `Phone` der Tabelle `Customers` aus der Beispieldatenbank Northwind verwendet. Das einfache Benutzersteuerelement zeigt Telefonnummern von Kunden in einem Standardformat von Telefonnummern mithilfe einer <xref:System.Windows.Forms.MaskedTextBox> und Festlegen der Maske auf eine Telefonnummer an.  
  
 Bei dieser exemplarischen Vorgehensweise lernen Sie Folgendes:  
  
- Erstellen Sie ein neues **Windows-Anwendung**.  
  
- Ihrem Projekt ein neues **Benutzersteuerelement** hinzufügen.  
  
- Entwerfen des Benutzersteuerelements im visuellen Designer.  
  
- Implementieren des `DefaultBindingProperty`-Attributs.  
  
- Erstellen eines Datasets mit dem **Datenquellenkonfiguration** Assistenten.  
  
- Legen Sie für die Spalte **Phone** im **Datenquellenfenster** fest, dass das neue Steuerelement verwendet wird.  
  
- Erstellen eines Formulars, um Daten in dem neuen Steuerelement anzuzeigen.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Für die Durchführung dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:  
  
- Zugriff auf die Beispieldatenbank Northwind.
  
## <a name="create-a-windows-application"></a>Erstellen Sie eine Windows-Anwendung  
 Der erste Schritt ist die Erstellung einer **Windows-Anwendung**.  
  
#### <a name="to-create-the-new-windows-project"></a>So erstellen Sie ein neues Windows-Projekt  
  
1. In Visual Studio aus der **Datei** im Menü Erstellen Sie ein neues **Projekt**.  
  
2. Nennen Sie das Projekt **SimpleControlWalkthrough**.  
  
3. Wählen Sie **Windows-Anwendung** , und klicken Sie auf **OK**. Weitere Informationen finden Sie unter [Clientanwendungen](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     Das Projekt **SimpleControlWalkthrough** wird erstellt und dem **Projektmappen-Explorer** hinzugefügt.  
  
## <a name="add-a-user-control-to-the-project"></a>Hinzufügen eines Benutzersteuerelements zum Projekt  
 In dieser exemplarischen Vorgehensweise erstellt ein einfaches, datenbindbares Steuerelement aus einer **Benutzersteuerelement**, fügen Sie also eine **Benutzersteuerelement** Element für die **SimpleControlWalkthrough** Projekt.  
  
#### <a name="to-add-a-user-control-to-the-project"></a>So fügen Sie dem Projekt ein Benutzersteuerelement hinzu  
  
1. Klicken Sie im Menü **Projekt** auf **Benutzersteuerelement hinzufügen**.  
  
2. Typ `PhoneNumberBox` in den Bereich Name ein und klicken Sie auf **hinzufügen**.  
  
     Das **PhoneNumberBox**-Steuerelement wird dem **Projektmappen-Explorer** hinzugefügt und im Designer geöffnet.  
  
## <a name="design-the-phonenumberbox-control"></a>Entwerfen des PhoneNumberBox-Steuerelements  
 Diese exemplarische Vorgehensweise erweitert das vorhandene <xref:System.Windows.Forms.MaskedTextBox>, sodass das `PhoneNumberBox`-Steuerelement erstellt wird.  
  
#### <a name="to-design-the-phonenumberbox-control"></a>Entwerfen des PhoneNumberBox-Steuerelements  
  
1. Ziehen Sie ein <xref:System.Windows.Forms.MaskedTextBox> aus der **Toolbox** auf die Entwurfsoberfläche des Benutzersteuerelements.  
  
2. Klicken Sie auf das Smarttag auf das soeben gezogene <xref:System.Windows.Forms.MaskedTextBox>-Objekt, und klicken Sie dann auf **Maske festlegen**.  
  
3. Wählen Sie **Telefonnummer** im Dialogfeld **Eingabeformat** aus, und klicken Sie auf **OK**, um die Maske festzulegen.  
  
## <a name="add-the-required-data-binding-attribute"></a>Fügen Sie das erforderliche Attribut für die Datenbindung hinzu  
 Implementieren Sie für einfache Steuerelemente, die Datenbindung unterstützen, das <xref:System.ComponentModel.DefaultBindingPropertyAttribute>.  
  
#### <a name="to-implement-the-defaultbindingproperty-attribute"></a>So implementieren Sie das Attribut DefaultBindingProperty  
  
1. Wechseln Sie für das `PhoneNumberBox`-Steuerelement zur Codeansicht. (Wählen Sie im Menü **Ansicht** den Befehl **Code** aus.)  
  
2. Ersetzen Sie den Code in `PhoneNumberBox` durch folgenden Code:  
  
     [!code-csharp[VbRaddataDisplaying#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/PhoneNumberBox.cs#3)]
     [!code-vb[VbRaddataDisplaying#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/PhoneNumberBox.vb#3)]  
  
3. Wählen Sie im Menü **Erstellen** die Option **Projektmappe erstellen**aus.  
  
## <a name="create-a-data-source-from-your-database"></a>Erstellen Sie eine Datenquelle aus der Datenbank  
 In diesem Schritt wird der **Assistent zum Konfigurieren von Datenquellen** verwendet, um eine Datenquelle anhand der `Customers`-Tabelle in der Beispieldatenbank Northwind zu erstellen. Sie benötigen Zugriff auf die Beispieldatenbank Northwind, um die Verbindung herstellen zu können.
  
#### <a name="to-create-the-data-source"></a>So erstellen Sie die Datenquelle  
  
1. Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.  
  
2. Klicken Sie im **Datenquellenfenster** auf **Neue Datenquelle hinzufügen**, um den **Assistenten zum Konfigurieren von Datenquellen** zu starten.  
  
3. Wählen Sie auf der Seite **Datenquellentyp auswählen** die Option **Datenbank** aus, und klicken Sie dann auf **Weiter**.  
  
4. Führen Sie auf der Seite **Wählen Sie Ihre Datenverbindung aus** einen der folgenden Schritte aus:  
  
    - Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank „Northwind“ verfügbar ist, wählen Sie diese aus.  
  
    - Klicken Sie auf **Neue Verbindung**, um das Dialogfeld **Add/Modify Connection** (Verbindung hinzufügen/ändern) zu öffnen.  
  
5. Falls die Datenbank ein Kennwort erfordern sollte, aktivieren Sie die Option für die Einbeziehung vertraulicher Daten, und klicken Sie dann auf **Weiter**.  
  
6. Klicken Sie auf der Seite **Save connection string to the Application Configuration file** (Verbindungszeichenfolge in der Programmkonfigurationsdatei speichern) auf **Weiter**.  
  
7. Erweitern Sie auf der Seite **Datenbankobjekte auswählen** den Knoten **Tabellen**.  
  
8. Wählen Sie die `Customers`-Tabelle aus, und klicken Sie anschließend auf **Fertig stellen**.  
  
     Das **NorthwindDataSet** wird dem Projekt hinzugefügt, und die Tabelle `Customers` wird im **Datenquellenfenster** angezeigt.  
  
## <a name="set-the-phone-column-to-use-the-phonenumberbox-control"></a>Festlegen der Spalte "Phone" auf das Steuerelement PhoneNumberBox verwendet  
 Im **Datenquellenfenster** können Sie vor dem Ziehen von Elementen auf das Formular festlegen, welches Steuerelement erstellt werden soll.  
  
#### <a name="to-set-the-phone-column-to-bind-to-the-phonenumberbox-control"></a>So legen Sie die Bindung der Spalte "Telefon" an das PhoneNumberBox-Steuerelement fest  
  
1. Öffnen Sie **Form1** im Designer.  
  
2. Erweitern Sie im **Datenquellenfenster** den Knoten **Customers**.  
  
3. Klicken Sie auf den Dropdownpfeil auf dem Knoten **Customers**, und wählen Sie **Details** aus der Steuerelementliste aus.  
  
4. Klicken Sie auf den Dropdownpfeil auf der Spalte **Phone**, und wählen Sie **Anpassen** aus.  
  
5. Wählen Sie im Dialogfeld **Data UI Customization Options** (Optionen für die Anpassung der Datenbenutzeroberfläche) in der Liste **Zugeordnete Steuerelemente** den Eintrag **PhoneNumberBox** aus.  
  
6. Klicken Sie auf den Dropdownpfeil auf der Spalte **Phone**, und wählen Sie **PhoneNumberBox** aus.  
  
## <a name="addcontrols-to-the-form"></a>Addcontrols zum Formular  
 Sie können die datengebundenen Steuerelemente erstellen, indem Sie Elemente aus dem **Datenquellenfenster** auf das Formular ziehen.  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>So erstellen Sie datengebundene Steuerelemente auf dem Formular  
  
- Ziehen Sie den Hauptknoten **Kunden** Knoten aus der **Datenquellen** auf das Formular, und überprüfen Sie, ob die `PhoneNumberBox` Steuerelement wird verwendet, um die Anzeige der Daten in die `Phone` Spalte.  
  
     Auf dem Formular werden datengebundene Steuerelemente mit beschreibenden Bezeichnungen sowie ein Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) für die Navigation in den Datensätzen angezeigt. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> und <xref:System.Windows.Forms.BindingNavigator> werden auf der Komponentenleiste angezeigt.  
  
## <a name="run-the-application"></a>Ausführen der Anwendung  
  
#### <a name="to-run-the-application"></a>So führen Sie die Anwendung aus  
  
- Drücken Sie F5, um die Anwendung auszuführen.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Entsprechend den Anforderungen an Ihre Anwendung können Sie nach der Erstellung eines Steuerelements, das Datenbindung unterstützt, noch weitere Schritte ausführen. Zu den typischen nächsten Schritten gehören Folgende:  
  
- Platzieren der benutzerdefinierten Steuerelemente in eine Steuerelementbibliothek, sodass Sie sie in anderen Anwendungen wiederverwenden können.  
  
- Erstellen von Steuerelementen, die komplexere Datenbindungsszenarien unterstützen. Weitere Informationen finden Sie unter [Erstellen eines Windows Forms-Benutzersteuerelements, das komplexe Datenbindung unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md) und [Erstellen eines Windows Forms-Benutzersteuerelements, die Bindung an Nachschlagedaten unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Festlegen des Steuerelements, das beim Ziehen aus dem Datenquellenfenster erstellt werden soll](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)

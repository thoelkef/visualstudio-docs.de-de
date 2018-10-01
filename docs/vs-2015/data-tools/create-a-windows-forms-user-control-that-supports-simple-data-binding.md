---
title: Erstellen eines Windows Forms-Benutzersteuerelements, die einfache Datenbindung unterstützt | Microsoft-Dokumentation
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
- custom controls [Visual Studio], Data Sources Window
- Data Sources Window, controls
ms.assetid: b1488366-6dfb-454e-9751-f42fd3f3ddfb
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a5cb2d1e9d1ea175122381c19fa93c9abc07b2a2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513635"
---
# <a name="create-a-windows-forms-user-control-that-supports-simple-data-binding"></a>Erstellen eines Windows Forms-Benutzersteuerelements, das einfache Datenbindung unterstützt
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Erstellen eines Benutzersteuerelements, die einfache Datenbindung unterstützt](https://docs.microsoft.com/visualstudio/data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding).  
  
  
Anzeigen von Daten in Formularen in Windows-Anwendungen können Sie vorhandenen Steuerelemente aus der **Toolbox**, oder Sie können benutzerdefinierte Steuerelemente erstellen, wenn Ihre Anwendung Funktionen erfordert, die in den Standardsteuerelementen nicht verfügbar ist. Diese exemplarische Vorgehensweise erläutert, wie Sie ein Steuerelement erstellen, das <xref:System.ComponentModel.DefaultBindingPropertyAttribute> implementiert. Steuerelemente, die <xref:System.ComponentModel.DefaultBindingPropertyAttribute> implementieren, können eine Eigenschaft enthalten, die an Daten gebunden werden kann. Solche Steuerelemente sind vergleichbar mit <xref:System.Windows.Forms.TextBox> oder <xref:System.Windows.Forms.CheckBox>.  
  
 Weitere Informationen über das Erstellen von Steuerelementen, finden Sie unter [Entwickeln von Windows Forms-Steuerelementen zur Entwurfszeit](http://msdn.microsoft.com/library/e5a8e088-7ec8-4fd9-bcb3-9078fd134829).  
  
 Bei der Erstellung von Steuerelementen für die Verwendung in Szenarios mit Datenbindung müssen Sie eine der folgenden Datenbindungsattribute implementieren:  
  
|Die Datenbindung Attributverwendung|  
|-----------------------------------|  
|Implementieren Sie <xref:System.ComponentModel.DefaultBindingPropertyAttribute> für einfache Steuerelemente, die eine einzige Spalte (oder Eigenschaft) von Daten anzeigen, wie das <xref:System.Windows.Forms.TextBox>-Steuerelement. (Dieser Prozess wird in dieser exemplarischen Vorgehensweise beschrieben.)|  
|Implementieren Sie <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> für Steuerelemente, die Listen (oder Tabellen) von Daten anzeigen, wie das <xref:System.Windows.Forms.DataGridView>-Steuerelement. Weitere Informationen finden Sie unter [Erstellen eines Windows Forms-Benutzersteuerelements, das komplexe Datenbindung unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|  
|Implementieren Sie die <xref:System.ComponentModel.LookupBindingPropertiesAttribute> auf Steuerelementen wie einem <xref:System.Windows.Forms.ComboBox>,das Listen (oder Tabellen) von Daten anzeigt, aber auch in einer einzelnen Spalte oder Eigenschaft vorhanden sein muss. Weitere Informationen finden Sie unter [Erstellen eines Windows Forms-Benutzersteuerelements, die Bindung an Nachschlagedaten unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|  
  
 In dieser exemplarischen Vorgehensweise wird ein einfaches Steuerelement erstellt, das Daten aus einer einzelnen Spalte in einer Tabelle anzeigt. In diesem Beispiel wird die Spalte `Phone` der Tabelle `Customers` aus der Beispieldatenbank Northwind verwendet. Das einfache Benutzersteuerelement zeigt Telefonnummern von Kunden in einem Standardformat von Telefonnummern mithilfe einer <xref:System.Windows.Forms.MaskedTextBox> und Festlegen der Maske auf eine Telefonnummer an.  
  
 Bei dieser exemplarischen Vorgehensweise lernen Sie Folgendes:  
  
-   Erstellen Sie ein neues **Windows-Anwendung**.  
  
-   Fügen Sie einen neuen **Benutzersteuerelement** zu Ihrem Projekt.  
  
-   Entwerfen des Benutzersteuerelements im visuellen Designer.  
  
-   Implementieren des `DefaultBindingProperty`-Attributs.  
  
-   Erstellen eines Datasets mit dem **Datenquellenkonfiguration** Assistenten.  
  
-   Legen Sie die **Phone** -Spalte in der **Datenquellen** Fenster, das das neue Steuerelement verwendet.  
  
-   Erstellen eines Formulars, um Daten in dem neuen Steuerelement anzuzeigen.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Für die Durchführung dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:  
  
-   Zugriff auf die Beispieldatenbank Northwind. Weitere Informationen finden Sie unter [Vorgehensweise: Installieren von Beispieldatenbanken](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="create-a-windows-application"></a>Erstellen Sie eine Windows-Anwendung  
 Der erste Schritt ist die Erstellung einer **Windows-Anwendung**.  
  
#### <a name="to-create-the-new-windows-project"></a>So erstellen Sie ein neues Windows-Projekt  
  
1.  In Visual Studio aus der **Datei** im Menü Erstellen Sie ein neues **Projekt**.  
  
2.  Nennen Sie das Projekt **SimpleControlWalkthrough**.  
  
3.  Wählen Sie **Windows-Anwendung** , und klicken Sie auf **OK**. Weitere Informationen finden Sie unter [Clientanwendungen](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     Die **SimpleControlWalkthrough** Projekt wird erstellt und hinzugefügt **Projektmappen-Explorer**.  
  
## <a name="add-a-user-control-to-the-project"></a>Fügen Sie dem Projekt ein Benutzersteuerelement  
 In dieser exemplarischen Vorgehensweise erstellt ein einfaches, datenbindbares Steuerelement aus einer **Benutzersteuerelement**, fügen Sie also eine **Benutzersteuerelement** Element für die **SimpleControlWalkthrough** Projekt.  
  
#### <a name="to-add-a-user-control-to-the-project"></a>So fügen Sie dem Projekt ein Benutzersteuerelement hinzu  
  
1.  Von der **Projekt** Menü wählen **Benutzersteuerelement hinzufügen**.  
  
2.  Typ `PhoneNumberBox` in den Bereich Name ein und klicken Sie auf **hinzufügen**.  
  
     Die **PhoneNumberBox** -Steuerelement hinzugefügt **Projektmappen-Explorer**, und im Designer geöffnet.  
  
## <a name="design-the-phonenumberbox-control"></a>Entwerfen des PhoneNumberBox-Steuerelements  
 Diese exemplarische Vorgehensweise erweitert das vorhandene <xref:System.Windows.Forms.MaskedTextBox>, sodass das `PhoneNumberBox`-Steuerelement erstellt wird.  
  
#### <a name="to-design-the-phonenumberbox-control"></a>Entwerfen des PhoneNumberBox-Steuerelements  
  
1.  Ziehen Sie eine <xref:System.Windows.Forms.MaskedTextBox> aus der **Toolbox** auf der Entwurfsoberfläche des Benutzersteuerelements.  
  
2.  Wählen Sie auf das Smarttag die <xref:System.Windows.Forms.MaskedTextBox> gerade gezogen haben, und klicken Sie **Maske festlegen**.  
  
3.  Wählen Sie **Telefonnummer** in die **Eingabeformat** (Dialogfeld), und klicken Sie auf **OK** zum Festlegen der Maske.  
  
## <a name="add-the-required-data-binding-attribute"></a>Fügen Sie das erforderliche Attribut für die Datenbindung hinzu  
 Implementieren Sie für einfache Steuerelemente, die Datenbindung unterstützen, das <xref:System.ComponentModel.DefaultBindingPropertyAttribute>.  
  
#### <a name="to-implement-the-defaultbindingproperty-attribute"></a>So implementieren Sie das Attribut DefaultBindingProperty  
  
1.  Wechseln Sie für das `PhoneNumberBox`-Steuerelement zur Codeansicht. (Auf der **Ansicht** Menü wählen **Code**.)  
  
2.  Ersetzen Sie den Code in `PhoneNumberBox` durch folgenden Code:  
  
     [!code-csharp[VbRaddataDisplaying#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/PhoneNumberBox.cs#3)]
     [!code-vb[VbRaddataDisplaying#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/PhoneNumberBox.vb#3)]  
  
3.  Wählen Sie im Menü **Erstellen** die Option **Projektmappe erstellen**aus.  
  
## <a name="create-a-data-source-from-your-database"></a>Erstellen Sie eine Datenquelle aus der Datenbank  
 Dieser Schritt verwendet den **Datenquellenkonfiguration**Assistenten zum Erstellen einer Datenquelle basierend auf den `Customers` -Tabelle in der Beispieldatenbank Northwind. Sie benötigen Zugriff auf die Beispieldatenbank Northwind, um die Verbindung herstellen zu können. Informationen zum Einrichten der Beispieldatenbank Northwind finden Sie unter [Vorgehensweise: Installieren von Beispieldatenbanken](../data-tools/how-to-install-sample-databases.md).  
  
#### <a name="to-create-the-data-source"></a>So erstellen Sie die Datenquelle  
  
1.  Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.  
  
2.  In der **Datenquellen** wählen Sie im Fenster **neue Datenquelle hinzufügen** zum Starten der **Datenquellenkonfiguration** Assistenten.  
  
3.  Auf der **wählen Sie einen Datenquellentyp** Seite **Datenbank**, und klicken Sie dann auf **Weiter**.  
  
4.  Auf der **wählen Sie Ihre Datenverbindung** eine der folgenden:  
  
    -   Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank „Northwind“ verfügbar ist, wählen Sie diese aus.  
  
    -   Wählen Sie **neue Verbindung** zum Starten der **Verbindung hinzufügen/ändern** Dialogfeld.  
  
5.  Wenn Ihre Datenbank ein Kennwort erfordert, wählen Sie die Option Einbeziehung vertraulicher Daten, und klicken Sie dann auf **Weiter**.  
  
6.  Auf der **Verbindungszeichenfolge in der Programmkonfigurationsdatei speichern** auf **Weiter**.  
  
7.  Auf der **Datenbankobjekte auswählen** Seite, erweitern Sie die **Tabellen** Knoten.  
  
8.  Wählen Sie die `Customers` Tabelle, und klicken Sie dann auf **Fertig stellen**.  
  
     Die **NorthwindDataSet** wird Ihrem Projekt hinzugefügt und die `Customers` Tabelle angezeigt wird, der **Datenquellen** Fenster.  
  
## <a name="set-the-phone-column-to-use-the-phonenumberbox-control"></a>Festlegen der Spalte "Phone" auf das Steuerelement PhoneNumberBox verwendet  
 In der **Datenquellen** Fenster können Sie das Steuerelement erstellt werden, vor dem Ziehen von Elementen auf das Formular festlegen.  
  
#### <a name="to-set-the-phone-column-to-bind-to-the-phonenumberbox-control"></a>So legen Sie die Bindung der Spalte "Telefon" an das PhoneNumberBox-Steuerelement fest  
  
1.  Open **Form1** im Designer.  
  
2.  Erweitern Sie die **Kunden** Knoten in der **Datenquellen** Fenster.  
  
3.  Klicken Sie auf die Dropdown-Pfeil der **Kunden** Knoten, und wählen Sie **Details** aus der Steuerungsliste.  
  
4.  Klicken Sie auf die Dropdown-Pfeil der **Phone** Spalte, und wählen Sie **anpassen**.  
  
5.  Wählen Sie die **PhoneNumberBox** aus der Liste der **zugeordnete Steuerelemente** in die **Optionen für die Anpassung** Dialogfeld.  
  
6.  Klicken Sie auf die Dropdown-Pfeil der **Phone** Spalte, und wählen Sie **PhoneNumberBox**.  
  
## <a name="addcontrols-to-the-form"></a>Addcontrols zum Formular  
 Sie können die datengebundenen Steuerelemente erstellen, durch Ziehen von Elementen aus der **Datenquellen** auf das Formular.  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>So erstellen Sie datengebundene Steuerelemente auf dem Formular  
  
-   Ziehen Sie den Hauptknoten **Kunden** Knoten aus der **Datenquellen** auf das Formular, und überprüfen Sie, ob die `PhoneNumberBox` Steuerelement wird verwendet, um die Anzeige der Daten in die `Phone` Spalte.  
  
     Auf dem Formular werden datengebundene Steuerelemente mit beschreibenden Bezeichnungen sowie ein Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) für die Navigation in den Datensätzen angezeigt. Ein [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, und <xref:System.Windows.Forms.BindingNavigator> werden in der Komponentenleiste angezeigt.  
  
## <a name="run-the-application"></a>Ausführen der Anwendung  
  
#### <a name="to-run-the-application"></a>So führen Sie die Anwendung aus  
  
-   Drücken Sie F5, um die Anwendung auszuführen.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Entsprechend den Anforderungen an Ihre Anwendung können Sie nach der Erstellung eines Steuerelements, das Datenbindung unterstützt, noch weitere Schritte ausführen. Zu den typischen nächsten Schritten gehören Folgende:  
  
-   Platzieren der benutzerdefinierten Steuerelemente in eine Steuerelementbibliothek, sodass Sie sie in anderen Anwendungen wiederverwenden können.  
  
-   Erstellen von Steuerelementen, die komplexere Datenbindungsszenarien unterstützen. Weitere Informationen finden Sie unter [Erstellen eines Windows Forms-Benutzersteuerelements, das komplexe Datenbindung unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md) und [Erstellen eines Windows Forms-Benutzersteuerelements, die Bindung an Nachschlagedaten unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Festlegen des Steuerelements, das beim Ziehen aus dem Datenquellenfenster erstellt werden soll](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)


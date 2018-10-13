---
title: 'Exemplarische Vorgehensweise: Anzeigen von Daten in einem Windows Form | Microsoft-Dokumentation'
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
- displaying data on forms, walkthroughs
- Windows Forms, displaying data
- Windows applications, displaying data
- data binding, Windows Forms
- data [Visual Studio], displaying on Windows Forms
- forms, displaying data
ms.assetid: f6e08c2c-c792-43de-adf3-3e52c0100225
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: f623f639458a9f5c9c055b5d6de384f6fd39cad1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49201201"
---
# <a name="walkthrough-displaying-data-on-a-windows-form"></a>Exemplarische Vorgehensweise: Anzeigen von Daten in einem Windows Form
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eines der häufigsten Szenarios bei der Anwendungsentwicklung ist das Anzeigen von Daten in einem Formular in einer Windows-Anwendung. Sie können Daten in einem Formular anzeigen, durch Ziehen von Elementen aus der [Fensters "Datenquellen"](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) auf das Formular. In dieser exemplarischen Vorgehensweise wird ein einfaches Formular erstellt, das Daten aus einer einzelnen Tabelle in jeweils verschiedenen Steuerelementen anzeigt. In diesem Beispiel wird die Tabelle `Customers` der Beispieldatenbank Northwind verwendet.  
  
 In dieser exemplarischen Vorgehensweise werden u. a. folgende Aufgaben veranschaulicht:  
  
-   Erstellen eines neuen **Windows-Anwendung** Projekt.  
  
-   Erstellen und Konfigurieren eines Datasets mithilfe der [Assistenten zur Datenquellenkonfiguration](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).  
  
-   Auswählen des Steuerelements, auf dem Formular erstellt werden, beim Ziehen von Elementen aus der **Datenquellen** Fenster. Weitere Informationen finden Sie unter [legen Sie das Steuerelement erstellt werden, beim Ziehen aus Datenquellenfenster](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Erstellen eines datengebundenen Steuerelements durch Ziehen von Elementen aus der **Datenquellen** auf das Formular.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Für die Durchführung dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:  
  
-   Zugriff auf die Beispieldatenbank Northwind. Weitere Informationen finden Sie unter [Vorgehensweise: Installieren von Beispieldatenbanken](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="creating-the-windows-application"></a>Erstellen der Windows-Anwendung  
 Der erste Schritt ist die Erstellung einer **Windows-Anwendung** Projekt.  
  
#### <a name="to-create-the-new-windows-application-project"></a>So erstellen Sie das neue Windows-Anwendungsprojekt  
  
1.  Von der **Datei** Menü ein neues Projekt erstellen.  
  
2.  Benennen Sie das Projekt mit `DisplayingDataonaWindowsForm`.  
  
3.  Wählen Sie **Windows-Anwendung** , und klicken Sie auf **OK**. Weitere Informationen finden Sie unter [Clientanwendungen](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     Die **DisplayingDataonaWindowsForm** Projekt wird erstellt und hinzugefügt **Projektmappen-Explorer**.  
  
## <a name="creating-the-data-source"></a>Erstellen der Datenquelle  
 Dieser Schritt wird erstellt, mit einer Datenquelle mithilfe der **Assistenten zur Datenquellenkonfiguration** basierend auf den `Customers` -Tabelle in der Beispieldatenbank Northwind. Sie benötigen Zugriff auf die Beispieldatenbank Northwind, um die Verbindung herstellen zu können. Informationen zum Einrichten der Beispieldatenbank Northwind finden Sie unter [Vorgehensweise: Installieren von Beispieldatenbanken](../data-tools/how-to-install-sample-databases.md).  
  
#### <a name="to-create-the-data-source"></a>So erstellen Sie die Datenquelle  
  
1.  Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.  
  
2.  In der **Datenquellen** wählen Sie im Fenster **neue Datenquelle hinzufügen** zum Starten der **Assistenten zur Datenquellenkonfiguration**.  
  
3.  Wählen Sie auf der Seite **Datenquellentyp auswählen** die Option **Datenbank** aus, und klicken Sie auf **Weiter**.  
  
4.  Auf der **wählen Sie Ihre Datenverbindung** Seite führen Sie einen der folgenden:  
  
    -   Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank „Northwind“ verfügbar ist, wählen Sie diese aus.  
  
         - oder -   
  
    -   Wählen Sie **neue Verbindung** zum Starten der **Verbindung hinzufügen/ändern** Dialogfeld...  
  
5.  Wenn Ihre Datenbank ein Kennwort erfordert, wählen Sie die Option Einbeziehung vertraulicher Daten, und klicken Sie dann auf **Weiter**.  
  
6.  Klicken Sie auf **Weiter** auf die **Verbindungszeichenfolge in der Programmkonfigurationsdatei speichern** Seite.  
  
7.  Erweitern Sie die **Tabellen** Knoten auf den **Datenbankobjekte auswählen** Seite.  
  
8.  Wählen Sie die **Kunden** Tabelle, und klicken Sie dann auf **Fertig stellen**.  
  
     Die **NorthwindDataSet** wird dem Projekt hinzugefügt und die **Kunden** Tabelle angezeigt wird, der **Datenquellen** Fenster.  
  
## <a name="setting-the-controls-to-be-created"></a>Festlegen der zu erstellenden Steuerelemente  
 In dieser exemplarischen Vorgehensweise werden die Daten in einem **Details** Layout, in denen die Daten in einzelnen Steuerelementen angezeigt. (Der alternative Ansatz ist die Standardeinstellung **Raster** Layout, die die Daten, in dem in angezeigt werden einer <xref:System.Windows.Forms.DataGridView> Steuerelement.)  
  
#### <a name="to-set-the-drop-type-for-the-items-in-the-data-sources-window"></a>So legen Sie den Ablagetyp für die Elemente im Datenquellenfenster fest  
  
1.  Erweitern Sie die **Kunden** Knoten in der **Datenquellen** Fenster.  
  
2.  Ändern Sie den Ablagetyp für die **Kunden** Tabelle **Details** dazu **Details** aus der Dropdown-Liste auf die **Kunden** Knoten. Weitere Informationen finden Sie unter [legen Sie das Steuerelement erstellt werden, beim Ziehen aus Datenquellenfenster](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
3.  Ändern der **"CustomerID"** Ablagetyp der Spalte, in eine Bezeichnung auswählen **Bezeichnung** aus der Steuerungsliste auf dem **"CustomerID"** Knoten.  
  
## <a name="creating-the-form"></a>Erstellen des Formulars  
 Erstellen Sie datengebundene Steuerelemente durch Ziehen von Elementen aus der **Datenquellen** auf das Formular.  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>So erstellen Sie datengebundene Steuerelemente auf dem Formular  
  
-   Ziehen Sie den Hauptknoten **Kunden** Knoten aus der **Datenquellen** auf das Formular.  
  
     Auf dem Formular werden datengebundene Steuerelemente mit beschreibenden Bezeichnungen sowie ein Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) für die Navigation in den Datensätzen angezeigt. Ein [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, und <xref:System.Windows.Forms.BindingNavigator> werden in der Komponentenleiste angezeigt.  
  
## <a name="testing-the-application"></a>Testen der Anwendung  
  
#### <a name="to-run-the-application"></a>So führen Sie die Anwendung aus  
  
-   Drücken Sie F5.  
  
-   Durchsuchen Sie die Datensätze mithilfe des <xref:System.Windows.Forms.BindingNavigator>-Steuerelements.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Entsprechend den Anforderungen an Ihre Anwendung können Sie nach der Erstellung eines datengebundenen Windows Forms noch weitere Schritte ausführen. Sie können an dieser exemplarischen Vorgehensweise beispielsweise folgende Verbesserungen vornehmen:  
  
-   Fügen Sie dem Formular Suchfunktionalität hinzu. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen einer parametrisierten Abfrage auf einer Windows Forms-Anwendung](http://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416).  
  
-   Fügen Sie eine Funktion hinzu, um Aktualisierungen an die Datenbank zurückzusenden. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Speichern von Daten in einer Datenbank (eine Tabelle)](http://msdn.microsoft.com/library/68befa96-7463-43e8-abcf-dc2f42ccd53d).  
  
-   Hinzufügen der `Orders` Tabelle mit dem Dataset durch Auswahl **DataSet mit Assistent konfigurieren** innerhalb der **Datenquellen** Fenster. Dann Sie Steuerelemente hinzu, die zugehörigen Daten, indem Sie ziehen anzeigen die **Bestellungen** Knoten (siehe unten die **Fax** Spalte innerhalb der **Kunden** Tabelle) auf das Formular. Weitere Informationen finden Sie unter [Vorgehensweise: Anzeigen von verknüpften Daten in einer Windows Forms-Anwendung](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweisen für Daten](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Neue Datenquelle hinzufügen](../data-tools/add-new-data-sources.md)   
 [Übersicht über TableAdapters](../data-tools/tableadapter-overview.md)
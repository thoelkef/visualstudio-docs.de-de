---
title: 'Vorgehensweise: Verbinden mit Daten in einer Datenbank | Microsoft-Dokumentation'
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
- databases, connecting to
- data sources, databases
- data [Visual Studio], connecting to databases
- data sources, creating
- database connections
ms.assetid: 6c56e54e-8834-4297-85aa-cc1a443ba556
caps.latest.revision: 55
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: e75de3c81270449da6fe6bb504b476b912f51583
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49273805"
---
# <a name="how-to-connect-to-data-in-a-database"></a>Gewusst wie: Herstellen einer Verbindung zu Daten in einer Datenbank
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die Anwendung mithilfe von Visual Studio mit einer Datenbank verbinden. Nach dem Erstellen der Datenverbindung erstellt Visual Studio ein Datenmodell, mit dem die Anwendung mit den Daten in der Datenbank interagiert. Die Objekte im Datenmodell werden im der [Fensters "Datenquellen"](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992). Anschließend können Sie datengebundene Steuerelemente durch Ziehen von Elementen aus der **Fensters "Datenquellen"** , einer Entwurfsoberfläche. Weitere Informationen finden Sie unter [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
 Dieses Thema enthält Anweisungen zum Herstellen einer Verbindung mit einer Datenbank und Erstellen der folgenden Datenmodelltypen:  
  
-   DataSet  
  
-   Entity Data Model (EDM)  
  
> [!NOTE]
>  Sie können mit Visual Studio LINQ to SQL-Klassen aus einer Datenbank erstellen. LINQ to SQL-Klassen werden jedoch nicht angezeigt, der **Datenquellen** Fenster, und kann daher nicht direkt in einen Designer zum Erstellen von datengebundenen Steuerelementen gezogen werden. Weitere Informationen zum Erstellen von LINQ to SQL-Klassen aus einer Datenbank finden Sie unter [Vorgehensweise: Erstellen von LINQ to SQL-Klassen zu Tabellen und Sichten (O/R Designer) zugeordnet](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
##  <a name="dataset"></a> Herstellen einer Verbindung mit einer Datenbank und Erstellen eines Datasets  
 Wenn Sie ein auf einer Datenbank basiertes Dataset erstellen, erstellt Visual Studio einen Satz von Klassen, die eine programmierbare Ansicht der Daten darstellen. Die Hauptklasse wird aufgerufen, eine *typisiertes Dataset*. Das typisierte Dataset enthält Datentabellenobjekte, die Tabellen in der Datenbank darstellen. Weitere Informationen zu typisierten "Datasets", finden Sie unter [datasettools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).  
  
 Nachdem Sie ein Dataset erstellt haben, können Sie datengebundene WPF- oder Windows Forms-Steuerelemente erstellen, indem Sie Datasetobjekte aus dem Datenquellenfenster in den WPF- oder Windows Forms-Designer ziehen.  
  
#### <a name="to-connect-your-application-to-a-database-and-create-a-dataset"></a>So verbinden Sie die Anwendung und erstellen ein Dataset  
  
1.  Öffnen Sie ein vorhandenes Projekt in Visual Studio, oder erstellen Sie ein neues Projekt.  
  
2.  Klicken Sie im Menü **Daten** auf **Neue Datenquelle hinzufügen**.  
  
     Die **Assistenten zur Datenquellenkonfiguration** wird geöffnet.  
  
3.  Auf der **wählen Sie einen Datenquellentyp** Seite **Datenbank**, und klicken Sie dann auf **Weiter**.  
  
4.  Auf der **Auswählen eines Datenbankmodells** Seite **Dataset**, und klicken Sie dann auf **Weiter**.  
  
5.  Auf der **wählen Sie Ihre Datenverbindung** Seite, wählen Sie eine Datenverbindung aus der Liste der verfügbaren Verbindungen aus, und klicken Sie dann auf **Weiter**.  
  
     Wenn die gewünschte Datenverbindung nicht verfügbar ist, erstellen Sie eine neue Verbindung mithilfe der Schritte in [erstellen eine neue Datenbankverbindung](#CreatingDataConnection).  
  
6.  Auf der **Verbindungszeichenfolge in der Anwendungskonfigurationsdatei speichern** optional Deaktivieren der **Ja, Verbindung speichern unter** Kontrollkästchen, wenn Sie die Verbindungszeichenfolge direkt in die kompilierte speichern möchten die Anwendung. Standardmäßig wird die Verbindung in der Anwendungskonfigurationsdatei gespeichert. Weitere Informationen finden Sie unter [Vorgehensweise: Speichern und Bearbeiten von Verbindungszeichenfolgen](~/E:/Repos/visualstudio-docs-pr/docs/data-tools/how-to-save-and-edit-connection-strings.md).  
  
7.  Auf der **Datenbankobjekte auswählen** Seite, wählen Sie die Datenbankobjekte, die Sie in Ihrer Anwendung verwenden. Sie haben auch die Möglichkeit, den standardmäßigen ersetzen **DatasetName**.  
  
8.  Klicken Sie auf **Fertig stellen**. Das Dataset, das Sie gerade erstellt haben, ist jetzt verfügbar ist, in der **Datenquellen** Fenster.  
  
    > [!NOTE]
    >  Wenn die **Datenquellen** nicht geöffnet ist, klicken Sie auf **Datenquellen anzeigen** auf die **Daten** Menü zum Öffnen des Fensters.  
  
9. Sie können nun ziehen Sie Elemente aus der **Datenquellen** in den WPF-Designer, im Windows Forms-Designer oder der [Component Designer](http://msdn.microsoft.com/library/61a3a450-5b15-465e-bd9a-72a6c8c2b282) zum Erstellen von datengebundenen Steuerelementen. Weitere Informationen finden Sie unter [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
##  <a name="edm"></a> Herstellen einer Verbindung mit der Datenbank, und erstellen ein Entity Data Model  
 Wenn Sie ein auf einer Datenbank basiertes Entity Data Model erstellen, erstellt Visual Studio einen Satz von Klassen, die eine programmierbare Ansicht der Daten darstellen. Weitere Informationen über Entity Data Models und ADO.NET Entity Framework finden Sie unter [Übersicht über Entity Framework](http://msdn.microsoft.com/library/a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0).  
  
 Nachdem Sie ein Entity Data Model erstellt haben, können Sie datengebundene WPF-Steuerelemente erstellen, indem Sie Entitätsobjekte aus dem Datenquellenfenster in den WPF-Designer ziehen.  
  
#### <a name="to-connect-your-application-to-a-database-and-create-an-entity-data-model"></a>So stellen Sie eine Verbindung zwischen der Anwendung und einer Datenbank her und erstellen ein Entity Data Model  
  
1.  Öffnen Sie ein vorhandenes Projekt in Visual Studio, oder erstellen Sie ein neues Projekt.  
  
2.  Führen Sie die Schritte in der **Entity Data Model-Assistenten** eine Verbindung mit einer Datenbank, und geben Sie den Inhalt des Modells. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen einer neuen EDMX-Datei](http://msdn.microsoft.com/en-us/beb8189e-e51c-4051-839c-9902c224abf2).  
  
3.  Nach Abschluss der **Entity Data Model-Assistenten**, das Entity Data Model, die Sie erstellt haben, die in der Entity Data Model-Designer wird geöffnet und die Datenobjekte stehen nun in der **Datenquellen** Fenster.  
  
    > [!NOTE]
    >  Wenn die **Datenquellen** nicht geöffnet ist, klicken Sie auf **Datenquellen anzeigen** auf die **Daten** Menü zum Öffnen des Fensters.  
  
4.  Wenn der WPF-Designer geöffnet ist, Sie können nun ziehen Sie Elemente aus der **Datenquellen** in den Designer zum Erstellen von Steuerelementen, die mit dem Entity Data Model gebunden sind. Weitere Informationen finden Sie unter [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md).  
  
     Wenn der Windows Forms-Designer geöffnet ist, Sie können keine Elemente ziehen, von der **Datenquellen** in den Designer. Zum Erstellen von an das Entity Data Model gebundenen Steuerelementen erstellen Sie das Projekt, fügen Sie eine neue auf dem Entity Data Model basierte Objektdatenquelle hinzu und ziehen anschließend die Objekte in den Designer.  
  
##  <a name="CreatingDataConnection"></a> Erstellen einer neuen Datenbankverbindung  
 Bei Verwendung der **Assistenten zur Datenquellenkonfiguration**oder **Entity Data Model-Assistenten**, geben Sie eine Verbindung mit der Datenbank, die Sie verwenden möchten. Wenn Sie noch keine Verbindung zur Datenbank hergestellt haben, führen Sie die folgenden Schritte aus, um die Verbindung zu herzustellen.  
  
 Diesen Anweisungen wird vorausgesetzt, Sie haben bereits begonnen der **Assistenten zur Datenquellenkonfiguration** oder **Entity Data Model-Assistenten** Siehe [eine Verbindung mit Datenbank herstellen, und Erstellen eines Datasets ](#dataset) und [eine Verbindung mit Datenbank herstellen, und erstellen ein Entity Data Model](#edm).  
  
#### <a name="to-create-a-new-database-connection"></a>So erstellen Sie eine Datenbankverbindung  
  
1.  Auf der **wählen Sie Ihre Datenverbindung** auf der Seite die **Assistenten zur Datenquellenkonfiguration** oder **Entity Data Model-Assistenten**, klicken Sie auf **neue Verbindung**.  
  
     Eine der folgenden Aktionen wird ausgeführt:  
  
    -   Wenn Sie bereits eine Datenverbindung in Visual Studio erstellt haben die **Verbindung hinzufügen** Dialogfeld wird geöffnet.  
  
    -   Wenn dies die erste Datenverbindung ist, Sie haben in Visual Studio erstellt, die **Datenquelle auswählen** Dialogfeld wird angezeigt. Wählen Sie den Typ der Datenbank, die Sie verwenden möchten, Herstellen einer Verbindung mit, und klicken Sie dann auf **OK** zum Anzeigen der **Verbindung hinzufügen** Dialogfeld.  
  
2.  In der **Verbindung hinzufügen** Dialogfeld Geben Sie die angeforderte Informationen. Die **Verbindung hinzufügen** Dialogfeld unterscheidet sich für jeden Typ des Datenanbieters.  
  
    > [!NOTE]
    >  Wenn die ausgewählte **Datenquelle** in die **Verbindung hinzufügen** Dialogfeld ist nicht der Datenquelle, die Sie möchten eine Verbindung herstellen möchten, klicken Sie auf **Änderung** zu öffnen der **Change Data Quelle** Dialogfeld ein, und wählen Sie dann auf eine andere Datenquelle.  
  
3.  In der **Verbindung hinzufügen** Dialogfeld klicken Sie auf **OK**.  
  
     Sie zurückkehren, um die **wählen Sie Ihre Datenverbindung** auf der Seite die **Assistenten zur Datenquellenkonfiguration** oder **Entity Data Model-Assistenten**.  
  
4.  Auf der **wählen Sie Ihre Datenverbindung** Seite, stellen Sie sicher, dass die neue Datenverbindung ausgewählt ist, und klicken Sie dann auf **Weiter**.  
  
5.  Führen Sie die verbleibenden Schritte der **Assistenten zur Datenquellenkonfiguration** oder **Entity Data Model-Assistenten**.  
  
## <a name="net-framework-security"></a>.NET Framework-Sicherheit  
 Das Speichern vertraulicher Informationen (z. B. ein Kennwort) kann sich auf die Sicherheit der Anwendung auswirken. Der Zugriff auf eine Datenbank lässt sich mithilfe der Windows-Authentifizierung (wird auch als integrierte Sicherheit bezeichnet) sicherer steuern. Weitere Informationen finden Sie unter [Protecting Connection Information (Schützen von Verbindungsinformationen)](http://msdn.microsoft.com/library/1471f580-bcd4-4046-bdaf-d2541ecda2f4).  
  
## <a name="see-also"></a>Siehe auch  
 [Neue Datenquelle hinzufügen](../data-tools/add-new-data-sources.md)   
 [Exemplarische Vorgehensweisen für Daten](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Herstellen einer Verbindung mit Daten in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Aufbauen der Verbindung zu einer Datenquelle](http://msdn.microsoft.com/library/9abc3f92-1be3-4e1a-b360-762dc689650e)
---
title: Erstellen von Datenanwendungen | Microsoft-Dokumentation
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
- data access [Visual Studio], creating applications
- applications [Visual Studio], data
- data [Visual Studio]
- data [Visual Studio], creating applications
ms.assetid: ab334d5f-4f49-4346-bce0-3325d6130b3e
caps.latest.revision: 41
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 4e5354d167dd6d3a1bef9beeb3dcaaaf24871bab
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49291309"
---
# <a name="creating-data-applications"></a>Erstellen von Datenanwendungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio stellt viele Entwurfszeittools bereit, um Ihnen die Erstellung von Anwendungen für Datenzugriffe zu ermöglichen. Diese Einführung bietet eine Übersicht über die grundlegenden Prozesse beim Erstellen solcher Datenanwendungen. Es werden keine Details aufgeführt, da diese Übersicht lediglich als allgemeine Informationsquelle und Ausgangspunkt für die zahlreichen weiteren Themen dienen soll, die mit der Erstellung einer Datenanwendung verknüpft sind.  
  
 Wenn Sie in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Anwendungen entwickeln, die auf Daten zugreifen, sind verschiedene Anforderungen zu beachten. Manchmal sollen die Daten nur auf einem Formular angezeigt werden, manchmal müssen Sie Möglichkeiten finden, Informationen mit anderen Anwendungen oder Prozessen auszutauschen.  
  
 Unabhängig davon, wozu Sie die Daten verwenden möchten, müssen Sie bestimmte grundlegende Konzepte kennen. Einige Details der Datenverarbeitung müssen Sie möglicherweise nie lernen. Beispielsweise müssen Sie eventuell nie eine Datenbank programmgesteuert erstellen. Dennoch ist es sehr sinnvoll, die grundlegenden Datenkonzepte sowie die Datentools (Assistenten und Designer) zu kennen, die in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zur Verfügung stehen.  
  
 Eine typische Datenanwendung verwendet die meisten der im folgenden Diagramm dargestellten Prozesse:  
  
 ![Grafik zum Datenzyklus](../data-tools/media/datacyclegraphicinfo.gif "Datacyclegraphicinfo")  
Der Datenzyklus  
  
 Orientieren Sie sich beim Erstellen der Anwendung an der Aufgabe, die damit ausgeführt werden soll. Wählen Sie mithilfe der folgenden Abschnitte die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Tools und -Objekte aus, die Ihnen zur Verfügung stehen.  
  
> [!NOTE]
>  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] stellt Assistenten bereit, um mehrere der im vorherigen Diagramm gezeigten Prozesse zu vereinfachen. Z. B. Ausführung der **Assistenten zur Datenquellenkonfiguration** enthält Ihre Anwendung genügend Informationen zum Verbinden mit Daten, erstellen ein typisiertes Dataset zum Empfangen von Daten und die Daten in Ihrer Anwendung einzubinden.  
  
 Schnell anzeigen, wie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] hilft Ihnen bei der Entwicklung von Data-Anwendungen finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer einfachen Datenanwendung](http://msdn.microsoft.com/library/c5d0968c-d86f-4ae9-a2e1-871f208a3bb3).  
  
## <a name="connecting-to-data"></a>Herstellen von Datenverbindungen  
 Damit Daten in Ihre Anwendung eingebunden (und Änderungen wieder an die Datenquelle übertragen) werden können, muss eine bidirektionale Kommunikation eingerichtet werden. Diese bidirektionale Kommunikation wird in der Regel von Objekten im Datenmodell behandelt.  
  
 Beispielsweise verbindet ein `TableAdapter` Anwendungen, die Datasets verwenden, mit einer Datenbank, und ein <xref:System.Data.Objects.ObjectContext> verbindet Entitäten im Entity Framework mit einer Datenbank. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] verfügt über mehrere Tools für die Erstellung von Verbindungen, die von der Anwendung verwendet werden können. Weitere Informationen zum Herstellen einer Verbindung Ihrer Anwendung und Daten finden Sie unter [herstellen von Datenverbindungen in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md).  
  
 Um zu erfahren, wie Sie die Datasets verwenden, um Ihre Anwendung mit Daten in einer Datenbank verbinden, finden Sie unter [Exemplarische Vorgehensweise: Verbinden mit Daten in einer Datenbank (Windows Forms)](http://msdn.microsoft.com/library/02d39aa6-8993-4602-be13-a13536af3d1c).  
  
## <a name="preparing-your-application-to-receive-data"></a>Vorbereiten der Anwendung auf den Empfang von Daten  
 In Anwendungen mit einem nicht verbundenen Datenmodell müssen Sie die Daten temporär in der Anwendung speichern, solange damit gearbeitet wird. Visual Studio verfügt über Tools, die Ihnen bei der Erstellung von Objekten helfen, mit denen Daten vorübergehend in einer Anwendung gespeichert werden können: Datasets, Entitäten und [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]-Objekte.  
  
> [!NOTE]
>  Eine Anwendung, die ein nicht verbundenes Datenmodell verwendet, stellt normalerweise eine Verbindung mit einer Datenbank her, führt eine Abfrage durch, mit der Daten in die Anwendung eingebunden werden, und bearbeitet die Daten anschließend offline, bevor erneut eine Verbindung mit der Datenbank hergestellt und die Datenbank aktualisiert wird.  
  
 Weitere Informationen zum Erstellen typisierter Datasets in Ihrer Anwendung finden Sie unter [Vorbereiten der Anwendung zum Empfangen von Daten](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad). Weitere Informationen zum Verwenden von Datasets in n-Tier-Anwendungen finden Sie unter [Trennen von Datasets und TableAdapters in verschiedene Projekte](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md).  
  
 Informationen zum Erstellen eines Datasets, die Schritte unter [Exemplarische Vorgehensweise: Erstellen eines Datasets mit Dataset-Designer](../data-tools/walkthrough-creating-a-dataset-with-the-dataset-designer.md).  
  
 Informationen zum Erstellen [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] Objekte, die Schritte unter [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen (O / R-Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233).  
  
## <a name="fetching-data-into-your-application"></a>Abrufen von Daten für die Anwendung  
 Unabhängig davon, ob Ihre Anwendung ein nicht verbundenes Datenmodell verwendet, müssen Sie in der Lage sein, Daten in die Anwendung einzubringen. Dazu führen Sie in einer Datenbank Abfragen oder gespeicherte Prozeduren aus. Anwendungen, die Daten in Datasets speichern führen Abfragen und gespeicherte Prozeduren mit `TableAdapter`s, während Anwendungen, die Daten in Entitäten zu speichern, Abfragen mit ausführen [LINQ to Entities](http://msdn.microsoft.com/library/641f9b68-9046-47a1-abb0-1c8eaeda0e2d) oder durch das Verbinden von Entitäten direkt mit gespeicherten Prozeduren. Weitere Informationen zum Erstellen und Bearbeiten von Abfragen mit TableAdapters finden Sie unter [Vorgehensweise: Erstellen von TableAdapter-Abfragen](../data-tools/how-to-create-tableadapter-queries.md) und [Vorgehensweise: Bearbeiten von TableAdapter-Abfragen](../data-tools/how-to-edit-tableadapter-queries.md).  
  
 Weitere Informationen zum Laden von Daten in Datasets sowie zum Ausführen von Abfragen und gespeicherte Prozeduren finden Sie unter [Abrufen von Daten in Ihrer Anwendung](../data-tools/fetching-data-into-your-application.md).  
  
 Informationen zum Laden von Daten in ein Dataset, die Schritte unter [Exemplarische Vorgehensweise: Anzeigen von Daten in einem Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md) und überprüfen Sie den Code im Ereignishandler Laden von Formularen.  
  
 Informationen zum Laden von Daten in [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] Objekte, die Schritte unter [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen (O / R-Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233).  
  
 Weitere Informationen zum Erstellen und Ausführen einer SQL-Abfrage, finden Sie unter [Vorgehensweise: Erstellen und Ausführen einer SQL-Anweisung, dass Zeilen gibt](http://msdn.microsoft.com/library/14637fc5-d42a-4cca-97ac-54c181ec3eed).  
  
 Gewusst wie: Ausführen einer gespeicherten Prozedur finden Sie unter [wie: Ausführen einer gespeicherten Prozedur, gibt Zeilen](http://msdn.microsoft.com/library/db3d7021-d3ef-4db8-b12a-b6146570355d).  
  
## <a name="displaying-data-on-forms"></a>Anzeigen von Daten in Formularen  
 Nach der Einbindung von Daten in die Anwendung erscheinen diese in der Regel in einem Formular, damit Benutzer sie anzeigen oder ändern können. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Stellt die [Fensters "Datenquellen"](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992), in dem Sie Elemente ziehen können, auf die Formulare zum automatischen Erstellen von datengebundenen Steuerelementen, die Daten anzeigen. Weitere Informationen zu datenbindungen und Anzeigen von Daten für Benutzer finden Sie unter [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
 Um zu erfahren, wie Sie Daten für Benutzer anzuzeigen, die Schritte in den folgenden exemplarischen Vorgehensweisen (Achten Sie insbesondere auf das Ziehen von Elementen aus der **Datenquellen** Fenster):  
  
-   [Exemplarische Vorgehensweise: Anzeigen von Daten in einem Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md).  
  
-   [Binden von WPF-Steuerelementen an einen WCF-Datendienst](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)  
  
-   [Exemplarische Vorgehensweise: Binden von Silverlight-Steuerelemente an einen WCF-Datendienst](http://msdn.microsoft.com/library/f3f08661-7d91-4185-8ed6-912d524d4c6b)  
  
## <a name="editing-data-in-your-application"></a>Bearbeiten von Daten in der Anwendung  
 Nachdem den Benutzern die Daten angezeigt wurden, werden diese die Daten wahrscheinlich ändern, indem sie neue Datensätze hinzufügen und Datensätze bearbeiten sowie löschen. Anschließend übertragen sie die Daten wieder zur Datenbank.  
  
 Weitere Informationen zum Arbeiten mit den Daten, die in das Dataset geladen wird, finden Sie unter [Bearbeiten von Daten in der Anwendung](../data-tools/editing-data-in-your-application.md).  
  
## <a name="validating-data"></a>Überprüfen von Daten  
 Wenn Sie Daten ändern, möchten Sie die Änderungen normalerweise überprüfen, bevor Sie die Werte wieder in das Dataset bzw. in die Datenbank übertragen lassen. *Überprüfung* ist der Name des Prozesses für Sie überprüft haben, dass diese neuen Werte für die Anforderungen Ihrer Anwendung zulässig sind. Zum Überprüfen sich ändernder Werte können Sie der Anwendung Logik hinzufügen. Visual Studio verfügt über Tools, die Sie beim Hinzufügen von Code unterstützen, mit dessen Hilfe Daten bei Spalten- und Zeilenänderungen überprüft werden. Weitere Informationen finden Sie unter [Validieren von Daten](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e).  
  
 Gewusst wie: Hinzufügen der datenvalidierung zu Ihrer Anwendung finden Sie unter [Exemplarische Vorgehensweise: Hinzufügen einer Validierung zu einem Dataset](http://msdn.microsoft.com/library/09351fab-d670-45e3-b53a-a944eff717e7).  
  
 Weitere Informationen zum Hinzufügen von Validierung zu einem Dataset, das in eine n-schichtige Anwendung aufgeteilt ist, finden Sie unter [Hinzufügen von Validierungen zu einem n-Tier-Dataset](../data-tools/add-validation-to-an-n-tier-dataset.md).  
  
## <a name="saving-data"></a>Speichern von Daten  
 Nachdem Sie an Ihrer Anwendung Änderungen vorgenommen und diese Änderungen validiert haben, sollen die Änderungen normalerweise in die Datenbank übertragen werden. In Anwendungen, die Daten in DataSets speichern, werden Daten in der Regel mithilfe eines TableAdapterManager gespeichert. Weitere Informationen finden Sie unter [Übersicht über TableAdapterManager](http://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650). Entity Framework-Anwendungen verwenden die <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> Methode zum Speichern von Daten.  
  
 Weitere Informationen zum Übertragen aktualisierter Daten in einer Datenbank finden Sie unter [Speichern von Daten](../data-tools/saving-data.md).  
  
 Informationen zum Senden von aktualisierter Daten aus einem Dataset mit einer Datenbank, die Schritte unter [Exemplarische Vorgehensweise: Speichern von Daten aus verknüpften Datentabellen (hierarchische Aktualisierung)](http://msdn.microsoft.com/library/50601bd7-a488-480c-9910-3c6570fa3a1b).  
  
## <a name="related-topics"></a>Verwandte Themen  
 [Übersicht über Datenanwendungen in Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)  
 Enthält Links zu Themen, in denen erörtert wird, wie Anwendungen, die mit Daten arbeiten, erstellt werden.  
  
 [Herstellen von Datenverbindungen in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)  
 Enthält Links zu Themen zur Verwendung von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zum Verbinden der Anwendung mit Daten und Erstellen von Datenquellen für Ihre Anwendungen.  
  
 [Vorbereiten der Anwendung zum Empfangen von Daten](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)  
 Enthält Links zu Themen, in denen erläutert wird, wie mit Datenmodellen in der Anwendung gearbeitet wird, einschließlich Datasets und Entity Data Models.  
  
 [Abrufen von Daten für die Anwendung](../data-tools/fetching-data-into-your-application.md)  
 Enthält Links zu Themen, in denen beschrieben wird, wie Daten in die Anwendung geladen werden.  
  
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)  
 Enthält Links zu Themen, in denen erläutert wird, wie Windows Forms-Steuerelemente, WPF-Steuerelemente und Silverlight-Steuerelemente an Datenquellen gebunden werden.  
  
 [Bearbeiten von Daten in der Anwendung](../data-tools/editing-data-in-your-application.md)  
 Enthält Links zu Themen, in denen beschrieben wird, wie Daten in der Anwendung geändert werden.  
  
 [Überprüfen von Daten](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)  
 Enthält Links zu Themen, in denen beschrieben wird, wie Datenänderungen eine Validierung hinzugefügt wird.  
  
 [Speichern von Daten](../data-tools/saving-data.md)  
 Enthält Links zu Themen, in denen erläutert wird, wie aktualisierte Daten von der Anwendung an eine Datenbank gesendet werden, oder wie die Daten in anderen Formaten wie z. B. XML gespeichert werden können.  
  
 [Tools zum Arbeiten mit Datenquellen in Visual Studio](http://msdn.microsoft.com/library/1e584c75-900a-49a0-a82a-d19172ef2eb3)  
 Enthält Links zu Themen über Tools, die Sie verwenden können, wie z. B. arbeiten mit Datenquellen in Visual Studio die **Datenquellen** Fenster und der ADO.NET Entity Data Model-Designer.
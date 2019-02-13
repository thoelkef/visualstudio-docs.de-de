---
title: Hinzufügen neuer Datenquellen
ms.date: 11/21/2018
ms.topic: conceptual
f1_keywords:
- vs.datasource.datasourcefieldspicker
helpviewer_keywords:
- data [Visual Studio], data sources
- data sources
ms.assetid: ed28c625-bb89-4037-bfde-cfa435d182a2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 05a07fc3cb72f923d28ff907c9aec69620cbd40d
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55955803"
---
# <a name="add-new-data-sources"></a>Hinzufügen neuer Datenquellen

Im Kontext des .NET Data-Tools in Visual Studio den Begriff *Datenquelle* bezieht sich auf .NET-Objekte, die eine Verbindung mit einem Datenspeicher herstellen und die Daten an eine .NET-Anwendung zur Verfügung zu stellen. Die Visual Studio-Designer können die Ausgabe von der Datenquelle, um die Codebausteine zu generieren, die die Daten zu Forms gebunden wird, wenn Drag & drop-Datenbankobjekte aus nutzen die **Datenquellen** Fenster. Diese Art von Datenquelle kann sein:

- Eine Klasse in einem Entity Framework-Datenmodell, das eine Art der Datenbank zugeordnet ist.

- Ein Dataset, das eine Art der Datenbank zugeordnet ist.

- Eine Klasse, die einen Netzwerkdienst, wie z. B. ein Windows Communication Foundation (WCF) Data-Dienst oder einen REST-Dienst darstellt.

- Eine Klasse, die SharePoint-Dienst darstellt.

- Eine Klasse oder eine Auflistung in der Projektmappe.

> [!NOTE]
> Wenn Sie nicht über die Datenbindung Features nutzen, gilt Datasets, die Entity Framework, LINQ to SQL, WCF, oder die SharePoint, das Konzept einer "Datenquelle" nicht. Einfach direkt an die Datenbank mithilfe von die SQLCommand-Objekte eine Verbindung herstellen Sie, und kommunizieren Sie direkt mit der Datenbank.

Sie erstellen und Bearbeiten von Datenquellen mithilfe der **Assistenten zur Datenquellenkonfiguration** in einer Windows Forms oder Windows Presentation Foundation-Anwendung. Erstellen Sie zunächst die Entitätsklassen für Entity Framework, und starten Sie den Assistenten dazu **Projekt** > **neue Datenquelle hinzufügen** (weiter unten in diesem Artikel ausführlicher beschrieben).

![Assistent zum Konfigurieren von Datenquellen](../data-tools/media/data-source-configuration-wizard.png)

## <a name="data-sources-window"></a>Datenquellenfenster

Nachdem Sie eine Datenquelle erstellen, wird Sie der **Datenquellen** Toolfenster.

> [!TIP]
> Zum Öffnen der **Datenquellen** , stellen Sie sicher, dass das Projekt geöffnet ist, und drücken Sie dann die **UMSCHALT**+**Alt**+**D**oder **Ansicht** > **Other Windows** > **Datenquellen**.

Ziehen Sie eine Datenquelle aus der **Datenquellen** Fenster auf eine Formularentwurfsoberfläche oder Steuerelement. Dies bewirkt, dass Codebausteine generiert werden, die die Daten aus dem Datenspeicher wird angezeigt.

Die folgende Abbildung zeigt ein Dataset, das auf ein Windows-Formular gelöscht wurde. Bei Auswahl von **F5** auf die Anwendung die Daten aus der zugrunde liegenden Datenbank wird in den Steuerelementen des Formulars angezeigt.

![Ziehen Sie von Datenquellenvorgang](../data-tools/media/raddata-data-source-drag-operation.png)

## <a name="data-source-for-a-database-or-a-database-file"></a>Datenquelle für eine Datenbank oder Datenbankdatei

Sie können ein Dataset oder ein Entity Framework-Datenmodell als Datenquelle für eine Datenbank oder Datenbankdatei verwenden erstellen.

### <a name="dataset"></a>DataSet

Um ein Dataset als Datenquelle zu erstellen, führen Sie die **Assistenten zur Datenquellenkonfiguration** dazu **Projekt** > **neue Datenquelle hinzufügen**. Wählen Sie die **Datenbank** Datenquelle geben, und führen Sie die aufforderungen, um entweder eine Verbindung mit neuen oder vorhandenen Datenbank oder einer Datenbankdatei angeben.

### <a name="entity-classes"></a>Entitätsklassen

Um ein Entity Framework-Modell als Datenquelle zu erstellen:

1. Führen Sie die **Entity Data Model-Assistenten** um Entitätsklassen zu erstellen. Wählen Sie **Projekt** > **neues Element hinzufügen** > **ADO.NET Entity Data Model**.

   ![Neues Projektelement für Entity Framework-Modell](../data-tools/media/raddata-new-entity-framework-model-project-item.png)

1. Wählen Sie die Methode, der Sie das Modell, indem Sie generieren möchten.

   ![Entity Data Model-Assistent](../data-tools/media/raddata-entity-data-model-wizard.png)

1. Fügen Sie das Modell als Datenquelle hinzu. Die generierten Klassen angezeigt, der **Assistenten zur Datenquellenkonfiguration** bei der Auswahl der **Objekte** Kategorie.

   ![Assistenten zur Datenquellenkonfiguration mit Entitätsklassen](../data-tools/media/raddata-data-source-configuration-wizard-with-entity-classes.png)

## <a name="data-source-for-a-service"></a>Datenquelle für einen Dienst

Führen Sie zum Erstellen einer Datenquelle von einem Dienst die **Assistenten zur Datenquellenkonfiguration** , und wählen Sie die **Service** Datenquellentyp. Dies ist nur eine Verknüpfung zu der **Hinzufügen eines Dienstverweises** Dialogfeld, das Sie auch zugreifen können, mit der rechten Maustaste in das Projekt im **Projektmappen-Explorer** und auswählen **Hinzufügen eines Dienstverweises**.

Wenn Sie eine Datenquelle mit einem Dienst erstellen, fügt Visual Studio einen Dienstverweis auf das Projekt hinzu. Visual Studio erstellt auch Proxyobjekte, die den Objekten entsprechen, die der Dienst zurückgibt. Zum Beispiel wird ein Dienst, der ein Dataset zurückgibt, im Projekt als Dataset dargestellt. Ein Dienst, der einen bestimmten Typ zurückgibt, wird in dem Projekt als der zurückgegebene Typ dargestellt.

Sie können eine Datenquelle mit den folgenden Diensttypen erstellen:

- [WCF Data Services](/dotnet/framework/data/wcf/wcf-data-services-overview)

- [WCF-Dienste](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

- Webdienste

    > [!NOTE]
    > Die Elemente in der **Datenquellen** hängen von den Daten, die der Dienst zurückgibt. Einige Dienste stellen möglicherweise nicht genügend Informationen bereit, damit der **Assistent zum Konfigurieren von Datenquellen** bindbare Objekte erstellen kann. Z. B. wenn der Dienst ein nicht typisiertes Dataset zurückgibt, keine Elemente angezeigt werden der **Datenquellen** anzeigen, wenn Sie den Assistenten abzuschließen. Dies ist darauf zurückzuführen, dass nicht typisierte Datasets kein Schema bereitstellen und der Assistent daher nicht über genügend Informationen zum Erstellen der Datenquelle verfügt.

## <a name="data-source-for-an-object"></a>Datenquelle für ein Objekt

Sie können eine Datenquelle mit jedem Objekt erstellen, das mindestens eine öffentliche Eigenschaft durch Ausführen des **Assistenten zum Konfigurieren von Datenquellen** und anschließendes Auswählen des Datenquellentyps **Objekt** verfügbar macht. Alle öffentlichen Eigenschaften eines Objekts werden im Fenster **Datenquellen** angezeigt. Wenn Sie Entity Framework verwenden und ein Modell generiert haben, ist dies die, in dem Sie die Entitätsklassen finden, die die Datenquellen für Ihre Anwendung sind.

Auf der **Datenobjekte auswählen** Seite, erweitern Sie die Knoten in der Strukturansicht, um die Objekte zu suchen, die Sie binden möchten. Die Strukturansicht enthält Knoten für Ihr Projekt für Assemblys und andere Projekte, die vom Projekt verwiesen werden.

Wenn Sie möchten die Bindung an ein Objekt in eine Assembly oder ein Projekt, das nicht in der Strukturansicht angezeigt wird, klicken Sie auf **Verweis hinzufügen** und verwenden Sie die **Add Reference Dialog Box** einen Verweis auf die Assembly oder ein Projekt hinzufügen. Nachdem Sie den Verweis hinzugefügt haben, wird die Assembly oder das Projekt der Strukturansicht hinzugefügt.

> [!NOTE]
> Sie müssen das Projekt zu erstellen, das die Objekte enthält, bevor die Objekte in der Strukturansicht angezeigt werden.

> [!NOTE]
> Um Drag & Drop-Datenbindung, unterstützen Objekte, implementieren die <xref:System.ComponentModel.ITypedList> oder <xref:System.ComponentModel.IListSource> Schnittstelle muss über einen Standardkonstruktor verfügen. Andernfalls, Visual Studio das Datenquellen-Objekt kann nicht instanziiert werden, und es wird ein Fehler angezeigt, wenn Sie das Element auf die Entwurfsoberfläche ziehen.

## <a name="data-source-for-a-sharepoint-list"></a>Datenquelle für eine SharePoint-Liste

Sie können eine Datenquelle aus einer SharePoint-Liste erstellen, indem Sie den **Assistenten zum Konfigurieren von Datenquellen** ausführen und den Datenquellentyp **SharePoint** auswählen. SharePoint macht Daten über WCF Data Services, damit erstellen eine SharePoint-Datenquelle erstellen eine Datenquelle mit einem Dienst identisch ist. Durch Auswahl des **SharePoint**-Elements im **Assistenten zum Konfigurieren von Datenquellen** wird das Dialogfeld **Dienstverweis hinzufügen** geöffnet, in dem Sie durch Zeigen auf den SharePoint-Server eine Verbindung mit dem SharePoint-Datendienst herstellen. Dies erfordert das SharePoint SDK.

## <a name="see-also"></a>Siehe auch

- [Visual Studio-Datentools für .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
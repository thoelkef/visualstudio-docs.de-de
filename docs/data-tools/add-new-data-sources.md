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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 555d32eb295e944060d2efe0b843e9d157b7c675
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301206"
---
# <a name="add-new-data-sources"></a>Hinzufügen neuer Datenquellen

Im Kontext von .NET-Datentools in Visual Studio bezieht sich der Begriff *Datenquelle* auf .NET-Objekte, die eine Verbindung zu einem Datenspeicher herstellen und die Daten für eine .NET-Anwendung verfügbar machen. Die Visual Studio-Designer können die Ausgabe der Datenquelle verwenden, um den Boilerplate-Code zu generieren, der die Daten an Formulare bindet, wenn Sie Datenbankobjekte aus dem Fenster **Datenquellen** ziehen und ablegen. Diese Art von Datenquelle kann sein:

- Eine Klasse in einem Entity Framework-Modell, die einer Art Datenbank zugeordnet ist.

- Ein Dataset, das einer Art Datenbank zugeordnet ist.

- Eine Klasse, die einen Netzwerkdienst darstellt, z. B. einen WCF-Datendienst (Windows Communication Foundation) oder einen REST-Dienst.

- Eine Klasse, die einen SharePoint-Dienst darstellt.

- Eine Klasse oder Auflistung in Ihrer Lösung.

> [!NOTE]
> Wenn Sie keine Datenbindungsfeatures, Datasets, Entity Framework, LINQ zu SQL, WCF oder SharePoint verwenden, gilt das Konzept einer "Datenquelle" nicht. Stellen Sie einfach eine direkte Verbindung mit der Datenbank her, indem Sie die SQLCommand-Objekte verwenden, und kommunizieren Sie direkt mit der Datenbank.

Sie erstellen und bearbeiten Datenquellen mithilfe des **Datenquellenkonfigurations-Assistenten** in einer Windows Forms- oder Windows Presentation Foundation-Anwendung. Erstellen Sie für Entity Framework zuerst Ihre Entitätsklassen, und starten Sie dann den Assistenten, indem Sie **Project** > **Add New Data Source** auswählen (weiter unten in diesem Artikel ausführlicher beschrieben).

![Assistent zum Konfigurieren von Datenquellen](../data-tools/media/data-source-configuration-wizard.png)

## <a name="data-sources-window"></a>Datenquellenfenster

Nachdem Sie eine Datenquelle erstellt haben, wird sie im Werkzeugfenster **Datenquellen** angezeigt.

> [!TIP]
> Um das Fenster **Datenquellen** zu öffnen, stellen Sie sicher, dass das Projekt geöffnet ist, und drücken Sie dann **Umschalthöhen**+**Alt**+**D,** oder wählen Sie Andere**Windows-Datenquellen****Other Windows** >  **anzeigen** > aus.

Sie können eine Datenquelle aus dem Fenster **Datenquellen** auf eine Formularentwurfsoberfläche oder ein Steuerelement ziehen. Dadurch wird Code codeplate generiert, der die Daten aus dem Datenspeicher anzeigt.

Die folgende Abbildung zeigt ein Dataset, das in einem Windows-Formular abgelegt wurde. Wenn Sie **F5** für die Anwendung auswählen, werden die Daten aus der zugrunde liegenden Datenbank in den Steuerelementen des Formulars angezeigt.

![Data Source-Drag-Vorgang](../data-tools/media/raddata-data-source-drag-operation.png)

## <a name="data-source-for-a-database-or-a-database-file"></a>Datenquelle für eine Datenbank oder datenbankdatei

Sie können ein Dataset oder ein Entity Framework-Modell erstellen, um es als Datenquelle für eine Datenbank oder Datenbankdatei zu verwenden.

### <a name="dataset"></a>Dataset

Um ein Dataset als Datenquelle zu erstellen, führen Sie den **Datenquellenkonfigurations-Assistenten aus,** indem Sie **Project** > **Add New Data Source**auswählen. Wählen **Database** Sie den Datenbank-Datenquellentyp aus, und folgen Sie den Anweisungen, um entweder eine neue oder vorhandene Datenbankverbindung oder eine Datenbankdatei anzugeben.

### <a name="entity-classes"></a>Entitätsklassen

So erstellen Sie ein Entity Framework-Modell als Datenquelle:

1. Führen Sie den **Entitätsdatenmodell-Assistenten** aus, um die Entitätsklassen zu erstellen. Wählen Sie **Projekt** > **Neues Element** > **hinzufügen ADO.NET Entitätsdatenmodell**.

   ![Neues Entity Framework-Modellprojektelement](../data-tools/media/raddata-new-entity-framework-model-project-item.png)

1. Wählen Sie die Methode aus, nach der Sie das Modell generieren möchten.

   ![Entity Data Model-Assistent](../data-tools/media/raddata-entity-data-model-wizard.png)

1. Fügen Sie das Modell als Datenquelle hinzu. Die generierten Klassen werden im **Datenquellenkonfigurations-Assistenten** angezeigt, wenn Sie die Kategorie **Objekte** auswählen.

   ![Datenquellenkonfigurations-Assistent mit Entitätsklassen](../data-tools/media/raddata-data-source-configuration-wizard-with-entity-classes.png)

## <a name="data-source-for-a-service"></a>Datenquelle für einen Dienst

Um eine Datenquelle aus einem Dienst zu erstellen, führen Sie den **Datenquellenkonfigurations-Assistenten** aus, und wählen Sie den **Dienstdatenquelltyp** aus. Dies ist nur eine Verknüpfung zum Dialogfeld **Dienstreferenz hinzufügen,** auf das Sie auch zugreifen können, indem Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt klicken und **Servicereferenz hinzufügen**auswählen.

Wenn Sie eine Datenquelle mit einem Dienst erstellen, fügt Visual Studio einen Dienstverweis auf das Projekt hinzu. Visual Studio erstellt auch Proxyobjekte, die den vom Dienst zurückgegebenen Objekten entsprechen. Zum Beispiel wird ein Dienst, der ein Dataset zurückgibt, im Projekt als Dataset dargestellt. Ein Dienst, der einen bestimmten Typ zurückgibt, wird in dem Projekt als der zurückgegebene Typ dargestellt.

Sie können eine Datenquelle mit den folgenden Diensttypen erstellen:

- [WCF-Datendienste](/dotnet/framework/data/wcf/wcf-data-services-overview)

- [WCF-Dienste](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

- WEB SERVICES

    > [!NOTE]
    > Die Elemente, die im Fenster **Datenquellen** angezeigt werden, sind von den Daten abhängig, die der Dienst zurückgibt. Einige Dienste stellen möglicherweise nicht genügend Informationen bereit, damit der **Assistent zum Konfigurieren von Datenquellen** bindbare Objekte erstellen kann. Wenn der Dienst beispielsweise ein nicht typisiertes Dataset zurückgibt, werden beim Abschließen des Assistenten keine Elemente im Fenster **Datenquellen** angezeigt. Dies ist darauf zurückzuführen, dass nicht typisierte Datasets kein Schema bereitstellen und der Assistent daher nicht über genügend Informationen zum Erstellen der Datenquelle verfügt.

## <a name="data-source-for-an-object"></a>Datenquelle für ein Objekt

Sie können eine Datenquelle mit jedem Objekt erstellen, das mindestens eine öffentliche Eigenschaft durch Ausführen des **Assistenten zum Konfigurieren von Datenquellen** und anschließendes Auswählen des Datenquellentyps **Objekt** verfügbar macht. Alle öffentlichen Eigenschaften eines Objekts werden im Fenster **Datenquellen** angezeigt. Wenn Sie Entity Framework verwenden und ein Modell generiert haben, finden Sie hier die Entitätsklassen, die die Datenquellen für Ihre Anwendung sind.

Erweitern Sie auf der Seite **Datenobjekte** auswählen die Knoten in der Strukturansicht, um die Objekte zu suchen, an die Sie eine Bindung binden möchten. Die Strukturansicht enthält Knoten für Ihr Projekt und für Assemblys und andere Projekte, auf die das Projekt verweist.

Wenn Sie eine Bindung an ein Objekt in einer Baugruppe oder einem Projekt binden möchten, das nicht in der Strukturansicht angezeigt wird, klicken Sie auf **Referenz hinzufügen,** und verwenden Sie das **Dialogfeld Referenz** hinzufügen, um einen Verweis auf die Baugruppe oder das Projekt hinzuzufügen. Nachdem Sie den Verweis hinzugefügt haben, wird die Baugruppe oder das Projekt der Strukturansicht hinzugefügt.

> [!NOTE]
> Möglicherweise müssen Sie das Projekt erstellen, das Ihre Objekte enthält, bevor die Objekte in der Strukturansicht angezeigt werden.

> [!NOTE]
> Um die Drag-and-Drop-Datenbindung zu <xref:System.ComponentModel.ITypedList> <xref:System.ComponentModel.IListSource> unterstützen, müssen Objekte, die die oder Schnittstelle implementieren, über einen Standardkonstruktor verfügen. Andernfalls kann Visual Studio das Datenquellenobjekt nicht instanziieren, und es wird ein Fehler angezeigt, wenn Sie das Element auf die Entwurfsoberfläche ziehen.

## <a name="data-source-for-a-sharepoint-list"></a>Datenquelle für eine SharePoint-Liste

Sie können eine Datenquelle aus einer SharePoint-Liste erstellen, indem Sie den **Assistenten zum Konfigurieren von Datenquellen** ausführen und den Datenquellentyp **SharePoint** auswählen. SharePoint macht Daten über WCF Data Services verfügbar, sodass das Erstellen einer SharePoint-Datenquelle mit dem Erstellen einer Datenquelle aus einem Dienst identisch ist. Durch Auswahl des **SharePoint**-Elements im **Assistenten zum Konfigurieren von Datenquellen** wird das Dialogfeld **Dienstverweis hinzufügen** geöffnet, in dem Sie durch Zeigen auf den SharePoint-Server eine Verbindung mit dem SharePoint-Datendienst herstellen. Dies erfordert das SharePoint SDK.

## <a name="see-also"></a>Weitere Informationen

- [Visual Studio-Datentools für .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)

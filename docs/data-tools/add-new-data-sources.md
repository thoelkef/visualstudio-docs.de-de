---
title: "Fügen Sie neue Datenquellen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.datasource.datasourcefieldspicker
helpviewer_keywords:
- data [Visual Studio], data sources
- data sources
ms.assetid: ed28c625-bb89-4037-bfde-cfa435d182a2
caps.latest.revision: "56"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 0c83367d383ab72194e5f83609b0f93d8602fdcd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="add-new-data-sources"></a>Neue Datenquellen hinzufügen
Im Kontext des .NET Data-Tools in Visual Studio den Begriff *Datenquelle* bezieht sich auf .NET-Objekten, die eine Verbindung mit einem Datenspeicher herstellen und die Daten an eine .NET-Anwendung verfügbar machen. Die Visual Studio-Designer nutzen können die Ausgabe von der Datenquelle, um den Standardcode zu generieren, die die Daten an Formulare bindet, beim Ziehen und Ablegen von Datenbankobjekte aus der **Datenquellen** Fenster. Diese Art von Datenquelle kann sein:  
  
-   Eine Klasse in einem Entity Framework-Modell, die eine Art der Datenbank zugeordnet ist.  
  
-   Ein Dataset, das eine Art der Datenbank zugeordnet ist.  
  
-   Eine Klasse, die einen Netzwerkdienst, beispielsweise einen Windows Communication Foundation (WCF) Data-Dienst oder einen REST-Dienst darstellt.  
  
-   Eine Klasse, die SharePoint-Dienst darstellt.  
  
-   Eine Klasse oder eine Auflistung in der Projektmappe.  
  
> [!NOTE]
>  Wenn Sie die Datenbindung-Funktionen nicht verwenden, gilt Datasets, Entity Framework, LINQ to SQL, WCF oder SharePoint, das Konzept der "Data Source" nicht. Nur Verbindung direkt mit der Datenbank mit den Objekten "SqlCommand" und kommunizieren direkt mit der Datenbank.  
  
 Sie erstellen und Bearbeiten von Datenquellen mithilfe der **Data Source Configuration Wizard** in einer Windows Forms- oder Windows Presentation Foundation-Anwendung. Erstellen Sie zunächst die Entitätsklassen für Entity Framework, und starten Sie den Assistenten durch auswählen **Projekt** > **neue Datenquelle hinzufügen** (ausführlicher weiter unten in diesem Artikel beschrieben).  
  
 ![Datenquellen Konfigurationsassistenten](../data-tools/media/data-source-configuration-wizard.png "Datenquellen Konfigurationsassistenten")  
  
 Nachdem Sie eine Datenquelle erstellt haben, erscheint in der **Datenquellen** Toolfenster (Umschalt + Alt + D oder **Ansicht** > **Weitere Fenster**  >  **Datenquelle**). Ziehen Sie eine Datenquelle aus der **Datenquellen** auf einem Formularentwurfsoberfläche oder Steuerelement. Dies bewirkt, dass Standardcode generiert werden – Code, der die Daten anzeigt, die im Datenspeicher für den Benutzer stammt. Die folgende Abbildung zeigt ein Dataset, das auf einem Windows Form gelöscht wurde. Wenn Sie F5 für die Anwendung ausgewählt haben, würden die Daten aus der zugrunde liegenden Datenbank in die Steuerelemente des Formulars angezeigt.  
  
 ![Datenquelle ziehen Vorgang](../data-tools/media/raddata-data-source-drag-operation.png "Raddata Datenquelle ziehen Vorgang")  
  
## <a name="data-source-for-a-database-or-a-database-file"></a>Datenquelle für eine Datenbank oder Datenbankdatei  
  
### <a name="dataset"></a>DataSet  
 Um ein Dataset als Datenquelle zu erstellen, führen Sie die **Datenquellen Konfigurations-Assistenten** (**Projekt** > **neue Datenquelle hinzufügen**), und wählen Sie die  **Datenbank** Datenquellentyp. Befolgen Sie die Anweisungen zum Angeben einer Verbindung mit neuen oder vorhandenen Datenbank oder eine Datenbankdatei.  
  
### <a name="entity-classes"></a>Entitätsklassen  
 Um eine Entity Framework-Modell als Datenquelle zu erstellen, führen Sie zuerst die **Entity Data Model-Assistenten** an die Entitätsklassen erstellt wurden (**Projekt** > **neues Element hinzufügen**  >  **ADO.NET Entity Data Model**).  
  
 ![Neues Projektelement für Entity Framework-Modell](../data-tools/media/raddata-new-entity-framework-model-project-item.png "Raddata neue Entity Framework Model-Projektelement")  
  
 Wählen Sie die Methode, die mit der Sie das Modell generieren möchten.  
  
 ![Assistent für Entity Data Model](../data-tools/media/raddata-entity-data-model-wizard.png "Raddata Entity Data Model-Assistenten")  
  
 Fügen Sie das Modell als Datenquelle. Die generierten Klassen angezeigt, der **Datenquellen Konfigurations-Assistenten** bei Auswahl der **Objekte** Kategorie.  
  
 ![Datenquellen-Assistenten mit Entitätsklassen Konfiguration](../data-tools/media/raddata-data-source-configuration-wizard-with-entity-classes.png "Raddata Datenquellen-Assistenten mit Entitätsklassen Konfiguration")  
  
## <a name="data-source-for-a-service"></a>Datenquelle für einen Dienst  
 Führen Sie zum Erstellen einer Datenquelle von einem Dienst die **Datenquellen Konfigurations-Assistenten** , und wählen Sie die **Service** Datenquellentyp. Dies ist genau genommen nur eine Verknüpfung zu den **Hinzufügen eines Dienstverweises** (Dialogfeld), die Sie auch zugreifen können, mit der rechten Maustaste das Projekt im **Projektmappen-Explorer** auswählen und **Hinzufügen eines Dienstverweises** .  
  
 Wenn Sie eine Datenquelle mit einem Dienst erstellen, fügt Visual Studio einen Dienstverweis auf das Projekt hinzu. Visual Studio erstellt auch Proxyobjekte, die den Objekten entsprechen, die der Dienst zurückgibt. Zum Beispiel wird ein Dienst, der ein Dataset zurückgibt, im Projekt als Dataset dargestellt. Ein Dienst, der einen bestimmten Typ zurückgibt, wird in dem Projekt als der zurückgegebene Typ dargestellt.  
  
 Sie können eine Datenquelle mit den folgenden Diensttypen erstellen:  
  
-   WCF Data Services. Weitere Informationen finden Sie unter [Übersicht](/dotnet/framework/data/wcf/wcf-data-services-overview).  
  
-   WCF-Dienste. Weitere Informationen finden Sie unter [Windows Communication Foundation-Dienste und WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md).  
  
-   Webdienste.  
  
    > [!NOTE]
    >  Die Elemente in der **Datenquellen** hängen von den Daten, die der Dienst zurückgibt. Einige Dienste möglicherweise nicht genügend Informationen bereit, die **Data Source Configuration Wizard** bindbare Objekte erstellen. Beispielsweise, wenn der Dienst ein nicht typisiertes Dataset zurückgibt, keine Elemente erscheinen in der **Datenquellen** Fenster, wenn Sie den Assistenten abschließen. Dies ist darauf zurückzuführen, dass nicht typisierte Datasets kein Schema bereitstellen und der Assistent daher nicht über genügend Informationen zum Erstellen der Datenquelle verfügt.  
  
## <a name="data-source-for-an-object"></a>Datenquelle für ein Objekt  
 Sie können eine Datenquelle erstellen, aller Objekte, die durch Ausführen einer oder mehreren öffentliche Eigenschaften verfügbar macht die **Datenquellen Konfigurations-Assistenten** auswählen und dann die **Objekt** Datenquellentyp. Alle öffentliche Eigenschaften eines Objekts angezeigt werden, der **Datenquellen** Fenster.   Wenn Sie Entity Framework verwenden und ein Modell generiert haben, ist dies, wo Sie die Entitätsklassen, die die Datenquellen für Ihre Anwendung finden.  
  
 Auf der **Auswählen der Datenobjekte** Seite, erweitern Sie die Knoten in der Strukturansicht, um die Objekte zu suchen, die Sie binden möchten. Die Strukturansicht enthält Knoten für das Projekt und für Assemblys und andere Projekte, die vom Projekt verwiesen werden.  
  
 Um eine Bindung an ein Objekt in eine Assembly oder ein Projekt, das nicht in der Strukturansicht angezeigt wird, klicken Sie auf **Verweis hinzufügen** und Verwenden der **hinzufügen Dialogfelds "Verweis"** So fügen Sie einen Verweis auf die Assembly oder das Projekt hinzu. Nachdem Sie den Verweis hinzugefügt haben, wird die Assembly oder das Projekt der Strukturansicht hinzugefügt.  
  
> [!NOTE]
>  Möglicherweise müssen Sie das Projekt zu erstellen, das die Objekte enthält, bevor die Objekte in der Strukturansicht angezeigt werden.  
  
> [!NOTE]
>  Drag & Drop-Datenbindung unterstützt Objekte implementiert, die <xref:System.ComponentModel.ITypedList> oder <xref:System.ComponentModel.IListSource> Schnittstelle muss über einen Standardkonstruktor verfügen. Andernfalls Visual Studio das Datenquellenobjekt kann nicht instanziiert werden, und es wird einen Fehler angezeigt, wenn Sie das Element auf die Entwurfsoberfläche ziehen.  
  
## <a name="data-source-for-a-sharepoint-list"></a>Datenquelle für eine SharePoint-Liste  
 Sie können eine Datenquelle aus einer SharePoint-Liste erstellen, durch Ausführen der **Datenquellen Konfigurations-Assistenten** und Auswählen der **SharePoint** Datenquellentyp. SharePoint macht Daten über [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)], sodass das Erstellen einer SharePoint-Datenquelle dem Erstellen einer Datenquelle von einem Dienst identisch ist. Auswählen der **SharePoint** Element der **Datenquellen Konfigurations-Assistenten** öffnet die **Hinzufügen eines Dienstverweises** Dialogfeld, in dem Sie eine Verbindung mit dem SharePoint-Datendienst herstellen Zeigen Sie auf der SharePoint-Server.  Dies erfordert das SharePoint-SDK.  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio-Datentools für .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
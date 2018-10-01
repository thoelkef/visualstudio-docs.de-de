---
title: Neue Datenquellen hinzufügen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.datasource.datasourcefieldspicker
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], data sources
- data sources
ms.assetid: ed28c625-bb89-4037-bfde-cfa435d182a2
caps.latest.revision: 60
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cb629119655327c7608025d66bb5e42d857d039d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513156"
---
# <a name="add-new-data-sources"></a>Neue Datenquelle hinzufügen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [neue Datenquellen hinzufügen](https://docs.microsoft.com/visualstudio/data-tools/add-new-data-sources).  
  
  
Im Kontext des .NET Data-Tools in Visual Studio den Begriff *Datenquelle* bezieht sich auf .NET-Objekte, die eine Verbindung mit einem Datenspeicher herstellen und die Daten an eine .NET-Anwendung verfügbar machen. Die Visual Studio-Designer können die Ausgabe von der Datenquelle, um die Codebausteine zu generieren, die die Daten zu Forms gebunden wird, wenn Drag & drop-Datenbankobjekte aus nutzen die **Datenquellen** Fenster. Diese Art von Datenquelle kann sein:  
  
-   Eine Klasse in einem Entity Framework-Datenmodell, das eine Art der Datenbank zugeordnet ist.  
  
-   Ein Dataset, das eine Art der Datenbank zugeordnet ist.  
  
-   Eine Klasse, die einen Netzwerkdienst, wie z. B. ein Windows Communication Foundation (WCF) Data-Dienst oder einen REST-Dienst darstellt.  
  
-   Eine Klasse, die SharePoint-Dienst darstellt.  
  
-   Eine Klasse oder eine Auflistung in der Projektmappe.  
  
> [!NOTE]
>  Wenn Sie keine Funktionen für die Datenbindung verwenden, gilt Datasets, die Entity Framework, LINQ to SQL, WCF, oder die SharePoint, das Konzept einer "Datenquelle" nicht. Einfach direkt an die Datenbank mithilfe von die SQLCommand-Objekte eine Verbindung herstellen Sie, und kommunizieren Sie direkt mit der Datenbank.  
  
 Sie erstellen und Bearbeiten von Datenquellen mithilfe der **Assistenten zur Datenquellenkonfiguration** in einer Windows Forms oder Windows Presentation Foundation-Anwendung. Erstellen Sie zunächst die Entitätsklassen für Entity Framework, und starten Sie den Assistenten dazu **Projekt** > **neue Datenquelle hinzufügen** (weiter unten in diesem Artikel ausführlicher beschrieben).  
  
 ![Datenquellen-Assistenten](../data-tools/media/data-source-configuration-wizard.png "Datenquellen-Assistenten")  
  
 Nachdem Sie eine Datenquelle erstellen, wird Sie der **Datenquellen** Toolfenster (Umschalt + Alt + D oder **Ansicht** > **andere Windows**  >  **Datenquelle**). Ziehen Sie eine Datenquelle aus der **Datenquellen** Fenster auf eine Formularentwurfsoberfläche oder Steuerelement. Dies bewirkt, dass Codebausteine generiert werden – Code, der die Daten anzeigt, die aus dem Datenspeicher für den Benutzer stammt. Die folgende Abbildung zeigt ein Dataset, das auf ein Windows-Formular gelöscht wurde. Wenn Sie F5 für die Anwendung ausgewählt haben, würden die Daten aus der zugrunde liegenden Datenbank in den Steuerelementen des Formulars angezeigt.  
  
 ![Datenquelle ziehen](../data-tools/media/raddata-data-source-drag-operation.png "Raddata Datenquelle ziehen")  
  
## <a name="data-source-for-a-database-or-a-database-file"></a>Datenquelle für eine Datenbank oder Datenbankdatei  
  
### <a name="dataset"></a>DataSet  
 Um ein Dataset als Datenquelle zu erstellen, führen Sie die **Assistenten zur Datenquellenkonfiguration** (**Projekt** > **Hinzufügen von neuen Daten** Quelle), und wählen Sie die  **Datenbank** Datenquellentyp. Befolgen Sie die Anweisungen zum Angeben einer Verbindung mit neuen oder vorhandenen Datenbank oder eine Datei aus.  
  
### <a name="entity-classes"></a>Entitätsklassen  
 Um ein Entity Framework-Datenmodell als Datenquelle zu erstellen, führen Sie zuerst die **Entity Data Model-Assistenten** zum Erstellen von Entitätsklassen (**Projekt** > **neues Element hinzufügen**  >  **ADO.NET Entity Data Model**).  
  
 ![Neues Projektelement für Entity Framework-Modell](../data-tools/media/raddata-new-entity-framework-model-project-item.png "Projektelement für Raddata neuen Entity Framework-Modell")  
  
 Wählen Sie die Methode, die nach der Erstellung des Modells werden sollen.  
  
 ![Assistent für Entity Data Model](../data-tools/media/raddata-entity-data-model-wizard.png "Raddata Entity Data Model-Assistenten")  
  
 Fügen Sie das Modell als Datenquelle hinzu. Die generierten Klassen angezeigt, der **Assistenten zur Datenquellenkonfiguration** bei der Auswahl der **Objekte** Kategorie.  
  
 ![Assistenten zur Datenquellenkonfiguration mit Entitätsklassen](../data-tools/media/raddata-data-source-configuration-wizard-with-entity-classes.png "Raddata Assistenten zur Datenquellenkonfiguration mit Entitätsklassen")  
  
## <a name="data-source-for-a-service"></a>Datenquelle für einen Dienst  
 Führen Sie zum Erstellen einer Datenquelle von einem Dienst die **Assistenten zur Datenquellenkonfiguration** , und wählen Sie die **Service** Datenquellentyp. Dies ist eigentlich nur eine Verknüpfung mit der **Hinzufügen eines Dienstverweises** Dialogfeld, das Sie auch zugreifen können, mit der rechten Maustaste in das Projekt im **Projektmappen-Explorer** , und wählen **Hinzufügen eines Dienstverweises** .  
  
 Wenn Sie eine Datenquelle mit einem Dienst erstellen, fügt Visual Studio einen Dienstverweis auf das Projekt hinzu. Visual Studio erstellt auch Proxyobjekte, die den Objekten entsprechen, die der Dienst zurückgibt. Zum Beispiel wird ein Dienst, der ein Dataset zurückgibt, im Projekt als Dataset dargestellt. Ein Dienst, der einen bestimmten Typ zurückgibt, wird in dem Projekt als der zurückgegebene Typ dargestellt.  
  
 Sie können eine Datenquelle mit den folgenden Diensttypen erstellen:  
  
-   WCF Data Services. Weitere Informationen finden Sie unter [Übersicht](http://msdn.microsoft.com/library/7924cf94-c9a6-4015-afc9-f5d22b1743bb).  
  
-   WCF-Datendienste. Weitere Informationen finden Sie unter [Windows Communication Foundation-Dienste und WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md).  
  
-   Webdienste.  
  
    > [!NOTE]
    >  Die Elemente in der **Datenquellen** hängen von den Daten, die der Dienst zurückgibt. Einige Dienste möglicherweise nicht genug Informationen bieten die **Assistenten zur Datenquellenkonfiguration** bindbare Objekte erstellen. Z. B. wenn der Dienst ein nicht typisiertes Dataset zurückgibt, keine Elemente angezeigt der **Datenquellen** anzeigen, wenn Sie den Assistenten abzuschließen. Dies ist darauf zurückzuführen, dass nicht typisierte Datasets kein Schema bereitstellen und der Assistent daher nicht über genügend Informationen zum Erstellen der Datenquelle verfügt.  
  
## <a name="data-source-for-an-object"></a>Datenquelle für ein Objekt  
 Sie können eine Datenquelle erstellen, über jedes Objekt, das eine oder mehrere öffentliche Eigenschaften mit macht die **Assistenten zur Datenquellenkonfiguration** auswählen und dann auf die **Objekt** Datenquellentyp. Alle öffentliche Eigenschaften eines Objekts werden angezeigt, der **Datenquellen** Fenster.   Wenn Sie Entity Framework verwenden und ein Modell generiert haben, ist dies, wo Sie die Entitätsklassen, die die Datenquellen für Ihre Anwendung finden.  
  
 Auf der **Datenobjekte auswählen** Seite, erweitern Sie die Knoten in der Strukturansicht, um die Objekte zu suchen, die Sie binden möchten. Die Strukturansicht enthält Knoten für Ihr Projekt für Assemblys und andere Projekte, die vom Projekt verwiesen werden.  
  
 Wenn Sie möchten die Bindung an ein Objekt in eine Assembly oder ein Projekt, das nicht in der Strukturansicht angezeigt wird, klicken Sie auf **Verweis hinzufügen** und verwenden Sie die **Add Reference Dialog Box** einen Verweis auf die Assembly oder ein Projekt hinzufügen. Nachdem Sie den Verweis hinzugefügt haben, wird die Assembly oder das Projekt der Strukturansicht hinzugefügt.  
  
> [!NOTE]
>  Sie müssen das Projekt zu erstellen, das die Objekte enthält, bevor die Objekte in der Strukturansicht angezeigt werden.  
  
> [!NOTE]
>  Um Drag & Drop-Datenbindung, unterstützen Objekte, implementieren die <xref:System.ComponentModel.ITypedList> oder <xref:System.ComponentModel.IListSource> Schnittstelle muss über einen Standardkonstruktor verfügen. Andernfalls, Visual Studio das Datenquellen-Objekt kann nicht instanziiert werden, und es wird eine Fehlermeldung angezeigt, wenn Sie das Element auf die Entwurfsoberfläche ziehen.  
  
## <a name="data-source-for-a-sharepoint-list"></a>Datenquelle für eine SharePoint-Liste  
 Sie können eine Datenquelle aus einer SharePoint-Liste erstellen, indem Sie Ausführung der **Assistenten zur Datenquellenkonfiguration** und Auswählen der **SharePoint** Datenquellentyp. SharePoint macht Daten über [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)], sodass das Erstellen einer SharePoint-Datenquelle ist dasselbe wie das Erstellen einer Datenquelle von einem Dienst. Auswählen der **SharePoint** Element der **Assistenten zur Datenquellenkonfiguration** öffnet die **Hinzufügen eines Dienstverweises** Dialogfeld, in dem Sie Herstellen einer Verbindung mit dem SharePoint-Datendienst indem Sie auf der SharePoint-Server zeigen.  Dies erfordert das SharePoint SDK.  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio-Datentools für .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)


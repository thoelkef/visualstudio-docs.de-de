---
title: Entwerfen eines Business Data Connectivity-Modells | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], designing a model
- Business Data Connectivity service [SharePoint development in Visual Studio], designing a model
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d0971dc9d445c7a492d934c0c2bdc9b47de92028
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2018
ms.locfileid: "34766063"
---
# <a name="design-a-business-data-connectivity-model"></a>Entwerfen eines Business Data Connectivity-Modells
  Entwickeln Sie ein Modell für den Business Data Connectivity (BDC)-Dienst, indem Sie eine Modelldatei Entitäten und Methoden hinzufügen. Eine Entität beschreibt eine Auflistung von Datenfeldern. Eine Entität kann z. B. eine Tabelle in einer Datenbank darstellen. Eine Methode führt eine Aufgabe, z. B. hinzufügen, löschen oder Aktualisieren von Daten, die durch die Entitäten dargestellt. Weitere Informationen finden Sie unter [Integrieren von Geschäftsdaten in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md).  
  
## <a name="add-entities"></a>Fügen Sie Entitäten hinzu
 Sie können eine Entität hinzufügen, durch Ziehen oder Kopieren einer **Entität** von Visual Studio **Toolbox** im BDC-Designer. Weitere Informationen finden Sie unter [wie: hinzufügen eine Entität zu einem Modell](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
 Definieren Sie die Felder der Entität in einer Klasse. Sie können z. B. ein Feld mit dem Namen hinzufügen `Address` auf eine `Customer` Klasse. Sie können das Projekt eine neue Klasse hinzugefügt oder verwenden eine vorhandene Klasse, die mit anderen Tools wie z. B. den Object Relational Designer (O/R-Designer) erstellt. Der Name der Entität und den Namen der Klasse, die für die Entität müssen nicht übereinstimmen. Sie beziehen sich die Klasse auf die Entität zu, wenn Sie die Methoden in Ihrem Modell definieren.  
  
## <a name="add-methods"></a>Hinzufügen von Methoden
 Der BDC-Dienst ruft Methoden in Ihrem Modell auf, wenn Benutzer anzeigen, hinzufügen, aktualisieren oder Löschen von Daten in einer Liste oder ein Webpart, das auf das Modell basiert. Sie müssen eine Methode für das Modell für jede Aufgabe hinzufügen, die der Benutzer ausführen kann. Erstellen Sie dazu einen der fünf grundlegenden Methodentypen von Methoden der **BDC-Methodendetails** Fenster. Die folgende Tabelle beschreibt die fünf grundlegenden Methoden eines BDC-Modells.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|Finder|Gibt eine Auflistung von Instanzen der Entität zurück. Wird aufgerufen, wenn der Benutzer die Liste oder das Webpart wird geöffnet. Weitere Informationen finden Sie unter [wie: Hinzufügen einer Finder-Methode](../sharepoint/how-to-add-a-finder-method.md).|  
|Spezifischer Finder|Gibt eine bestimmte Entität-Instanz zurück. Wird aufgerufen, wenn ein Benutzer die Details eines bestimmten Elements in einer Liste anzeigt. Weitere Informationen finden Sie unter [wie: Hinzufügen einer bestimmten Finder-Methode](../sharepoint/how-to-add-a-specific-finder-method.md).|  
|Creator|Fügt neue Daten an die Datenquelle einer Entität. Wird aufgerufen, wenn Benutzer wählen Sie die **neues Element** Schaltfläche auf dem Menüband eine Liste, die auf das Modell basiert. Weitere Informationen finden Sie unter [wie: Hinzufügen einer Creator-Methode](../sharepoint/how-to-add-a-creator-method.md).|  
|Updater|Ändert die Daten in einer Liste an. Wird aufgerufen, wenn Benutzer Informationen in einer Liste zu aktualisieren. Weitere Informationen finden Sie unter [wie: Hinzufügen einer Updater-Methode](../sharepoint/how-to-add-an-updater-method.md).|  
|Deleter|Entfernt Daten. Wird aufgerufen, wenn Benutzer ein Element aus der Liste löschen. Weitere Informationen finden Sie unter [wie: Hinzufügen einer Deleter-Methode](../sharepoint/how-to-add-a-deleter-method.md).|  
  
## <a name="define-method-parameters"></a>Definieren von Methodenparameter
 Wenn Sie eine Methode erstellen, fügt Visual Studio die Eingabe- und Parameter, die für den Methodentyp geeignet sind. Diese Parameter dienen nur Platzhalter. In den meisten Fällen müssen Sie die Parameter ändern, damit sie übergeben werden oder den richtigen Typ Daten zurückgeben. Standardmäßig gibt z. B. eine Finder-Methode eine Zeichenfolge an. In den meisten Fällen möchten Sie den Rückgabeparameter der Finder-Methode ändern, sodass sie eine Auflistung von Entitäten zurückgibt. Sie erreichen, die durch den Typdeskriptor des Parameters ändern. Ein Typdeskriptor ist eine Auflistung von Attributen, die den Datentyp eines Parameters beschreibt. Weitere Informationen finden Sie unter [Vorgehensweise: Definieren des Typdeskriptors eines Parameters](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
 Visual Studio ermöglicht Ihnen das Kopieren von Typdeskriptoren zwischen Parametern im Modell. Sie können z. B. einen Typdeskriptor mit dem Namen definieren `CustomerTD` für den Rückgabeparameter der `GetCustomer` Methode. Sie kopieren können die `CustomerTD` Typdeskriptor in der **BDC-Explorer**, und fügen Sie diesem Typdeskriptor für die Eingabeparameter des der `CreateCustomer` Methode. Dadurch können Sie den gleichen Typdeskriptor mehr als einmal definieren müssen.  
  
## <a name="method-instances"></a>Methodeninstanzen
 Wenn Sie eine Methode erstellen, fügt Visual Studio eine Standardinstanz-Methode hinzu. Eine Methodeninstanz ist ein Verweis auf eine Methode sowie die Standardwerte für die Parameter an. Eine einzelne Methode, die mehrere Methodeninstanzen aufweisen kann. Jede Instanz ist eine Kombination aus der Methodensignatur und einen Satz von Standardwerten. Weitere Informationen finden Sie unter [Vorgehensweise: Definieren des Typdeskriptors eines Parameters](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
 Wenn Sie das Projekt ausführen, werden Methodeninstanzen in einer Dropdownliste über die SharePoint-Liste angezeigt. Benutzer können Methodeninstanzen zum Anzeigen der Daten auswählen.  
  
 Um die Standardwerte für die Methodeninstanz hinzufügen möchten, müssen Sie das XML des Modells direkt geändert. Weitere Informationen finden Sie unter ["DefaultValue"](http://go.microsoft.com/fwlink/?LinkID=169279).  
  
## <a name="add-filter-descriptors"></a>Hinzufügen von Filterdeskriptoren
 Consumer des Modells sollten beim Abrufen von Instanzen einer Entität, die bestimmte Kriterien erfüllen. Um diese Funktionalität zu aktivieren, können Sie ein Filterdeskriptors zu einer Methode hinzufügen. Filterdeskriptoren ermöglichen Modell Consumer zum Filtern von Resultsets Methode durch die Werte an Methoden übergeben werden, bevor sie ausgeführt werden. Weitere Informationen finden Sie unter [wie: Hinzufügen von Filterparameter für Vorgänge mit Limit-Instanzen aus dem externen System](http://go.microsoft.com/fwlink/?LinkID=169267).  
  
 SharePoint bietet verschiedene Funktionen, mit die Benutzer Filterwerte angeben können. Geschäftsdaten-Webparts bieten z. B. einen Text-Feld "Filter". Benutzer können die Daten in einer Liste durch Eingabe eines Werts in das Textfeld zu beschränken. Weitere Informationen zum Hinzufügen eines Filterdeskriptors zu einer Methode finden Sie unter [wie: Hinzufügen eines Filterdeskriptors zu einer Finder-Methode](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md).  
  
### <a name="filter-descriptor-properties"></a>Filter Descriptor-Eigenschaften
 Müssen Sie den Wert der Festlegen der **Typdeskriptor zugeordnete**, **Name**, und **Typ** Eigenschaften eines Filterdeskriptors. Alle anderen Eigenschaften sind optional.  
  
 Die **Typdeskriptor zugeordnete** Eigenschaft bezieht sich die Filterdeskriptors für einen Eingabeparameter. Wenn ein Benutzer einen Filterwert angibt, übergibt der BDC-Dienst diesen Wert an die Methode mithilfe des Eingabeparameters an.  
  
 Die **Typ** Eigenschaft beschreibt das Filtern Muster, das Sie verwenden möchten. In SharePoint wirkt sich auf das Filtermuster gewählten den Text, der in der Benutzeroberfläche (UI) angezeigt wird. Z. B. für einen Vergleichsoperator Filtermuster Text **gleich** als ein Steuerelement über eine Business Data-Webpart angezeigt wird. Weitere Informationen zu jeder Filtermuster, finden Sie unter [von BDC unterstützte Filter](http://go.microsoft.com/fwlink/?LinkId=169287).  
  
 Weitere Informationen zu den Eigenschaften eines Filterdeskriptors finden Sie unter [FilterDescriptor](http://go.microsoft.com/fwlink/?LinkID=169280).  
  
### <a name="provide-default-values"></a>Angeben von Standardwerten
 In einigen Fällen kann der Benutzer einen Filterwert nicht bereitstellen. Sie können einen Standardwert bereitstellen, indem Sie einen Standardwert an die Methodeninstanz oder durch Festlegen des Standardwerts in der Code der Methode. Weitere Informationen dazu, wie Sie einen Standardwert für die Methodeninstanz hinzufügen, finden Sie unter [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282). Ein Beispiel zum Festlegen des Standardwert eines Eingabeparameters im Code der Methode finden Sie unter [wie: Hinzufügen eines Filterdeskriptors zu einer Finder-Methode](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md).  
  
## <a name="validate-the-model"></a>Überprüfen des Modells
 Sie können Ihr Modell während der Entwicklung überprüfen. Visual Studio identifiziert Probleme, die das Modell Sie verhindern können, wie erwartet verhält. Diese Probleme werden angezeigt, in der Visual Studio **Fehlerliste**.  
  
 Sie können ein Modell überprüfen, indem Sie das Kontextmenü für den BDC-Designer öffnen, und drücken Sie dann die **Validate**. Wenn das Modell keine Fehler enthält, werden sie in der **Fehlerliste**. Sie können schnell den Cursor bewegen, die an den Code, die einen Fehler enthält, indem Sie auf den Fehler in der Liste doppelklicken. Als Alternative können Sie wählen Sie die **F8** oder **UMSCHALT**+**F8** Tasten wiederholt Schritt vorwärts oder rückwärts durch die Fehler in der Liste.  
  
 Validierungsfehler können auftreten, wenn die Regeln des Modells in irgendeiner Form verletzt werden. Z. B. wenn die **"IsCollection"** von einem Typdeskriptor ist-Eigenschaftensatz auf **"true"**, aber keine untergeordneten Typdeskriptoren vorhanden sind, tritt ein Validierungsfehler angezeigt. Möglicherweise müssen Sie die finden Sie in den Regeln der ein BDC-Modell zu Fehlern zu verstehen, die in Visual Studio angezeigt werden **Fehlerliste**. Weitere Informationen zu den Regeln für ein BDC-Modell finden Sie unter [BDCMetadata Schema](http://go.microsoft.com/fwlink/?LinkID=169275).  
  
## <a name="debug-the-solution-that-contains-the-model"></a>Debuggen Sie die Lösung mit dem Modell
 Sie können den Code Debuggen, wie Sie Code in Visual Studio debuggen. Zum Debuggen von Code, legen Sie Haltepunkte im Code an einer beliebigen Stelle, und klicken Sie dann starten Sie den Debugger zu. Visual Studio öffnet die SharePoint-Website. Erstellen Sie in SharePoint eine Liste oder ein Webpart, das Ihre Geschäftsdaten verwendet. Anschließend können Sie den Code schrittweise. Weitere Informationen zum Debuggen von SharePoint-Projekte finden Sie unter [SharePoint-Lösungen zur Problembehandlung](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
 Sie können auch Code in benutzerdefinierten Assemblys Debuggen, die Sie dem Projekt hinzu. Allerdings müssen Sie zum Debuggen von Code in einer benutzerdefinierten Assembly die Assembly zum Lösungspaket hinzufügen. Weitere Informationen finden Sie unter [wie: Hinzufügen und Entfernen zusätzlicher Assemblys](../sharepoint/how-to-add-and-remove-additional-assemblies.md).  
  
 Weitere Informationen zu eine benutzerdefinierte Assembly zum Projekt hinzufügen, finden Sie unter [wie: Einfügen einer benutzerdefinierten Assembly in eine BDC-Funktion](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md).  
  
### <a name="configure-bdc-security"></a>Konfigurieren der BDC-Sicherheit
 Sie müssen möglicherweise die Sicherheitseinstellungen in SharePoint zu ändern, bevor Sie die Lösung Debuggen können. Diese Einstellungen zu ändern, öffnen Sie die Business Data Connectivity-Dienstanwendung in SharePoint 2010 Central Administration-Website. In der **Berechtigungen für den Metadatenspeicher festlegen** (Dialogfeld), fügen Sie Ihr Benutzerkonto hinzu, und wählen Sie dann eine der folgenden Optionen:  
  
|Aufgabe|Option|  
|----------|------------|  
|Zum Bereitstellen von Modellen für den BDC-Dienst.|Bearbeiten|  
|Zum Erstellen von Listen und Webparts mithilfe von externen Typen Inhalt (Entitäten) in Ihrem Modell.|In den Clients ausgewählt werden.|  
|Klicken Sie zum Erstellen, lesen, aktualisieren und Löschen von Entitätsdaten.|Ausführen|  
  
 Weitere Informationen zu diesen Einstellungen finden Sie unter [Business Data Connectivity-Dienst Management](http://go.microsoft.com/fwlink/?LinkID=178883).  
  
 Sie können auch die Sicherheitsberechtigungen für die einzelnen Modelle oder externe Inhaltstypen festlegen. Weitere Informationen zum Festlegen der Sicherheitsberechtigungen eines Modells finden Sie unter [BDC-Modell-Management](http://go.microsoft.com/fwlink/?LinkID=178884). Weitere Informationen zum Festlegen der Sicherheitsberechtigungen für eine externe Inhaltstypen finden Sie unter [Verwalten von externen Inhaltstypen](http://go.microsoft.com/fwlink/?LinkID=178885).  
  
> [!NOTE]  
>  Verwenden Sie diese Einstellungen, um eine Lösung auf dem lokalen SharePoint-Server zu debuggen. Weitere Informationen zum Konfigurieren von BDC-bezogene Sicherheitseinstellungen Produktionsservers SharePoint finden Sie unter [Geschäftsdaten-Verbindungsdienste Sicherheitsübersicht](http://go.microsoft.com/fwlink/?LinkID=178886).  
  
### <a name="retract-models-that-become-corrupt"></a>Ziehen Sie Modelle, die beschädigt werden, zurück.
 Beim erstmaligen Starten des Debuggers, stellt Visual Studio das gesamte Modell in SharePoint bereit. Danach jedes Mal aktualisiert Visual Studio das Modell in SharePoint, mit allen Änderungen, die Sie zwischen Bereitstellungen vornehmen.  
  
 Es gibt möglicherweise Situationen, in denen Visual Studio vollständig des Modells aus SharePoint zurückgezogen werden sollen. Beispielsweise kann ein Modell beschädigt werden.  Legen Sie das Modell in SharePoint Sie zum erneuten Bereitstellen der **inkrementelles Update** Eigenschaft des Modells, um **"false"**, und klicken Sie dann den Debugger zu starten. Die **inkrementelles Update** Eigenschaft wird in der **Eigenschaften** Fenster, wenn Sie den Knoten auswählen, die das Modell im darstellt der **BDC-Explorer**. Standardmäßig ist der Name des Modells **BdcModel1**.  
  
### <a name="change-identifier-names-of-entities-in-the-model"></a>Ändern von Bezeichnernamen von Entitäten im Modell
 Wenn Sie den Namen eines Bezeichners nach der Bereitstellung des Modells ändern, wird möglicherweise einen Fehler bei der Bereitstellung erhalten. Dieser Fehler kann nicht aufgelöst werden, durch Festlegen der **inkrementelles Update** Eigenschaft des Modells, um **"false"**. Sie müssen das Modell manuell zurücknehmen, und stellen Sie die Projektmappe erneut bereit. Weitere Informationen finden Sie unter [SharePoint-Lösungen zur Problembehandlung](../sharepoint/troubleshooting-sharepoint-solutions.md). Sie können diesen Fehler vermeiden, indem die **inkrementelles Update** Eigenschaft **"false"** vor Beginn der Bereitstellung des Modells.  
  
## <a name="locate-documentation-for-bdc-model-elements"></a>Suchen Sie die Dokumentation für BDC-Modellelemente
 Visual Studio fügt ein XML-Element für das Modell für jede Entität-Methode oder ein anderes Element aus, die Sie erstellen. Elementattribute angezeigt werden, als Eigenschaften in der **Eigenschaften** Fenster. Informationen zu den Elementen und Attributen, die Visual Studio generiert, wenn Sie das Modell entwerfen, finden Sie unter [BDCMetadata Schema](http://go.microsoft.com/fwlink/?LinkID=169275).  
  
## <a name="related-topics"></a>Verwandte Themen
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[Übersicht über Entwurfstools für BDC-Modelle](../sharepoint/bdc-model-design-tools-overview.md)|Beschreibt die Tools, die Sie verwenden können, um ein Modell für den BDC visuell zu entwerfen.|  
|[Vorgehensweise: Hinzufügen einer Entität zu einem Modell](../sharepoint/how-to-add-an-entity-to-a-model.md)|Veranschaulicht das Hinzufügen von externen Inhaltstypen oder Entitäten, auf das Modell.|  
|[Vorgehensweise: Hinzufügen einer Finder-Methode](../sharepoint/how-to-add-a-finder-method.md)|Veranschaulicht das Hinzufügen eine Methode, die Benutzern ermöglicht, eine Liste der Entitäten in einer Liste oder -Webpart anzeigen.|  
|[Vorgehensweise: Hinzufügen einer bestimmten Finder-Methode](../sharepoint/how-to-add-a-specific-finder-method.md)|Veranschaulicht das Hinzufügen eine Methode, die Benutzern das Anzeigen der Details einer bestimmten Entität ermöglicht.|  
|[Vorgehensweise: Hinzufügen einer Creator-Methode](../sharepoint/how-to-add-a-creator-method.md)|Veranschaulicht das Hinzufügen eine Methode, die Benutzer Datensätze mit einer Datenquelle direkt aus einer Liste oder einem Webpart hinzufügen können.|  
|[Vorgehensweise: Hinzufügen einer Deleter-Methode](../sharepoint/how-to-add-a-deleter-method.md)|Veranschaulicht das Hinzufügen eine Methode, die Benutzern ermöglicht, Daten aus einer Datenquelle mithilfe der Optionen in der Benutzeroberfläche (UI) einer Liste oder ein Webpart zu entfernen.|  
|[Vorgehensweise: Hinzufügen einer Updater-Methode](../sharepoint/how-to-add-an-updater-method.md)|Veranschaulicht das Hinzufügen eine Methode, die Benutzern ermöglicht, direkt aus einer Liste oder einem Webpart Datensätze in einer Datenquelle ändern.|  
|[Vorgehensweise: Hinzufügen eines Parameters zu einer Methode](../sharepoint/how-to-add-a-parameter-to-a-method.md)|Veranschaulicht, wie das Fenster "Klassendetails-Methode" in Visual Studio zu verwenden, um Eingabe-und den Rückgabetyp einer Methode hinzufügen.|  
|[Vorgehensweise: Definieren des Typdeskriptors für einen Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)|Veranschaulicht das Parameterdatentypen im Modell zu definieren.|  
|[Vorgehensweise: Definieren einer Methodeninstanz](../sharepoint/how-to-define-a-method-instance.md)|Veranschaulicht das Erstellen einer Instanz einer Methode, die der BDC ausgeführt wird.|  
|[Vorgehensweise: Hinzufügen eines Filterdeskriptors zu einer Finder-Methode](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)|Zeigt, wie Benutzern beschränken die Anzahl der Instanzen, die von einer Finder-Methode zurückgegebene aktiviert.|  
|[Erstellen einer Assoziation zwischen Entitäten](../sharepoint/creating-an-association-between-entities.md)|Beschreibt, wie Sie Beziehungen zwischen Entitäten im Modell definieren können. Geschäftsdaten-Webparts, externen Listen und benutzerdefinierten Anwendungen können diese datenbeziehungen in einer Benutzeroberfläche (UI) anzeigen.|  
|[Vorgehensweise: Erstellen einer Assoziation zwischen Entitäten](../sharepoint/how-to-create-an-association-between-entities.md)|Zeigt, wie Beziehungen zwischen Entitäten im Modell definiert.|  
|[Exemplarische Vorgehensweise: Erstellen einer externen Liste in SharePoint mithilfe von Geschäftsdaten](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)|Enthält schrittweise Anleitungen, in denen das Erstellen und Testen eines Modells, das Kontakte in einer externen SharePoint-Liste angezeigt werden.|  
|[Integrieren von Geschäftsdaten in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)|Bietet einen Überblick über das Erstellen und Entwerfen von Modellen für den BDC-Dienst.|  
  

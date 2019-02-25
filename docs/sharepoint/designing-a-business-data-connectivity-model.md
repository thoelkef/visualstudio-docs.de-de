---
title: Entwerfen eines Business Data Connectivity-Modells | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], designing a model
- Business Data Connectivity service [SharePoint development in Visual Studio], designing a model
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bf2fd868927a7e8380d5c079c2f8dc86d5385961
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56628415"
---
# <a name="design-a-business-data-connectivity-model"></a>Entwerfen eines Business Data Connectivity-Modells
  Sie können ein Modell für den Business Data Connectivity (BDC)-Dienst entwickeln, durch das Hinzufügen von Entitäten und Methoden auf eine Modelldatei. Eine Entität beschreibt eine Auflistung von Datenfeldern. Beispielsweise kann eine Entität eine Tabelle in einer Datenbank darstellen. Eine Methode führt eine Aufgabe wie das Hinzufügen, löschen oder Aktualisieren von Daten, die von den Entitäten dargestellt. Weitere Informationen finden Sie unter [Integrieren von Geschäftsdaten in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md).

## <a name="add-entities"></a>Hinzufügen von Entitäten
 Hinzufügen einer Entität können durch Ziehen oder Kopieren einer **Entität** von Visual Studio **Toolbox** im BDC-Designer. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen eine Entität zu einem Modell](../sharepoint/how-to-add-an-entity-to-a-model.md).

 Definieren Sie die Felder der Entität in einer Klasse ein. Beispielsweise können Sie ein Feld mit dem Namen hinzufügen `Address` zu einem `Customer` Klasse. Sie können eine neue Klasse zum Projekt hinzufügen oder verwenden Sie eine vorhandene Klasse, die mit anderen Tools wie z. B. den Object Relational Designer (O/R Designer) erstellt. Der Name der Entität und den Namen der Klasse, die die Entität darstellt, müssen nicht übereinstimmen. Sie beziehen sich die Klasse auf die Entität zu, wenn Sie die Methoden in Ihrem Modell definieren.

## <a name="add-methods"></a>Fügen Sie Methoden hinzu
 Der BDC-Dienst ruft Methoden in Ihrem Modell auf, wenn Benutzer anzeigen, hinzufügen, aktualisieren oder Löschen von Daten in einer Liste oder ein Webpart, das auf das Modell basiert. Sie müssen eine Methode für das Modell für jede Aufgabe hinzufügen, die der Benutzer ausführen kann. Methoden erstellen, indem Sie auf eines der fünf grundlegende Methodentypen der **BDC-Methodendetails** Fenster. Die folgende Tabelle beschreibt die fünf grundlegenden Methoden eines BDC-Modells.

|Methode|Beschreibung|
|------------|-----------------|
|Finder|Gibt eine Auflistung von Instanzen der Entität zurück. Wird aufgerufen, wenn der Benutzer die Liste oder -Webpart geöffnet wird. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen eine Finder-Methode](../sharepoint/how-to-add-a-finder-method.md).|
|Spezifischer Finder|Gibt eine bestimmte Entitätsinstanz zurück. Wird aufgerufen, wenn ein Benutzer die Details eines bestimmten Elements in einer Liste anzeigt. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen eine bestimmte Finder-Methode](../sharepoint/how-to-add-a-specific-finder-method.md).|
|Creator|Fügt neue Daten an die Datenquelle einer Entität. Wird aufgerufen, wenn der Benutzer die **neues Element** Schaltfläche auf dem Menüband einer Liste, die für das Modell basiert. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen eine Creator-Methode](../sharepoint/how-to-add-a-creator-method.md).|
|Updater|Ändert die Daten in einer Liste an. Wird aufgerufen, wenn der Benutzer Informationen in einer Liste zu aktualisieren. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen eine Updater-Methode](../sharepoint/how-to-add-an-updater-method.md).|
|Deleter|Entfernt Daten. Wird aufgerufen, wenn Benutzer ein Element aus der Liste löschen. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen eine Deleter-Methode](../sharepoint/how-to-add-a-deleter-method.md).|

## <a name="define-method-parameters"></a>Definieren Sie die Parameter der Methode
 Wenn Sie eine Methode erstellen, fügt Visual Studio die Eingabe- und Parameter, die für den Methodentyp geeignet sind. Diese Parameter sind nur Platzhalter. In den meisten Fällen müssen Sie die Parameter ändern, damit sie übergeben, oder geben Sie den richtigen Datentyp zurück. Standardmäßig gibt z. B. eine Finder-Methode eine Zeichenfolge an. In den meisten Fällen möchten Sie den Rückgabeparameter der Finder-Methode ändern, sodass sie eine Auflistung von Entitäten zurückgibt. Sie können das erreichen, durch den Typdeskriptor des Parameters ändern. Ein Typdeskriptor ist eine Auflistung von Attributen, die den Datentyp eines Parameters beschreibt. Weitere Informationen finden Sie unter [Vorgehensweise: Definieren des Typdeskriptors für einen Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

 Visual Studio ermöglicht Ihnen das Kopieren von Typdeskriptoren zwischen Parametern im Modell. Sie können z. B. einen Typdeskriptor, mit dem Namen definieren `CustomerTD` für den Rückgabeparameter der `GetCustomer` Methode. Können Sie kopieren die `CustomerTD` Typdeskriptor in die **BDC-Explorer**, und fügen Sie diesem Typdeskriptor an den Eingabeparameter, der die `CreateCustomer` Methode. Dies verhindert, dass Sie den gleichen Typdeskriptor mehr als einmal definieren müssen.

## <a name="method-instances"></a>Methodeninstanzen
 Wenn Sie eine Methode erstellen, fügt Visual Studio eine Standardinstanz-Methode. Methodeninstanz ist ein Verweis auf eine Methode sowie die Standardwerte für die Parameter an. Eine einzelne Methode kann es sich um mehrere Methodeninstanzen verwenden. Jede Instanz ist eine Kombination aus der Signatur der Methode und eine Gruppe von Standardwerten. Weitere Informationen finden Sie unter [Vorgehensweise: Definieren des Typdeskriptors für einen Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

 Wenn Sie das Projekt ausführen, werden Methodeninstanzen in einer Dropdown-Liste über die SharePoint-Liste angezeigt. Benutzer können Methodeninstanzen zum Anzeigen der Daten wählen.

 Um die Standardwerte für die Methodeninstanz hinzufügen möchten, müssen Sie den XML-Code des Modells direkt zu ändern. Weitere Informationen finden Sie unter [DefaultValue](http://go.microsoft.com/fwlink/?LinkID=169279).

## <a name="add-filter-descriptors"></a>Filterdeskriptoren hinzufügen
 Consumer des Modells sollten Instanzen einer Entität abrufen, die bestimmte Kriterien erfüllen. Um diese Funktionalität zu aktivieren, können Sie ein Filterdeskriptors zu einer Methode hinzufügen. Filterdeskriptoren ermöglichen Modell Consumer zum Filtern des Resultsets für die Methode durch die Werte an Methoden übergeben werden, bevor sie ausgeführt werden. Weitere Informationen finden Sie unter [Vorgehensweise: Vorgänge zum Begrenzen von Instanzen aus dem externen System Filterparameter hinzugefügt](http://go.microsoft.com/fwlink/?LinkID=169267).

 SharePoint bietet verschiedene Funktionen, die Benutzern ermöglichen, Werte bereitzustellen. Geschäftsdaten-Webparts bieten beispielsweise einen Text-Feld "Filter". Benutzer können die Daten in einer Liste durch Eingabe eines Werts in das Textfeld einschränken. Weitere Informationen über das Hinzufügen eines Filterdeskriptors zu einer Methode finden Sie unter [Vorgehensweise: Hinzufügen ein Filterdeskriptors zu einer Finder-Methode](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md).

### <a name="filter-descriptor-properties"></a>Filtern Sie die Eigenschaften des nachrichtendeskriptors
 Sie müssen festlegen, den Wert des der **zugeordnete Typdeskriptoren**, **Namen**, und **Typ** Eigenschaften eines Filterdeskriptors. Alle anderen Eigenschaften sind optional.

 Die **zugeordnete Typdeskriptoren** Eigenschaft der Filterdeskriptor für einen Eingabeparameter. Wenn ein Benutzer einen Filterwert bereitstellt, übergibt der BDC-Dienst diesen Wert an die Methode mithilfe des Eingabeparameters an.

 Die **Typ** Eigenschaft beschreibt das Filtern Muster, das Sie verwenden möchten. In SharePoint das Filtermuster, die, das Sie auswählen, wirkt sich auf den Text, der in der Benutzeroberfläche (UI) angezeigt wird. Z. B. für ein Vergleichsoperator, das den Text Muster filtern **gleich** als oberhalb eines Business-Webparts-Steuerelement angezeigt wird. Weitere Informationen zu einzelnen Filtermustern, finden Sie unter [von BDC unterstützte Filter](http://go.microsoft.com/fwlink/?LinkId=169287).

 Weitere Informationen zu den Eigenschaften eines Filterdeskriptors finden Sie unter [FilterDescriptor](http://go.microsoft.com/fwlink/?LinkID=169280).

### <a name="provide-default-values"></a>Geben Sie Standardwerte
 In einigen Fällen kann der Benutzer nicht über einen Filterwert angeben. Sie können einen Standardwert bereitstellen, durch den Standardwert für die Methodeninstanz hinzufügen oder den Standardwert festlegen, im Code der Methode. Weitere Informationen dazu, wie Sie einen Standardwert für die Methodeninstanz hinzufügen, finden Sie unter [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282). Ein Beispiel zum Festlegen den Standardwert eines Eingabeparameters in den Code der Methode, finden Sie unter [Vorgehensweise: Hinzufügen ein Filterdeskriptors zu einer Finder-Methode](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md).

## <a name="validate-the-model"></a>Validieren des Modells
 Sie können das Modell während der Entwicklung überprüfen. Visual Studio identifiziert Probleme, die das Modell verhindern wie erwartet verhält. Diese Probleme werden angezeigt, in der Visual Studio **Fehlerliste**.

 Sie können ein Modell überprüfen, indem Sie das Kontextmenü für den BDC-Designer öffnen und dann auf **überprüfen**. Wenn das Modell keine Fehler enthält, werden sie in der **Fehlerliste**. Sie können schnell den Cursor bewegen, die auf den Code, die einen Fehler enthält, indem Sie auf den Fehler in der Liste doppelklicken. Als Alternative können Sie die **F8** oder **UMSCHALT**+**F8** Tasten wiederholt Schritt vorwärts oder rückwärts durch die Fehler in der Liste.

 Wenn die Regeln des Modells in irgendeiner Weise verletzt werden können, treten Validierungsfehler auf. Z. B. wenn die **"IsCollection"** von einem Typdeskriptor-Eigenschaftensatz auf **"true"**, aber keine untergeordneten Typdeskriptoren vorhanden sind, tritt ein Validierungsfehler angezeigt. Möglicherweise müssen Sie verweisen, die den Regeln für ein BDC-Modell, um einige Fehler zu verstehen, die in der Visual Studio angezeigt werden **Fehlerliste**. Weitere Informationen zu den Regeln der ein BDC-Modell finden Sie unter [BDCMetadata Schema](http://go.microsoft.com/fwlink/?LinkID=169275).

## <a name="debug-the-solution-that-contains-the-model"></a>Debuggen Sie die Lösung mit dem Modell
 Sie können den Code Debuggen, wie Sie Code in Visual Studio debuggen. Um Ihren Code zu debuggen, legen Sie Haltepunkte an einer beliebigen Stelle im Code, und klicken Sie dann starten Sie den Debugger zu. Visual Studio öffnet die SharePoint-Website. Erstellen Sie in SharePoint eine Liste oder ein Webpart, das Ihre Geschäftsdaten verwendet. Anschließend können Sie den Code durchlaufen. Weitere Informationen zum Debuggen von SharePoint-Projekte finden Sie unter [Problembehandlung bei SharePoint-Lösungen](../sharepoint/troubleshooting-sharepoint-solutions.md).

 Sie können auch Code in benutzerdefinierten Assemblys Debuggen, die Sie dem Projekt hinzu. Um Code in einer benutzerdefinierten Assembly zu debuggen, müssen Sie jedoch die Assembly dem Lösungspaket hinzufügen. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen und Entfernen zusätzlicher Assemblys](../sharepoint/how-to-add-and-remove-additional-assemblies.md).

 Weitere Informationen zu Ihrem Projekt eine benutzerdefinierte Assembly hinzufügen, finden Sie unter [Vorgehensweise: Einfügen einer benutzerdefinierte Assembly in eine BDC-Funktion](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md).

### <a name="configure-bdc-security"></a>Konfigurieren der BDC-Sicherheit
 Sie müssen möglicherweise die Sicherheitseinstellungen in SharePoint zu ändern, bevor Sie Ihre Lösung Debuggen können. Um diese Einstellungen zu ändern, öffnen Sie die Business Data Connectivity-Dienstanwendung in SharePoint 2010 Central Administration-Website. In der **Festlegen von Metadaten Store Berechtigungen** (Dialogfeld), fügen Sie Ihr Benutzer hinzu, und wählen Sie dann eine der folgenden Optionen:

|Aufgabe|Option|
|----------|------------|
|Um Modelle mit dem BDC-Dienst bereitzustellen.|Bearbeiten|
|Zum Erstellen von Listen und Webparts mithilfe von externen Typen Inhalt (Entitäten) in Ihrem Modell.|Bei Clients ausgewählt werden.|
|Um zu erstellen, lesen, aktualisieren und Löschen von Entitätsdaten.|Ausführen|

 Weitere Informationen zu diesen Einstellungen finden Sie unter [Business Data Connectivity-dienstverwaltung](http://go.microsoft.com/fwlink/?LinkID=178883).

 Sie können auch Codezugriffssicherheits-Berechtigungen für einzelne Modelle oder externe Inhaltstypen festlegen. Weitere Informationen zum Festlegen der Sicherheitsberechtigungen eines Modells finden Sie unter [BDC-Modell-Management](http://go.microsoft.com/fwlink/?LinkID=178884). Weitere Informationen dazu, wie Sie die Sicherheitsberechtigungen von einem externen Inhaltstyp festgelegt werden, finden Sie unter [externe Verwaltung dieser Inhaltstypen](http://go.microsoft.com/fwlink/?LinkID=178885).

> [!NOTE]
>  Verwenden Sie diese Einstellungen, um das Debuggen einer Lösung auf dem lokalen SharePoint-Server. Weitere Informationen zum Konfigurieren des SharePoint-Server der produktionsumgebung BDC-bezogene Einstellungen finden Sie unter [Geschäftsdaten-Verbindungsdienste Sicherheitsübersicht](http://go.microsoft.com/fwlink/?LinkID=178886).

### <a name="retract-models-that-become-corrupt"></a>Zurückziehen von Modellen, die beschädigt
 Zum ersten Mal beim Starten des Debuggers, stellt Visual Studio das gesamte Modell für SharePoint bereit. Danach für jedes Mal aktualisiert Visual Studio das Modell in SharePoint mit den Änderungen, die Sie zwischen den Bereitstellungen vornehmen.

 Es gibt möglicherweise Situationen, in denen Sie Visual Studio das Modell aus SharePoint vollständig entfernen möchten. Beispielsweise kann ein Modell beschädigt werden.  Um Ihr Modell auf SharePoint erneut bereitzustellen, legen Sie die **inkrementelles Update** Eigenschaft des Modells, das **"false"**, und klicken Sie dann den Debugger starten. Die **inkrementelles Update** Eigenschaft angezeigt wird, der **Eigenschaften** anzeigen, wenn Sie den Knoten auswählen, die das Modell im darstellt der **BDC-Explorer**. Standardmäßig ist der Name des Modells **BdcModel1**.

### <a name="change-identifier-names-of-entities-in-the-model"></a>Bezeichnernamen von Entitäten im Modell ändern
 Wenn Sie den Namen eines Bezeichners ändern, nachdem Sie das Modell bereitstellen, können Sie einen Fehler bei der Bereitstellung erhalten. Dieser Fehler kann nicht aufgelöst werden, durch Festlegen der **inkrementelles Update** Eigenschaft des Modells, das **"false"**. Sie müssen das Modell manuell zurücknehmen, und klicken Sie dann die Lösung erneut bereitstellen. Weitere Informationen finden Sie unter [Problembehandlung bei SharePoint-Lösungen](../sharepoint/troubleshooting-sharepoint-solutions.md). Dieser Fehler kann vermieden werden, durch Festlegen der **inkrementelles Update** Eigenschaft **"false"** vor dem Beginn der Bereitstellung des Modells.

## <a name="locate-documentation-for-bdc-model-elements"></a>Hier finden Sie Dokumentation für BDC-Modell-Elemente
 Visual Studio fügt ein XML-Element für das Modell für jede Entität, Methode oder ein anderes Element, das Sie erstellen. Elementattribute angezeigt werden, als Eigenschaften in der **Eigenschaften** Fenster. Informationen zu den Elementen und Attributen, die Visual Studio generiert, wenn Sie das Modell entwerfen, finden Sie unter [BDCMetadata Schema](http://go.microsoft.com/fwlink/?LinkID=169275).

## <a name="related-topics"></a>Verwandte Themen

|Titel|Beschreibung|
|-----------|-----------------|
|[Übersicht über Entwurfstools für BDC-Modell](../sharepoint/bdc-model-design-tools-overview.md)|Beschreibt die Tools, die Sie verwenden können, um ein Modell für den BDC visuell zu entwerfen.|
|[Vorgehensweise: Hinzufügen einer Entitätstyps zu einem Modell](../sharepoint/how-to-add-an-entity-to-a-model.md)|Erfahren Sie, wie Sie externe Inhaltstypen oder Entitäten, die dem Modell hinzufügen.|
|[Vorgehensweise: Hinzufügen einer Finder-Methode](../sharepoint/how-to-add-a-finder-method.md)|Erfahren Sie, wie zum Hinzufügen einer Methode, die Benutzern ermöglicht, eine Liste der Entitäten in einer Liste oder -Webpart anzeigen.|
|[Vorgehensweise: Hinzufügen einer bestimmten Finder-Methode](../sharepoint/how-to-add-a-specific-finder-method.md)|Erfahren Sie, wie zum Hinzufügen einer Methode, die Benutzern ermöglicht, die Details einer bestimmten Entität anzuzeigen.|
|[Vorgehensweise: Hinzufügen einer Creator-Methode](../sharepoint/how-to-add-a-creator-method.md)|Erfahren Sie, wie zum Hinzufügen einer Methode, die Benutzern ermöglicht, die Datensätze einer Datenquelle direkt aus einer Liste oder einem Webpart hinzufügen.|
|[Vorgehensweise: Hinzufügen einer Deleter-Methode](../sharepoint/how-to-add-a-deleter-method.md)|Erfahren Sie, wie zum Hinzufügen einer Methode, die Benutzern ermöglicht, Daten aus einer Datenquelle mithilfe der Optionen in der Benutzeroberfläche (UI) einer Liste oder ein Webpart zu entfernen.|
|[Vorgehensweise: Hinzufügen einer Updater-Methode](../sharepoint/how-to-add-an-updater-method.md)|Erfahren Sie, wie zum Hinzufügen einer Methode, die Benutzern ermöglicht, direkt aus einer Liste oder einem Webpart Datensätze in einer Datenquelle zu ändern.|
|[Vorgehensweise: Fügen Sie einen Parameter einer Methode](../sharepoint/how-to-add-a-parameter-to-a-method.md)|Erfahren Sie, wie Sie das Fenster "Klassendetails-Methode" in Visual Studio zu verwenden, um die Eingabe-und Rückgabe einer Methode hinzufügen.|
|[Vorgehensweise: Definieren des Typdeskriptors für einen parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)|Erfahren Sie, wie Datentypen im Modell zu definieren.|
|[Vorgehensweise: Definieren einer Methodeninstanz](../sharepoint/how-to-define-a-method-instance.md)|Erfahren Sie, wie eine Instanz einer Methode zu erstellen, die der BDC ausgeführt wird.|
|[Vorgehensweise: Hinzufügen eines Filterdeskriptors zu einer Finder-Methode](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)|Erfahren Sie, wie von Benutzern begrenzen die Anzahl der Instanzen, die von einer Finder-Methode zurückgegebene aktiviert.|
|[Erstellen einer Assoziation zwischen Entitäten](../sharepoint/creating-an-association-between-entities.md)|Beschreibt, wie Sie Beziehungen zwischen Entitäten im Modell definieren können. Geschäftsdaten-Webparts, External Lists und benutzerdefinierte Anwendungen können diese datenbeziehungen in einer Benutzeroberfläche (UI) anzeigen.|
|[Vorgehensweise: Erstellen einer Assoziation zwischen Entitäten](../sharepoint/how-to-create-an-association-between-entities.md)|Erfahren Sie, wie Sie Beziehungen zwischen Entitäten im Modell zu definieren.|
|[Exemplarische Vorgehensweise: Erstellen eines externen Liste in SharePoint mithilfe von Geschäftsdaten](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)|Enthält schrittweise Anleitungen, die zeigen, wie Sie erstellen und Testen eines Modells, das Kontakte in einer externen SharePoint-Liste angezeigt.|
|[Integrieren von Geschäftsdaten in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)|Bietet einen Überblick über das Erstellen und Entwerfen von Modellen für den BDC-Dienst.|

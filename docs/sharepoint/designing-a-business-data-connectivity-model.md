---
title: "Entwerfen eines Business Data Connectivity-Modells | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "BDC [SharePoint-Entwicklung in Visual Studio], Entwerfen eines Modells"
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], Entwerfen eines Modells"
ms.assetid: 19cad8cf-8a82-4000-84cf-1e5aff54e5af
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# Entwerfen eines Business Data Connectivity-Modells
  Sie können ein Modell für den Business Data Connectivity \(BDC\)\-Dienst entwickeln, indem Sie einer Modelldatei Entitäten und Methoden hinzufügen.  Eine Entität beschreibt eine Auflistung von Datenfeldern.  Eine Entität kann z. B. eine Tabelle in einer Datenbank darstellen.  Eine Methode dient zum Ausführen einer Aufgabe wie Hinzufügen, Löschen oder Aktualisieren von Daten, die durch die Entitäten dargestellt werden.  Weitere Informationen finden Sie unter [Integrieren von Geschäftsdaten in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md).  
  
## Hinzufügen von Entitäten  
 Sie können eine Entität hinzufügen, indem Sie den **Entität** von **Werkzeugkasten** in Visual Studio auf den BDC\-Designer ziehen oder kopieren.  Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen einer Entität zu einem Modell](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
 Definieren Sie die Felder der Entität in einer Klasse.  Beispielsweise können Sie einer `Customer`\-Klasse ein Feld mit der Bezeichnung `Address` hinzufügen.  Sie können dem Projekt entweder eine neue Klasse hinzufügen oder eine vorhandene Klasse verwenden, die mit anderen Tools wie dem Object Relational Designer \(O\/R\-Designer\) erstellt wurde.  Der Name der Entität muss nicht dem Namen der Klasse entsprechen, die für die Entität steht.  Die Verknüpfung von Klasse und Entität erfolgt beim Definieren der Methoden im Modell.  
  
## Hinzufügen von Methoden  
 Vom BDC\-Dienst werden Methoden im Modell aufgerufen, wenn Benutzer Informationen in einer auf dem Modell basierenden Liste oder in einem entsprechenden Webpart anzeigen, hinzufügen, aktualisieren oder löschen.  Dem Modell muss für jede Aufgabe, die der Benutzer ausführen kann, eine Methode hinzugefügt werden.  Wählen Sie zum Erstellen von Methoden im Fenster **BDC\-Methodendetails** einen der fünf grundlegenden Methodentypen aus.  In der folgenden Tabelle werden die fünf grundlegenden Methoden eines BDC\-Modells beschrieben:  
  
|Methode|**Beschreibung**|  
|-------------|----------------------|  
|Finder|Gibt eine Auflistung mit Entitätsinstanzen zurück.  Wird aufgerufen, wenn der Benutzer die Liste oder das Webpart öffnet.  Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen einer Finder-Methode](../sharepoint/how-to-add-a-finder-method.md).|  
|Spezifischer Finder|Gibt eine bestimmte Entitätsinstanz zurück.  Wird aufgerufen, wenn ein Benutzer die Details eines bestimmten Elements in einer Liste anzeigt.  Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen einer bestimmten Finder-Methode](../sharepoint/how-to-add-a-specific-finder-method.md).|  
|Creator|Fügt der Datenquelle einer Entität neue Daten hinzu.  Wird aufgerufen, wenn Benutzer die Schaltfläche **Neues Element** auf dem Menüband einer Liste auswählen, die auf dem Modell basiert.  Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen einer Creator-Methode](../sharepoint/how-to-add-a-creator-method.md).|  
|Updater|Ändert die Daten in einer Liste.  Wird aufgerufen, wenn Benutzer Informationen in einer Liste aktualisieren.  Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen einer Updater-Methode](../sharepoint/how-to-add-an-updater-method.md).|  
|Deleter|Entfernt Daten.  Wird aufgerufen, wenn Benutzer ein Element aus der Liste löschen.  Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen einer Deleter-Methode](../sharepoint/how-to-add-a-deleter-method.md).|  
  
## Definieren von Methodenparametern  
 Beim Erstellen einer Methode werden von Visual Studio die für den Methodentyp geeigneten Eingabe\- und Ausgabeparameter hinzugefügt.  Bei diesen Parametern handelt es sich lediglich um Platzhalter.  Meist müssen die Parameter geändert werden, damit sie übergeben werden oder die korrekte Art von Daten zurückgegeben wird.  So wird beispielsweise von einer Finder\-Methode standardmäßig eine Zeichenfolge zurückgegeben.  In den meisten Fällen muss der Rückgabeparameter der Finder\-Methode jedoch geändert werden, sodass eine Auflistung mit Entitäten zurückgegeben wird.  Ändern Sie hierzu den Typdeskriptor des Parameters.  Bei einem Typdeskriptor handelt es sich um eine Auflistung von Attributen zum Beschreiben des Datentyps eines Parameters.  Weitere Informationen finden Sie unter [How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
 Mithilfe von Visual Studio können Typdeskriptoren zwischen Parametern im Modell kopiert werden.  So können Sie beispielsweise für den Rückgabeparameter der `GetCustomer`\-Methode einen Typdeskriptor mit der Bezeichnung `CustomerTD` definieren.  Den `CustomerTD`\-Typdeskriptor können Sie im BDC\-Explorer kopieren und anschließend in den Eingabeparameter der `CreateCustomer`\-Methode einfügen.  Dadurch muss ein Typdeskriptor immer nur jeweils einmal definiert werden.  
  
##  <a name="MethodInstances"></a> Methodeninstanzen  
 Beim Erstellen einer Methode wird von Visual Studio eine Standardmethodeninstanz hinzugefügt.  Eine Methodeninstanz umfasst einen Verweis auf eine Methode sowie die Standardwerte für die Parameter.  Eine einzelne Methode kann über mehrere Methodeninstanzen verfügen.  Jede Instanz ist eine Kombination aus der Methodensignatur und einem Satz von Standardwerten.  Weitere Informationen finden Sie unter [How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
 Beim Ausführen des Projekts werden die Methodeninstanzen in einer Dropdownliste über der SharePoint\-Liste angezeigt.  Benutzer können Methodeninstanzen auswählen, um die Daten anzuzeigen.  
  
 Wenn Sie der Methodeninstanz Standardwerte hinzufügen möchten, müssen Sie direkt den XML\-Code des Modells ändern.  Weitere Informationen finden Sie unter [DefaultValue](http://go.microsoft.com/fwlink/?LinkID=169279).  
  
## Hinzufügen von Filterdeskriptoren  
 Von Consumern des Modells müssen unter Umständen Instanzen einer Entität abgerufen werden, die einigen Kriterien entsprechen.  Zum Aktivieren dieser Funktion können Sie einer Methode einen Filterdeskriptor hinzufügen.  Filterdeskriptoren ermöglichen Modellconsumern das Filtern von Methodenresultsets. Hierzu werden Werte an Methoden übergeben, bevor diese ausgeführt werden.  Weitere Informationen finden Sie unter [Gewusst wie: Fügen Sie Grenzen\-Instanzen Filterparameter Operationen vom externen System hinzu](http://go.microsoft.com/fwlink/?LinkID=169267).  
  
 Von SharePoint werden mehrere Funktionen bereitgestellt, die Benutzern das Angeben von Filterwerten ermöglichen.  So steht beispielsweise in Geschäftsdatenwebparts ein Filtertextfeld zur Verfügung.  Benutzer können die Daten in einer Liste einschränken, indem sie einen Wert in das Textfeld eingeben.  Weitere Informationen zum Hinzufügen eines Filterdeskriptors zu einer Methode finden Sie unter [Gewusst wie: Hinzufügen eines Filterdeskriptors zu einer Finder-Methode](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md).  
  
### Filterdeskriptoreigenschaften  
 Die Werte der Eigenschaften **Zugeordnete Typdeskriptoren**, **Name** und **Typ** eines Filterdeskriptors müssen festgelegt werden.  Alle anderen Eigenschaften sind optional.  
  
 Durch die Eigenschaft **Zugeordnete Typdeskriptoren** wird der Filterdeskriptor mit einem Eingabeparameter verknüpft.  Wenn ein Benutzer einen Filterwert angibt, wird dieser Wert vom BDC\-Dienst unter Verwendung des Eingabeparameters an die Methode übergeben.  
  
 Mit der Eigenschaft **Typ** wird das zu verwendende Filtermuster beschrieben.  In SharePoint hat das ausgewählte Filtermuster Auswirkungen auf den Text, der auf der Benutzeroberfläche \(User Interface, UI\) angezeigt wird.  So wird beispielsweise bei einem Filtermuster mit Vergleichsoperator der Text **ist gleich** als Steuerelement über einem Geschäftsdatenwebpart angezeigt.  Weitere Informationen über jedes gewünschte Filtermuster, Sie finden. [Typen von den Filtern die von der BDC](http://go.microsoft.com/fwlink/?LinkId=169287)  
  
 Weitere Informationen zu den Eigenschaften eines Filterdeskriptors, Sie finden. [FilterDescriptor](http://go.microsoft.com/fwlink/?LinkID=169280)  
  
### Angeben von Standardwerten  
 In einigen Fällen gibt der Benutzer unter Umständen keinen Filterwert an.  Sie können einen Standardwert angeben, indem Sie der Methodeninstanz einen Standardwert hinzufügen oder den Standardwert im Code der Methode festlegen.  Weitere Informationen darüber, eines Standardwerts zur Methodeninstanz finden, Sie [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282) hinzugefügt wird.  Ein Beispiel für das Festlegen des Standardwerts eines Eingabeparameters im Code der Methode finden Sie unter [Gewusst wie: Hinzufügen eines Filterdeskriptors zu einer Finder-Methode](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md).  
  
## Überprüfen des Modells  
 Das Modell kann während der Entwicklung überprüft werden.  Von Visual Studio werden Probleme erkannt, die dazu führen können, dass sich das Modell nicht wie geplant verhält.  Diese Probleme werden in der Fehlerliste von Visual Studio angezeigt.  
  
 Sie können ein Modell überprüfen, indem Sie das Kontextmenü für den BDC\-Designer öffnen und dann **Überprüfen** auswählen.  Wenn das Modell alle Fehler enthält, werden diese in **Fehlerliste**.  Sie können den Cursor auf den Code schnell verschieben, der einen Fehler enthält, indem Sie auf den Fehler in der Liste doppelklickt.  Alternativ können Sie die UMSCHALT\+F8\-TASTEN F8 oder wiederholt wählen, um zu schrittweise rückwärts oder rückwärts durch die Fehler in der Liste.  
  
 Validierungsfehler können auftreten, wenn gegen die Regeln für das Modell verstoßen wird.  So tritt beispielsweise ein Validierungsfehler auf, wenn die Eigenschaft **IsCollection** eines Typdeskriptors auf **true** festgelegt ist, aber keine untergeordneten Typdeskriptoren vorhanden sind.  Gegebenenfalls ist ein Blick in die Regeln eines BDC\-Modells erforderlich, um einige der Fehler aus der Fehlerliste von Visual Studio nachvollziehen zu können.  Weitere Informationen zu den Regeln eines BDC\-Modells, Sie finden [BDCMetadata\-Schema](http://go.microsoft.com/fwlink/?LinkID=169275).  
  
## Debuggen der Lösung mit dem Modell  
 Gehen Sie zum Debuggen des Codes genauso vor wie bei beliebigem anderem Code in Visual Studio.  Legen Sie zum Debuggen des Codes an beliebiger Stelle im Code Haltepunkte fest, und starten Sie anschließend den Debugger.  Die SharePoint\-Website wird geöffnet.  Erstellen Sie in SharePoint eine Liste oder ein Webpart mit Ihren Geschäftsdaten.  Anschließend kann der Code schrittweise durchlaufen werden.  Weitere Informationen zum Debuggen von SharePoint\-Projekten finden Sie unter [Problembehandlung bei SharePoint-Lösungen](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
 Sie können auch Code in benutzerdefinierten Assemblys debuggen, die Sie dem Projekt hinzufügen.  Um Code in einer benutzerdefinierten Assembly debuggen zu können, müssen Sie die Assembly jedoch zum Projektmappenpaket hinzufügen.  Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen und Entfernen zusätzlicher Assemblys](../sharepoint/how-to-add-and-remove-additional-assemblies.md).  
  
 Weitere Informationen zum Hinzufügen einer benutzerdefinierten Assembly zum Projekt finden Sie unter [Gewusst wie: Einfügen einer benutzerdefinierten Assembly in eine BDC-Funktion](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md).  
  
### Konfigurieren der BDC\-Sicherheit  
 Möglicherweise müssen zunächst die Sicherheitseinstellungen in SharePoint geändert werden, damit Sie die Lösung debuggen können.  Öffnen Sie zum Ändern dieser Einstellungen auf der Website "SharePoint 2010\-Zentraladministration" die Business Data Connectivity\-Dienstanwendung.  Fügen Sie im Dialogfeld **Berechtigungen für den Metadatenspeicher festlegen** Ihr Benutzerkonto hinzu, und wählen Sie eine der folgenden Optionen aus:  
  
|Aufgabe|Option|  
|-------------|------------|  
|Bereitstellen von Modellen für den BDC\-Dienst|Bearbeiten|  
|Erstellen von Listen und Webparts unter Verwendung externer Inhaltstypen \(Entitäten\) im Modell|Auswählbar in Clients|  
|Erstellen, Lesen, Aktualisieren und Löschen von Entitätsdaten|Ausführen|  
  
 Weitere Informationen zu diesen Einstellungen finden, Sie. [Business Data Connectivity\-Dienstverwaltung](http://go.microsoft.com/fwlink/?LinkID=178883)  
  
 Sicherheitsberechtigungen können auch für einzelne Modelle oder externe Inhaltstypen festgelegt werden.  Weitere Informationen darüber, wie die Sicherheitsberechtigungen eines Modells, finden Sie festlegen [BDC\-Modellverwaltung](http://go.microsoft.com/fwlink/?LinkID=178884).  Weitere Informationen darüber, wie die Sicherheitsberechtigungen eines externen Inhaltstyps, finden Sie festlegen [Externe Inhaltstypverwaltung](http://go.microsoft.com/fwlink/?LinkID=178885).  
  
> [!NOTE]  
>  Verwenden Sie diese Einstellungen, um eine Lösung auf dem lokalen SharePoint\-Server zu debuggen.  Weitere Informationen dazu, wie BDC\-bezogener Sicherheitseinstellungen auf SharePoint\-Server, finden Sie konfiguriert [Business Data Connectivity enthält Sicherheitsübersicht aus](http://go.microsoft.com/fwlink/?LinkID=178886).  
  
### Zurückziehen beschädigter Modelle  
 Wenn Sie das erste Mal den Debugger starten, wird das vollständige Modell für SharePoint bereitgestellt.  Danach wird das Modell in SharePoint jeweils mit den Änderungen aktualisiert, die seit der letzten Bereitstellung vorgenommen wurden.  
  
 In bestimmten Situationen kann es erforderlich sein, das Modell vollständig aus SharePoint zurückzuziehen.  Ein Modell könnte beispielsweise beschädigt werden.  Wenn Sie das Modell erneut für SharePoint bereitstellen möchten, legen Sie die Eigenschaft **Inkrementelle Aktualisierung** des Modells auf **False** fest, und starten Sie anschließend den Debugger.  Die Eigenschaft **Inkrementelle Aktualisierung** wird im Eigenschaftenfenster angezeigt, wenn Sie im BDC\-Explorer den Knoten auswählen, der für das Modell steht.  Standardmäßig lautet der Name des Modells **BdcModel1**.  
  
### Ändern von Bezeichnernamen von Entitäten im Modell  
 Wenn Sie den Namen eines Bezeichners ändern, nachdem Sie das Modell bereitgestellt haben, wird u. U. ein Bereitstellungsfehler ausgegeben.  Sie können diesen Fehler durch Festlegen der Eigenschaft **Inkrementelle Aktualisierung** auf **False** nicht beheben.  Sie müssen das Modell manuell zurücknehmen und anschließend neu bereitstellen.  Weitere Informationen finden Sie unter [Problembehandlung bei SharePoint-Lösungen](../sharepoint/troubleshooting-sharepoint-solutions.md).  Sie können diesen Fehler vermeiden, indem Sie die Eigenschaft **Inkrementelle Aktualisierung** auf **False** festlegen, bevor Sie das Modell erstmalig bereitstellen.  
  
## Suchen der Dokumentation für BDC\-Modellelemente  
 Von Visual Studio wird dem Modell für jede Entität, jede Methode und jedes andere erstellte Element ein XML\-Element hinzugefügt.  Elementattribute werden im Eigenschaftenfenster als Eigenschaften angezeigt.  Informationen zu den Elementen und Attributen, die Visual Studio generiert, während Sie das Modell entwerfen, Sie finden. [BDCMetadata\-Schema](http://go.microsoft.com/fwlink/?LinkID=169275)  
  
## Verwandte Themen  
  
|Titel|**Beschreibung**|  
|-----------|----------------------|  
|[Übersicht über Entwurfstools für BDC-Modelle](../sharepoint/bdc-model-design-tools-overview.md)|Beschreibt die Tools zum visuellen Entwerfen eines Modells für die BDC.|  
|[Gewusst wie: Hinzufügen einer Entität zu einem Modell](../sharepoint/how-to-add-an-entity-to-a-model.md)|Veranschaulicht das Hinzufügen externer Inhaltstypen \(oder Entitäten\) zum Modell.|  
|[Gewusst wie: Hinzufügen einer Finder-Methode](../sharepoint/how-to-add-a-finder-method.md)|Veranschaulicht das Hinzufügen einer Methode, die Benutzern das Anzeigen einer Liste mit Entitäten in einer Liste oder in einem Webpart ermöglicht.|  
|[Gewusst wie: Hinzufügen einer bestimmten Finder-Methode](../sharepoint/how-to-add-a-specific-finder-method.md)|Veranschaulicht das Hinzufügen einer Methode, die Benutzern das Anzeigen der Details einer bestimmten Entität ermöglicht.|  
|[Gewusst wie: Hinzufügen einer Creator-Methode](../sharepoint/how-to-add-a-creator-method.md)|Veranschaulicht das Hinzufügen einer Methode, dank der Benutzer direkt in einer Liste oder in einem Webpart Datensätze zu einer Datenquelle hinzufügen können.|  
|[Gewusst wie: Hinzufügen einer Deleter-Methode](../sharepoint/how-to-add-a-deleter-method.md)|Veranschaulicht das Hinzufügen einer Methode, die es Benutzern ermöglicht, Daten mithilfe der Benutzeroberflächenoptionen einer Liste oder eines Webparts aus einer Datenquelle zu entfernen.|  
|[Gewusst wie: Hinzufügen einer Updater-Methode](../sharepoint/how-to-add-an-updater-method.md)|Veranschaulicht das Hinzufügen einer Methode, dank der Benutzer direkt in einer Liste oder in einem Webpart Datensätze in einer Datenquelle ändern können.|  
|[Gewusst wie: Hinzufügen eines Parameters zu einer Methode](../sharepoint/how-to-add-a-parameter-to-a-method.md)|Veranschaulicht das Hinzufügen von Eingabe\- und Rückgabeparametern zu einer Methode mithilfe des Fensters "Methodendetails" in Visual Studio.|  
|[How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)|Veranschaulicht das Definieren von Parameterdatentypen im Modell.|  
|[Gewusst wie: Definieren einer Methodeninstanz](../sharepoint/how-to-define-a-method-instance.md)|Veranschaulicht das Erstellen einer Instanz einer Methode, die von der BDC ausgeführt wird.|  
|[Gewusst wie: Hinzufügen eines Filterdeskriptors zu einer Finder-Methode](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)|Veranschaulicht, wie Benutzern das Beschränken der von einer Finder\-Methode zurückgegebenen Anzahl von Instanzen ermöglicht werden kann.|  
|[Erstellen einer Assoziation zwischen Entitäten](../sharepoint/creating-an-association-between-entities.md)|Beschreibt das Definieren von Beziehungen zwischen Entitäten im Modell.  Diese Datenbeziehungen können auf der Benutzeroberfläche von Geschäftsdatenwebparts, externen Listen und benutzerdefinierten Anwendungen angezeigt werden.|  
|[Gewusst wie: Erstellen einer Assoziation zwischen Entitäten](../sharepoint/how-to-create-an-association-between-entities.md)|Veranschaulicht das Definieren von Beziehungen zwischen Entitäten im Modell.|  
|[Exemplarische Vorgehensweise: Erstellen einer externen Liste in SharePoint mithilfe von Geschäftsdaten](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)|Enthält schrittweise Anweisungen zum Erstellen und Testen eines Modells, mit dem Kontakte in einer externen SharePoint\-Liste angezeigt werden.|  
|[Integrieren von Geschäftsdaten in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)|Enthält eine Übersicht über das Erstellen und Entwerfen von Modellen für den BDC\-Dienst.|  
  
  
---
title: "Windows Communication Foundation Services and WCF Data Services in Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "services, WCF Data"
  - "WCF services, binding to"
  - "WCF services, asynchronous service methods"
  - "service references [Visual Studio]"
  - "WCF Data Services"
  - "asynchronous calls"
  - "service references [Visual Studio], type sharing"
  - "endpoints [WCF]"
  - "asynchronous service methods"
  - "service references [Visual Studio] endpoints"
  - "WCF services, type sharing"
  - "Windows Communication Foundation, in Visual Studio"
  - "services, WCF"
  - "WCF service, Visual Studio"
  - "data services, WCF"
  - "services, in Visual Studio"
  - "data binding [Visual Studio], WCF"
  - "service endpoints [Visual Studio]"
  - "service references [Visual Studio], asynchronous calls"
  - "services, Windows Communication Foundation"
  - "type sharing in WCF services"
  - "WCF services, endpoints"
  - "service method, called asynchronously[Visual Studio]"
ms.assetid: d56f12cb-e139-4fec-b3e4-488383356642
caps.latest.revision: 26
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Windows Communication Foundation Services and WCF Data Services in Visual Studio
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 2008 umfasst Tools für die Arbeit mit Windows Communication Foundation \(WCF\) und [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]. Dabei handelt es sich um Microsoft\-Technologie zum Erstellen verteilter Anwendungen.  Dieses Thema enthält eine Einführung in Dienste aus der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Sicht.  
  
## Was ist WCF?  
 [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)] ist ein einheitliches Framework zum Erstellen verteilter Anwendungen, die sicher, zuverlässig, transaktiv und interoperabel sind.  In früheren Versionen von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] konnten verschiedene Technologien für das Kommunizieren zwischen Anwendungen verwendet werden.  
  
 Wenn Informationen für die gemeinsame Nutzung bereitgestellt werden sollten, auf die von einer beliebigen Plattform zugegriffen werden konnte, wurde ein Webdienst \(auch als ASMX\-Webdienst bezeichnet\) verwendet.  Wenn lediglich Daten zwischen einem Client und einem Server verschoben werden sollten, der unter dem Betriebssystem Windows ausgeführt wurde, wurde .NET Remoting verwendet.  Wenn transaktive Kommunikation benötigt wurde, wurden Enterprise\-Dienste \(DCOM\) verwendet, und bei Verwendung eines Warteschlangenmodells wurde Message Queuing \(auch MSMQ\) eingesetzt.  
  
 WCF bündelt die Funktionalität all dieser Technologien in einem einheitlichen Programmiermodell.  Dadurch wird die Entwicklung verteilter Anwendungen vereinfacht.  
  
#### Was sind WCF Data Services?  
 Bei [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] handelt es sich um Dienste, die direkt mit einer Datenbank interagieren, sodass Sie Daten mithilfe von standardmäßigen HTTP\-Verben wie GET, POST, PUT oder DELETE zurückgeben können.  [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] sind normalerweise gut für Anwendungen geeignet, die zum Erstellen, Aktualisieren oder Löschen von Datensätzen in einer Datenbank verwendet werden.  Weitere Informationen finden Sie unter [ADO.NET Data Services\-Framework](http://go.microsoft.com/fwlink/?LinkID=119952) \(möglicherweise in englischer Sprache\).  
  
### WCF\-Programmiermodell  
 Das WCF\-Programmiermodell basiert auf der Kommunikation zwischen zwei Entitäten: einem WCF\-Dienst und einem WCF\-Client.  Das Programmiermodell ist im <xref:System.ServiceModel>\-Namespace in [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] gekapselt.  
  
#### WCF\-Dienst  
 Ein WCF\-Dienst basiert auf einer Schnittstelle, durch die ein Vertrag zwischen dem Dienst und dem Client definiert wird.  Sie ist mit einem <xref:System.ServiceModel.ServiceContractAttribute>\-Attribut markiert, wie im folgenden Code dargestellt:  
  
 [!code-cs[WCFWalkthrough#6](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.cs)]
 [!code-vb[WCFWalkthrough#6](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.vb)]  
  
 [!code-cs[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.cs)]
 [!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.vb)]  
  
 Sie definieren von einem WCF\-Dienst verfügbar gemachte Funktionen oder Methoden, indem Sie sie mit einem <xref:System.ServiceModel.OperationContractAttribute>\-Attribut markieren.  Außerdem können Sie serialisierte Daten verfügbar machen, indem Sie einen zusammengesetzten Typ mit einem <xref:System.Runtime.Serialization.DataContractAttribute>\-Attribut markieren.  Dadurch wird die Datenbindung in einem Client ermöglicht.  
  
 Nachdem eine Schnittstelle und die zugehörigen Methoden definiert wurden, werden sie in einer Klasse gekapselt, durch die die Schnittstelle implementiert wird.  Eine einzelne WCF\-Dienstklasse kann mehrere Dienstverträge implementieren.  
  
 Ein WCF\-Dienst wird verfügbar gemacht, damit er von einem so genannten *Endpunkt* verwendet werden kann.  Der Endpunkt stellt die einzige Möglichkeit zur Kommunikation mit dem Dienst dar. Es ist nicht möglich, über einen direkten Verweis auf den Dienst zuzugreifen, wie dies bei anderen Klassen der Fall ist.  
  
 Ein Endpunkt besteht aus einer Adresse, einer Bindung und einem Vertrag.  Durch die Adresse wird festgelegt, wo sich ein Dienst befindet: unter einer URL, einer FTP\-Adresse, einem Netzwerkpfad oder lokalen Pfad.  Eine Bindung legt fest, wie Sie mit dem Dienst kommunizieren.  WCF\-Bindungen bieten ein vielseitiges Modell zum Angeben eines Protokolls wie HTTP oder FTP, eines Sicherheitsmechanismus wie der Windows\-Authentifizierung bzw. von Benutzernamen und Kennwörtern und vielem mehr.  Ein Vertrag umfasst die Vorgänge, die von der WCF\-Dienstklasse verfügbar gemacht werden.  
  
 Für einen einzelnen WCF\-Dienst können mehrere Endpunkte verfügbar gemacht werden.  Dies ermöglicht es verschiedenen Clients, auf unterschiedliche Weise mit demselben Dienst zu kommunizieren.  Beispielsweise kann ein Dienst für Bankgeschäfte einen Endpunkt für Bankangestellte und einen weiteren für externe Kunden bereitstellen, wobei jede Gruppe eine andere Adresse, Bindung und\/oder einen anderen Vertrag verwendet.  
  
#### WCF\-Client  
 Ein WCF\-Client besteht aus einem *Proxy*, durch den eine Anwendung mit einem WCF\-Dienst kommunizieren kann, und einem Endpunkt, der einem für den Dienst definierten Endpunkt entspricht.  Der Proxy wird auf Clientseite in der Datei app.config generiert und enthält Informationen über die vom Service verfügbar gemachten Typen und Methoden.  Bei Diensten, die mehrere Endpunkte verfügbar machen, kann der Client den am besten geeigneten Dienst auswählen, beispielsweise für die Kommunikation über HTTP und die Verwendung der Windows\-Authentifizierung.  
  
 Nachdem ein WCF\-Client erstellt wurde, können Sie im Code auf den Dienst wie auf jedes andere Objekt verweisen.  Um z. B. die oben veranschaulichte `GetData`\-Methode aufzurufen, würden Sie mit dem folgenden Beispiel vergleichbaren Code schreiben:  
  
 [!code-cs[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.cs)]
 [!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.vb)]  
  
## WCF\-Tools in Visual Studio  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 2008 bietet Tools, die Sie beim Erstellen sowohl von WCF\-Diensten als auch von WCF\-Clients unterstützen.  Eine exemplarische Vorgehensweise zur Veranschaulichung der Tools finden Sie unter [Walkthrough: Creating and Accessing WCF Services](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md).  
  
### Erstellen und Testen von WCF\-Diensten  
 Sie können die WCF\-Vorlagen in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] als Grundlage verwenden, um schnell einen eigenen Dienst zu erstellen.  Anschließend können Sie den Dienst mithilfe des automatischen Hosts des WCF\-Diensts und WCF\-Testclients debuggen und testen.  Zusammen bieten diese Tools einen schnellen, zweckmäßigen Debug\- und Testzyklus und vermeiden, dass in einer frühen Phase ein Commit für ein Hostmodell ausgeführt werden muss.  
  
#### WCF\-Vorlagen  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-WCF\-Vorlagen stellen eine grundlegende Klassenstruktur zur Dienstentwicklung bereit.  Im Dialogfeld **Neues Projekt hinzufügen** stehen mehrere WCF\-Vorlagen zur Verfügung.  Dazu gehören WCF\-Dienstbibliotheksprojekte, WCF\-Dienstwebwebsites und WCF\-Dienstelementvorlagen.  
  
 Wenn Sie eine Vorlage auswählen, werden Dateien für einen Dienstvertrag, eine Dienstimplementierung und eine Dienstkonfiguration hinzugefügt.  Alle erforderlichen Attribute wurden bereits hinzugefügt, wodurch ein einfacher Dienst vom Typ "Hello World" erstellt wurde und Sie keinerlei Code schreiben mussten.  Natürlich würden Sie zur Bereitstellung von Funktionen und Methoden für einen echten Dienst weiteren Code hinzufügen, die Vorlage stellt jedoch die grundlegende Basis bereit.  
  
 Weitere Informationen über WCF\-Vorlagen finden Sie unter [WCF Visual Studio\-Vorlagen](../Topic/WCF%20Visual%20Studio%20Templates.md).  
  
#### WCF\-Diensthost  
 Wenn Sie den [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Debugger \(durch Drücken von F5\) für ein WCF\-Dienstprojekt starten, wird das Tool für den WCF\-Diensthost automatisch gestartet, um den Dienst lokal zu hosten.  Der WCF\-Diensthost listet die Dienste in einem WCF\-Dienstprojekt auf, lädt die Projektkonfiguration und instanziiert einen Host für jeden gefundenen Dienst.  
  
 Mithilfe des WCF\-Diensthosts können Sie einen WCF\-Dienst testen, ohne dass zusätzlicher Code geschrieben oder während der Entwicklung ein Commit für einen bestimmten Host ausgeführt werden muss.  
  
 Weitere Informationen über den WCF\-Diensthost finden Sie unter [WCF\-Diensthost \(WcfSvcHost.exe\)](../Topic/WCF%20Service%20Host%20\(WcfSvcHost.exe\).md).  
  
#### WCF\-Testclient  
 Mit dem WCF\-Testclienttool können Sie Testparameter eingeben, diese Eingabe an einen WCF\-Dienst senden und die vom Dienst zurückgesendete Antwort anzeigen.  In Kombination mit dem WCF\-Diensthost bietet das Tool eine benutzerfreundliche Lösung zum Testen von Diensten.  
  
 Wenn Sie F5 drücken, um ein WCF\-Dienstprojekt zu debuggen, wird der WCF\-Testclient geöffnet und eine Liste der in der Konfigurationsdatei definierten Dienstendpunkte angezeigt.  Sie können die Parameter testen und den Dienst starten und dieses Verfahren wiederholen, um Dienste kontinuierlich zu testen und zu überprüfen.  
  
 Weitere Informationen über den WCF\-Testclient finden Sie unter [WCF\-Testclient \(WcfTestClient.exe\)](../Topic/WCF%20Test%20Client%20\(WcfTestClient.exe\).md).  
  
### Zugreifen auf WCF\-Dienste in Visual Studio  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] vereinfacht die Aufgabe beim Erstellen von WCF\-Clienten und automatisch generiert einen Proxy und einen Endpunkt für Dienste, die Sie hinzufügen, indem Sie das Dialogfeld **Dienstverweis hinzufügen** verwenden.  Alle erforderlichen Konfigurationsinformationen werden der Datei "app.config" hinzugefügt. In den meisten Fällen muss der Dienst nur instanziiert werden, um ihn verwenden zu können.  
  
 Im Dialogfeld **Dienstverweis hinzufügen** können Sie die Adresse eines Dienstes eingeben oder einen in der Projektmappe definierten Dienst suchen.  Das Dialogfeld gibt eine Liste von Diensten sowie von Vorgängen zurück, die von diesen Diensten bereitgestellt werden.  Außerdem können Sie den Namespace definieren, durch den Sie im Code auf die Dienste verweisen.  
  
 Das Dialogfeld **Dienstverweis konfigurieren** ermöglicht es Ihnen, die Konfiguration für einen Dienst anzupassen.  Sie können die Adresse eines Diensts ändern, Zugriffsebene, asynchrones Verhalten und Meldungsvertragstypen festlegen und die Wiederverwendung von Typen konfigurieren.  
  
## Gewusst wie: Wählen Sie einen Dienstendpunkt aus  
 Einige WCF \(Windows Communication Foundation\)\-Dienste machen mehrere Endpunkte verfügbar, über die ein Client mit dem Dienst kommunizieren kann.  Beispielsweise könnte ein Dienst einen Endpunkt verfügbar machen, der eine HTTP\-Bindung und Benutzername\/Kennwort\-Sicherheit verwendet, und einen zweiten Endpunkt, der FTP und Windows\-Authentifizierung verwendet.  Der erste Endpunkt könnte von Anwendungen verwendet werden, die von außerhalb einer Firewall auf den Dienst zugreifen, während der zweite in einem Intranet verwendet werden könnte.  
  
 In einem solchen Fall kann `endpointConfigurationName` als Parameter für den Konstruktor eines Dienstverweises angegeben werden.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### So wählen Sie einen Dienstendpunkt aus  
  
1.  Fügen Sie einen Verweis auf einen WCF\-Dienst hinzu.  Weitere Informationen finden Sie unter [How to: Add, Update, or Remove a Service Reference](../Topic/How%20to:%20Add,%20Update,%20or%20Remove%20a%20Service%20Reference.md).  
  
2.  Fügen Sie im Code\-Editor einen Konstruktor für den Dienstverweis hinzu:  
  
    ```vb#  
    Dim proxy As New ServiceReference.Service1Client(  
    ```  
  
    ```c#  
    ServiceReference.Service1Client proxy = new ServiceReference.Service1Client(  
    ```  
  
    > [!NOTE]
    >  Ersetzen Sie *ServiceReference* durch den Namespace für den Dienstverweis, und ersetzen Sie *Service1Client* durch den Namen des Diensts.  
  
3.  Eine IntelliSense\-Liste mit den Überladungen für den Konstruktor wird angezeigt.  Wählen Sie die Überladung `endpointConfigurationName As String` aus.  
  
4.  Nach der Überladung geben Sie `=` *ConfigurationName* ein, wobei *ConfigurationName* der Name des Endpunkts ist, den Sie verwenden möchten.  
  
    > [!NOTE]
    >  Die Namen der verfügbaren Endpunkte finden Sie in der Datei app.config.  
  
#### So finden Sie die verfügbaren Endpunkte eines WCF\-Diensts  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf die Datei app.config des Projekts, das den Dienstverweis enthält, und klicken Sie dann auf **Öffnen**.  Die Datei wird im Code\-Editor angezeigt.  
  
2.  Suchen Sie das `<Client>`\-Tag in der Datei.  
  
3.  Suchen Sie unterhalb des `<Client>`\-Tags nach einem Tag, das mit `<Endpoint>` beginnt.  
  
     Wenn der Dienstverweis mehrere Endpunkte bereitstellt, sind zwei oder mehr `<Endpoint`\-Tags vorhanden.  
  
4.  Im `<EndPoint>`\-Tag befindet sich ein `name="`*SomeService*`"`\-Parameter \(wobei *SomeService* ein Endpunktname ist\).  Dies ist der Name für den Endpunkt, der der Überladung `endpointConfigurationName As String` eines Konstruktors eines Dienstverweises übergeben werden kann.  
  
## Gewusst wie: Rufen Sie eine Dienst\-Methode asynchron an  
 Die meisten Methoden in WCF \(Windows Communication Foundation\)\-Diensten können entweder synchron oder asynchron aufgerufen werden.  Durch ansynchrones Aufrufen kann eine Anwendung bei einer langsamen Verbindung weiter ausgeführt werden, während die Methode aufgerufen wird.  
  
 Wird einem Projekt ein Dienstverweis hinzugefügt, wird er standardmäßig für den synchronen Aufruf von Methoden konfiguriert.  Sie können dieses Verhalten auf asynchrone Methodenaufrufe umstellen, indem Sie eine Einstellung im Dialogfeld **Dienstverweis konfigurieren** ändern.  
  
> [!NOTE]
>  Diese Option wird für jeden Dienst gesondert festgelegt.  Wenn eine Methode für einen Dienst asynchron aufgerufen wird, müssen alle Methoden asynchron aufgerufen werden.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### So wird eine Dienstmethode asynchron aufgerufen  
  
1.  Wählen Sie den Dienstverweis im **Projektmappen\-Explorer** aus.  
  
2.  Klicken Sie im Menü **Projekt** auf **Dienstverweis konfigurieren**.  
  
3.  Aktivieren Sie im Dialogfeld **Dienstverweis konfigurieren** das Kontrollkästchen **Asynchrone Vorgänge generieren**.  
  
## Gewusst wie: Binden Sie die Daten, die von einem Dienst zurückgegeben werden  
 Sie können die von einem WCF \(Windows Communication Foundation\)\-Dienst zurückgegebenen Daten genauso wie jede andere Datenquelle an ein Steuerelement binden.  Wenn Sie einen Verweis auf einen WCF\-Dienst hinzufügen und dieser Dienst zusammengesetzte Typen zum Zurückgeben von Daten enthält, werden sie automatisch dem Fenster **Datenquellen** hinzugefügt.  
  
#### So binden Sie ein Steuerelement an ein von einem WCF\-Dienst zurückgegebenes einzelnes Datenfeld  
  
1.  Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.  Das Fenster **Datenquellen** wird angezeigt.  
  
2.  Erweitern Sie im Fenster **Datenquellen** den Knoten für den Dienstverweis.  Alle von dem Dienst zurückgegebenen zusammengesetzten Typen werden angezeigt.  
  
3.  Erweitern Sie einen Knoten für einen Typ.  Die Datenfelder für diesen Typ werden angezeigt.  
  
4.  Wählen Sie ein Feld aus, und klicken Sie auf den Dropdownpfeil, um eine Liste mit Steuerelementen anzuzeigen, die für diesen Datentyp verfügbar sind.  
  
5.  Klicken Sie auf den Typ von Steuerelement, an das Sie Daten binden möchten.  
  
6.  Ziehen Sie das Feld auf ein Formular.  Das Steuerelement wird dem Formular zusammen mit einer <xref:System.Windows.Forms.BindingSource>\-Komponente und einer <xref:System.Windows.Forms.BindingNavigator>\-Komponente hinzugefügt.  
  
7.  Wiederholen Sie die Schritte 4 bis 6 für alle weiteren Felder, die Sie binden möchten.  
  
#### So binden Sie ein Steuerelement an einen von einem WCF\-Dienst zurückgegebenen zusammengesetzten Typ  
  
1.  Wählen Sie im Menü **Daten** die Option **Datenquellen anzeigen** aus.  Das Fenster **Datenquellen** wird angezeigt.  
  
2.  Erweitern Sie im Fenster **Datenquellen** den Knoten für den Dienstverweis.  Alle von dem Dienst zurückgegebenen zusammengesetzten Typen werden angezeigt.  
  
3.  Wählen Sie einen Knoten für einen Typ aus, und klicken Sie auf den Dropdownpfeil, um eine Liste der verfügbaren Optionen anzuzeigen.  
  
4.  Klicken Sie auf **DataGridView**, um die Daten in einem Raster anzuzeigen, oder auf **Details**, um die Daten in einzelnen Steuerelementen anzuzeigen.  
  
5.  Ziehen Sie den Knoten auf das Formular.  Die Steuerelemente werden dem Formular zusammen mit einer <xref:System.Windows.Forms.BindingSource>\-Komponente und einer <xref:System.Windows.Forms.BindingNavigator>\-Komponente hinzugefügt.  
  
## Gewusst wie: Konfigurieren eines Diensts Wiederverwendung vorhandener Typen  
 Wenn einem Projekt ein Dienstverweis hinzugefügt wird, werden alle in dem Dienst definierten Typen im lokalen Projekt generiert.  In vielen Fällen werden dabei doppelte Typen erstellt, wenn ein Dienst gebräuchliche [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Typen verwendet oder wenn Typen in einer gemeinsam genutzten Bibliothek definiert sind.  
  
 Um dieses Problem zu vermeiden, werden Typen in referenzierten Assemblys standardmäßig freigegeben.  Wenn Sie die Typfreigabe für eine oder mehrere Assemblys deaktivieren möchten, können Sie dies im Dialogfeld **Dienstverweis konfigurieren** durchführen.  
  
#### So deaktivieren Sie die Typfreigabe in einer einzelnen Assembly  
  
1.  Wählen Sie den Dienstverweis im **Projektmappen\-Explorer** aus.  
  
2.  Klicken Sie im Menü **Projekt** auf **Dienstverweis konfigurieren**.  
  
3.  Wählen Sie im Dialogfeld **Dienstverweis konfigurieren** die Option **Typen in folgenden Assemblys, auf die verwiesen wird, wiederverwenden** aus.  
  
4.  Aktivieren Sie das Kontrollkästchen für jede Assembly, in der Sie die Typfreigabe aktivieren möchten.  Zum Deaktivieren der Typfreigabe für eine Assembly lassen Sie das Kontrollkästchen leer.  
  
#### So deaktivieren Sie die Typfreigabe in allen Assemblys  
  
1.  Wählen Sie den Dienstverweis im **Projektmappen\-Explorer** aus.  
  
2.  Klicken Sie im Menü **Projekt** auf **Dienstverweis konfigurieren**.  
  
3.  Deaktivieren Sie im Dialogfeld **Dienstverweis konfigurieren** das Kontrollkästchen **Typen in Assemblys, auf die verwiesen wird, wiederverwenden**.  
  
## Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|------------------|  
|[Walkthrough: Creating and Accessing WCF Services](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md)|Stellt ein Schritt\-für\-Schritt\-Beispiel zum Erstellen und Verwenden von WCF\-Diensten in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bereit.|  
|[Walkthrough: Creating and Accessing a WCF Data Service in Visual Studio](../data-tools/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework.md)|Enthält ein Schritt\-für\-Schritt\-Beispiel zum Erstellen und Verwenden von [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|[Verwenden der WCF\-Entwicklungstools](../Topic/Using%20the%20WCF%20Development%20Tools.md)|Erläutert, wie WCF\-Dienste in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] erstellt und getestet werden.|  
|[How to: Add, Update, or Remove a Service Reference](../Topic/How%20to:%20Add,%20Update,%20or%20Remove%20a%20Service%20Reference.md)|Beschreibt, wie WCF\-Dienste in einem Projekt hinzugefügt, aktualisiert oder entfernt werden.|  
|[How to: Add, Update, or Remove a WCF Data Service Reference](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)|Erläutert, wie [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] verwendet werden und wie auf sie verwiesen wird.|  
|[How to: Add a Reference to a Web Service](../Topic/How%20to:%20Add%20a%20Reference%20to%20a%20Web%20Service.md)|Beschreibt, wie Sie einem Projekt einen Verweis auf einen XML \(ASMX\)\-Webdienst hinzufügen.|  
|[Troubleshooting Service References](../data-tools/troubleshooting-service-references.md)|Beschreibt einige häufig auftretende Fehler bei Dienstverweisen sowie Methoden zur Problembehandlung.|  
|[Debuggen von WCF\-Diensten](../debugger/debugging-wcf-services.md)|Beschreibt allgemeine Debugprobleme und \-verfahren für WCF\-Dienste.|  
|[Windows Communication Foundation Authentication Service Overview](../Topic/Windows%20Communication%20Foundation%20Authentication%20Service%20Overview.md)|Beschreibt, wie WCF verwendet wird, um einen Rollendienst für eine Website bereitzustellen.|  
|[Messaging in the .NET Compact Framework](http://msdn.microsoft.com/de-de/fb74d82c-f81e-46f9-aceb-f875c5c6be4f)|Erläutert die Unterstützung für die WCF\-Messagingebene in .NET Compact Framework.|  
|[Exemplarische Vorgehensweise: Erstellen einer N\-Tier\-Datenanwendung](../data-tools/walkthrough-creating-an-n-tier-data-application.md)|Enthält schrittweise Anweisungen zum Erzeugen eines typisierten DataSets und zur Aufteilung des TableAdapter\-Codes und des DataSet\-Codes in mehrere Projekte.|  
|[Add Service Reference Dialog Box](../Topic/Add%20Service%20Reference%20Dialog%20Box.md)|Beschreibt die Benutzeroberflächenelemente des Dialogfelds **Dienstverweis hinzufügen**.|  
|[Dialogfeld "Dienstverweis konfigurieren"](../data-tools/configure-service-reference-dialog-box.md)|Beschreibt die Benutzeroberflächenelemente des Dialogfelds **Dienstverweis konfigurieren**.|  
  
## Verweis  
 <xref:System.ServiceModel>  
  
 <xref:System.Data.Services>
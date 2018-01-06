---
title: Windows Communication Foundation-Dienste und WCF Data Services in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- services, WCF Data
- WCF services, binding to
- WCF services, asynchronous service methods
- service references [Visual Studio]
- WCF Data Services
- asynchronous calls
- service references [Visual Studio], type sharing
- endpoints [WCF]
- asynchronous service methods
- service references [Visual Studio] endpoints
- WCF services, type sharing
- Windows Communication Foundation, in Visual Studio
- services, WCF
- WCF service, Visual Studio
- data services, WCF
- services, in Visual Studio
- data binding [Visual Studio], WCF
- service endpoints [Visual Studio]
- service references [Visual Studio], asynchronous calls
- services, Windows Communication Foundation
- type sharing in WCF services
- WCF services, endpoints
- service method, called asynchronously[Visual Studio]
ms.assetid: d56f12cb-e139-4fec-b3e4-488383356642
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 898cdbd15367aef6ac48d35a44b1ccb4a3deded9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="windows-communication-foundation-services-and-wcf-data-services-in-visual-studio"></a>Windows Communication Foundation-Dienste und WCF Data Services in Visual Studio
Visual Studio enthält Tools zum Arbeiten mit der Windows Communication Foundation (WCF) und [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)], Microsoft-Technologien zum Erstellen von verteilten Anwendungen. Dieses Thema enthält eine Einführung in die Dienste aus einer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Perspektive. Die vollständige Dokumentation finden Sie unter [WCF Data Services 4.5](/dotnet/framework/data/wcf/index).  
  
## <a name="what-is-wcf"></a>Was ist WCF?  
 [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)]ist ein einheitliches Framework zum Erstellen von sicheren, zuverlässigen transaktive und interoperabler verteilte Anwendungen. Er ersetzt die ältere prozessübergreifende Kommunikation-Technologien wie ASMX-Webdienste, .NET Remoting, Enterprise Services (DCOM) und MSMQ. WCF vereint die Funktionen dieser Technologien für die unter ein einheitliches Programmiermodell. Dies vereinfacht die Erfahrung der Entwicklung von verteilten Anwendungen.  
  
#### <a name="what-are-wcf-data-services"></a>Was sind WCF Data Services  
 [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]ist eine Implementierung des Open Data (OData)-Protokolls standard.  WCF Data Services können, die Sie Tabellendaten als Satz von REST-APIs, sodass Sie zum Zurückgeben von Daten mithilfe von standardmäßigen HTTP-Verben wie GET, POST, PUT oder Löschen verfügbar machen. Auf der Serverseite werden von WCF Data Services abgelöst wird [ASP.NET Web API](http://www.asp.net/web-api) zum Erstellen von neuer OData-Diensten. Die WCF Data Services-Clientbibliothek weiterhin eine gute Wahl für die Nutzung von OData-Dienste in einer .NET-Anwendung aus Visual Studio (**Projekt &#124; Hinzufügen eines Dienstverweises**). Weitere Informationen finden Sie unter [WCF Data Services 4.5](http://go.microsoft.com/fwlink/?LinkID=119952).  
  
### <a name="wcf-programming-model"></a>WCF-Programmiermodell  
 Das WCF-Webprogrammiermodell basiert darauf, dass die Kommunikation zwischen zwei Entitäten: einen WCF-Dienst und einem WCF-Client. Das Programmiermodell gekapselt ist, der <xref:System.ServiceModel> Namespace in der [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
#### <a name="wcf-service"></a>WCF-Dienst  
 Ein WCF-Dienst basiert auf einer Schnittstelle, die ein Vertrag zwischen dem Dienst und dem Client definiert. Sie wird markiert, mit einem <xref:System.ServiceModel.ServiceContractAttribute> Attribut, wie im folgenden Code dargestellt:  
  
 [!code-csharp[WCFWalkthrough#6](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.cs)]
 [!code-vb[WCFWalkthrough#6](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.vb)]  
  
 [!code-csharp[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.cs)]
 [!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.vb)]  
  
 Sie definieren, Funktionen oder Methoden, die von einem WCF-Dienst verfügbar gemacht werden, durch die Markierung mit einem <xref:System.ServiceModel.OperationContractAttribute> Attribut. Darüber hinaus können Sie serialisierte Daten verfügbar machen, durch die Markierung eines zusammengesetzten Typs mit einem <xref:System.Runtime.Serialization.DataContractAttribute> Attribut. Dies ermöglicht die Datenbindung in einem Client.  
  
 Nachdem eine Schnittstelle und seine Methoden definiert sind, werden sie in einer Klasse gekapselt, die die Schnittstelle implementiert. Eine einzelne WCF-Dienstklasse kann mehrere Dienstverträge implementieren.  
  
 Ein WCF-Dienst wird verfügbar gemacht, für Sie Verbrauch durch was genannt wird ein *Endpunkt*. Der Endpunkt stellt die einzige Möglichkeit, mit dem Dienst kommunizieren; Sie können nicht den Dienst über keinen direkten Verweis zugreifen, wie bei anderen Klassen aus.  
  
 Ein Endpunkt besteht aus einer Adresse, einer Bindung und einem Vertrag. Die Adresse definiert, in dem der Dienst befindet. Dies kann eine URL, eine FTP-Adresse, Netzwerk oder ein lokaler Pfad sein. Eine Bindung definiert die Möglichkeit, die Sie mit dem Dienst kommunizieren. WCF-Bindungen bieten eine vielseitige Modell für ein Protokoll wie z. B. HTTP oder FTP, einen Sicherheitsmechanismus wie Windows-Authentifizierung oder Benutzernamen und Kennwörter angeben und vieles mehr. Ein Vertrag enthält die Vorgänge, die von der WCF-Dienstklasse verfügbar gemacht werden.  
  
 Mehrere Endpunkte können für einen einzelnen WCF-Dienst verfügbar gemacht werden. Dadurch wird anderen Clients die Kommunikation mit dem gleichen Dienst auf unterschiedliche Weise. Beispielsweise könnte ein Banking-Dienst geben Sie einen Endpunkt für Mitarbeiter und ein anderes für externe Kunden jeweils mit einer anderen Adresse, Bindung, und/oder Vertrag.  
  
#### <a name="wcf-client"></a>WCF-Client  
 Ein WCF-Client besteht aus einem *Proxy* mit der eine Anwendung für die Kommunikation mit einem WCF-Dienst und ein Endpunkt, der einen Endpunkt übereinstimmt, die für den Dienst definierten. Der Proxy wird in der Datei "App.config" auf dem Client generiert und enthält Informationen über die Typen und Methoden, die vom Dienst verfügbar gemacht werden. Für Dienste, die mehrere Endpunkte verfügbar machen, kann der Client das Zertifikat auszuwählen, die am besten der Anforderungen, z. B. über HTTP kommunizieren und Windows-Authentifizierung verwenden.  
  
 Nachdem ein WCF-Client erstellt wurde, verweisen Sie den Dienst in Ihrem Code genau wie ein anderes Objekt. Beispielsweise rufen Sie die `GetData` -Methode, Schreiben Sie Code, der die folgenden ähnelt:  
  
 [!code-csharp[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.cs)]
 [!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.vb)]  
  
## <a name="wcf-tools-in-visual-studio"></a>WCF-Tools in Visual Studio  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]bietet Tools, mit denen Sie die WCF-Dienste und WCF-Clients zu erstellen. Eine exemplarische Vorgehensweise, die die Tools veranschaulicht, finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines einfachen WCF-Diensts in Windows Forms](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md).  
  
### <a name="creating-and-testing-wcf-services"></a>Erstellen und Testen von WCF-Dienste  
 Sie können die WCF [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Vorlagen als Grundlage verwenden, um schnell einen eigenen Dienst zu erstellen. Sie können dann WCF-Dienst-Auto-Host und WCF-Testclient verwenden, Debuggen und Testen Sie den Dienst. Diese Tools bieten eine schnelle und bequeme Debug- und Testzyklus zusammen und die Anforderung an, für eine hosting-Modell in einem frühen Stadium zu übernehmen.  
  
#### <a name="wcf-templates"></a>WCF-Vorlagen  
 WCF [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Vorlagen stellen eine grundlegende Klassenstruktur zur Dienstentwicklung bereit. Es stehen mehrere WCF-Vorlagen in der **neues Projekt hinzufügen** (Dialogfeld). Dazu gehören WCF-Dienstbibliotheksprojekte, WCF-Dienst-Websites und WCF-Dienst-Elementvorlagen.  
  
 Wenn Sie eine Vorlage auswählen, werden die Dateien für einen Dienstvertrag, einer dienstimplementierung und eine Dienstkonfiguration hinzugefügt. Alle erforderlichen Attribute wurden bereits hinzugefügt, erstellen einen einfache "Hello World"-Typ des Diensts, und Sie keinen Code schreiben. Sie werden natürlich Code hinzufügen, um Funktionen und-Methoden für Ihren Dienst realen bereitstellen möchten, aber die Vorlagen bieten die grundlegenden Foundation.  
  
 Weitere Informationen zu WCF-Vorlagen finden Sie unter [WCF Visual Studio-Vorlagen](/dotnet/framework/wcf/wcf-vs-templates).  
  
#### <a name="wcf-service-host"></a>WCF-Diensthost  
 Beim Starten der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] debugger (durch Drücken von F5) für eine WCF-Dienstprojekt, die WCF-Diensthost-Tool automatisch gestartet wird, um den Dienst lokal zu hosten. WCF-Diensthost listet die Dienste in einem WCF-Dienstprojekt, lädt die Projektkonfiguration und instanziiert einen Host für jeden gefundenen Dienst.  
  
 Mithilfe von WCF-Diensthost können Sie einen WCF-Dienst testen, ohne zusätzlichen Code schreiben oder an einen bestimmten Host bei der Entwicklung bereitstellen.  
  
 Weitere Informationen zu WCF-Diensthost finden Sie unter [WCF-Diensthost (WcfSvcHost.exe)](/dotnet/framework/wcf/wcf-service-host-wcfsvchost-exe).  
  
#### <a name="wcf-test-client"></a>WCF-Testclient  
 Der WCF-Testclient-Tool können Sie Testparameter, übermitteln, die Eingabe an einen WCF-Dienst, und zeigen Sie an die Antwort, die der Dienst zurücksendet. Es bietet es sich um einen geeigneten Dienst testen Sie sie mit WCF-Diensthost kombinieren. Das Tool finden Sie in den Ordner \Common7\IDE, die für Visual Studio 2015 installiert in Laufwerk "c:" sieht: **C:\Program Files (x86) \Microsoft Visual Studio 14.0\Common7\IDE\\**.  
  
 Drücken von F5 zum Debuggen eines WCF-Dienst wird von WCF-Testclient wird geöffnet und zeigt eine Liste der Endpunkte, die in der Konfigurationsdatei definiert sind. Sie können die Parameter testen und starten Sie den Dienst und wiederholen Sie diesen Vorgang, um kontinuierlich zu testen und überprüfen den Dienst.  
  
 Weitere Informationen zu WCF-Testclient finden Sie unter [WCF-Testclient (WcfTestClient.exe)](/dotnet/framework/wcf/wcf-test-client-wcftestclient-exe).  
  
### <a name="accessing-wcf-services-in-visual-studio"></a>Zugreifen auf WCF-Dienste in Visual Studio  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]vereinfacht die Aufgabe des Erstellens von WCF-Clients, generieren automatisch einen Proxy und einen Endpunkt für Dienste, die Sie hinzufügen, indem Sie mit der **Hinzufügen eines Dienstverweises** (Dialogfeld). Alle erforderlichen Konfigurationsinformationen wird die Datei "App.config" hinzugefügt. Die meisten Fällen ist, müssen Sie, den Dienst instanziieren, um es verwenden.  
  
 Die **Hinzufügen eines Dienstverweises** Dialogfeld können Sie die Adresse für einen Dienst eingeben oder nach einem Dienst zu suchen, die in der Projektmappe definiert wird. Das Dialogfeld gibt eine Liste von Diensten und die Vorgänge, die von diesen Diensten bereitgestellt werden. Darüber hinaus können Sie den Namespace definieren, mit dem Sie die Dienste im Code verweist.  
  
 Die **Dienstverweis** Dialogfeld können Sie die Konfiguration für einen Dienst anzupassen. Sie können die Adresse für einen Dienst ändern, Zugriffsebene, asynchrones Verhalten und Nachrichtenvertragstypen angeben und Wiederverwendung von konfigurieren.  
  
## <a name="how-to-select-a-service-endpoint"></a>Vorgehensweise: Auswählen eines Dienstendpunkts  
Einige Windows Communication Foundation (WCF)-Dienste verfügbar machen mehrere Endpunkte, die über die ein Client mit dem Dienst kommunizieren kann. Z. B. ein Dienst ist zur Verfügung stellt einen Endpunkt, der ein HTTP-Bindung und ein beispielbenutzername verwendet / kennwortsicherheit und einen zweiten Endpunkt, der FTP- und Windows-Authentifizierung verwendet. Der erste Endpunkt kann von Anwendungen, die Zugriff auf den Dienst aus außerhalb einer Firewall verwendet werden, während das zweite in einem Intranet verwendet werden kann.  
  
In diesem Fall können Sie angeben der `endpointConfigurationName` als Parameter an den Konstruktor für einen Dienstverweis.  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-select-a-service-endpoint"></a>Wählen Sie einen Dienstendpunkt  
  
1.  Einen Verweis auf einen WCF-Dienst hinzufügen, indem Sie mit der rechten Maustaste im Projektmappen-Explorer des Projektknoten und **Hinzufügen eines Dienstverweises**.
  
2.  Fügen Sie im Code-Editor einen Konstruktor für den Dienstverweis hinzu:  
  
    ```vb  
    Dim proxy As New ServiceReference.Service1Client(  
    ```  
  
    ```csharp  
    ServiceReference.Service1Client proxy = new ServiceReference.Service1Client(  
    ```  
  
    > [!NOTE]
    >  Ersetzen Sie *ServiceReference* mit dem Namespace für den Dienstverweis und Ersetzen *Service1Client* mit dem Namen des Diensts.  
  
3.  Eine IntelliSense-Liste wird mit den Überladungen des Konstruktors angezeigt. Wählen Sie die `endpointConfigurationName As String` überladen.  
  
4.  Geben Sie nach der Überladung `=` *ConfigurationName*, wobei *ConfigurationName* ist der Name des Endpunkts, den Sie verwenden möchten.  
  
    > [!NOTE]
    >  Wenn Sie die Namen der verfügbaren Endpunkte nicht kennen, können Sie diese in der Datei "App.config" suchen.  
  
#### <a name="to-find-the-available-endpoints-for-a-wcf-service"></a>Um die verfügbaren Endpunkte für einen WCF-Dienst gefunden werden.  
  
1.  In **Projektmappen-Explorer**mit der rechten Maustaste auf die Datei "App.config" für das Projekt, das den Dienstverweis enthält, und klicken Sie dann auf **öffnen**. Die Datei wird im Code-Editor angezeigt.  
  
2.  Suchen Sie nach der `<Client>` -Tag in der Datei.  
  
3.  Suchen Sie unterhalb der `<Client>` Tag für ein Tag, die mit beginnt `<Endpoint>`.  
  
     Wenn der Dienstverweis mehrere Endpunkte enthält, werden zwei oder mehr `<Endpoint` Tags.  
  
4.  Innerhalb der `<EndPoint>` Tag Sie finden eine `name="` *SomeService* `"` Parameter (, in denen *SomeService* einen Endpunktnamen darstellt). Dies ist der Name für den Endpunkt, der übergeben werden kann die `endpointConfigurationName As String` Überladung für einen Konstruktor für einen Dienstverweis.  
  
## <a name="how-to-call-a-service-method-asynchronously"></a>Vorgehensweise: Asynchrones Aufrufen eine Dienstmethode  
Die meisten Methoden in Windows Communication Foundation (WCF)-Dienste können synchron oder asynchron aufgerufen werden. Eine Methode asynchron aufrufen, kann die Anwendung weiterhin funktionsfähig, während die Methode aufgerufen wird, wenn er über eine langsame Verbindung verwendet wird.  
  
Standardmäßig Wenn ein Projekt ein Dienstverweis hinzugefügt wird ist es so konfiguriert, dass synchron Aufrufen von Methoden. Sie können das Verhalten ändern zum Aufrufen von Methoden asynchron durch Ändern einer Einstellung in der **Dienstverweis konfigurieren** (Dialogfeld).  
  
> [!NOTE]
>  Diese Option wird auf einer pro-Dienst-Basis festgelegt. Wenn eine Methode für einen Dienst asynchron aufgerufen wird, müssen alle Methoden asynchron aufgerufen werden.  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-call-a-service-method-asynchronously"></a>Eine Dienstmethode asynchron aufrufen.  
  
1.  In **Projektmappen-Explorer**, wählen Sie den Dienstverweis.  
  
2.  Auf der **Projekt** Menü klicken Sie auf **Dienstverweis konfigurieren**.  
  
3.  In der **Dienstverweis konfigurieren** wählen Sie im Dialogfeld die **asynchrone Vorgänge generieren** Kontrollkästchen.  
  
## <a name="how-to-bind-data-returned-by-a-service"></a>Vorgehensweise: Binden von Daten, die von einem Dienst zurückgegeben werden.  
Sie können Daten von einem Windows Communication Foundation (WCF)-Dienst an ein Steuerelement zurückgegeben wird, ebenso wie jede andere Datenquelle an ein Steuerelement gebunden werden kann, binden. Wenn Sie einen Verweis auf einen WCF-Dienst hinzufügen, wenn der Dienst zusammengesetzte Typen enthält, die Daten zurückgeben, werden sie automatisch hinzugefügt die **Datenquellen** Fenster.  
  
#### <a name="to-bind-a-control-to-single-data-field-returned-by-a-wcf-service"></a>Ein Steuerelement für einen WCF-Dienst zurückgegebenes einzelnes Datenfeld gebunden.  
  
1.  Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**. Die **Datenquellen** Fenster wird angezeigt.  
  
2.  In der **Datenquellen** Fenster, erweitern Sie den Knoten für den Dienstverweis. Alle zusammengesetzten Typen, die vom Dienst zurückgegeben werden angezeigt.  
  
3.  Erweitern Sie den Knoten für einen Typ aus. Die Datenfelder für diesen Typ werden angezeigt.  
  
4.  Wählen Sie ein Feld aus, und klicken Sie auf den Dropdown-Pfeil, um eine Liste der Steuerelemente anzuzeigen, die für den Datentyp verfügbar sind.  
  
5.  Klicken Sie auf den Typ des Steuerelements, das Sie binden möchten.  
  
6.  Ziehen Sie das Feld auf das Formular. Das Steuerelement wird dem Formular zusammen mit hinzugefügt werden eine <xref:System.Windows.Forms.BindingSource> Komponente und eine <xref:System.Windows.Forms.BindingNavigator> Komponente.  
  
7.  Wiederholen Sie Schritt 4, obwohl 6 für alle anderen, die Felder Sie binden möchten.  
  
#### <a name="to-bind-a-control-to-composite-type-returned-by-a-wcf-service"></a>So binden Sie ein Steuerelement an zusammengesetzter Typ zurückgegeben, die von einem WCF-Dienst  
  
1.  Auf der **Daten** klicken Sie im Menü **Datenquellen anzeigen**. Die **Datenquellen** Fenster wird angezeigt.  
  
2.  In der **Datenquellen** Fenster, erweitern Sie den Knoten für den Dienstverweis. Alle zusammengesetzten Typen, die vom Dienst zurückgegeben werden angezeigt.  
  
3.  Wählen Sie einen Knoten für einen Typ aus, und klicken Sie auf den Dropdown-Pfeil, um eine Liste der verfügbaren Optionen anzuzeigen.  
  
4.  Klicken Sie auf **DataGridView** zum Anzeigen der Daten in einem Raster oder **Details** zum Anzeigen der Daten in einzelnen Steuerelementen.  
  
5.  Ziehen Sie den Knoten auf das Formular. Werden die Steuerelemente hinzugefügt werden, auf dem Formular zusammen mit einem <xref:System.Windows.Forms.BindingSource> Komponente und eine <xref:System.Windows.Forms.BindingNavigator> Komponente.  
  
## <a name="how-to-configure-a-service-to-reuse-existing-types"></a>Vorgehensweise: Konfigurieren eines Diensts zum Wiederverwenden vorhandener Typen  
Wenn ein Projekt ein Dienstverweis hinzugefügt wird, werden alle im Dienst definierten Typen im lokalen Projekt generiert. In vielen Fällen dabei doppelte Typen erstellt, wenn ein Dienst verwendet allgemeine [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Typen oder wenn die Typen in einer freigegebenen Bibliothek definiert wurden.  
  
Um dieses Problem zu vermeiden, werden die Typen in referenzierten Assemblys standardmäßig freigegeben. Wenn Sie die Typfreigabe für eine oder mehrere Assemblys deaktivieren möchten, Sie können dazu die **Dienstverweis** (Dialogfeld).  
  
#### <a name="to-disable-type-sharing-in-a-single-assembly"></a>Zum Deaktivieren der Typfreigabe in einer einzelnen assembly  
  
1.  In **Projektmappen-Explorer**, wählen Sie den Dienstverweis.  
  
2.  Auf der **Projekt** Menü klicken Sie auf **Dienstverweis konfigurieren**.  
  
3.  In der **Dienstverweis** wählen Sie im Dialogfeld **Typen in Assemblys, auf die verwiesen wird, wiederverwenden**.  
  
4.  Wählen Sie das Kontrollkästchen für jede Assembly, in dem Sie die Typfreigabe aktivieren möchten. Zum Deaktivieren der Typfreigabe für eine Assembly lassen Sie das Kontrollkästchen deaktiviert.  
  
#### <a name="to-disable-type-sharing-in-all-assemblies"></a>Zum Deaktivieren der Typfreigabe in allen Assemblys  
  
1.  In **Projektmappen-Explorer**, wählen Sie den Dienstverweis.  
  
2.  Auf der **Projekt** Menü klicken Sie auf **Dienstverweis konfigurieren**.  
  
3.  In der **Dienstverweis** deaktivieren Sie im Dialogfeld die **Typen in Assemblys verwiesen wird, wiederverwenden** Kontrollkästchen.  
  
## <a name="related-topics"></a>Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[Exemplarische Vorgehensweise: Erstellen eines einfachen WCF-Diensts in Windows Forms](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md)|Enthält eine schrittweise Demonstration erstellen und Verwenden von WCF-Diensten in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|[Exemplarische Vorgehensweise: Erstellen von und Zugreifen auf einen WCF-Datendienst in Visual Studio](../data-tools/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework.md)|Enthält eine schrittweise Demonstration zum Erstellen und Verwenden von [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|[Verwenden der WCF-Entwicklungstools](/dotnet/framework/wcf/using-the-wcf-development-tools)|Erläutert das Erstellen und Testen von WCF-Diensten in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
||[Gewusst wie: Hinzufügen, Aktualisieren oder Entfernen eines WCF-Datendienstverweises](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)|Erläutert, wie zum Verweisen auf und verwenden Sie [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|[Problembehandlung bei Dienstverweisen](../data-tools/troubleshooting-service-references.md)|Zeigt Dienstverweise sowie ihre Verwendung zu verhindern, dass einige häufige Fehler, die auftreten können.|  
|[Debuggen von WCF-Diensten](../debugger/debugging-wcf-services.md)|Beschreibt allgemeine Debugprobleme und Techniken, die beim Debuggen von WCF-Dienste auftreten können.|  
|[Exemplarische Vorgehensweise: Erstellen einer N-Tier-Datenanwendung](../data-tools/walkthrough-creating-an-n-tier-data-application.md)|Liefert eine Schritt-für-Schritt-Anleitung für das Erstellen eines typisierten Datasets und das Aufteilen des Codes für TableAdapter und Dataset in mehrere Projekte.|  
|[Dienstverweis konfigurieren (Dialogfeld)](../data-tools/configure-service-reference-dialog-box.md)|Beschreibt die Elemente der Benutzeroberfläche von der **Dienstverweis konfigurieren** (Dialogfeld).|  
  
## <a name="reference"></a>Verweis  
 <xref:System.ServiceModel>  
  
 <xref:System.Data.Services>  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio-Datentools für .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
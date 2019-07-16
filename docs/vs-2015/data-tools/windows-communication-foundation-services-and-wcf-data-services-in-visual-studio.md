---
title: Windows Communication Foundation-Dienste und WCF Data Services
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
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
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 68f2b400cc92673131dea2fc281b830df86019f7
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65704384"
---
# <a name="windows-communication-foundation-services-and-wcf-data-services-in-visual-studio"></a>Windows Communication Foundation-Dienste und WCF Data Services in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio enthält Tools für die Arbeit mit Windows Communication Foundation (WCF) und [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)], Microsoft-Technologien für die Erstellung verteilter Anwendungen. Dieses Thema enthält eine Einführung in die Dienste von einem [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Perspektive. Die vollständige Dokumentation finden Sie unter [WCF Data Services 4.5](https://msdn.microsoft.com/library/73d2bec3-7c92-4110-b905-11bb0462357a).

## <a name="what-is-wcf"></a>Was ist WCF?
 [!INCLUDE[vsindigo](../includes/vsindigo-md.md)] ist ein einheitliches Framework zum Erstellen von sicherer, zuverlässiger, Transaktiver und interoperabler verteilte Anwendungen. Er ersetzt ältere prozessübergreifende Kommunikation-Technologien wie ASMX Web Services, .NET Remoting, Enterprise Services (DCOM) und MSMQ. WCF vereint die Funktionalität der alle diese Technologien unter ein einheitliches Programmiermodell. Dies vereinfacht die Benutzeroberfläche der Entwicklung von verteilten Anwendungen.

#### <a name="what-are-wcf-data-services"></a>Was sind WCF Data Services
 [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] ist eine Implementierung des Open Data (OData)-Protokolls standard.  WCF Data Services können Sie die tabellarischen Daten verfügbar machen, als eine Reihe von REST-APIs, sodass Sie zurückgegeben wird, dass die Daten mithilfe von HTTP-Standardverben wie GET, POST, PUT oder DELETE. Klicken Sie auf der Serverseite werden durch WCF Data Services ersetzt wird [ASP.NET Web-API](http://www.asp.net/web-api) zum Erstellen von neuer OData-Diensten. Die WCF Data Services-Clientbibliothek ist weiterhin eine gute Wahl für die Nutzung von OData-Dienste in einer .NET-Anwendung aus Visual Studio (**Projekt &#124; Hinzufügen eines Dienstverweises**). Weitere Informationen finden Sie unter [WCF Data Services 4.5](http://go.microsoft.com/fwlink/?LinkID=119952).

### <a name="wcf-programming-model"></a>WCF-Programmiermodell
 Das Programmiermodell von WCF basiert darauf, dass Kommunikation zwischen zwei Entitäten: eine WCF-Dienst und einen WCF-Client. Das Programmiermodell gekapselt ist, der <xref:System.ServiceModel> -Namespace in der [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

#### <a name="wcf-service"></a>WCF-Dienst
 Ein WCF-Dienst basiert auf einer Schnittstelle, die einen Vertrag zwischen dem Dienst und dem Client definiert. Gekennzeichnet mit einem <xref:System.ServiceModel.ServiceContractAttribute> Attribut, wie im folgenden Code gezeigt:

 [!code-csharp[WCFWalkthrough#6](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1.cs#6)]
 [!code-vb[WCFWalkthrough#6](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1.vb#6)]

 [!code-csharp[WCFWalkthrough#1](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1.cs#1)]
 [!code-vb[WCFWalkthrough#1](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1.vb#1)]

 Sie definieren Funktionen oder Methoden, die von einem WCF-Dienst verfügbar gemacht werden, durch Markieren sie mit einem <xref:System.ServiceModel.OperationContractAttribute> Attribut. Darüber hinaus können Sie serialisierte Daten bereitstellen, indem Sie markieren einen zusammengesetzten Typ mit einem <xref:System.Runtime.Serialization.DataContractAttribute> Attribut. Dies ermöglicht die Datenbindung in einem Client.

 Nachdem Sie eine Schnittstelle und die zugehörigen Methoden definiert sind, werden sie in einer Klasse gekapselt, die die Schnittstelle implementiert. Eine einzelne Klasse des WCF-Dienst kann mehrere Dienstverträge implementieren.

 Ein WCF-Dienst wird verfügbar gemacht, für die Nutzung durch was genannt wird ein *Endpunkt*. Der Endpunkt stellt die einzige Möglichkeit, mit dem Dienst kommunizieren; Sie können nicht über einen direkten Verweis den Dienst zugreifen, wie Sie mit anderen Klassen tun würden.

 Ein Endpunkt besteht aus einer Adresse, einer Bindung und einen Vertrag. Die Adresse definiert, in dem der Dienst befindet. Dies kann eine URL, eine FTP-Adresse, Netzwerk oder ein lokaler Pfad sein. Eine Bindung definiert die Methode, die Sie mit dem Dienst kommunizieren. WCF-Bindungen bieten ein vielseitiges Modell für die Angabe eines Protokolls wie HTTP oder FTP, einen Sicherheitsmechanismus, z. B. Windows-Authentifizierung oder mit Benutzernamen und Kennwörtern, und vieles mehr. Ein Vertrag umfasst die Vorgänge, die von der WCF-Dienst-Klasse verfügbar gemacht werden.

 Mehrere Endpunkte können für einen einzelnen WCF-Dienst verfügbar gemacht werden. Dadurch können unterschiedliche Clients kommunizieren mit den gleichen Dienst auf verschiedene Arten. Ein Banking-Dienst kann z. B. Geben Sie einen Endpunkt für Mitarbeiter und eine für externe Kunden jeweils eine andere Adresse, Bindung, verwenden und/oder Vertrag.

#### <a name="wcf-client"></a>WCF-Client
 Ein WCF-Client besteht aus einem *Proxy* , ermöglicht einer Anwendung für die Kommunikation mit einem WCF-Dienst und ein Endpunkt, der einem Endpunkt entspricht, die für den Dienst definiert. Der Proxy wird in der Datei "App.config" auf dem Client generiert und enthält Informationen über die Typen und Methoden, die vom Dienst verfügbar gemacht werden. Für Dienste, die mehrere Endpunkte verfügbar machen, kann der Client den auswählen, die am besten ihre Anforderungen, z. B., kommunizieren über HTTP und Windows-Authentifizierung verwenden.

 Nachdem Sie ein WCF-Client erstellt wurde, verweisen Sie auf den Dienst in Ihrem Code wie jedes andere Objekt. Beispielsweise rufen Sie die `GetData` -Methode, würden Sie Code, der ähnlich wie die folgende schreiben:

 [!code-csharp[WCFWalkthrough#3](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/form1.cs#3)]
 [!code-vb[WCFWalkthrough#3](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/form1.vb#3)]

## <a name="wcf-tools-in-visual-studio"></a>WCF-Tools in Visual Studio
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bietet Tools zum Erstellen von WCF-Dienste und WCF-Clients. Eine exemplarische Vorgehensweise, die die Tools veranschaulicht, finden Sie unter [Exemplarische Vorgehensweise: Erstellen einen einfachen WCF-Dienst in Windows Forms](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md).

### <a name="creating-and-testing-wcf-services"></a>Erstellen und Testen von WCF-Dienste
 Sie können die WCF verwenden [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Vorlagen als Grundlage verwenden, um schnell Ihre eigenen Dienst zu erstellen. Dann können WCF-Dienst-Auto-Host und WCF-Testclient zum Debuggen und Testen Sie den Dienst. Diese Tools Geben Sie einen schnellen und komfortablen Debug- und Testzyklus zusammen und vermeiden, dass eine hosting-Modell in einer frühen Phase zu übergeben.

#### <a name="wcf-templates"></a>WCF-Vorlagen
 WCF [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Vorlagen stellen eine grundlegende Klassenstruktur zur Dienstentwicklung bereit. Mehrere WCF-Vorlagen stehen in der **neues Projekt hinzufügen** Dialogfeld. Dazu gehören die WCF-Dienstbibliotheksprojekte, WCF-Dienst-Websites und WCF-Dienst-Elementvorlagen.

 Wenn Sie eine Vorlage auswählen, werden die Dateien für einen Dienstvertrag, einer dienstimplementierung und eine Konfiguration hinzugefügt. Alle erforderlichen Attribute bereits hinzugefügt werden, erstellen einen einfachen "Hello World"-Typ des Diensts, und Sie keinen Code schreiben. Sie möchten werden natürlich Code hinzufügen, um Funktionen und Methoden für den Dienst realen bereitzustellen, aber die Vorlagen bieten die grundlegenden Grundlage.

 Weitere Informationen zu WCF-Vorlagen finden Sie unter [WCF Visual Studio-Vorlagen](https://msdn.microsoft.com/library/6a608575-3535-4190-89da-911e24c8374f).

#### <a name="wcf-service-host"></a>WCF-Diensthost
 Beim Starten der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] debugger (durch Drücken von F5) für einen WCF-Dienstprojekt, der WCF-Diensthost-Tool automatisch gestartet wird, um den Dienst lokal hosten. WCF-Diensthost listet die Dienste in einem WCF-Dienst-Projekt, lädt die Projektkonfiguration und instanziiert einen Host für die einzelnen Dienste, die es findet.

 Verwenden Sie WCF-Diensthost, können Sie einen WCF-Dienst testen, ohne zusätzlichen Code schreiben oder einen bestimmten Host bei der Entwicklung.

 Weitere Informationen zu WCF-Diensthost finden Sie unter [WCF-Diensthost (WcfSvcHost.exe)](https://msdn.microsoft.com/library/8643a63d-a357-4c39-bd6c-cdfdf71e370e).

#### <a name="wcf-test-client"></a>WCF-Testclient
 Das WCF-Testclient-Tool ermöglicht Ihnen das Eingeben der Testparameter, übermitteln, die Eingabe an einen WCF-Dienst, und zeigen Sie die Antwort, die der Dienst zurücksendet. Es bietet es sich um einen geeigneten Dienst testen bei Kombination mit WCF-Diensthost. Das Tool im Ordner \Common7\IDE finden Sie die für Visual Studio 2015 auf Laufwerk, die installiert "c:" Hier ist: **C:\Programme\Microsoft Dateien (x86) \Microsoft Visual Studio 14.0\Common7\IDE\\**.

 Wenn Sie F5, um ein WCF-Dienstprojekt Debuggen drücken, wird WCF-Testclient öffnet und zeigt eine Liste der Dienstendpunkte, die in der Konfigurationsdatei definiert sind. Sie können die Parameter testen und starten Sie den Dienst und wiederholen Sie diesen Vorgang, um kontinuierlich zu testen und überprüfen Ihren Dienst.

 Weitere Informationen zu WCF-Testclient, finden Sie unter [WCF-Testclient (WcfTestClient.exe)](https://msdn.microsoft.com/library/d4302855-677f-4640-aa90-c5d785d72fb7).

### <a name="accessing-wcf-services-in-visual-studio"></a>Zugreifen auf WCF-Diensten in Visual Studio
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] vereinfacht die Aufgabe des Erstellens von WCF-Clients, die automatisch generiert einen Proxy und einen Endpunkt für Dienste, die Sie hinzufügen, indem Sie mit der **Hinzufügen eines Dienstverweises** Dialogfeld. Alle erforderlichen Konfigurationsinformationen wird die Datei "App.config" hinzugefügt. Den meisten Fällen ist alles, was man dazu Unternehmen muss den Dienst instanziiert, um sie zu verwenden.

 Die **Hinzufügen eines Dienstverweises** Dialogfeld können Sie die Adresse für einen Dienst eingeben oder Suchen nach einem Dienst, der in der Projektmappe definiert ist. Das Dialogfeld gibt einer Liste der Dienste und die Vorgänge, die von diesen Diensten bereitgestellt werden. Darüber hinaus können Sie den Namespace definieren, mit dem Sie die Dienste im Code verweist.

 Die **Dienstverweis** Dialogfeld können Sie die Konfiguration für einen Dienst anzupassen. Sie können ändern Sie die Adresse für einen Dienst, Zugriffsebene, asynchrones Verhalten und Nachrichtenvertragstypen angeben und konfigurieren die Wiederverwendung von Typen.

## <a name="how-to-select-a-service-endpoint"></a>Vorgehensweise: Wählen Sie einen Dienstendpunkt
 Einige Windows Communication Foundation (WCF)-Dienste verfügbar machen, mehrere Endpunkte, die über denen ein Client mit dem Dienst kommunizieren kann. Z. B. ein Dienst möglicherweise verfügbar zu machen einen Endpunkt, der ein HTTP-Bindung und ein beispielbenutzername verwendet / kennwortsicherheit und einen zweiten Endpunkt, der FTP- und Windows-Authentifizierung verwendet. Der erste Endpunkt kann von Anwendungen, die Zugriff auf den Dienst aus außerhalb einer Firewall, verwendet werden, während das zweite in einem Intranet verwendet werden kann.

 In diesem Fall können Sie angeben der `endpointConfigurationName` als Parameter an den Konstruktor für einen Dienstverweis.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-select-a-service-endpoint"></a>Auswählen ein Dienstendpunkts

1. Fügen Sie einen Verweis auf einen WCF-Dienst durch einen Rechtsklick auf den Projektknoten im Projektmappen-Explorer und auswählen **Hinzufügen eines Dienstverweises**

2. Fügen Sie im Code-Editor einen Konstruktor für den Dienstverweis hinzu:

    ```vb
    Dim proxy As New ServiceReference.Service1Client(
    ```

    ```csharp
    ServiceReference.Service1Client proxy = new ServiceReference.Service1Client(
    ```

    > [!NOTE]
    > Ersetzen Sie dies *ServiceReference* mit dem Namespace für den Dienstverweis und *Service1Client* mit dem Namen des Diensts.

3. Mit den Überladungen des Konstruktors wird eine IntelliSense-Liste angezeigt. Wählen Sie die `endpointConfigurationName As String` überladen.

4. Geben Sie nach der Überladung `=` *ConfigurationName*, wobei *ConfigurationName* ist der Name des Endpunkts, den Sie verwenden möchten.

    > [!NOTE]
    > Wenn Sie die Namen der verfügbaren Endpunkte nicht kennen, finden Sie sie in der Datei "App.config".

#### <a name="to-find-the-available-endpoints-for-a-wcf-service"></a>Um die verfügbaren Endpunkte für einen WCF-Dienst gefunden werden.

1. In **Projektmappen-Explorer**mit der rechten Maustaste auf die Datei "App.config" für das Projekt, das den Dienstverweis enthält, und klicken Sie dann auf **öffnen**. Die Datei wird im Code-Editor angezeigt.

2. Suchen Sie nach der `<Client>` Tag in der Datei.

3. Suchen Sie unterhalb der `<Client>` Tag für ein Tag, die mit beginnt `<Endpoint>`.

     Wenn der Dienstverweis über mehrere Endpunkte bereitstellt, werden zwei oder mehr `<Endpoint` Tags.

4. In der `<EndPoint>` Tag Sie finden eine `name="` *"SomeService"* `"` Parameter (, in denen *"SomeService"* ein Endpunktname). Dies ist der Name für den Endpunkt übergeben werden kann, die die `endpointConfigurationName As String` Überladung des Konstruktors für einen Dienstverweis.

## <a name="how-to-call-a-service-method-asynchronously"></a>Vorgehensweise: Eine Dienstmethode asynchron aufrufen
 Die meisten Methoden in Windows Communication Foundation (WCF)-Dienste können entweder synchron oder asynchron aufgerufen werden. Eine Methode asynchron aufgerufen, ermöglicht der Anwendung, funktionieren weiterhin, während die Methode aufgerufen wird, wenn sie über eine langsame Verbindung ausgeführt wird.

 In der Standardeinstellung ein Dienstverweises zu einem Projekt hinzugefügt wird ist er dafür konfiguriert, synchron Aufrufen von Methoden. Sie können das Verhalten zum Aufrufen von Methoden asynchron durch das Ändern einer Einstellung im Ändern der **Dienstverweis konfigurieren** Dialogfeld.

> [!NOTE]
> Diese Option wird auf einer pro-Dienst-Basis festgelegt. Wenn eine Methode für einen Dienst asynchron aufgerufen wird, müssen alle Methoden asynchron aufgerufen werden.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-call-a-service-method-asynchronously"></a>Eine Dienstmethode asynchron aufrufen.

1. In **Projektmappen-Explorer**, wählen Sie den Dienstverweis.

2. Auf der **Projekt** Menü klicken Sie auf **Dienstverweis konfigurieren**.

3. In der **Dienstverweis konfigurieren** wählen Sie im Dialogfeld die **asynchrone Vorgänge generieren** Kontrollkästchen.

## <a name="how-to-bind-data-returned-by-a-service"></a>Vorgehensweise: Binden von Daten, die von einem Dienst zurückgegeben werden.
 Sie können ebenso, wie Sie eine beliebige andere Datenquelle an ein Steuerelement binden können an ein Steuerelement von einem Windows Communication Foundation (WCF)-Dienst zurückgegebene Daten binden. Wenn Sie einen Verweis auf einen WCF-Dienst hinzufügen, wenn der Dienst zusammengesetzte Typen enthält, die Daten zurückgeben, werden sie automatisch hinzugefügt die **Datenquellen** Fenster.

#### <a name="to-bind-a-control-to-single-data-field-returned-by-a-wcf-service"></a>Zum Binden eines Steuerelements auf einzelnen Datenfeld, die von einem WCF-Dienst zurückgegeben

1. Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**. Die **Datenquellen** Fenster wird angezeigt.

2. In der **Datenquellen** Fenster, erweitern Sie den Knoten für den Dienstverweis. Alle zusammengesetzten Typen, die vom Dienst zurückgegebenen werden angezeigt.

3. Erweitern Sie den Knoten für einen Typ aus. Die Datenfelder für diesen Typ werden angezeigt.

4. Wählen Sie ein Feld aus, und klicken Sie auf die Dropdown-Pfeil, um eine Liste der Steuerelemente anzuzeigen, die für den Datentyp zur Verfügung stehen.

5. Klicken Sie auf den Typ des Steuerelements, das Sie binden möchten.

6. Ziehen Sie das Feld in ein Formular aus. Das Steuerelement wird hinzugefügt werden, auf das Formular zusammen mit einer <xref:System.Windows.Forms.BindingSource> Komponente und eine <xref:System.Windows.Forms.BindingNavigator> Komponente.

7. Wiederholen Sie Schritte 4, obwohl 6 für alle anderen, die Felder Sie binden möchten.

#### <a name="to-bind-a-control-to-composite-type-returned-by-a-wcf-service"></a>Zum Binden eines Steuerelements zu zusammengesetzter Typ zurückgegeben, die von einem WCF-Dienst

1. Auf der **Daten** , wählen Sie im Menü **Datenquellen anzeigen**. Die **Datenquellen** Fenster wird angezeigt.

2. In der **Datenquellen** Fenster, erweitern Sie den Knoten für den Dienstverweis. Alle zusammengesetzten Typen, die vom Dienst zurückgegebenen werden angezeigt.

3. Wählen Sie einen Knoten für einen Typ aus, und klicken Sie auf die Dropdown-Pfeil, um eine Liste der verfügbaren Optionen anzuzeigen.

4. Klicken Sie auf **DataGridView** zum Anzeigen der Daten in einem Raster oder **Details** zum Anzeigen der Daten in einzelnen Steuerelementen.

5. Ziehen Sie den Knoten aus, auf das Formular. Werden die Steuerelemente hinzugefügt werden, auf das Formular zusammen mit einem <xref:System.Windows.Forms.BindingSource> Komponente und eine <xref:System.Windows.Forms.BindingNavigator> Komponente.

## <a name="how-to-configure-a-service-to-reuse-existing-types"></a>Vorgehensweise: Konfigurieren Sie einen Dienst, um die Wiederverwendung von vorhandener Types
 Wenn ein Projekt ein Dienstverweis hinzugefügt wird, werden alle im Dienst definierten Typen im lokalen Projekt generiert. In vielen Fällen dabei doppelte Typen erstellt, wenn ein Dienst verwendet allgemeine [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Typen oder wenn die Typen in einer freigegebenen Bibliothek definiert werden.

 Um dieses Problem zu vermeiden, werden die Typen in referenzierten Assemblys standardmäßig freigegeben. Wenn Sie die Typfreigabe für eine oder mehrere Assemblys deaktivieren möchten, Sie können dazu die **Dienstverweis** Dialogfeld.

#### <a name="to-disable-type-sharing-in-a-single-assembly"></a>Deaktivieren der Typfreigabe in einer einzelnen assembly

1. In **Projektmappen-Explorer**, wählen Sie den Dienstverweis.

2. Auf der **Projekt** Menü klicken Sie auf **Dienstverweis konfigurieren**.

3. In der **Dienstverweis** wählen Sie im Dialogfeld **Typen in referenzierten Assemblys wiederverwenden**.

4. Wählen Sie das Kontrollkästchen für jede Assembly, in dem Sie die Typfreigabe aktivieren möchten. Um die Typfreigabe für eine Assembly zu deaktivieren, lassen Sie das Kontrollkästchen deaktiviert.

#### <a name="to-disable-type-sharing-in-all-assemblies"></a>Deaktivieren der Typfreigabe in allen Assemblys

1. In **Projektmappen-Explorer**, wählen Sie den Dienstverweis.

2. Auf der **Projekt** Menü klicken Sie auf **Dienstverweis konfigurieren**.

3. In der **Dienstverweis** Dialogfeld das Kontrollkästchen der **Typen in referenzierten Assemblys wiederverwenden** Kontrollkästchen.

## <a name="related-topics"></a>Verwandte Themen

|Titel|Beschreibung|
|-----------|-----------------|
|[Exemplarische Vorgehensweise: Erstellen eines einfachen WCF-Diensts in Windows Forms](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md)|Enthält eine schrittweise Demonstration zum Erstellen und Verwenden von WCF-Dienste in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|
|[Exemplarische Vorgehensweise: Erstellen eines WCF-Datendiensts mit WPF und Entity Framework](../data-tools/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework.md)|Enthält eine schrittweise Demonstration zum Erstellen und Verwenden von [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|
|[Verwenden der WCF-Entwicklungstools](https://msdn.microsoft.com/library/054adb87-c244-4d5a-83d1-0b2b44bd454b)|Erläutert das Erstellen und Testen von WCF-Dienste in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|
|[Vorgehensweise: Hinzufügen, aktualisieren oder Entfernen eines Dienstverweises](https://msdn.microsoft.com/library/cacc14bd-4455-4a44-be78-d2ac16113dd9)|Beschreibt das Hinzufügen, aktualisieren oder Entfernen von WCF-Diensten aus einem Projekt.|
|[Vorgehensweise: Hinzufügen, Aktualisieren oder Entfernen eines WCF-Datendienstverweises](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)|Erläutert, wie referenziert und verwendet [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|
|[Problembehandlung bei Dienstverweisen](../data-tools/troubleshooting-service-references.md)|Dienstverweise und vermeiden sie, dass bietet einige häufige Fehler, die auftreten können.|
|[Debuggen von WCF-Diensten](../debugger/debugging-wcf-services.md)|Beschreibt allgemeine Debugprobleme und Techniken, die beim Debuggen von WCF-Diensten auftreten können.|
|[Übersicht über den Windows Communication Foundation-Authentifizierung](https://msdn.microsoft.com/library/6e121a28-89e8-4974-88a8-70aaa6a7d52b)|Beschreibt, wie WCF zu verwenden, um einen Rollendienst für eine Website bereitzustellen.|
|[Exemplarische Vorgehensweise: Erstellen einer n-schichtigen Datenanwendung](../data-tools/walkthrough-creating-an-n-tier-data-application.md)|Liefert eine Schritt-für-Schritt-Anleitung für das Erstellen eines typisierten Datasets und das Aufteilen des Codes für TableAdapter und Dataset in mehrere Projekte.|
|[Dienstverweis konfigurieren (Dialogfeld)](../data-tools/configure-service-reference-dialog-box.md)|Beschreibt die Elemente der Benutzeroberfläche von der **Dienstverweis konfigurieren** Dialogfeld.|

## <a name="reference"></a>Referenz
 <xref:System.ServiceModel>

 <xref:System.Data.Services>

## <a name="see-also"></a>Siehe auch
 [Visual Studio-Datentools für .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)

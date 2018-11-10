---
title: Optimieren des Azure-Codes in Visual Studio | Microsoft-Dokumentation
description: Erfahren Sie, wie Azure Code Optimierungstools in Visual Studio den Code robuster und leistungsstärker zu gestalten.
author: ghogen
manager: douge
ms.assetid: ed48ee06-e2d2-4322-af22-07200fb16987
ms.topic: conceptual
ms.custom: vs-azure
ms.workload: azure-vs
ms.date: 11/11/2016
ms.author: ghogen
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.openlocfilehash: d1d0f5a69015a6c6596e1a2b7ee85b12f4116d6b
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "51001775"
---
# <a name="optimizing-your-azure-code"></a>Optimieren Ihres Azure-Codes
Wenn Sie apps, die Microsoft Azure verwenden programmieren, gibt es einige Programmierpraktiken, die Sie befolgen sollten, um Probleme mit der Skalierbarkeit der app, die Verhalten und die Leistung in einer Cloudumgebung zu vermeiden. Microsoft bietet ein Azure Code Analysis-Tool, das erkennt, die mehrere dieser häufig auftretenden Probleme identifiziert und behoben werden kann. Sie können das Tool in Visual Studio über NuGet herunterladen.

## <a name="azure-code-analysis-rules"></a>Azure Code Analysis-Regeln
Das Azure Code Analysis Tool verwendet die folgenden Regeln, um Ihre Azure-Code automatisch zu kennzeichnen, wenn der gefundenen Problemen – Auswirkungen auf die Leistung. Erkannte Probleme werden als Warnungen oder Compilerfehler angezeigt. Codefehlerbehebungen oder Vorschläge zum Beheben der Warnung oder Fehler werden häufig über ein Glühbirnensymbol bereitgestellt.

## <a name="avoid-using-default-in-process-session-state-mode"></a>Vermeiden Sie die Verwendung der standardmäßigen der Sitzungszustandsmodus (in-Process)
### <a name="id"></a>Id
AP0000

### <a name="description"></a>Beschreibung
Wenn Sie die standardmäßigen (in-Process) Sitzungszustandsmodus für Cloud-Anwendungen verwenden, können Sie den Sitzungszustand verlieren.

Teilen Sie Ihre Ideen und ihr Feedback über [Azure Code Analysis-Feedback](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Grund
Standardmäßig ist die in der Datei "Web.config" angegebene Sitzungszustandsmodus in-Process. Darüber hinaus standardmäßig, wenn kein Eintrag in der Konfigurationsdatei angegeben ist, der Modus der Sitzungszustand in Bearbeitung. Der in-Process-Modus speichert den Sitzungszustand im Arbeitsspeicher auf dem Webserver. Wenn eine Instanz neu gestartet wird, oder eine neue Instanz für den Lastenausgleich oder die Failoverunterstützung verwendet wird, wird der Sitzungszustand im Arbeitsspeicher auf dem Webserver gespeichert nicht gespeichert. Diese Situation verhindert, dass die Anwendung wird in der Cloud skalierbar.

Der ASP.NET-Sitzungszustand unterstützt verschiedene Speicheroptionen für Sitzungszustandsdaten: InProc, StateServer, SQLServer, Benutzerdefiniert, und Off. Es wird empfohlen, wie z. B. benutzerdefinierte Modus zum Hosten von Daten auf einem externen Sitzungszustandsspeicher zu verwenden [Azure-Sitzungszustandsanbieter für Redis](http://go.microsoft.com/fwlink/?LinkId=401521).

### <a name="solution"></a>Lösung
Eine empfohlene Lösung ist zum Speichern des Sitzungsstatus in einem managed Cache Service. Erfahren Sie, wie Sie mit [Azure-Sitzungszustandsanbieter für Redis](http://go.microsoft.com/fwlink/?LinkId=401521) zum Speichern des Sitzungsstatus. Sie können den Sitzungszustand auch speichern, an anderen Orten, um sicherzustellen, dass Ihre Anwendung in der Cloud skalierbar ist. Weitere Informationen zu alternativen Lösungen finden [Sitzungszustandsmodi](https://msdn.microsoft.com/library/ms178586).

## <a name="run-method-should-not-be-async"></a>Run-Methode sollte nicht asynchron sein.
### <a name="id"></a>Id
AP1000

### <a name="description"></a>Beschreibung
Erstellen Sie asynchrone Methoden (z. B. ["await"](https://msdn.microsoft.com/library/hh156528.aspx)) außerhalb von den [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) Methode und rufen Sie dann die asynchronen Methoden über [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx). Deklarieren der [ [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) ](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) Async-Methode führt dazu, dass die workerrolle in eine Neustartschleife eintritt.

Teilen Sie Ihre Ideen und ihr Feedback über [Azure Code Analysis-Feedback](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Grund
Aufrufen asynchroner Methoden innerhalb der [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) Methode bewirkt, dass die Clouddienst-Runtime die workerrolle wiederverwendet. Wenn eine workerrolle gestartet wird, nimmt gesamte programmausführung innerhalb der [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) Methode. Beenden der [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) Methode bewirkt, dass die workerrolle neu gestartet. Wenn die Workerrollen-Runtime die asynchronen Methode erreicht, sendet alle Vorgänge nach der asynchronen Methode und gibt dann zurück. Dies bewirkt, dass die Worker-Rolle zum Beenden der [ [ [ [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) ](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) ](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) ](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) -Methode, und starten Sie neu. In der nächsten Iteration der Ausführung wird die Worker-Rolle die asynchronen Methode wieder erreicht, und Sie neu gestartet wird, verursacht die Worker-Rolle ebenfalls wiederverwendet.

### <a name="solution"></a>Lösung
Platzieren Sie alle asynchronen Vorgänge außerhalb der der [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) Methode. Rufen Sie dann die umgestaltete asynchrone Methode innerhalb der [ [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) ](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) Methode, z. B. runasync().Wait". Das Azure Code Analysis Tool können Sie dieses Problem zu beheben.

Der folgende Codeausschnitt veranschaulicht die Codefehlerbehebung für dieses Problem:

```
public override void Run()
{
    RunAsync().Wait();
}

public async Task RunAsync()
{
    //Asynchronous operations code logic
    // This is a sample worker implementation. Replace with your logic.

    Trace.TraceInformation("WorkerRole1 entry point called");

    HttpClient client = new HttpClient();

    Task<string> urlString = client.GetStringAsync("http://msdn.microsoft.com");

    while (true)
    {
        Thread.Sleep(10000);
        Trace.TraceInformation("Working");

        string stream = await urlString;
    }

}
```

## <a name="use-service-bus-shared-access-signature-authentication"></a>Service Bus Shared Access Signature-Authentifizierung verwenden
### <a name="id"></a>Id
AP2000

### <a name="description"></a>Beschreibung
Verwenden Sie Shared Access Signature (SAS) für die Authentifizierung. Access Control Service (ACS) ist für Service Bus-Authentifizierung als veraltet markiert wird.

Teilen Sie Ihre Ideen und ihr Feedback über [Azure Code Analysis-Feedback](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Grund
Aus Sicherheitsgründen ist Azure Active Directory ACS-Authentifizierung mit SAS-Authentifizierung ersetzt. Finden Sie unter [Azure Active Directory ist die Zukunft von ACS](https://cloudblogs.microsoft.com/enterprisemobility/2013/06/22/azure-active-directory-is-the-future-of-acs/) Informationen zum Übergangsplan.

### <a name="solution"></a>Lösung
Verwenden Sie SAS-Authentifizierung in Ihren apps. Das folgende Beispiel zeigt, wie Sie ein vorhandenes SAS-Token zu verwenden, um eine Service Bus-Namespace oder Entität zuzugreifen.

```
MessagingFactory listenMF = MessagingFactory.Create(endpoints, new StaticSASTokenProvider(subscriptionToken));
SubscriptionClient sc = listenMF.CreateSubscriptionClient(topicPath, subscriptionName);
BrokeredMessage receivedMessage = sc.Receive();
```

Finden Sie unter den folgenden Themen Weitere Informationen.

* Eine Übersicht finden Sie unter [freigegebenen SAS-Authentifizierung mit Service Bus](https://msdn.microsoft.com/library/dn170477.aspx)
* [Gewusst wie: Verwenden von freigegebenen SAS-Authentifizierung mit Service Bus](https://msdn.microsoft.com/library/dn205161.aspx)
* Ein Beispielprojekt finden Sie unter [mithilfe von Shared Access Signature (SAS)-Authentifizierung mit Service Bus-Abonnements](http://code.msdn.microsoft.com/windowsazure/Using-Shared-Access-e605b37c)

## <a name="consider-using-onmessage-method-to-avoid-receive-loop"></a>Erwägen Sie OnMessage-Methode, um zu vermeiden, "Empfangsschleife"
### <a name="id"></a>Id
AP2002

### <a name="description"></a>Beschreibung
Auf einer "Empfangsschleife," zu vermeiden Aufrufen der **OnMessage** Methode ist eine bessere Lösung für den Empfang von Nachrichten als das Aufrufen der **Receive** Methode. Allerdings bei Verwendung von muss die **Receive** -Methode und eine nicht standardmäßige Serverwartezeit angeben, stellen Sie sicher, dass die Serverwartezeit mehr als eine Minute.

Teilen Sie Ihre Ideen und ihr Feedback über [Azure Code Analysis-Feedback](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Grund
Beim Aufrufen von **OnMessage**, startet der Client ein internes Nachrichtensystem, das die Warteschlange oder das Abonnement ständig abruft. Dieses Nachrichtensystem enthält eine unendliche Schleife, die einen Aufruf zum Empfangen von Nachrichten ausgibt. Wenn der Aufruf ein auftritt Timeout, wird einen neuen Aufruf ausgegeben. Das Timeoutintervall wird durch den Wert bestimmt die [OperationTimeout](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.messagingfactorysettings.operationtimeout.aspx) Eigenschaft der [MessagingFactory](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.messagingfactory.aspx), der verwendet wird.

Der Vorteil der Verwendung **OnMessage** im Vergleich zu **Receive** besteht darin, dass Benutzer nicht manuell Nachrichten abrufen, behandeln Sie Ausnahmen, mehrere Nachrichten gleichzeitig verarbeiten und die Nachrichten abschließen.

Wenn Sie aufrufen **Receive** ohne Verwendung des Standardwerts, achten Sie darauf die *ServerWaitTime* Wert ist länger als eine Minute. Festlegen von *ServerWaitTime* auf mehr als eine Minute verhindert, dass den Server Timeout, bevor die Nachricht vollständig empfangen wurde.

### <a name="solution"></a>Lösung
Informieren Sie die folgenden Codebeispiele für die empfohlene Verwendung an. Weitere Informationen finden Sie unter [QueueClient.OnMessage Method (Microsoft.ServiceBus.Messaging)](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.queueclient.onmessage.aspx)und [QueueClient.Receive Method (Microsoft.ServiceBus.Messaging)](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.queueclient.receive.aspx).

Um die Leistung von Azure-Messaginginfrastruktur zu verbessern, finden Sie unter dem Entwurfsmuster [Einführung in asynchrone Nachrichten](https://msdn.microsoft.com/library/dn589781.aspx).

Im folgenden ist ein Beispiel der Verwendung von **OnMessage** zum Empfangen von Nachrichten.

```
void ReceiveMessages()
{
    // Initialize message pump options.
    OnMessageOptions options = new OnMessageOptions();
    options.AutoComplete = true; // Indicates if the message-pump should call complete on messages after the callback has completed processing.
    options.MaxConcurrentCalls = 1; // Indicates the maximum number of concurrent calls to the callback the pump should initiate.
    options.ExceptionReceived += LogErrors; // Enables you to get notified of any errors encountered by the message pump.

    // Start receiving messages.
    QueueClient client = QueueClient.Create("myQueue");
    client.OnMessage((receivedMessage) => // Initiates the message pump and callback is invoked for each message that is recieved, calling close on the client will stop the pump.
    {
        // Process the message.
    }, options);
    Console.WriteLine("Press any key to exit.");
    Console.ReadKey();
```

Im folgenden ist ein Beispiel der Verwendung von **Receive** mit der standardmäßigen Serverwartezeit.

```
string connectionString =  
CloudConfigurationManager.GetSetting("Microsoft.ServiceBus.ConnectionString");

QueueClient Client =  
    QueueClient.CreateFromConnectionString(connectionString, "TestQueue");

while (true)  
{   
   BrokeredMessage message = Client.Receive();
   if (message != null)
   {
      try  
      {
         Console.WriteLine("Body: " + message.GetBody<string>());
         Console.WriteLine("MessageID: " + message.MessageId);
         Console.WriteLine("Test Property: " +  
            message.Properties["TestProperty"]);

         // Remove message from queue
         message.Complete();
      }

      catch (Exception)
      {
         // Indicate a problem, unlock message in queue
         message.Abandon();
      }
   }
```

Im folgenden ist ein Beispiel der Verwendung von **Receive** mit einer nicht standardmäßigen Serverwartezeit.

```
while (true)  
{   
   BrokeredMessage message = Client.Receive(new TimeSpan(0,1,0));

   if (message != null)
   {
      try  
      {
         Console.WriteLine("Body: " + message.GetBody<string>());
         Console.WriteLine("MessageID: " + message.MessageId);
         Console.WriteLine("Test Property: " +  
            message.Properties["TestProperty"]);

         // Remove message from queue
         message.Complete();
      }

      catch (Exception)
      {
         // Indicate a problem, unlock message in queue
         message.Abandon();
      }
   }
}
```
## <a name="consider-using-asynchronous-service-bus-methods"></a>Erwägen Sie asynchrone Service Bus-Methoden
### <a name="id"></a>Id
AP2003

### <a name="description"></a>Beschreibung
Verwenden Sie asynchrone Service Bus-Methoden zur Verbesserung der Leistung beim brokermessaging.

Teilen Sie Ihre Ideen und ihr Feedback über [Azure Code Analysis-Feedback](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Grund
Verwenden asynchroner Methoden ermöglicht die Parallelität von Anwendungsprogrammen, da es sich bei Ausführung der einzelnen Aufrufe den Hauptthread blockiert wird. Bei Verwendung von Service Bus messaging-Methoden, Ausführen eines Vorgangs (senden, empfangen, löschen usw.) nimmt Zeit in Anspruch. Diese Zeit schließt die Verarbeitung des Vorgangs durch den Service Bus-Dienst sowie die Wartezeit für die Anforderung und Antwort. Vorgänge zum Erhöhen der Anzahl von Vorgängen pro Zeitraum müssen parallel ausgeführt. Weitere Informationen finden Sie in [bewährte Methoden für Leistung Verbesserungen mithilfe von Service Bus-Brokermessaging](https://msdn.microsoft.com/library/azure/hh528527.aspx).

### <a name="solution"></a>Lösung
Finden Sie unter [QueueClient-Klasse (Microsoft.ServiceBus.Messaging)](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.queueclient.aspx) Informationen zur Verwendung die empfohlene asynchrone Methode.

Um die Leistung von Azure-Messaginginfrastruktur zu verbessern, finden Sie unter dem Entwurfsmuster [Einführung in asynchrone Nachrichten](https://msdn.microsoft.com/library/dn589781.aspx).

## <a name="consider-partitioning-service-bus-queues-and-topics"></a>Betrachten Sie die Partitionierung von Service Bus-Warteschlangen und Themen
### <a name="id"></a>Id
AP2004

### <a name="description"></a>Beschreibung
Partitionieren von Service Bus-Warteschlangen und Themen für eine bessere Leistung mit Service Bus-messaging.

Teilen Sie Ihre Ideen und ihr Feedback über [Azure Code Analysis-Feedback](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Grund
Partitionieren von Service Bus-Warteschlangen und Themen ist, steigert die Leistung Leistungsdurchsatz und dienstverfügbarkeit, da der Gesamtdurchsatz einer partitionierten Warteschlange oder eines Themas nicht mehr durch die Leistung eines einzelnen nachrichtenbrokers oder Nachrichtenspeichers beschränkt wird. Darüber hinaus kein vorübergehender Ausfall eines Nachrichtenspeichers eine partitionierte Warteschlange oder ein Thema zur Verfügung. Weitere Informationen finden Sie unter [Partitionieren von Messagingentitäten](https://msdn.microsoft.com/library/azure/dn520246.aspx).

### <a name="solution"></a>Lösung
Der folgende Codeausschnitt veranschaulicht die Partitionierung von nachrichtenentitäten.

```
// Create partitioned topic.
NamespaceManager ns = NamespaceManager.CreateFromConnectionString(myConnectionString);
TopicDescription td = new TopicDescription(TopicName);
td.EnablePartitioning = true;
ns.CreateTopic(td);
```

Weitere Informationen finden Sie unter [partitionierte Service Bus-Warteschlangen und-Themen | Microsoft Azure-Blog](https://azure.microsoft.com/blog/2013/10/29/partitioned-service-bus-queues-and-topics/) und sehen Sie sich die [Microsoft Azure Service Bus – partitionierte Warteschlange](https://code.msdn.microsoft.com/windowsazure/Service-Bus-Partitioned-7dfd3f1f) Beispiel.

## <a name="do-not-set-sharedaccessstarttime"></a>Stellen Sie keine SharedAccessStartTime
### <a name="id"></a>Id
AP3001

### <a name="description"></a>Beschreibung
Vermeiden Sie die Verwendung von SharedAccessStartTimeset auf die aktuelle Uhrzeit auf die um Richtlinie für den freigegebenen Zugriff sofort zu starten. Sie müssen nur zum Festlegen dieser Eigenschaft, wenn Sie die freigegebene Zugriffsrichtlinie zu einem späteren Zeitpunkt starten möchten.

Teilen Sie Ihre Ideen und ihr Feedback über [Azure Code Analysis-Feedback](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Grund
Die uhrsynchronisierung verursacht einen leichten Zeitunterschied zwischen Rechenzentren. Beispielsweise logisch, dass das Festlegen der Startzeit einer SAS-Speicherrichtlinie die aktuelle Uhrzeit per "DateTime.Now" oder eine ähnliche Methode bewirkt, dass die SAS-Richtlinie sofort wirksam wird. Die leichten Zeitunterschiede zwischen Rechenzentren können jedoch Probleme verursachen, da einige rechenzentrumzeiten etwas höher als die Startzeit, während andere vor möglicherweise. Daher kann die SAS-Richtlinie schnell (oder sogar sofort) ablaufen lassen, wenn die Lebensdauer der Richtlinie zu kurz angesetzt ist.

Weitere Informationen zur Verwendung von Shared Access Signature für Azure-Speicher finden Sie unter [Introducing Table SAS (Shared Access Signature), Warteschlangen-SAS und Aktualisieren auf Blob-SAS – Microsoft Azure Storage-Teamblog – Homepage der Website – MSDN-Blogs](http://blogs.msdn.com/b/windowsazurestorage/archive/2012/06/12/introducing-table-sas-shared-access-signature-queue-sas-and-update-to-blob-sas.aspx).

### <a name="solution"></a>Lösung
Entfernen Sie die Anweisung, die Startzeit der shared Access-Richtlinie festgelegt. Das Azure Code Analysis Tool bietet eine Lösung für dieses Problem. Weitere Informationen zur sicherheitsverwaltung finden Sie im Entwurfsmuster [Valet-Schlüsselmuster](https://msdn.microsoft.com/library/dn568102.aspx).

Der folgende Codeausschnitt veranschaulicht die Codefehlerbehebung für dieses Problem.

```
// The shared access policy provides  
// read/write access to the container for 10 hours.
blobPermissions.SharedAccessPolicies.Add("mypolicy", new SharedAccessBlobPolicy()
{
   // To ensure SAS is valid immediately, don’t set start time.
   // This way, you can avoid failures caused by small clock differences.
   SharedAccessExpiryTime = DateTime.UtcNow.AddHours(10),
   Permissions = SharedAccessBlobPermissions.Write |
      SharedAccessBlobPermissions.Read
});
```

## <a name="shared-access-policy-expiry-time-must-be-more-than-five-minutes"></a>SAS-Richtlinie Ablaufzeit mehr als fünf Minuten sein müssen
### <a name="id"></a>Id
AP3002

### <a name="description"></a>Beschreibung
Es kann sein, wie bis zu fünf Minuten Unterschied Uhren zwischen Rechenzentren an verschiedenen Standorten aufgrund einer Bedingung, bekannt als "zeitabweichung." Um zu verhindern, dass die SAS legen richtlinientoken früher als geplant, die Ablaufzeit auf mehr als fünf Minuten betragen.

Teilen Sie Ihre Ideen und ihr Feedback über [Azure Code Analysis-Feedback](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Grund
Rechenzentren an verschiedenen Standorten weltweit werden mithilfe eines Uhrsignals synchronisiert. Da Uhrsignal die unterschiedlichen Standorte erreicht es dauert, kann es sein eine zeitvarianz zwischen Rechenzentren an verschiedenen geografischen Standorten, zwar alles angeblich synchronisiert wird. Der Zeitunterschied kann es sich um die Shared Access-Richtlinie Start Startzeit und das Ablaufintervall Intervall auswirken. Geben Sie aus diesem Grund, um sicherzustellen, dass die Shared Access-Richtlinie sofort wirksam wird, nicht die Startzeit an. Darüber hinaus stellen Sie sicher, dass die Ablaufzeit mehr als 5 Minuten zu frühe Zeitüberschreitung zu verhindern.

Weitere Informationen zur Verwendung von Shared Access Signature für Azure-Speicher finden Sie unter [Introducing Table SAS (Shared Access Signature), Warteschlangen-SAS und Aktualisieren auf Blob-SAS – Microsoft Azure Storage-Teamblog – Homepage der Website – MSDN-Blogs](http://blogs.msdn.com/b/windowsazurestorage/archive/2012/06/12/introducing-table-sas-shared-access-signature-queue-sas-and-update-to-blob-sas.aspx).

### <a name="solution"></a>Lösung
Weitere Informationen zur sicherheitsverwaltung finden Sie im Entwurfsmuster [Valet-Schlüsselmuster](https://msdn.microsoft.com/library/dn568102.aspx).

Folgendes ist ein Beispiel für die Startzeit für eine Shared Access-Richtlinie nicht angegeben.

```
// The shared access policy provides  
// read/write access to the container for 10 hours.
blobPermissions.SharedAccessPolicies.Add("mypolicy", new SharedAccessBlobPolicy()
{
   // To ensure SAS is valid immediately, don’t set start time.
   // This way, you can avoid failures caused by small clock differences.
   SharedAccessExpiryTime = DateTime.UtcNow.AddHours(10),
   Permissions = SharedAccessBlobPermissions.Write |
      SharedAccessBlobPermissions.Read
});
```

Folgendes ist ein Beispiel für die Startzeit für eine Shared Access-Richtlinie mit einer richtlinienablaufdauer größer als fünf Minuten.

```
// The shared access policy provides  
// read/write access to the container for 10 hours.
blobPermissions.SharedAccessPolicies.Add("mypolicy", new SharedAccessBlobPolicy()
{
   // To ensure SAS is valid immediately, don’t set start time.
   // This way, you can avoid failures caused by small clock differences.
  SharedAccessStartTime = new DateTime(2014,1,20),   
 SharedAccessExpiryTime = new DateTime(2014, 1, 21),
   Permissions = SharedAccessBlobPermissions.Write |
      SharedAccessBlobPermissions.Read
});
```

Weitere Informationen finden Sie unter [erstellen und Verwenden einer Shared Access Signature](https://msdn.microsoft.com/library/azure/jj721951.aspx).

## <a name="use-cloudconfigurationmanager"></a>Verwenden von CloudConfigurationManager
### <a name="id"></a>Id
AP4000

### <a name="description"></a>Beschreibung
Mithilfe der [ConfigurationManager](https://msdn.microsoft.com/library/system.configuration.configurationmanager\(v=vs.110\).aspx) -Klasse für Projekte, wie z. B. Azure-Website und Azure mobile Services, treten keine Laufzeitprobleme. Als bewährte Methode, es ist jedoch eine gute Idee, verwenden Sie die Cloud[ConfigurationManager](https://msdn.microsoft.com/library/system.configuration.configurationmanager\(v=vs.110\).aspx) als einheitliches Verfahren zum Verwalten von Konfigurationen für alle Azure-Cloud-Anwendungen.

Teilen Sie Ihre Ideen und ihr Feedback über [Azure Code Analysis-Feedback](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Grund
CloudConfigurationManager liest die für die anwendungsumgebung geeignete Konfigurationsdatei.

[CloudConfigurationManager](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.cloudconfigurationmanager.aspx)

### <a name="solution"></a>Lösung
Gestalten Sie Ihren Code, um die [CloudConfigurationManager-Klasse](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.cloudconfigurationmanager.aspx). Eine Codefehlerbehebung für dieses Problem wird vom Azure Code Analysis Tool bereitgestellt.

Der folgende Codeausschnitt veranschaulicht die Codefehlerbehebung für dieses Problem. Ersetzen

`var settings = ConfigurationManager.AppSettings["mySettings"];`

durch

`var settings = CloudConfigurationManager.GetSetting("mySettings");`

Hier ist ein Beispiel für die Konfigurationseinstellung in der Datei "App.config" oder "Web.config" zu speichern. Die Einstellungen dem AppSettings-Abschnitt der Konfigurationsdatei hinzufügen. Im folgenden finden die Datei "Web.config" für das vorherige Codebeispiel.

```
<appSettings>
    <add key="webpages:Version" value="3.0.0.0" />
    <add key="webpages:Enabled" value="false" />
    <add key="ClientValidationEnabled" value="true" />
    <add key="UnobtrusiveJavaScriptEnabled" value="true" />
    <add key="mySettings" value="[put_your_setting_here]"/>
  </appSettings>  
```

## <a name="avoid-using-hard-coded-connection-strings"></a>Vermeiden Sie die Verwendung von hartcodierten Verbindungszeichenfolgen
### <a name="id"></a>Id
AP4001

### <a name="description"></a>Beschreibung
Wenn Sie hartcodierte Verbindungszeichenfolgen verwenden, und Sie diese später aktualisieren möchten, müssen Sie Änderungen am Quellcode vornehmen und die Anwendung neu kompilieren. Aber wenn Sie die Verbindungszeichenfolgen in einer Konfigurationsdatei speichern, können Sie sie später ändern, indem einfach die Konfigurationsdatei aktualisieren.

Teilen Sie Ihre Ideen und ihr Feedback über [Azure Code Analysis-Feedback](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Grund
Eine hartcodierung Verbindungszeichenfolgen ist kein empfehlenswertes Verfahren, da es zu Problemen führt, wenn Verbindungszeichenfolgen schnell geändert werden müssen. Darüber hinaus, wenn das Projekt in quellcodeverwaltung eingecheckt werden muss, führen hartcodierte Verbindungszeichenfolgen von Sicherheitsrisiken, da die Zeichenfolgen im Quellcode angezeigt werden können.

### <a name="solution"></a>Lösung
Store-Verbindungszeichenfolgen in den Konfigurationsdateien oder die Azure-Umgebungen.

* Verwenden Sie für eigenständige Anwendungen "App.config", um die Verbindungszeichenfolgen-Einstellungen zu speichern.
* Verwenden Sie für IIS-gehostete Webanwendungen "Web.config", um Verbindungszeichenfolgen zu speichern.
* Verwenden Sie für ASP.NET vNext-Anwendungen Datei "Configuration.JSON" zum Speichern von Verbindungszeichenfolgen aus.

Weitere Informationen zur Verwendung von Konfigurationsdateien wie web.config oder app.config finden Sie unter [ASP.NET-Webkonfiguration](https://msdn.microsoft.com/library/vstudio/ff400235\(v=vs.100\).aspx). Weitere Informationen zur Azure-Umgebungsvariablen finden Sie unter [Azure-Websites: wie Anwendungs- und Verbindungszeichenfolgen](https://azure.microsoft.com/blog/2013/07/17/windows-azure-web-sites-how-application-strings-and-connection-strings-work/). Informationen zum Speichern von Verbindungszeichenfolgen in der quellcodeverwaltung finden Sie unter [vermeiden des Einfügens von vertraulichen Informationen wie Verbindungszeichenfolgen in Dateien, die im Quellcode-Repository gespeichert sind](http://www.asp.net/aspnet/overview/developing-apps-with-windows-azure/building-real-world-cloud-apps-with-windows-azure/source-control).

## <a name="use-diagnostics-configuration-file"></a>Verwenden der diagnosekonfigurationsdatei
### <a name="id"></a>Id
AP5000

### <a name="description"></a>Beschreibung
Anstatt diagnoseeinstellungen in Ihrem Code wie z. B. mithilfe der Microsoft.WindowsAzure.Diagnostics-Programmier-API zu konfigurieren, sollten Sie diagnoseeinstellungen in der Datei "Diagnostics.wadcfg" konfigurieren. (Oder "Diagnostics.wadcfgx", wenn Sie Azure SDK 2.5 verwenden). Auf diese Weise können Sie diagnoseeinstellungen ändern, ohne den Code neu kompilieren.

Teilen Sie Ihre Ideen und ihr Feedback über [Azure Code Analysis-Feedback](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Grund
Bevor Sie Azure SDK 2.5 (das Azure-Diagnose 1.3 verwendet), Azure Diagnostics (WAD) mithilfe mehrerer unterschiedliche Methoden konfiguriert werden konnte: Hinzufügen zum Konfigurations-Blob im Speicher mithilfe von imperativem Code, der deklarativen Konfiguration oder der Standardwert die Konfiguration. Allerdings ist die bevorzugte Methode zum Konfigurieren der Diagnose verwendet eine XML-Konfigurationsdatei ("Diagnostics.wadcfg" oder "diagnositcs.wadcfgx" für SDK 2.5 und höher) im Anwendungsprojekt. Bei dieser Vorgehensweise kann die Datei "Diagnostics.wadcfg" vollständig definiert die Konfiguration und werden aktualisiert und erneut bereitgestellt werden. Mischen die Verwendung der Konfigurationsdatei "Diagnostics.wadcfg" mit den programmgesteuerten Methoden der konfigurationsfestlegung mithilfe der [DiagnosticMonitor](https://msdn.microsoft.com/library/microsoft.windowsazure.diagnostics.diagnosticmonitor.aspx)oder [RoleInstanceDiagnosticManager](https://msdn.microsoft.com/library/microsoft.windowsazure.diagnostics.management.roleinstancediagnosticmanager.aspx)Klassen zu Verwirrung führen. Finden Sie unter [initialisieren oder Ändern von Azure-Diagnosekonfiguration](https://msdn.microsoft.com/library/azure/hh411537.aspx) für Weitere Informationen.

Ab WAD 1.3 (Teil von Azure SDK 2.5), ist es nicht mehr möglich, Code zum Konfigurieren der Diagnose zu verwenden. Daher können Sie nur die Konfiguration, die beim Anwenden oder aktualisieren die Diagnose-Erweiterung bereitstellen.

### <a name="solution"></a>Lösung
Verwenden Sie den diagnosekonfigurationsdesigner, um die diagnoseeinstellungen in die diagnosekonfigurationsdatei ("diagnositcs.wadcfg" oder "diagnositcs.wadcfgx" für SDK 2.5 und höher) verschieben. Es wird empfohlen, dass es sich bei der Installation [Azure SDK 2.5](http://go.microsoft.com/fwlink/?LinkId=513188) und die aktuellste Diagnosefunktion zu verwenden.

1. Klicken Sie im Kontextmenü für die Rolle, die Sie konfigurieren möchten, wählen Sie Eigenschaften, und wählen Sie dann auf die Registerkarte "Konfiguration".
2. In der **Diagnose** Abschnitt, stellen Sie sicher, dass die **Aktivieren der Diagnose** das Kontrollkästchen aktiviert ist.
3. Wählen Sie die **konfigurieren** Schaltfläche.

   ![Zugreifen auf die Option "Diagnose aktivieren"](./media/vs-azure-tools-optimizing-azure-code-in-visual-studio/IC796660.png)

   Finden Sie unter [Konfigurieren der Diagnose für Azure Cloud Services und Virtual Machines](vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md) für Weitere Informationen.

## <a name="avoid-declaring-dbcontext-objects-as-static"></a>Vermeiden Sie die Deklaration von DbContext-Objekten als statisch
### <a name="id"></a>Id
AP6000

### <a name="description"></a>Beschreibung
Zur Einsparung von Arbeitsspeicher zu vermeiden, deklarieren DBContext-Objekten als statisch.

Teilen Sie Ihre Ideen und ihr Feedback über [Azure Code Analysis-Feedback](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Grund
DBContext-Objekte enthalten die Abfrageergebnisse aus jedem Aufruf. Statische DBContext-Objekte werden nicht gelöscht werden, bis die Anwendungsdomäne entladen wird. Aus diesem Grund kann ein statisches DBContext-Objekt große Mengen an Arbeitsspeicher belegen.

### <a name="solution"></a>Lösung
Deklarieren Sie DBContext als lokale Variable oder nicht statisches Instanzenfeld, verwenden sie für eine Aufgabe, und lassen Sie sie nach der Verwendung verworfen werden.

Folgenden MVC-Controller-Klasse gezeigt, wie die "DbContext"-Objekt verwendet wird.

```
public class BlogsController : Controller
    {
        //BloggingContext is a subclass to DbContext        
        private BloggingContext db = new BloggingContext();
        // GET: Blogs
        public ActionResult Index()
        {
            //business logics…
            return View();
        }
        protected override void Dispose(bool disposing)
        {
            if (disposing)
            {
                db.Dispose();
            }
            base.Dispose(disposing);
        }
    }
```

## <a name="next-steps"></a>Nächste Schritte
Weitere Informationen zur Optimierung und Problembehandlung von Azure-apps finden Sie unter [Problembehandlung bei Web-Apps in Azure App Service mithilfe von Visual Studio](/azure/app-service/web-sites-dotnet-troubleshoot-visual-studio).

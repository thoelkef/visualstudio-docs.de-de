---
title: Einführung in Azure Functions
description: Verwenden von Azure-Funktionen in Visual Studio für Mac
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 25CD47A4-5B32-4734-8EF3-E24A02AABF29
ms.openlocfilehash: 5d787efbd09ad7f2d4a1f5f72b8f1493d8c6c587
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2018
ms.locfileid: "33870411"
---
# <a name="introduction-to-azure-functions"></a>Einführung in Azure Functions

Mithilfe von Azure Functions können Sie ereignisgesteuerte Codeausschnitte – Funktionen – in einer Cloud erstellen und ausführen, ohne Infrastruktur bereitstellen und verwalten zu müssen. Weitere Informationen zu Azure Functions finden Sie in der [Dokumentation zu Azure Functions](https://docs.microsoft.com/azure/azure-functions/).

## <a name="requirements"></a>Anforderungen

Die Azure Function-Tools sind im Lieferumfang von **Visual Studio für Mac 7.5** enthalten.

Sie benötigen zum Erstellen und Bereitstellen von Funktionen außerdem ein Azure-Abonnement, das Sie kostenlos über [https://azure.com/free](https://azure.com/free) erhalten.

## <a name="creating-your-first-azure-functions-project"></a>Erstellen Ihres ersten Azure Functions-Projekts

1. Klicken Sie in Visual Studio auf **Datei > Neue Projektmappe...**. 
2. Klicken Sie im Dialogfeld „Neues Projekt“ unter **Cloud > Allgemein** auf eine Azure Functions-Vorlage, und klicken Sie auf **Weiter**:

    ![Dialogfeld „Neues Projekt“, in dem die Option „Azure Functions“ angezeigt wird](media/azure-functions-image1.png)

3. Geben Sie einen **Projektnamen** ein, und klicken Sie auf **Erstellen**.

Visual Studio für Mac erstellt ein .NET Standard-Projekt mit einer HttpTrigger-Standardfunktion. Außerdem sind NuGet-Verweise auf eine Vielzahl von **Azure WebJobs**-Paketen sowie das Paket **Newtonsoft.Json** im Lieferumfang enthalten.

![Visual Studio für Mac-Editor, in dem eine ganz neue Azure-Funktion aus einer Vorlage angezeigt wird](media/azure-functions-newproj.png)

Das neue Projekt enthält die folgenden Dateien:

* **HttpTrigger.cs**: Diese Klasse enthält Codebausteine für eine mit einer über HTTP ausgelösten Funktion. Außerdem enthält sie ein **FunctionName**-Attribute mit dem Funktionsnamen und dem Triggerattribut **HttpTrigger**, das angibt, dass die Funktion von einer HTTP-Anforderung ausgelöst wird. Weitere Informationen zur Funktionsmethode finden Sie in dem Artikel [C#-Entwicklerreferenz zu Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-dotnet-class-library).
* **host.json**: Diese Datei beschreibt die globalen Konfigurationsoptionen für den Functions-Host. Eine Beispieldatei und Informationen zu den für diese Datei verfügbaren Einstellungen finden Sie unter [host.json-Referenz für Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-host-json).
* **local.settings.json**: Diese Datei enthält alle Einstellungen zur lokalen Ausführung von Funktionen. Diese Einstellungen werden von den Azure Functions Core-Tools verwendet. Weitere Informationen finden Sie in der [Datei für lokale Einstellungen](https://docs.microsoft.com/en-us/azure/azure-functions/functions-run-local#local-settings-file) im Artikel „Azure Functions Core-Tools“.

Wenn Sie jetzt ein neues Azure Functions-Projekt in Visual Studio für Mac erstellt haben, können Sie nun über Ihren lokalen Computer die von HTTP ausgelöste Standardfunktion testen.

<!--
## Create an Azure storage account

[Describe why this step is necessary and what it does]

1. Log on to your account at [https://portal.azure.com](https://portal.azure.com).
2. Under the **Favorites** section, located on the left of the screen, select **Storage Accounts**:
    ![]()
3. Select **Add** to create a new storage account:
    ![]()
4. Enter a globally unique name for the **Name** and reuse it for the **Resource group**. You can keep all the other items as their default.
    ![]()
5. Click **Create**. It might take a few minutes to create the storage account. You'll get a notification once it has been successfully created.
6. Select the **Go to resource** button from the notification:
    ![]()
-->

## <a name="testing-the-function-locally"></a>Lokales Testen der Funktion

Mit der Azure Functions-Unterstützung in Visual Studio für Mac können Sie Ihre Funktion auf dem lokalen Entwicklungscomputer testen und debuggen.

1. Wenn Sie Ihre Funktion lokal testen möchten, drücken Sie auf die Schaltfläche **Ausführen** in Visual Studio für Mac:

    ![Schaltfläche zum Starten des Debugvorgangs in Visual Studio für Mac](media/azure-functions-run.png)

1. Wenn Sie das Projekt ausführen, wird der lokale Debugvorgang für die Azure-Funktion ausgeführt und ein neues Terminalfenster geöffnet (s. folgende Abbildung): 

    ![Terminalfenster, das die Ausgabe der Funktion anzeigt](media/azure-functions-terminal.png) 

    Kopieren Sie die URL aus der Ausgabe.

3. Fügen Sie die URL zu der HTTP-Anforderung in die Adressleiste Ihres Browsers ein. Fügen Sie die Abfragezeichenfolge `?name=<yourname>` an das Ende der URL ein, und führen Sie die Anforderung aus. Im folgenden Bild wird die Antwort auf die lokale GET-Anforderung im Browser angezeigt, die von der Funktion zurückgegeben wird:

    ![HTTP-Anforderung im Browser](media/azure-functions-httpreq.png)

## <a name="creating-a-new-function"></a>Erstellen einer neuen Funktion

Mithilfe von Funktionsvorlagen können Sie schnell mithilfe der am häufigsten verwendeten Trigger und Vorlagen neue Funktionen erstellen. Wenn ein neues Azure Functions-Projekt erstellt wird, wird automatisch eine HttpTrigger-Funktion hinzugefügt. Gehen Sie wie folgt vor, wenn Sie einen anderen Funktionstyp erstellen möchten:

1. Entfernen Sie die **HttpTrigger.cs**-Datei, indem Sie mit der rechten Maustaste auf diese und dann mit der linken auf **Entfernen** klicken. Klicken Sie dann in der folgenden Warnung auf **Löschen**, um die Datei aus dem Projekt zu entfernen:

    ![Dialogfeld zum Entfernen der Datei aus dem Projekt](media/azure-functions-remove.png)

2. Wenn Sie eine neue Funktion hinzufügen möchten, klicken Sie erst mit der rechten Maustaste auf den Projektnamen und dann mit der linken auf **Hinzufügen > Funktion hinzufügen...**:

    ![Kontextaktion zum Hinzufügen einer neuen Funktion](media/azure-functions-addnew.png)

3. Wählen Sie über das Dialogfeld **Neue Azure-Funktion** die Funktion aus, die Sie benötigen:

    ![Dialogfeld „Neue Azure-Funktion“](media/azure-functions-newfunction.png)

    Im folgenden Abschnitt finden Sie eine Liste der Azure Function-Vorlagen.

## <a name="available-function-templates"></a>Verfügbare Funktionsvorlagen

- **HTTP**: Lösen Sie die Ausführung Ihres Codes über eine HTTP-Anforderung aus. Es gibt explizite Vorlagen für die folgenden HTTP-Trigger:
    - Http GET CRUD
    - Http POST CRUD
    - HTTP-Trigger mit Parametern
    - HTTP-Trigger
- **Timer**: Führen Sie eine Bereinigung oder andere Stapelaufgaben für einen vordefinierten Zeitplan aus. Diese Vorlage beinhaltet zwei Felder: ein Name und ein Zeitplan, bei dem es sich um einen CRON-Ausdruck handelt, der aus sechs Feldern besteht. Weitere Informationen finden Sie unter [Erstellen einer Funktion in Azure, die von einem Timer ausgelöst wird](https://docs.microsoft.com/azure/azure-functions/functions-create-scheduled-function).
- **GitHub Trigger**: Antworten Sie auf Ereignisse, die in Ihren GitHub-Repositorys auftreten. Weitere Informationen finden Sie unter [Erstellen einer Funktion, die durch einen GitHub-Webhook ausgelöst wird](https://docs.microsoft.com/azure/azure-functions/functions-create-github-webhook-triggered-function).
    - GitHub commenter: eine Funktion, die immer dann ausgeführt wird und einen Kommentar hinzufügt, wenn sie einen GitHub-Webhook für ein Problem oder einen Pull Request empfängt.
    - GitHub WebHook: eine C#-Funktion, die ausgeführt wird, wenn sie einen GitHub-Webhook empfängt
- **Blob Trigger**: eine Funktion, die Azure Storage-Blobs verarbeitet, wenn diese zu einem Container hinzugefügt werden. Neben dem Funktionsnamen beinhaltet diese Vorlage auch eine Pfad- und eine Verbindungseigenschaft. Die Pfadeigenschaft ist der Pfad innerhalb Ihres Speicherkontos, der vom Trigger überwacht wird. Das Verbindungskonto ist der Name der App-Einstellung, die die Verbindungszeichenfolge für Ihr Speicherkonto enthält. Weitere Informationen finden Sie unter [Erstellen einer Funktion, die durch Azure Blob Storage ausgelöst wird](https://docs.microsoft.com/azure/azure-functions/functions-create-storage-blob-triggered-function).
- **Queue Trigger**: eine Funktion, die auf Meldungen antwortet, wenn diese in die Azure Storage-Warteschlange aufgenommen werden. Neben dem Funktionsnamen beinhaltet diese Vorlage einen **Pfad** (den Namen der Warteschlange, aus der die Meldung gelesen wird) und die Speicherkonto-**Verbindung** (der Name der App-Einstellung mit der Verbindungszeichenfolge des Speicherkontos). Weitere Informationen finden Sie unter [Erstellen einer Funktion, die durch Azure Queue Storage ausgelöst wird](https://docs.microsoft.com/azure/azure-functions/functions-create-storage-queue-triggered-function).
- **Generic WebHook**: eine einfache Funktion, die immer dann ausgeführt wird, wenn eine Anforderung von einem Dienst empfangen wird, der Webhooks unterstützt. Weitere Informationen finden Sie unter [Erstellen einer Funktion, die durch einen generischen Webhook ausgelöst wird](https://docs.microsoft.com/azure/azure-functions/functions-create-generic-webhook-triggered-function).
- **Image Resizer**: eine Funktion, die Images mit geänderter Größe erstellt, wenn einem Container ein Blob hinzugefügt wird. Diese Vorlage beinhaltet einen Pfad und eine Verbindungszeichenfolge für den Trigger, eine kleine Imageausgabe und eine mittelgroße Imageausgabe.
- **SAS Token**: eine Funktion, die ein SAS-Token für einen angegebenen Azure Storage-Container und einen Blobnamen generiert. Neben dem Funktionsnamen beinhaltet diese Vorlage auch eine Pfad- und eine Verbindungseigenschaft. Die Pfadeigenschaft ist der Pfad innerhalb Ihres Speicherkontos, der vom Trigger überwacht wird. Das Verbindungskonto ist der Name der App-Einstellung, die die Verbindungszeichenfolge für Ihr Speicherkonto enthält. Die **Zugriffsrechte** müssen ebenfalls festgelegt werden. Die Autorisierungsstufe kontrolliert, ob die Funktion einen API-Schlüssel verlangt und welcher Schlüssel verwendet werden soll. „Function“ verwendet einen Funktionsschlüssel und „Admin“ verwendet den Masterschlüssel. Weitere Informationen finden Sie in dem Beispiel [C# Azure Function for generating SAS tokens (Azure-Funktion in C# zum Generieren von SAS-Token)](https://azure.microsoft.com/resources/samples/functions-dotnet-sas-token/).
- **Durable functions orchestration**: Mithilfe von Durable Functions können Sie zustandsbehaftete Funktionen in einer Umgebung ohne Server schreiben. Die Erweiterung verwaltet den Status, Prüfpunkte und führt einen Neustart durch. Weitere Informationen finden Sie in den Leitfäden zu Azure Functions unter [Übersicht über Durable Functions (Vorschauversion)](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview).
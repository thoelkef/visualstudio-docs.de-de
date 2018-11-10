---
title: Testen der Leistung eines Clouddiensts | Microsoft-Dokumentation
description: Testen der Leistung eines Clouddiensts mit Visual Studio-profiler
author: mikejo5000
manager: douge
ms.assetid: 7a5501aa-f92c-457c-af9b-92ea50914e24
ms.topic: conceptual
ms.tgt_pltfrm: multiple
ms.workload: na
ms.date: 11/11/2016
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.openlocfilehash: 25b60e5e4072a0523d17082a5c5646e5bb1ade6a
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "51001731"
---
# <a name="testing-the-performance-of-a-cloud-service"></a>Testen der Leistung eines Clouddiensts
## <a name="overview"></a>Übersicht
Sie können die Leistung eines Cloud-Diensts testen, es gibt folgende Möglichkeiten:

* Verwenden Sie Azure-Diagnose zum Sammeln von Informationen zu Anforderungen und Verbindungen und Websitestatistiken zu überprüfen, die zeigen, wie der Dienst aus Kundenperspektive führt aus. Zum Einstieg finden Sie unter [Konfigurieren der Diagnose für Azure Cloud Services und Virtual Machines](http://go.microsoft.com/fwlink/p/?LinkId=623009).
* Verwenden Sie Visual Studio-Profiler, um eine detaillierte Analyse der computingaspekte der dienstausführung zu erhalten. Wie in diesem Thema wird beschrieben, können Sie den Profiler, um die Leistung zu messen, wie ein Dienst in Azure ausgeführt wird. Informationen dazu, wie Sie den Profiler verwenden, um die Leistung zu messen, wie ein Dienst in einem Serveremulator lokal ausgeführt wird, finden Sie unter [Testen der Leistung einer lokalen Azure-Clouddiensts im Serveremulator mithilfe der Visual Studio-Profiler](http://go.microsoft.com/fwlink/p/?LinkId=262845).

## <a name="choosing-a-performance-testing-method"></a>Auswählen eines leistungsprüfverfahrens
### <a name="use-azure-diagnostics-to-collect"></a>Verwenden Sie Azure-Diagnose zum Sammeln von:
* Statistiken zu Webseiten oder Dienste, z.B. Anforderungen und Verbindungen.
* Statistiken zu Rollen, z. B. wie oft eine Rolle neu gestartet wird.
* Legen allgemeine Informationen zur speicherauslastung, z. B. den Prozentsatz der Zeit, die der Garbage Collector benötigt oder der Speicherplatz einer ausgeführten Rolle.

### <a name="use-the-visual-studio-profiler-to"></a>Verwenden des Visual Studio Profilers:
* Bestimmen Sie, welche Funktionen die meiste Zeit dauern.
* Messen Sie, wie lange jeder Teil eines rechenintensiven Programms genau dauert.
* Vergleichen Sie die detaillierten Leistungsberichte für zwei Versionen eines Diensts.
* Analysieren der speicherbelegung, ausführlicher als die Ebene einzelner speicherbelegungen.
* Analysieren von Parallelitätsproblemen in Multithreadcode.

Wenn Sie den Profiler verwenden, können Sie Daten erfassen, wenn ein Clouddienst lokal oder in Azure ausgeführt wird.

### <a name="collect-profiling-data-locally-to"></a>Sammeln Sie Profilerstellungsdaten lokal zu:
* Testen der Leistung eines Teils einer Cloud-Diensts, z. B. die Ausführung einer bestimmten workerrolle, die keine realistische simulierte Last erfordert.
* Testen Sie die Leistung eines Clouddiensts in Isolation unter kontrollierten Bedingungen.
* Testen Sie die Leistung eines Clouddiensts, bevor Sie sie in Azure bereitstellen.
* Testen Sie die Leistung eines Clouddiensts privat, ohne Beeinträchtigung der vorhandenen Bereitstellungen.
* Testen Sie die Leistung des Diensts, ohne dass die Gebühren für die Ausführung in Azure anfallen.

### <a name="collect-profiling-data-in-azure-to"></a>Erfassen Sie Profilerstellungsdaten in Azure:
* Testen der Leistung eines Clouddiensts unter einer simulierten oder realen Last.
* Verwenden Sie die Instrumentationsmethode sammeln von Profilerstellungsdaten, wie weiter unten in diesem Thema wird beschrieben.
* Testen Sie die Leistung des Diensts, in der gleichen Umgebung wie, wann der Dienst in der Produktion ausgeführt wird.

Üblicherweise simulieren Sie einen Load Test Cloud-Diensten unter Normal oder Belastung.

## <a name="profiling-a-cloud-service-in-azure"></a>Profilerstellung für einen Clouddienst in Azure
Wenn Sie Ihren Clouddienst aus Visual Studio veröffentlichen, können Sie das Profil für den Dienst und angeben, die Ihnen die Informationen geben die gewünschten Einstellungen für die profilerstellung. Eine Profilerstellungssitzung wird für jede Instanz einer Rolle gestartet. Weitere Informationen zum Veröffentlichen Ihres Diensts aus Visual Studio finden Sie unter [Veröffentlichen in Azure-Clouddienst aus Visual Studio](https://msdn.microsoft.com/library/azure/ee460772.aspx).

Weitere Informationen zur leistungsprofilerstellung in Visual Studio finden Sie unter [Beginners Guide to Performance Profiling](https://msdn.microsoft.com/library/azure/ms182372.aspx) und [Analysieren der Anwendungsleistung durch Verwenden von Profilerstellungstools](https://msdn.microsoft.com/library/azure/z9z62c29.aspx).

> [!NOTE]
> Sie können entweder IntelliTrace oder profilerstellung, wenn Sie Ihren Cloud-Dienst veröffentlichen. Sie können nicht beide Verfahren aktivieren.
> 
> 

### <a name="profiler-collection-methods"></a>Profiler-Sammlungsmethoden
Sie können verschiedene Erfassungsmethoden für die profilerstellung verwenden, basierend auf Ihrer Leistungsprobleme:

* **CPU-Sampling** – diese Methode sammelt Anwendungsstatistiken, die für die erste Analyse der CPU-Auslastungsproblemen nützlich sind. CPU-Sampling ist die empfohlene Methode zum Starten der meisten leistungsuntersuchungen. Es gibt keine großen Auswirkungen auf die Anwendung, die beim Sammeln von Samplingdaten für CPU-profilerstellung ausgeführt wird.
* **Instrumentation** – diese Methode sammelt detaillierte Zeiterfassungsdaten, die für fokussierte Analysen sowie für die Analyse von Eingabe/Ausgabe-Leistungsproblemen nützlich sind. Die Instrumentationsmethode zeichnet jeden Eintrag, beenden und Funktionsaufruf der Funktionen in einem Modul während der profilerstellung. Mithilfe dieser Methode können ausführliche Zeitsteuerungsdaten zu einem Abschnitt des Codes erfasst werden. Zudem werden mit dieser Methode die Auswirkungen von Eingabe- und Ausgabeoperationen auf die Leistung der Anwendung besser verständlich. Diese Methode ist für einen Computer mit einem 32-Bit-Betriebssystem deaktiviert. Diese Option steht nur, wenn Sie den Cloud-Dienst im Serveremulator nicht lokal in Azure ausführen.
* **.NET Memory Allocation** – diese Methode sammelt .NET Framework-Speicherbelegungsdaten mithilfe der Sampling-Profilerstellungsmethode. Die gesammelten Daten enthält, die Anzahl und Größe von zugeordneten Objekten.
* **Parallelität** – diese Methode erfasst Ressourcenkonfliktdaten sowie Prozess- und Threadausführungsdaten Ausführung, die bei der Analyse von Anwendungen mit mehreren Threads und Prozessen hilfreich sind. Die Parallelitätsmethode erfasst Daten für jedes Ereignis, das die Ausführung des Codes blockiert, z. B., wenn ein Thread darauf wartet, dass der gesperrte Zugriff auf eine Anwendungsressource freigegeben wird. Diese Methode ist hilfreich für das Analysieren von Multithreadanwendungen.
* Sie können auch aktivieren **Profilerstellung für Ebeneninteraktion**, die zusätzliche Informationen zu den Ausführungszeiten synchroner ADO.NET-Aufrufe bietet-Aufrufe von Anwendungen mit mehreren Ebenen, die mit einer oder mehreren Datenbanken kommunizieren. Sie können Ebeneninteraktionsdaten mit einem der folgenden Profilerstellungsmethoden erfassen. Weitere Informationen zur profilerstellung für Ebeneninteraktion finden Sie unter [Ansicht "Ebeneninteraktionen"](https://msdn.microsoft.com/library/azure/dd557764.aspx).

## <a name="configuring-profiling-settings"></a>Konfigurieren von profilerstellungseinstellungen
Die folgende Abbildung zeigt, wie profilerstellungseinstellungen im Dialogfeld "Azure-Anwendung veröffentlichen" konfigurieren.

![Profilerstellungseinstellungen konfigurieren](./media/vs-azure-tools-performance-profiling-cloud-services/IC526984.png)

> [!NOTE]
> So aktivieren Sie die **aktivieren die profilerstellung** Kontrollkästchen, benötigen Sie den Profiler, installiert auf dem lokalen Computer, die Sie verwenden, um Ihre Cloud-Dienst veröffentlichen. Der Profiler wird standardmäßig installiert, bei der Installation von Visual Studio.
> 
> 

### <a name="to-configure-profiling-settings"></a>So konfigurieren Sie profilerstellungseinstellungen
1. Klicken Sie im Projektmappen-Explorer das Kontextmenü für Ihr Azure-Projekt öffnen, und wählen Sie dann **veröffentlichen**. Ausführliche Anweisungen dazu, wie Sie einen Cloud-Dienst veröffentlichen, finden Sie unter [Veröffentlichen eines Clouddiensts mit den Azure Tools](http://go.microsoft.com/fwlink/p?LinkId=623012).
2. In der **Azure-Anwendung veröffentlichen** im Dialogfeld ausgewählt haben die **Erweiterte Einstellungen** Registerkarte.
3. Wählen Sie zum Aktivieren der profilerstellung der **aktivieren die profilerstellung** Kontrollkästchen.
4. Um Ihre profilerstellungseinstellungen zu konfigurieren, wählen die **Einstellungen** Hyperlink. Das Dialogfeld "Profilerstellungseinstellungen" wird angezeigt.
5. Von der **welche Methode der profilerstellung Sie verwenden möchten** Optionsschaltflächen, wählen Sie den Typ der profilerstellung, die Sie benötigen.
6. Wählen Sie zum Sammeln von Profilerstellungsdaten für Ebeneninteraktion das **Profilerstellung für Ebeneninteraktion aktivieren** Kontrollkästchen.
7. Um die Einstellungen zu speichern, wählen die **OK** Schaltfläche.
   
    Wenn Sie diese Anwendung veröffentlichen, werden diese Einstellungen verwendet, um die Profilerstellungssitzung für jede Rolle zu erstellen.

## <a name="viewing-profiling-reports"></a>Anzeigen von Profilerstellungsberichten
Eine Profilerstellungssitzung wird für jede Instanz einer Rolle im Cloud-Dienst erstellt. Zum Anzeigen Ihrer Profilerstellungsberichte jeder Sitzung in Visual Studio können Sie das Server-Explorer-Fenster anzeigen und wählen Sie dann auf den Azure Compute-Knoten, wählen Sie eine Instanz einer Rolle. Sie können dann der Profilerstellungsbericht anzeigen, wie in der folgenden Abbildung dargestellt.

![Anzeigen von Profilerstellungsberichten in Azure](./media/vs-azure-tools-performance-profiling-cloud-services/IC748914.png)

### <a name="to-view-profiling-reports"></a>Zum Anzeigen von Berichten der Profilerstellungstools
1. Wählen Sie den Server-Explorer-Fenster in Visual Studio anzeigen zu können, in der Menüleiste anzeigen, Server-Explorer.
2. Wählen Sie den Azure Compute-Knoten, und wählen Sie dann auf die Azure-bereitstellungsknoten für den Clouddienst, den Sie zum Profil ausgewählt, wenn Sie in Visual Studio veröffentlicht.
3. Um Profilerstellungsberichte für eine Instanz anzuzeigen, wählen Sie die Rolle im Dienst, öffnen Sie das Kontextmenü für eine bestimmte Instanz aus, und wählen Sie dann **Profilerstellungsbericht anzeigen**.
   
    Der Bericht, eine VSP-Datei wird nun aus Azure heruntergeladen, und der Status des Downloads wird im Azure-Aktivitätsprotokoll. Wenn der Download abgeschlossen ist, wird der Profilerstellungsbericht auf einer Registerkarte im Editor für Visual Studio mit dem Namen <Role name> *<Instance Number>* <identifier>VSP. Zusammengefasste Daten für den Bericht wird angezeigt.
4. Wählen Sie den Typ der Ansicht, die Sie möchten, um verschiedene Ansichten des Berichts, in der Liste Aktuelle Ansicht anzuzeigen. Weitere Informationen finden Sie unter [Berichtsansichten der Profilerstellungstools](https://msdn.microsoft.com/library/azure/bb385755.aspx).

## <a name="next-steps"></a>Nächste Schritte
[Debuggen von Cloud Services](https://msdn.microsoft.com/library/azure/ee405479.aspx)

[Veröffentlichen in Azure-Clouddienst aus Visual Studio](https://msdn.microsoft.com/library/azure/ee460772.aspx)


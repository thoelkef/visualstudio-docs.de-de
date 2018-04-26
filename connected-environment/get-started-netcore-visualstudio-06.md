---
title: 'Erstellen einer .NET Core-Entwicklungsumgebung mit Containern unter Verwendung von Kubernetes in der Cloud mit Visual Studio, Schritt 6: Informationen zur Entwicklung im Team | Microsoft-Dokumentation'
author: ghogen
ms.author: ghogen
ms.date: 04/05/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Schnelle Kubernetes-Entwicklung mit Containern und Microservices in Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, Container
manager: douge
ms.openlocfilehash: b4bc1f44e63614346f4e2d149e76becabdcb8c71
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="get-started-on-connected-environment-with-net-core-and-visual-studio"></a>Erste Schritte in Connected Environment mit .NET Core und Visual Studio

Vorheriger Schritt: [Aufrufen eines weiteren Containers](get-started-netcore-visualstudio-05.md)

## <a name="learn-about-team-development"></a>Informationen zur Entwicklung im Team

Bisher haben Sie den Code der Anwendung ausgeführt, als wären Sie der einzige Entwickler, der an der App arbeitet. In diesem Abschnitt erfahren Sie, wie die Entwicklung im Team durch Connected Environment optimiert wird:
* Entwicklerteams können zusammen in einer Entwicklungsumgebung arbeiten.
* Jeder Entwickler kann seinen Code separat durchlaufen, ohne befürchten zu müssen, dass er den Code von jemand anderem beschädigt.
* Code kann mithilfe von End-to-End-Tests vor dem Committen des Codes überprüft werden, ohne dass Abhängigkeiten imitiert oder simuliert werden müssen.

## <a name="challenges-with-developing-microservices"></a>Herausforderungen bei der Entwicklung von Microservices
Momentan ist die Beispielanwendung nicht sehr komplex. Bei der tatsächlichen Entwicklung entstehen allerdings schnell Probleme, wenn weitere Dienste hinzugefügt werden und das Entwicklerteam wächst.

Angenommen, Sie arbeiten an einem Dienst, der mit Dutzenden anderen Diensten interagiert.

1. Dann kann es sein, dass nicht mehr alle Dienste lokal für die Entwicklung ausgeführt werden können. Möglicherweise verfügt Ihr Entwicklungscomputer nicht über genügend Ressourcen, um die gesamte App auszuführen. Oder Ihre App verfügt über Endpunkte, die öffentlich erreichbar sein müssen (z.B. wenn Ihre App auf einen Webhook einer SaaS-App reagiert).
1. Sie können versuchen, nur die erforderlichen Dienste auszuführen. Das bedeutet jedoch, dass Sie alle Abhängigkeiten kennen müssen (z.B. Abhängigkeiten von Abhängigkeiten). Oder Sie wissen möglicherweise nicht, wie Ihre Abhängigkeiten erstellt und ausgeführt werden, da Sie nicht an ihnen gearbeitet haben.
1. Einige Entwickler greifen auf das Simulieren oder Imitieren vieler ihrer Dienstabhängigkeiten zurück. Das kann in manchen Fällen zwar hilfreich sein, aber das Verwalten solcher Imitate ist ebenfalls mit einem Entwicklungsaufwand verbunden. Außerdem führt dies dazu, dass Ihre Entwicklungsumgebung sich stark von der Produktion unterscheidet und sich kleine Fehler einschleichen können.
1. Daraus folgt, dass jegliche Art von End-to-End-Tests schwierig durchzuführen sind. Integrationstests können eigentlich nur nach dem Commit durchgeführt werden, weshalb später im Entwicklungszyklus Probleme auftreten können.

    ![](media/microservices-challenges.png)

## <a name="work-in-a-shared-development-environment"></a>Arbeiten in einer freigegebenen Entwicklungsumgebung
Mit Connected Environment können Sie eine *freigegebene* Entwicklungsumgebung in Azure einrichten. Jeder Entwickler kann sich auf seinen Teil der Anwendung konzentrieren und *Code vor dem Committen* in einer Umgebung iterativ entwickeln, die alle anderen Dienste und Cloudressourcen bereits enthält, von denen ihre Szenarios abhängig sind. Abhängigkeiten sind immer aktuell, und die Entwickler arbeiten auf eine Weise, die der Produktion ähnelt.

## <a name="work-in-your-own-space"></a>Arbeiten in Ihrem eigenen Bereich
Wenn Sie Code für Ihren Dienst entwickeln, befindet sich dieser die meiste Zeit nicht in einem fehlerfreien Zustand, bevor Sie ihn einchecken. Das Formen, Testen, und Experimentieren mit Projektmappen trägt iterativ weiterhin zur Entwicklung Ihres Codes bei. Connected Environment stellt das Konzept eines **Bereichs** bereit, das Ihnen ermöglicht, isoliert zu arbeiten, ohne den Bereich Ihrer Teammitglieder zu beeinträchtigen.

Gehen Sie wie folgt vor, um sicherzustellen, dass die Dienste `webfrontend` und `mywebapi` in Ihrer Entwicklungsumgebung und **im `mainline`-Bereich** ausgeführt werden.
1. Schließen Sie für beide Dienste sämtliche F5-Sitzungen bzw. Debugsitzungen, aber lassen Sie die Projekte in den einzelnen Visual Studio-Fenstern geöffnet.
2. Wechseln Sie zum Fenster von Visual Studio, das das `mywebapi`-Projekt enthält, und drücken Sie STRG+F5, um den Dienst ohne den angefügten Debugger auszuführen.
3. Wechseln Sie zum Fenster von Visual Studio, das das `webfrontend`-Projekt enthält, und drücken Sie STRG+F5, um dieses ebenfalls auszuführen.

> [!Note]
Manchmal müssen Sie erst Ihren Browser aktualisieren, wenn die Webseite angezeigt wird, nachdem Sie STRG+F5 gedrückt haben.

Jeder, der die öffentliche URL öffnet und zur Web-App navigiert, ruft den Codepfad auf, den Sie vorher geschrieben haben und der unter Verwendung des Standardbereichs `mainline` über beide Dienste ausgeführt wird. Angenommen, Sie wollen jetzt mit der Entwicklung von `mywebapi` fortfahren, und Sie wollen vermeiden, dass andere Entwickler gestört werden, die dieselbe Entwicklungsumgebung verwenden. Dafür können Sie Ihren eigenen Bereich einrichten.

### <a name="create-a-new-space"></a>Erstellen eines neuen Bereichs
Sie können über Visual Studio zusätzliche Bereiche erstellen, die verwendet werden, wenn Sie Ihren Dienst mit F5 oder STRG+F5 ausführen. Sie können die Bereiche beliebig benennen und flexibel ausdehnen (z.B. `sprint4` oder `demo`).

Gehen Sie zum Erstellen eines neuen Bereichs wie folgt vor:
1. Wechseln Sie zu dem Fenster von Visual Studio, das das `mywebapi`-Projekt enthält.
2. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und klicken Sie anschließend auf **Eigenschaften**.
3. Klicken Sie auf der linken Seite auf die Registerkarte **Debuggen**, damit die Einstellungen für Connected Environment angezeigt werden.
4. Über diese Einstellungen können Sie Connected Environment und/oder den Bereich ändern oder erstellen, der verwendet wird, wenn Sie F5 oder STRG+F5 verwenden. *Vergewissern Sie sich, dass die zuvor erstellte Connected Environment ausgewählt ist.*
5. Klicken Sie in der Dropdownliste unter **Bereich** auf **<Create New Space…>** (Neuen Bereich erstellen).

    ![](images/Settings.png)

6. Geben Sie im Dialogfeld **Add Space** (Bereich hinzufügen) einen Namen für den Bereich ein, und klicken Sie auf **OK**. Ich habe meinen Namen („scott“) für den neuen Bereich verwendet, damit meine Kollegen erkennen können, dass ich in diesem Bereich arbeite.

    ![](images/AddSpace.png)

7. Jetzt sollten Ihre Entwicklungsumgebung und Ihr neuer Bereich auf der Eigenschaftenseite des Projekts ausgewählt sein.

    ![](images/Settings2.png)

### <a name="update-code-for-mywebapi"></a>Aktualisieren von Code für *mywebapi*

1. Nehmen Sie im `mywebapi`-Projekt wie folgt eine Codeänderung an der `string Get(int id)`-Methode in der `ValuesController.cs`-Datei vor:
 
    ```csharp
    [HttpGet("{id}")]
    public string Get(int id)
    {
        return "mywebapi now says something new";
    }
    ```

2. Legen Sie in diesem aktualisierten Codeblock einen Breakpoint fest, falls Sie dies noch nicht getan haben.
3. Drücken Sie F5, um den `mywebapi`-Dienst zu starten. Dann wird der Dienst in Ihrer Entwicklungsumgebung unter Verwendung des ausgewählten Bereichs (hier `scott`) gestartet.

An dieser Stelle wird ein Diagramm angezeigt, mit dessen Hilfe Sie die Funktionsweise der verschiedenen Bereiche besser nachvollziehen können. Der blaue Pfad stellt eine Anforderung über den `mainline`-Bereich dar. Dabei handelt es sich um den Standardpfad, der verwendet wird, wenn der URL kein Bereich vorangestellt ist. Der grüne Pfad stellt eine Anforderung über den `scott`-Bereich dar.

![](media/Space-Routing.png)

Mithilfe dieser in Connected Environment integrierten Funktion können Sie End-to-End-Tests von Codes in einer freigegebenen Umgebung durchführen, ohne dass jeder Entwickler sämtliche Dienste in seinem Bereich neu erstellen muss. Beachten Sie, dass dieses Routing die Weitergabe von Headern im App-Code erfordert, wie im vorherigen Schritt dieses Leitfadens veranschaulicht.

## <a name="test-code-running-in-the-scott-space"></a>Testen von Code, der im `scott`-Bereich ausgeführt wird
Zum Testen Ihrer neuen Version von `mywebapi` in Verbindung mit `webfrontend` öffnen Sie in Ihrem Browser die öffentliche URL für den Zugriffspunkt für `webfrontend` (z.B. https://webfrontend-teamenv.vsce.io), und wechseln Sie zur Seite „Info“. Dann sollte die ursprüngliche Nachricht „Hello from webfrontend and Hello from mywebapi“ (Willkommen in webfrontend und Willkommen in mywebapi) angezeigt werden.

Fügen Sie jetzt der URL den Zusatz „scott“ hinzu, sodass sie in etwa wie folgt lautet: https://scott-webfrontend-teamenv.vsce.io. Aktualisieren Sie anschließend den Browser. Sie sollten dann den Breakpoint erreichen, den Sie in Ihrem `mywebapi`-Projekt festgelegt haben. Klicken Sie auf F5, um fortzufahren. Dann sollte in Ihrem Browser die neue Meldung „Hello from webfrontend and mywebapi now says something new“ (Die Begrüßungsmeldungen von webfrontend und mywebapi haben sich verändert) angezeigt werden. Dies liegt daran, dass der Pfad zu Ihrem aktualisierten Code in `mywebapi` im Bereich `scott` ausgeführt wird.

> [!div class="nextstepaction"]
> [Zusammenfassung](get-started-netcore-visualstudio-07.md)
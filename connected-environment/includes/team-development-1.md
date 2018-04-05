Bisher haben Sie den Code der Anwendung ausgeführt, als wären Sie der einzige Entwickler, der an der App arbeitet. In diesem Abschnitt erfahren Sie, wie die Entwicklung im Team durch Connected Environment optimiert wird:
* Entwicklerteams können zusammen in einer Entwicklungsumgebung arbeiten.
* Jeder Entwickler kann seinen Code separat durchlaufen, ohne befürchten zu müssen, dass er den Code von jemand anderem beschädigt.
* Code kann mithilfe von End-to-End-Tests vor dem Committen des Codes überprüft werden, ohne dass Abhängigkeiten imitiert oder simuliert werden müssen.

## <a name="challenges-with-developing-microservices"></a>Herausforderungen bei der Entwicklung von Microservices
Momentan ist die Beispielanwendung nicht sehr komplex. Bei der tatsächlichen Entwicklung entstehen allerdings schnell Probleme, wenn weitere Dienste hinzugefügt werden und das Entwicklungsteam wächst.

Angenommen, Sie arbeiten an einem Dienst, der mit Dutzenden anderen Diensten interagiert.

1. Dann kann es sein, dass nicht mehr alle Dienste lokal für die Entwicklung ausgeführt werden können. Möglicherweise verfügt Ihr Entwicklungscomputer nicht über genügend Ressourcen, um die gesamte App auszuführen. Oder Ihre App verfügt über Endpunkte, die öffentlich erreichbar sein müssen (z.B. wenn Ihre App auf einen Webhook einer SaaS-App reagiert).
1. Sie können versuchen, nur die erforderlichen Dienste auszuführen. Das bedeutet jedoch, dass Sie alle Abhängigkeiten kennen müssen (z.B. Abhängigkeiten von Abhängigkeiten). Oder Sie wissen möglicherweise nicht, wie Ihre Abhängigkeiten erstellt und ausgeführt werden, da Sie nicht an ihnen gearbeitet haben.
1. Einige Entwickler greifen auf das Simulieren oder Imitieren vieler ihrer Dienstabhängigkeiten zurück. Das kann in manchen Fällen zwar hilfreich sein, aber das Verwalten solcher Imitate ist ebenfalls mit einem Entwicklungsaufwand verbunden. Außerdem führt dies dazu, dass Ihre Entwicklungsumgebung sich stark von der Produktion unterscheidet und sich kleine Fehler einschleichen können.
1. Daraus folgt, dass jegliche Art von End-to-End-Tests schwierig durchzuführen sind. Integrationstests können eigentlich nur nach dem Commit durchgeführt werden, weshalb später im Entwicklungszyklus Probleme auftreten können.

![](../media/microservices-challenges.png)


## <a name="work-in-a-shared-development-environment"></a>Arbeiten in einer freigegebenen Entwicklungsumgebung
Mit Connected Environment können Sie eine *freigegebene* Entwicklungsumgebung in Azure einrichten. Jeder Entwickler kann sich auf seinen Teil der Anwendung konzentrieren und *Code vor dem Committen* in einer Umgebung iterativ entwickeln, die alle anderen Dienste und Cloudressourcen bereits enthält, von denen ihre Szenarios abhängig sind. Abhängigkeiten sind immer auf dem neuesten Stand, und die Entwickler arbeiten auf eine Weise, die der Produktion ähnelt.

## <a name="work-in-your-own-space"></a>Arbeiten in Ihrem eigenen Bereich
Wenn Sie Code für Ihren Dienst entwickeln, befindet sich dieser die meiste Zeit nicht in einem fehlerfreien Zustand, bevor Sie ihn einchecken. Das Formen, Testen, und Experimentieren mit Projektmappen trägt mit jedem Schritt weiterhin zur Entwicklung Ihres Codes bei. Connected Environment stellt das Konzept eines **Bereichs** bereit, das Ihnen ermöglicht, isoliert zu arbeiten, ohne den Bereich Ihrer Teammitglieder zu beeinträchtigen.

> [!Note]
> Schließen Sie alle Fenster von Visual Studio Code für beide Dienste, und führen Sie dann `vsce up -d` in jedem Stammordner des Diensts aus, bevor Sie fortfahren. (Dies ist eine Einschränkung der Vorschauversion.)

Betrachten Sie einmal näher, wo die Dienste derzeit ausgeführt werden. Führen Sie den Befehl `vsce list` aus und eine Ausgabe, die der Folgenden ähnelt, wird angezeigt:

```
Name         Space     Chart              Ports   Updated     Access Points
-----------  --------  -----------------  ------  ----------  -------------------------
mywebapi     mainline  mywebapi-0.1.0     80/TCP  2m ago     <not attached>
webfrontend  mainline  webfrontend-0.1.0  80/TCP  1m ago     https://webfrontend-contosodev.vsce.io
```

Die Spalte „Bereich“ gibt an, dass beide Dienste in einem Bereich namens `mainline` ausgeführt werden. Jeder, der die öffentliche URL öffnet und zur Web-App navigiert, ruft den Codepfad auf, den Sie vorher geschrieben haben und der über beide Dienste ausgeführt wird. Angenommen, Sie möchten mit der Entwicklung von `mywebapi` fortfahren. Wie können Sie das tun, ohne andere Entwickler zu unterbrechen, die diese Entwicklungsumgebung verwenden? Dafür können Sie Ihren eigenen Bereich einrichten.

## <a name="create-a-space"></a>Erstellen eines Bereichs
Zum Ausführen Ihrer eigenen Version von `mywebapi` in einem anderen Bereich als `mainline`, erstellen Sie Ihren eigenen Bereich:
``` 
vsce space create --name scott
```

Im obigen Beispiel wird der Name des Autors für den neuen Bereich verwendet, damit das Team sehen kann, wer in diesem Bereich arbeitet. Sie können Ihren Bereich jedoch beliebig benennen, z.B. „sprint4“ oder „demo“. 

Führen Sie den Befehl `vsce space list` aus, um eine Liste aller Bereiche in der Entwicklungsumgebung anzuzeigen. Neben dem momentan ausgewählten Bereich wird ein Sternchen (*) angezeigt. In diesem Fall wurde der Bereich namens „scott“ bei der Erstellung automatisch ausgewählt. Mit dem Befehl `vsce space select` können Sie jederzeit einen anderen Bereich auswählen.

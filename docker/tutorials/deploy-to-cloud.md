---
title: 'Docker-Tutorial-Teil 9: Bereitstellen in der Cloud'
description: Stellen Sie eine docker-App für einen Cloud-Dienst zum Hosting bereit.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 661f9f6833b5ac5d42aacde7f228b042bef00bb0
ms.sourcegitcommit: c4212f40df1a16baca1247cac2580ae699f97e4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/31/2020
ms.locfileid: "89176766"
---
# <a name="deploy-to-the-cloud"></a>Bereitstellen in der Cloud

Nachdem Sie Ihre APP lokal ausgeführt haben, können Sie sich über die Ausführung in der Cloud Gedanken machen, damit andere Benutzer darauf zugreifen und Sie verwenden können. Zu diesem Zweck verwenden Sie docker-Kontexte. Ein Kontext ist der Ort, an dem Sie derzeit mit Containern arbeiten. Zurzeit verfügen Sie nur über Ihren "Standard"-Kontext, sodass Sie eine Cloud hinzufügen und Ihre APP für die APP bereitstellen müssen.

## <a name="create-your-cloud-context"></a>Erstellen Sie Ihren cloudkontext

1. Um zu beginnen, können Sie sehen, welche Kontexte Sie haben, indem Sie sich den Abschnitt "Kontexte" im docker-Panel ansehen:

   ![Zeigt nur den Standardkontext an](media/defaultcontext.png)

Der Standardkontext für lokale Arbeit sollte nur angezeigt werden.

1. Zum Bereitstellen in der Cloud müssen Sie einen neuen ACI-Kontext erstellen, aber zu diesem Zweck benötigen Sie zunächst die Azure-Konto Erweiterung für die Authentifizierung bei Azure.

   ![Azure-Erweiterung hinzufügen](media/addazureextension.png)

Sie müssen ein Azure-Konto einrichten, falls Sie noch nicht über ein Konto verfügen.

1. Nun können Sie den neuen ACI-Kontext erstellen. Klicken Sie hierzu im Abschnitt **Kontexte** der Docker-Sicht auf die Schaltfläche Plus.

   ![Erstellen Ihres ACI-Kontexts](media/createnewcontext.png)

Dadurch werden Sie gefragt, unter welcher Ressourcengruppe Sie diese Container ausführen möchten. Wählen Sie entweder eine vorhandene Gruppe mithilfe der Pfeiltasten aus, oder verwenden Sie die Standardoption, um die neue Gruppe zu verwenden.

![Auswählen der Ressourcengruppe](media/selectresourcegroup.png)

Sie können jetzt Ihren ACI-Kontext auflisten und mit der rechten Maustaste darauf klicken, um den aktuellen Fokus/in Gebrauch zu machen:

![Es kann ein neuer ACI-Kontext ausgewählt werden.](media/listofcontexts.png)

## <a name="run-containers-in-the-cloud"></a>Ausführen von Containern in der Cloud

1. Verwenden Sie nun ihren ACI-Kontext, und führen Sie den Container aus.

   ```bash
   docker context use myacicontext
   docker run  -dp 3000:3000 <username>/getting-started
   ```

1. Wenn Sie diese ausgeführt haben, betrachten Sie nun den Container in ihrem Kontext.

   ![Im ACI-Kontext laufender Container](media/contextcontainer.png)

1. Um dies zu überprüfen, klicken Sie mit der rechten Maustaste auf den Container wird ausgeführt, und wählen Sie **in Browser anzeigen aus**.

   ![Container in ACI mit öffentlicher IP-Adresse](media/containerinaci.png)

Und Sie können sehen, dass der Container in einer öffentlichen IP-Adresse ausgeführt wird und ordnungsgemäß funktioniert.

1. Nun können Sie sich den laufenden Container ansehen, um zu sehen, wie er funktioniert. Sie können beginnen, indem Sie die Container Protokolle sehen:
 
 ```bash
   docker logs distracted-jackson
   ```

1. Sie können auch einen exec in ihren Container durchführt, wie dies bei einem lokalen Container der Fall ist.
 
 ```bash
   docker exec -it distracted-jackson sh
   ```

1. Wenn Sie den Arbeitsbereich bereinigt haben und sicherstellen möchten, dass die Ausführung des Test Containers weiterhin nicht in Rechnung gestellt wird, können Sie einfach mit der rechten Maustaste auf den ausgetretenen Container klicken und **Entfernen**auswählen.

## <a name="recap"></a>Zusammenfassung

Fantastisch, Sie haben nun ihre Arbeitsauslastung übernommen und die Cloud zum ersten Mal erfolgreich in der Cloud bereitgestellt. Sie können all dies von der Befehlszeile aus innerhalb Ihres ACI-Kontexts mithilfe von `docker run` ausführen und auch verwenden `docker compose up` , um Ihre Anwendungen mit mehreren Containern auszuführen. Weitere Informationen zum Ausführen ihrer Container in der Cloud finden Sie in der erweiterten [Dokumentation zur Verwendung von ACI](https://docs.docker.com/engine/context/aci-integration/).

## <a name="next-steps"></a>Nächste Schritte

Fahren Sie mit dem Tutorial fort.

> [!div class="nextstepaction"]
> [Was kommt als nächstes](whats-next.md)

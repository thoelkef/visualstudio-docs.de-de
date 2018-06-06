---
title: Fügen Sie neue Verbindungen hinzu
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: a7b580f8bd04c4fbce9518d903a568bbd0f9175a
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34747091"
---
# <a name="add-new-connections"></a>Fügen Sie neue Verbindungen hinzu

Sie können testen Sie die Verbindung mit einer Datenbank oder den Dienst und Durchsuchen von Inhalt von Datenbanken und Schemas, mit **Server-Explorer**, **Cloud Explorer**, oder **SQL Server-Objekt-Explorer**. Die Funktionalität dieser Fenster überschneidet sich zu einem gewissen Grad. Die grundlegenden Unterschiede sind:

- Server-Explorer

   In Visual Studio standardmäßig installiert. Dient zum Testen von Verbindungen und SQL Server-Datenbanken, alle anderen Datenbanken, die ein ADO.NET-Anbieter installiert ist und einige Azure-Dienste anzeigen. Zeigt auch Objekte auf niedriger Ebene, z. B. System-Leistungsindikatoren, Ereignisprotokolle und Meldungswarteschlangen. Wenn eine Datenquelle keine ADO.NET-Anbieter verfügt, sie hier angezeigt wird nicht, aber dennoch können Sie sie aus Visual Studio durch programmgesteuerten Herstellen einer Verbindung.

- Cloud-Explorer

   Installieren Sie dieses Fenster manuell als Visual Studio-Erweiterung dazu **Tools**, **Erweiterungen und Updates**, **Online**, **Visual Studio Markeplace**. Bietet speziellen Funktionen zum Durchsuchen und Herstellen einer Verbindung mit Azure-Dienste.

- SQL Server-Objekt-Explorer

   Mit SQL Server Data Tools installiert sind und unter der **Ansicht** Menü. Wenn Sie es nicht sehen, wechseln Sie zu **Programme und Funktionen** in der Systemsteuerung finden Sie Visual Studio, und wählen Sie dann **Änderung** das Installationsprogramm erneut ausführen, nach dem Aktivieren des Kontrollkästchens für SQL Server Data Tools. Verwendung **Objekt-Explorer von SQL Server** Ansicht SQL-Datenbanken (Wenn sie einen ADO.NET-Anbieter haben), neue Datenbanken erstellen, Ändern von Schemas, gespeicherte Prozeduren erstellen, Abrufen von Verbindungszeichenfolgen, Anzeigen der Daten und vieles mehr. SQL-Datenbanken, die keine ADO.NET-Anbieter installiert sein, werden hier angezeigt, aber Sie können weiterhin eine Verbindung herstellen, diese programmgesteuert.

## <a name="add-a-connection-in-server-explorer"></a>Fügen Sie im Server-Explorer eine Verbindung hinzu

Um eine Verbindung mit der Datenbank zu erstellen, klicken Sie auf die **Verbindung hinzufügen** Symbol **Server-Explorer**, oder mit der rechten Maustaste im **Server-Explorer** auf die **Daten Verbindungen** Knoten, und wählen **Verbindung hinzufügen**. Von hier aus können Sie auch mit einer Datenbank auf einem anderen Server, SharePoint-Dienst oder ein Azure-Dienst verbinden.

![Symbol "Server-Explorer neue Verbindung"](../data-tools/media/raddata-server-explorer-new-connection-icon.png)

Daraufhin wird die **Verbindung hinzufügen** (Dialogfeld). Hier haben wir den Namen der SQL Server-LocalDB-Instanz eingegeben.

![Neue Verbindung hinzufügen](../data-tools/media/raddata-add-new-connection-dialog.png)

## <a name="change-the-provider"></a>Ändern Sie den Anbieter

Wenn die Datenquelle nicht wünschen ist, klicken Sie auf die **Änderung** Schaltfläche, um eine neue Datenquelle und/oder einen neuen ADO.NET-Datenanbieter auszuwählen. Der neue Anbieter ggf. aufgefordert, Ihre Anmeldeinformationen, abhängig von der Konfiguration.

![Änderung AD0.NET-Datenanbieter](../data-tools/media/raddata-change-ad0.net-data-provider.png)

## <a name="test-the-connection"></a>Testen der Verbindung

Nachdem Sie die Datenquelle ausgewählt haben, klicken Sie auf **Testverbindung**. Wenn es nicht erfolgreich, müssen Sie zur Problembehandlung bei basierend auf der Dokumentation des Herstellers.

![Testverbindung](../data-tools/media/raddata-test-connection.png)

Wenn der Test erfolgreich ist, sind Sie bereit für die Erstellung einer *Datenquelle*, also in ein Visual Studio-Begriff, der tatsächlich bedeutet eine *Datenmodell* auf Grundlage der zugrunde liegenden Datenbank oder der Dienst.

## <a name="see-also"></a>Siehe auch

- [Visual Studio-Datentools für .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
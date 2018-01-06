---
title: "Neue Verbindungen hinzufügen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 26a45e8fe44e2e0945a105711ae84b1082d5c891
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
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

![Symbol "Server-Explorer neue Verbindung"](../data-tools/media/raddata-server-explorer-new-connection-icon.png "Raddata Symbol "neue Verbindung zu Server-Explorer"")

Daraufhin wird die **Verbindung hinzufügen** (Dialogfeld). Hier haben wir den Namen der SQL Server-LocalDB-Instanz eingegeben.  

![Neue Verbindung hinzufügen](../data-tools/media/raddata-add-new-connection-dialog.png "Raddata neue Verbindungsdialogfeld hinzufügen")  

## <a name="change-the-provider"></a>Ändern Sie den Anbieter

Wenn die Datenquelle nicht wünschen ist, klicken Sie auf die **Änderung** Schaltfläche, um eine neue Datenquelle und/oder einen neuen ADO.NET-Datenanbieter auszuwählen. Der neue Anbieter ggf. aufgefordert, Ihre Anmeldeinformationen, abhängig von der Konfiguration.

![Datenanbieter AD0.NET ändern](../data-tools/media/raddata-change-ad0.net-data-provider.png "Raddata ändern AD0.NET-Datenanbieter")

## <a name="test-the-connection"></a>Testen der Verbindung

Nachdem Sie die Datenquelle ausgewählt haben, klicken Sie auf **Testverbindung**. Wenn es nicht erfolgreich, müssen Sie zur Problembehandlung bei basierend auf der Dokumentation des Herstellers.

![Verbindung testen](../data-tools/media/raddata-test-connection.png "Raddata Verbindung testen")

Wenn der Test erfolgreich ist, sind Sie bereit für die Erstellung einer *Datenquelle*, also in ein Visual Studio-Begriff, der tatsächlich bedeutet eine *Datenmodell* auf Grundlage der zugrunde liegenden Datenbank oder der Dienst.

## <a name="see-also"></a>Siehe auch

[Visual Studio-Datentools für .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
---
title: Neue Verbindungen hinzufügen
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 927edacf968ed92eddea96f93cc4f67cbd137fcc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53880597"
---
# <a name="add-new-connections"></a>Neue Verbindungen hinzufügen

Sie können die Verbindung mit einer Datenbank oder einem Dienst zu testen und Durchsuchen von Inhalt von Datenbanken und Schemas, mithilfe von **Server-Explorer**, **Cloud-Explorer**, oder **SQL Server-Objekt-Explorer**. Die Funktionalität dieser Windows überschneidet sich zu einem gewissen Grad. Die grundlegenden Unterschiede sind:

- Server-Explorer

   Standardmäßig in Visual Studio installiert. Kann zum Testen von Verbindungen und Anzeigen von SQL Server-Datenbanken, alle anderen Datenbanken, die einen ADO NET-Anbieter installiert haben und einige Azure-Dienste verwendet werden. Zeigt auch die Low-Level-Objekte, z. B. Leistungsindikatoren, Ereignisprotokolle und Meldungswarteschlangen. Wenn eine Datenquelle keine ADO NET-Anbieter verfügt, es hier angezeigt wird nicht, aber dennoch können Sie sie aus Visual Studio durch programmgesteuertes Verbinden von.

- Cloud-Explorer

   Installieren Sie dieses Fenster manuell wie Visual Studio-Erweiterung dazu **Tools** > **Erweiterungen und Updates** > **Online**  >  **Visual Studio Marketplace unter**. Bietet speziellen Funktionen zum Durchsuchen und eine Verbindung mit Azure-Dienste.

- SQL Server-Objekt-Explorer

   Mit SQL Server Data Tools installiert und unter der **Ansicht** Menü. Wenn Sie es nicht angezeigt wird, wechseln Sie zu **Programme und Funktionen** in der Systemsteuerung Suchen nach Visual Studio, und wählen Sie dann **Änderung** das Installationsprogramm erneut ausführen, nach dem Aktivieren des Kontrollkästchens für SQL Server Data Tools. Verwendung **Objekt-Explorer von SQL Server** zu Ansicht SQL-Datenbanken (Wenn sie einen ADO.NET-Anbieter verfügen), neue Datenbanken erstellen, Ändern von Schemas, gespeicherte Prozeduren erstellen, Abrufen von Verbindungszeichenfolgen, zeigen Sie die Daten und vieles mehr. SQL-Datenbanken, die keine ADO.NET-Anbieter installiert sein, nicht hier angezeigt, aber Sie können weiterhin darauf Programmgesteuertes verbinden.

## <a name="add-a-connection-in-server-explorer"></a>Fügen Sie im Server-Explorer eine Verbindung hinzu

Um eine Verbindung mit der Datenbank zu erstellen, klicken Sie auf die **Verbindung hinzufügen** Symbol **Server-Explorer**, oder mit der rechten Maustaste im **Server-Explorer** auf die **Daten Verbindungen** Knoten, und wählen **Verbindung hinzufügen**. Von hier aus können Sie auch in eine Datenbank auf einem anderen Server, SharePoint-Dienst oder ein Azure-Dienst verbinden.

![Symbol "Server-Explorer neue Verbindung"](../data-tools/media/raddata-server-explorer-new-connection-icon.png)

Dadurch wird die **Verbindung hinzufügen** Dialogfeld. Hier haben wir den Namen der SQL Server LocalDB-Instanz eingegeben.

![Neue Verbindung hinzufügen](../data-tools/media/raddata-add-new-connection-dialog.png)

## <a name="change-the-provider"></a>Wechseln Sie den Anbieter

Wenn die Datenquelle nicht gewünscht ist, klicken Sie auf die **Änderung** Schaltfläche, um eine neue Datenquelle bzw. den neuen ADO.NET-Datenanbieter auswählen. Der neue Anbieter möglicherweise bitten, Ihre Anmeldeinformationen ein, je nachdem, wie Sie es konfiguriert.

![Änderung AD0.NET-Datenanbieter](../data-tools/media/raddata-change-ad0.net-data-provider.png)

## <a name="test-the-connection"></a>Verbindung testen

Nachdem Sie die Datenquelle ausgewählt haben, klicken Sie auf **Testverbindung**. Wenn sie nicht erfolgreich ist, müssen Sie zur Problembehandlung basierend auf der Dokumentation des Herstellers.

![Testverbindung](../data-tools/media/raddata-test-connection.png)

Wenn der Test erfolgreich ist, sind Sie bereit zum Erstellen einer *Datenquelle*, dies ist ein Visual Studio-Begriff, der eigentlich bedeutet, dass eine *Datenmodell* , basiert auf die zugrunde liegende Datenbank oder den Dienst.

## <a name="see-also"></a>Siehe auch

- [Visual Studio-Datentools für .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
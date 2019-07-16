---
title: Neue Verbindung hinzufügen | Microsoft-Dokumentation
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 8a93c287-2834-4a83-a590-bdc3fe8d293f
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ff1ec43d6faec329db6138598d84e47db009113e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68192512"
---
# <a name="add-new-connections"></a>Neue Verbindungen hinzufügen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die Verbindung mit einer Datenbank oder einem Dienst zu testen und Durchsuchen von Inhalt von Datenbanken und Schemas, mithilfe von **Server-Explorer**, **Cloud-Explorer**, oder **SQL Server-Objekt-Explorer**. Die Funktionalität dieser Windows überschneidet sich zu einem gewissen Grad. Die grundlegenden Unterschiede sind:  
  
 Server-Explorer  
 Standardmäßig in Visual Studio installiert. Kann zum Testen von Verbindungen und Anzeigen von SQL Server-Datenbanken, alle anderen Datenbanken, die einen ADO NET-Anbieter installiert haben und einige Azure-Dienste verwendet werden. Zeigt auch die Low-Level-Objekte, z. B. Leistungsindikatoren, Ereignisprotokolle und Meldungswarteschlangen. Wenn eine Datenquelle keine ADO NET-Anbieter verfügt, es hier angezeigt wird nicht, aber dennoch können Sie sie aus Visual Studio durch programmgesteuertes Verbinden von.  
  
 Cloud-Explorer  
 Installieren Sie dieses Fenster manuell wie Visual Studio-Erweiterung dazu **Tools** > **Erweiterungen und Updates** > **Online**  >  **Visual Studio-Katalog**. Bietet speziellen Funktionen zum Durchsuchen und eine Verbindung mit Azure-Dienste.  
  
 SQL Server-Objekt-Explorer  
 Mit SQL Server Data Tools installiert und unter der **Ansicht** Menü. Wenn Sie es nicht angezeigt wird, wechseln Sie zu **Programme und Funktionen** in der Systemsteuerung Suchen nach Visual Studio, und wählen Sie dann **Änderung** das Installationsprogramm erneut ausführen, nach dem Aktivieren des Kontrollkästchens für SQL Server Data Tools. Verwendung **Objekt-Explorer von SQL Server** zu Ansicht SQL-Datenbanken (Wenn sie einen ADO.NET-Anbieter verfügen), neue Datenbanken erstellen, Ändern von Schemas, gespeicherte Prozeduren erstellen, Abrufen von Verbindungszeichenfolgen, zeigen Sie die Daten und vieles mehr. SQL-Datenbanken, die keine ADO.NET-Anbieter installiert sein, nicht hier angezeigt, aber Sie können weiterhin darauf Programmgesteuertes verbinden.  
  
## <a name="add-a-connection-in-server-explorer"></a>Fügen Sie im Server-Explorer eine Verbindung hinzu  
 Um eine Verbindung mit der Datenbank zu erstellen, klicken Sie auf die **Verbindung hinzufügen** Symbol **Server-Explorer**, oder mit der rechten Maustaste im **Server-Explorer** auf die **Daten Verbindungen** Knoten, und wählen **Verbindung hinzufügen**. Von hier aus können Sie auch in eine Datenbank auf einem anderen Server, SharePoint-Dienst oder ein Azure-Dienst verbinden.  
  
 ![Symbol "Server-Explorer neue Verbindung"](../data-tools/media/raddata-server-explorer-new-connection-icon.png "Raddata neue Verbindung zu Server-Explorer-Symbol")  
  
 Dadurch wird die **Verbindung hinzufügen** Dialogfeld. Hier haben wir den Namen der SQL Server LocalDB-Instanz eingegeben.  
  
 ![Neue Verbindung hinzufügen](../data-tools/media/raddata-add-new-connection-dialog.png "Raddata hinzufügen neue Dialogfeld \"Verbindung\"")  
  
## <a name="change-the-provider"></a>Wechseln Sie den Anbieter  
 Wenn die Datenquelle nicht gewünscht ist, klicken Sie auf die **Änderung** Schaltfläche, um eine neue Datenquelle bzw. den neuen ADO.NET-Datenanbieter auswählen. Der neue Anbieter möglicherweise bitten, Ihre Anmeldeinformationen ein, je nachdem, wie Sie es konfiguriert.  
  
 ![Datenanbieter AD0.NET ändern](../data-tools/media/raddata-change-ad0-net-data-provider.png "Raddata Änderung AD0.NET-Datenanbieter")  
  
## <a name="test-the-connection"></a>Verbindung testen  
 Nachdem Sie die Datenquelle ausgewählt haben, klicken Sie auf **Testverbindung**. Wenn sie nicht erfolgreich ist, müssen Sie zur Problembehandlung basierend auf der Dokumentation des Herstellers.  
  
 ![Die Testverbindung](../data-tools/media/raddata-test-connection.png "Raddata Verbindung testen")  
  
 Wenn der Test erfolgreich ist, sind Sie bereit zum Erstellen einer *Datenquelle*, dies ist ein Visual Studio-Begriff, der eigentlich bedeutet, dass eine *Datenmodell* , basiert auf die zugrunde liegende Datenbank oder den Dienst.  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio-Datentools für .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)

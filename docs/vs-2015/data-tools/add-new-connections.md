---
title: Neue Verbindungen hinzufügen | Microsoft-Dokumentation
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 8a93c287-2834-4a83-a590-bdc3fe8d293f
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 44146613fb43b6fc4269741ba09b94629f888d5f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72673075"
---
# <a name="add-new-connections"></a>Neue Verbindungen hinzufügen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die Verbindung mit einer Datenbank oder einem Dienst testen und Datenbankinhalte und-Schemas mithilfe von **Server-Explorer**, **Cloud-Explorer**oder **SQL Server-Objekt-Explorer**untersuchen. Die Funktionalität dieser Fenster überschneidet sich in gewisser Weise. Die grundlegenden Unterschiede lauten:

 Server-Explorer standardmäßig in Visual Studio installiert. Kann verwendet werden, um Verbindungen zu testen und SQL Server Datenbanken, alle anderen Datenbanken mit installiertem ADO.NET-Anbieter und einige Azure-Dienste anzuzeigen. Zeigt auch Objekte auf niedriger Ebene, z. b. Systemleistungs Indikatoren, Ereignisprotokolle und Nachrichten Warteschlangen. Wenn eine Datenquelle keinen ADO.NET-Anbieter aufweist, wird Sie hier nicht angezeigt, Sie können Sie jedoch auch in Visual Studio verwenden, indem Sie Programm gesteuert eine Verbindung herstellen.

 Cloud-Explorer dieses Fenster manuell als Visual Studio-Erweiterung zu installieren, indem Sie **Tools**  > **Erweiterungen und Updates**  > **Online**  > **Visual Studio Gallery**auswählen. Bietet spezialisierte Funktionen zum untersuchen und verbinden mit Azure-Diensten.

 SQL Server-Objekt-Explorer mit SQL Server Data Tools installiert und im Menü **Ansicht** sichtbar. Wenn Sie dort nicht angezeigt wird, navigieren Sie in der Systemsteuerung zu **Programme und Funktionen** , suchen Sie nach Visual Studio, und wählen Sie dann **ändern** aus, um den Installer erneut auszuführen, nachdem Sie das Kontrollkästchen für SQL Server Data Tools ausgewählt haben. Verwenden Sie **SQL Server-Objekt-Explorer** zum Anzeigen von SQL-Datenbanken (wenn Sie über einen ADO.NET-Anbieter verfügen), erstellen Sie neue Datenbanken, ändern Sie Schemas, erstellen Sie gespeicherte Prozeduren, rufen Sie Verbindungs Zeichenfolgen, Daten anzeigen usw. SQL-Datenbanken, die keinen ADO.NET-Anbieter installiert haben, werden hier nicht angezeigt, aber Sie können weiterhin Programm gesteuert eine Verbindung mit Ihnen herstellen.

## <a name="add-a-connection-in-server-explorer"></a>Hinzufügen einer Verbindung in Server-Explorer
 Um eine Verbindung mit der Datenbank herzustellen, klicken Sie in **Server-Explorer**auf das Symbol **Verbindung hinzufügen** , oder klicken Sie mit der rechten Maustaste auf **Server-Explorer** auf dem Knoten **Datenverbindungen** , und wählen Sie **Verbindung hinzufügen**aus. Von hier aus können Sie auch eine Verbindung mit einer Datenbank auf einem anderen Server, einem SharePoint-Dienst oder einem Azure-Dienst herstellen.

 ![Symbol "neue Verbindung Server-Explorer"](../data-tools/media/raddata-server-explorer-new-connection-icon.png "Symbol für raddata Server-Explorer neue Verbindung")

 Dadurch wird das Dialogfeld **Verbindung hinzufügen** geöffnet. Hier haben wir den Namen der SQL Server localdb-Instanz eingegeben.

 ![Neue Verbindung hinzufügen](../data-tools/media/raddata-add-new-connection-dialog.png "Dialog Feld "raddata-Verbindung hinzufügen"")

## <a name="change-the-provider"></a>Ändern des Anbieters
 Wenn die Datenquelle nicht Ihren Wünschen entspricht, klicken Sie auf die Schaltfläche **ändern** , um eine neue Datenquelle und/oder einen neuen ADO.NET-Datenanbieter auszuwählen. Je nachdem, wie Sie Sie konfiguriert haben, kann der neue Anbieter ihre Anmelde Informationen anfordern.

 ![Ändern der AD0.NET-Datenanbieter](../data-tools/media/raddata-change-ad0-net-data-provider.png "raddata-Änderung AD0.NET Datenanbieter")

## <a name="test-the-connection"></a>Verbindung testen
 Nachdem Sie die Datenquelle ausgewählt haben, klicken Sie auf **Verbindung testen**. Wenn dies nicht gelingt, müssen Sie basierend auf der Dokumentation des Herstellers eine Problembehandlung durchführen.

 ![Verbindung testen](../data-tools/media/raddata-test-connection.png "raddata-Test Verbindung")

 Wenn der Test erfolgreich ist, können Sie eine *Datenquelle*erstellen, die ein Visual Studio-Begriff ist, der tatsächlich ein *Datenmodell* ist, das auf der zugrunde liegenden Datenbank oder dem zugrunde liegenden Dienst basiert.

## <a name="see-also"></a>Siehe auch
 [Visual Studio-Datentools für .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)

---
title: Visual Studio-Datentools für C++ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a3849d9-1bc7-47d1-805e-1755223ccba2
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: cecad69f6df283ed005afd00a6b9bedbd51c6cd5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47522509"
---
# <a name="visual-studio-data-tools-for-c"></a>Visual Studio-Datentools für C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Visual Studio-Datentools für C++](https://docs.microsoft.com/visualstudio/data-tools/visual-studio-data-tools-for-cpp).  
  
  
Systemeigener C++-Code kann oft die schnellste beim Zugreifen auf Datenquellen verwendet werden. Data Tools für C++-Anwendungen in Visual Studio ist jedoch nicht so umfangreich wie es für .NET-Anwendungen ist. Z. B. können nicht die Daten-Datenquellen-Fenster verwendet werden, ziehen und Ablegen von Datenquellen auf einer Entwurfsoberfläche C++. Wenn Sie eine objektrelationale Ebene benötigen, müssen Sie einen eigenen Handler erstellen, oder verwenden Sie ein Produkt von Drittanbietern.  Dies gilt auch für die Datenbindung Funktionalität, obwohl Anwendungen, die die Microsoft Foundation Class-Bibliothek verwenden einige Datenbankklassen mit Dokumenten und Ansichten, verwenden können, um Daten im Arbeitsspeicher speichern und für den Benutzer anzuzeigen. Weitere Informationen finden Sie unter [-Datenzugriff in Visual C++](https://msdn.microsoft.com/library/7wtdsdkh.aspx) .  
  
 Zum Verbinden mit SQL-Datenbanken können systemeigene C++-Anwendungen, die ODBC- und OLE DB-Treiber und der ADO-Anbieter, der in Windows enthalten sind.     Diese können auf eine beliebige Datenbank verbinden, die diese Schnittstellen unterstützt. Der ODBC-Treiber ist der Standard. OLE DB wird für die Abwärtskompatibilität bereitgestellt. Weitere Informationen zu diesen Data-Technologien, finden Sie unter [Windows Data Access Components](https://msdn.microsoft.com/library/windows/desktop/aa968814\(v=vs.85\).aspx)  
  
 Profitieren Sie von benutzerdefinierten Funktionen in SQL Server 2005 und höher verwenden die [SQL Server Native Client](https://msdn.microsoft.com/sqlserver/aa937733). Der native Client enthält auch den SQL Server-ODBC-Treiber und der SQL Server-OLE DB-Anbieter in eine systemeigene dynamic Link Library (DLL). Anwendungen mit APIs in systemeigenem Code (ODBC, OLE DB und ADO) für Microsoft SQL Server unterstützt werden.  SQL Server Native Client wird mit SQL Server Data Tools installiert. Dem Programmierleitfaden für ist hier: [SQL Server Native Client-Programmierung](https://msdn.microsoft.com/library/ms130892.aspx).  
  
## <a name="to-connect-to-localdb-through-odbc-and-sql-native-client-from-a-c-application"></a>Aus einer C++-Anwendung eine Verbindung mit LocalDB über ODBC und SQL Native Client  
  
1.  Installieren Sie SQL Server Datatools.  
  
2.  Wenn Sie eine Beispiel-SQL-Datenbank für die Verbindung benötigen, laden Sie die Northwind-Datenbank, und Entzippen Sie sie an einem neuen Speicherort.  
  
3.  Verwenden Sie SQL Server Management Studio, um den entzippten Datei Northwind.mdf auf LocalDB anzufügen. Wenn SQL Server Management Studio gestartet wird, verbinden Sie mit (Localdb) \MSSQLLocalDB.  
  
     ![SSMS-Verbindungsdialogfeld](../data-tools/media/raddata-ssms-connect-dialog.png "Raddata SSMS-Verbindungsdialogfeld")  
  
     Klicken Sie dann mit der rechten Maustaste auf den Knoten "Localdb" im linken Bereich, und wählen **Anfügen**.  
  
     ![Datenbank Anfügen von SSMS](../data-tools/media/raddata-ssms-attach-database.png "Raddata SSMS Anfügen der Datenbank")  
  
4.  Laden Sie das ODBC-Windows-SDK-Beispiel, und Entzippen Sie sie an einem neuen Speicherort. Dieses Beispiel zeigt die grundlegende ODBC-Befehle, die für die Verbindung mit einer Datenbank und Ausgeben von Abfragen und Befehle verwendet werden. Weitere Informationen finden Sie Informationen zu diesen Funktionen in der [Microsoft Open Database Connectivity (ODBC)](https://msdn.microsoft.com/library/windows/desktop/ms710252\(v=vs.85\).aspx). Wenn Sie zunächst die Projektmappe laden (er befindet sich im Ordner "C++"), bietet Visual Studio zum Aktualisieren der Lösung auf die aktuelle Version von Visual Studio. Klicken Sie auf **Ja**.  
  
5.  Um den nativen Client verwenden zu können, benötigen Sie die Headerdatei und der Lib-Datei. Diese Dateien enthalten Funktionen und spezifischen Definitionen für SQL Server, über die ODBC-Funktionen in sql.h definiert. In **Projekt** > **Eigenschaften** > **VC++-Verzeichnisse**, fügen Sie die folgenden include-Verzeichnis hinzu:  
  
 **\<Systemlaufwerk >: \Programme\Microsoft SQL Server\110\SDK\Include** und diesem Bibliotheksverzeichnis:  
  
 **c:\Program Files\Microsoft SQL Server\110\SDK\Lib**  
  
6.  Fügen Sie diese Zeilen in odbcsql.cpp hinzu. Die #define wird verhindert, dass irrelevante OLE DB-Definitionen aus, das kompiliert wird.  
  
    ```  
    #define _SQLNCLI_ODBC_  
    #include <sqlncli.h>  
    ```  
  
     Beachten Sie, dass das Beispiel nicht tatsächlich die native Client-Funktionalität, verwendet damit die vorherigen Schritte nicht erforderlich, dafür sind zu kompilieren und auszuführen. Aber das Projekt ist jetzt für die Sie verwenden diese Funktion konfiguriert. Weitere Informationen finden Sie unter [SQL Server Native Client-Programmierung](https://msdn.microsoft.com/library/ms130892\(v=sql.130\).aspx).  
  
7.  Geben Sie den zu verwendenden im Subsystem ODBC-Treiber. Im Beispiel wird das Treiber Verbindungszeichenfolgen-Attribut in als ein Befehlszeilenargument übergeben. In **Projekt** > **Eigenschaften** > **Debuggen**, fügen Sie diesen Befehlsargument hinzu:  
  
    ```  
    DRIVER="SQL Server Native Client 11.0"  
    ```  
  
8.  Drücken Sie F5, um die Anwendung zu erstellen und auszuführen. Daraufhin sollte ein Dialogfeld aus dem Treiber, die Sie aufgefordert werden, geben Sie eine Datenbank. Geben Sie `(localdb)\MSSQLLocalDB`, und überprüfen Sie **vertrauenswürdige Verbindung**. Drücken Sie **OK**. Eine Konsole mit Nachrichten, die eine erfolgreiche Verbindung angeben, sollte angezeigt werden. Außerdem sollte eine Eingabeaufforderung angezeigt werden, können Sie in einer SQL-Anweisung eingeben. Der folgende Bildschirm zeigt eine Beispielabfrage und die Ergebnisse:  
  
     ![ODBC-Beispiel-Abfrageausgabe](../data-tools/media/raddata-odbc-sample-query-output.png "Raddata ODBC-Beispiel-Abfrageausgabe")  
  
## <a name="see-also"></a>Siehe auch  
 [Zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)



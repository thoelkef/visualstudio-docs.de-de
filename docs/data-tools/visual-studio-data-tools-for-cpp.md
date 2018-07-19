---
title: Visual Studio-Datentools für C++
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CPP
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
- cplusplus
ms.openlocfilehash: fe50ecd01b8f3112340510a78f76d6e380ec3136
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/29/2018
ms.locfileid: "37117029"
---
# <a name="visual-studio-data-tools-for-c"></a>Visual Studio-Datentools für C++

Systemeigener C++-Code kann oft die schnellste beim Zugreifen auf Datenquellen verwendet werden. Data Tools für C++-Anwendungen in Visual Studio ist jedoch nicht so umfangreich wie es für .NET-Anwendungen ist. Z. B. können nicht die Daten-Datenquellen-Fenster verwendet werden, ziehen und Ablegen von Datenquellen auf einer Entwurfsoberfläche C++. Wenn Sie eine objektrelationale Ebene benötigen, müssen Sie einen eigenen Handler erstellen, oder verwenden Sie ein Produkt von Drittanbietern.  Dies gilt auch für die Datenbindung Funktionalität, obwohl Anwendungen, die die Microsoft Foundation Class-Bibliothek verwenden einige Datenbankklassen mit Dokumenten und Ansichten, verwenden können, um Daten im Arbeitsspeicher speichern und für den Benutzer anzuzeigen. Weitere Informationen finden Sie unter [-Datenzugriff in Visual C++](/cpp/data/data-access-in-cpp).

Zum Verbinden mit SQL-Datenbanken können systemeigene C++-Anwendungen, die ODBC- und OLE DB-Treiber und der ADO-Anbieter, der in Windows enthalten sind. Diese können auf eine beliebige Datenbank verbinden, die diese Schnittstellen unterstützt. Der ODBC-Treiber ist der Standard. OLE DB wird für die Abwärtskompatibilität bereitgestellt. Weitere Informationen zu diesen Data-Technologien, finden Sie unter [Windows Data Access Components](https://msdn.microsoft.com/library/windows/desktop/aa968814.aspx).

Profitieren Sie von benutzerdefinierten Funktionen in SQL Server 2005 und höher verwenden die [SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client). Der native Client enthält auch den SQL Server-ODBC-Treiber und der SQL Server-OLE DB-Anbieter in eine systemeigene dynamic Link Library (DLL). Anwendungen mit APIs in systemeigenem Code (ODBC, OLE DB und ADO) für Microsoft SQL Server unterstützt werden.  SQL Server Native Client wird mit SQL Server Data Tools installiert. Dem Programmierleitfaden für ist hier: [SQL Server Native Client-Programmierung](/sql/relational-databases/native-client/sql-server-native-client-programming).

## <a name="to-connect-to-localdb-through-odbc-and-sql-native-client-from-a-c-application"></a>Aus einer C++-Anwendung eine Verbindung mit LocalDB über ODBC und SQL Native Client

1.  Installieren Sie SQL Server Datatools.

2.  Wenn Sie eine Beispiel-SQL-Datenbank für die Verbindung benötigen, laden Sie die Northwind-Datenbank, und Entzippen Sie sie an einem neuen Speicherort.

3.  Verwenden Sie SQL Server Management Studio, um den entzippten Anfügen *Northwind.mdf* Datei LocalDB. Wenn SQL Server Management Studio gestartet wird, verbinden Sie mit (Localdb) \MSSQLLocalDB.

     ![SSMS-Verbindungsdialogfeld](../data-tools/media/raddata-ssms-connect-dialog.png)

     Klicken Sie dann mit der rechten Maustaste auf den Knoten "Localdb" im linken Bereich, und wählen **Anfügen**.

     ![SSMS die Datenbank anfügen](../data-tools/media/raddata-ssms-attach-database.png)

4.  Laden Sie das ODBC-Windows-SDK-Beispiel, und Entzippen Sie sie an einem neuen Speicherort. Dieses Beispiel zeigt die grundlegende ODBC-Befehle, die für die Verbindung mit einer Datenbank und Ausgeben von Abfragen und Befehle verwendet werden. Weitere Informationen finden Sie Informationen zu diesen Funktionen in der [Microsoft Open Database Connectivity (ODBC)](/sql/odbc/microsoft-open-database-connectivity-odbc). Wenn Sie zunächst die Projektmappe laden (er befindet sich im Ordner "C++"), bietet Visual Studio zum Aktualisieren der Lösung auf die aktuelle Version von Visual Studio. Klicken Sie auf **Ja**.

5.  Um den nativen Client verwenden zu können, müssen Sie die *Header* Datei und *Lib* Datei. Diese Dateien enthalten Funktionen und spezifischen Definitionen für SQL Server, über die ODBC-Funktionen in sql.h definiert. In **Projekt** > **Eigenschaften** > **VC++-Verzeichnisse**, fügen Sie die folgenden include-Verzeichnis hinzu:

**%ProgramFiles%\Microsoft SQL Server\110\SDK\Include**

Und dieses Bibliotheksverzeichnis:

**%ProgramFiles%\Microsoft SQL Server\110\SDK\Lib**

6.  Fügen Sie diese Zeilen in *odbcsql.cpp*. Die #define wird verhindert, dass irrelevante OLE DB-Definitionen aus, das kompiliert wird.

    ```cpp
    #define _SQLNCLI_ODBC_
    #include <sqlncli.h>
    ```

    Beachten Sie, dass das Beispiel nicht tatsächlich die native Client-Funktionalität, verwendet damit die vorherigen Schritte nicht erforderlich, dafür sind zu kompilieren und auszuführen. Aber das Projekt ist jetzt für die Sie verwenden diese Funktion konfiguriert. Weitere Informationen finden Sie unter [Programmierung für SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client).

7.  Geben Sie den zu verwendenden im Subsystem ODBC-Treiber. Im Beispiel wird das Treiber Verbindungszeichenfolgen-Attribut in als ein Befehlszeilenargument übergeben. In **Projekt** > **Eigenschaften** > **Debuggen**, fügen Sie diesen Befehlsargument hinzu:

    ```cpp
    DRIVER="SQL Server Native Client 11.0"
    ```

8.  Drücken Sie **F5**, um die Anwendung zu erstellen und auszuführen. Daraufhin sollte ein Dialogfeld aus dem Treiber, die Sie aufgefordert werden, geben Sie eine Datenbank. Geben Sie `(localdb)\MSSQLLocalDB`, und überprüfen Sie **vertrauenswürdige Verbindung**. Drücken Sie **OK**. Eine Konsole mit Nachrichten, die eine erfolgreiche Verbindung angeben, sollte angezeigt werden. Außerdem sollte eine Eingabeaufforderung angezeigt werden, können Sie in einer SQL-Anweisung eingeben. Der folgende Bildschirm zeigt eine Beispielabfrage und die Ergebnisse:

     ![ODBC-Beispiel-Abfrageausgabe](../data-tools/media/raddata-odbc-sample-query-output.png)

## <a name="see-also"></a>Siehe auch

- [Zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
---
title: "Visual Studio-Tools mit Daten für C++ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 3a3849d9-1bc7-47d1-805e-1755223ccba2
caps.latest.revision: "9"
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.technology: vs-data-tools
ms.openlocfilehash: c5952c4ab8e8adac0338d406800a15a8a0b12989
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="visual-studio-data-tools-for-c"></a>Visual Studio-Tools mit Daten für C++
Systemeigener C++-Code kann oft die schnellste beim Zugreifen auf Datenquellen. Daten für C++-Anwendungen in Visual Studio-Tools ist jedoch nicht so umfangreich wie für .NET-Anwendungen ist. Data Sources Windows können z. B. verwendet werden, Drag & drop-Datenquellen auf einer C++-Entwurfsoberfläche. Wenn Sie eine objektrelationale Ebene benötigen, müssen Sie einen eigenen Handler erstellen oder ein Produkt eines Drittanbieters verwenden.  Dasselbe gilt für Datenbindungsfunktion, obwohl Anwendungen, die die Microsoft Foundation Class-Bibliothek verwenden zum Speichern von Daten im Arbeitsspeicher, und zeigen Sie es dem Benutzer einige Datenbankklassen mit Dokumenten und Ansichten, verwenden können. Weitere Informationen finden Sie unter [-Datenzugriff in Visual C++](https://msdn.microsoft.com/en-us/library/7wtdsdkh.aspx) .  
  
 Zur Verbindung mit SQL-Datenbanken können systemeigene C++-Anwendungen, die ODBC- und OLE DB-Treiber und den ADO-Anbieter, die in Windows enthalten sind. Diese können auf eine beliebige Datenbank verbinden, die diese Schnittstellen unterstützt. Der ODBC-Treiber ist die Standardoption. OLE DB wird aus Gründen der Abwärtskompatibilität. Weitere Informationen zu diesen datentechnologien, finden Sie unter [Windows Data Access Components](https://msdn.microsoft.com/en-us/library/windows/desktop/aa968814\(v=vs.85\).aspx)  
  
 Nutzen von benutzerdefinierten Funktionen in SQL Server 2005 und höher, verwenden die [SQL Server Native Client](https://msdn.microsoft.com/en-us/sqlserver/aa937733). Der native Client enthält außerdem die SQL Server-ODBC-Treiber und der SQL Server OLE DB-Anbieter in eine systemeigene dynamic Link Library (DLL). Anwendungen mit APIs in systemeigenem Code (ODBC, OLE DB und ADO) für Microsoft SQL Server unterstützt werden.  SQL Server Native Client wird mit SQL Server Data Tools installiert. Die Programmierung Handbuch finden Sie hier: [SQL Server Native Client-Programmierung](https://msdn.microsoft.com/en-us/library/ms130892.aspx).  
  
## <a name="to-connect-to-localdb-through-odbc-and-sql-native-client-from-a-c-application"></a>Von einer C++-Anwendung eine Verbindung auf "LocalDB" über ODBC und SQL Native Client  
  
1.  Installieren von SQL Server Datatools.  
  
2.  Wenn Sie eine SQL-Beispieldatenbank für die Verbindung benötigen, laden Sie die Northwind-Datenbank, und Entpacken Sie es an einem neuen Speicherort.  
  
3.  Verwenden Sie SQL Server Management Studio, um die entzippt anzufügende Datei auf "LocalDB" anzufügen. Beim Starten von SQL Server Management Studio eine Verbindung herstellen Sie, um \MSSQLLocalDB (Localdb).  
  
     ![Dialogfeld "Verbindung" SSMS](../data-tools/media/raddata-ssms-connect-dialog.png "Raddata SSMS-Verbindungsdialogfeld")  
  
     Klicken Sie dann mit der rechten Maustaste auf den Knoten "Localdb" im linken Bereich, und wählen Sie **Anfügen**.  
  
     ![Datenbank anfügen SSMS](../data-tools/media/raddata-ssms-attach-database.png "Raddata SSMS Anfügen der Datenbank")  
  
4.  Herunterladen Sie der ODBC-Windows-SDK-Beispiel und Entpacken Sie es an einem neuen Speicherort. Dieses Beispiel zeigt die grundlegende ODBC-Befehle, die für die Verbindung mit einer Datenbank und Abfragen und Befehle verwendet werden. Weitere Informationen finden Sie Informationen zu diesen Funktionen in der [Microsoft Open Database Connectivity (ODBC)](https://msdn.microsoft.com/en-us/library/windows/desktop/ms710252\(v=vs.85\).aspx). Wenn Sie zuerst die Projektmappe laden (er befindet sich im Ordner "C++"), bietet Visual Studio auf die aktuelle Version von Visual Studio die Projektmappe zu aktualisieren. Klicken Sie auf **Ja**.  
  
5.  Um die native Client verwenden zu können, benötigen Sie die Headerdatei und Lib-Datei. Diese Dateien enthalten Funktionen und Definitionen, die spezifisch für SQL Server, über die ODBC-Funktionen in sql.h definiert. In **Projekt** > **Eigenschaften** > **VC++-Verzeichnisse**, fügen Sie die folgenden Includeverzeichnis hinzu:  
  
 **\<Systemlaufwerk >: \Programme\Microsoft SQL Server\110\SDK\Include** und das Verzeichnis für diese Bibliothek:  
  
 **c:\Program Files\Microsoft SQL Server\110\SDK\Lib**  
  
6.  Fügen Sie die folgenden Zeilen in odbcsql.cpp hinzu. Die #define wird verhindert, dass irrelevante OLE DB-Definitionen aus, das kompiliert wird.  
  
    ```C++  
    #define _SQLNCLI_ODBC_  
    #include <sqlncli.h>  
    ```  
  
     Beachten Sie, dass das Beispiel nicht tatsächlich die native Client-Funktionalität, verwendet damit die vorhergehenden Schritte nicht erforderlich, dafür sind zu kompilieren und auszuführen. Aber das Projekt jetzt zur Verwendung dieser Funktionen konfiguriert wurde. Weitere Informationen finden Sie unter [SQL Server Native Client-Programmierung](https://msdn.microsoft.com/en-us/library/ms130892\(v=sql.130\).aspx).  
  
7.  Geben Sie den zu verwendenden im Subsystem ODBC-Treiber. Im Beispiel wird der Treiber Verbindungszeichenfolgen-Attribut in als Befehlszeilenargument übergeben. In **Projekt** > **Eigenschaften** > **Debuggen**, fügen Sie dieses Befehlsargument hinzu:  
  
    ```C++  
    DRIVER="SQL Server Native Client 11.0"  
    ```  
  
8.  Drücken Sie F5, um die Anwendung zu erstellen und auszuführen. Ein Dialogfeld aus dem Treiber, die Sie eine Datenbank geben dazu aufgefordert werden, sollte angezeigt werden. Geben Sie `(localdb)\MSSQLLocalDB`, und überprüfen Sie **vertrauenswürdige Verbindung verwenden**. Press **OK**. Eine Konsole mit Nachrichten, die eine erfolgreiche Verbindung angeben, sollte angezeigt werden. Es sollte eine Eingabeaufforderung angezeigt werden, können Sie in einer SQL-Anweisung eingeben. Der folgende Bildschirm zeigt eine Beispielabfrage und die Ergebnisse:  
  
     ![ODBC-Beispiel-Abfrageausgabe](../data-tools/media/raddata-odbc-sample-query-output.png "Raddata ODBC-Beispiel-Abfrageausgabe")  
  
## <a name="see-also"></a>Siehe auch  
 [Zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
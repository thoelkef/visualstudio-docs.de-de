---
title: Daten Tools fürC++
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CPP
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
- cplusplus
ms.openlocfilehash: 33c91a7c21a04624d71692d12b7a7f15a16e1d67
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72639503"
---
# <a name="visual-studio-data-tools-for-c"></a>Visual Studio-Datentools für C++

Native C++ kann häufig die schnellste Leistung bieten, wenn Sie auf Datenquellen zugreifen. Daten Tools für C++ Anwendungen in Visual Studio sind jedoch nicht so umfangreich wie für .NET-Anwendungen. Beispielsweise kann das Fenster **Datenquellen** nicht zum Ziehen und Ablegen von Datenquellen auf eine C++ Entwurfs Oberfläche verwendet werden. Wenn Sie eine Objekt relationale Ebene benötigen, müssen Sie Ihre eigenen Schreiben oder ein Drittanbieter Produkt verwenden. Das gleiche gilt für die Daten Bindungs Funktionalität, obwohl Anwendungen, die die Microsoft Foundation Class-Bibliothek verwenden, einige Datenbankklassen und Dokumente und Sichten verwenden können, um Daten im Arbeitsspeicher zu speichern und für den Benutzer anzuzeigen. Weitere Informationen finden Sie unter [Datenzugriff in Visual C++ ](/cpp/data/data-access-in-cpp).

Zum Herstellen einer Verbindung mit SQL- C++ Datenbanken können native Anwendungen die ODBC-und OLE DB-Treiber und den in Windows enthaltenen ADO-Anbieter verwenden. Diese können eine Verbindung mit jeder Datenbank herstellen, die diese Schnittstellen unterstützt. Der ODBC-Treiber ist der Standard. OLE DB wird aus Gründen der Abwärtskompatibilität bereitgestellt. Weitere Informationen zu diesen Daten Technologien finden Sie unter [Windows Data Access Components](/previous-versions/windows/desktop/ms692897(v=vs.85)).

Um die benutzerdefinierte Funktionalität in SQL Server 2005 und höher zu nutzen, verwenden Sie den [SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client). Der Native Client enthält auch den SQL Server ODBC-Treiber und den SQL Server OLE DB-Anbieter in einer nativen dll (Dynamic Link Library). Diese unterstützen Anwendungen, die APIs mit System eigenem Code (ODBC, OLE DB und ADO) verwenden, um Microsoft SQL Server. SQL Server Native Client wird mit SQL Server Data Tools installiert. Das Programmier Handbuch finden Sie hier: [SQL Server Native Client-Programmierung](/sql/relational-databases/native-client/sql-server-native-client-programming).

## <a name="to-connect-to-localdb-through-odbc-and-sql-native-client-from-a-c-application"></a>So stellen Sie über ODBC eine Verbindung mit localdb her C++ und SQL Native Client aus einer-Anwendung

1. Installieren Sie SQL Server Data Tools.

2. Wenn Sie eine Beispiel-SQL-Datenbank für die Verbindung benötigen, laden Sie die Northwind-Datenbank herunter, und entpacken Sie Sie an einem neuen Speicherort.

3. Verwenden Sie SQL Server Management Studio, um die entzippte Datei *Northwind. mdf* an localdb anzufügen. Wenn SQL Server Management Studio gestartet wird, stellen Sie eine Verbindung mit (localdb) \mssqllocaldbher.

   ![Dialogfeld "SSMS Connect"](../data-tools/media/raddata-ssms-connect-dialog.png)

   Klicken Sie dann mit der rechten Maustaste auf den Knoten localdb im linken Bereich, und wählen Sie **Anfügen**aus.

   ![SSMS-Anfüge Datenbank](../data-tools/media/raddata-ssms-attach-database.png)

4. Laden Sie das ODBC-Windows SDK Beispiel herunter, und entpacken Sie es an einem neuen Speicherort. Dieses Beispiel zeigt die grundlegenden ODBC-Befehle, die verwendet werden, um eine Verbindung mit einer Datenbank herzustellen und Abfragen und Befehle auszugeben. Weitere Informationen zu diesen Funktionen finden Sie im [Microsoft Open Database Connectivity (ODBC)](/sql/odbc/microsoft-open-database-connectivity-odbc). Wenn Sie die Projekt C++ Mappe zum ersten Mal laden (diese befindet sich im Ordner), bietet Visual Studio eine Aktualisierung der Projekt Mappe auf die aktuelle Version von Visual Studio an. Klicken Sie auf **Ja**.

5. Um den Native Client verwenden zu können, benötigen Sie die *Header* Datei und die *lib* -Datei. Diese Dateien enthalten Funktionen und Definitionen, die für SQL Server spezifisch sind, außer den in SQL. h definierten ODBC-Funktionen. Fügen Sie in **Projekt**  > **Eigenschaften**  > **VC + +-Verzeichnissen**das folgende Includeverzeichnis hinzu:

   **%ProgramFiles%\Microsoft SQL Server\110\SDK\Include**

   Und dieses Bibliotheksverzeichnis:

   **%ProgramFiles%\Microsoft SQL Server\110\SDK\Lib**

6. Fügen Sie diese Zeilen in " *ODBCSQL. cpp*" hinzu. Der #define verhindert, dass irrelevante OLE DB Definitionen kompiliert werden.

   ```cpp
   #define _SQLNCLI_ODBC_
   #include <sqlncli.h>
   ```

    Beachten Sie, dass im Beispiel tatsächlich keine der Native Client-Funktionen verwendet wird, sodass die vorangehenden Schritte nicht erforderlich sind, damit Sie kompiliert und ausgeführt werden können. Das Projekt ist nun jedoch so konfiguriert, dass Sie diese Funktion verwenden können. Weitere Informationen finden Sie unter [SQL Server Native Client-Programmierung](/sql/relational-databases/native-client/sql-server-native-client).

7. Geben Sie an, welcher Treiber im ODBC-Subsystem verwendet werden soll. Das Beispiel übergibt das Attribut für die Treiber Verbindungs Zeichenfolge in als Befehlszeilenargument. Fügen Sie in **Project**  > **Properties**  > **Debugging**das folgende Befehls Argument hinzu:

   ```cpp
   DRIVER="SQL Server Native Client 11.0"
   ```

8. Drücken Sie **F5**, um die Anwendung zu erstellen und auszuführen. Es sollte ein Dialogfeld mit dem Treiber angezeigt werden, in dem Sie aufgefordert werden, eine Datenbank einzugeben. Geben Sie `(localdb)\MSSQLLocalDB` ein, und aktivieren Sie **Vertrauenswürdige Verbindung verwenden**. Klicken Sie auf **OK**. Es sollte eine Konsole mit Meldungen angezeigt werden, die auf eine erfolgreiche Verbindung hinweisen. Außerdem sollte eine Eingabeaufforderung angezeigt werden, in der Sie eine SQL-Anweisung eingeben können. Der folgende Bildschirm zeigt eine Beispiel Abfrage und die Ergebnisse:

   ![Ausgabe der ODBC-Beispiel Abfrage](../data-tools/media/raddata-odbc-sample-query-output.png)

## <a name="see-also"></a>Siehe auch

- [Zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
---
title: "Integrieren von SQL Server mit R Tools für Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 4/28/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 919dfc34-234a-489e-91bf-74a4cefae26c
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: 44ae1fd825997ff5eab1448ebd86f88a130172a1
ms.contentlocale: de-de
ms.lasthandoff: 05/12/2017

---


# <a name="working-with-sql-server-and-r"></a>Arbeiten mit SQL Server und R

R Tools für Visual Studio (RTVS) nutzt die hervorragende Unterstützung von Visual Studio für SQL Server, damit Datenspezialisten einfach mit SQL-Datenbanken arbeiten können, z.B. um SQL-Abfragen zu erstellen und auszuführen und mit gespeicherten Prozeduren zu arbeiten.

> [!Note]
> Um mit SQL und R zu arbeiten, müssen Sie die SQL Server-Datentools installiert haben:
> - Visual Studio 2017: Führen Sie das Installationsprogramm von Visual Studio aus, und wählen Sie den Datenspeicher und die Verarbeitungsworkload aus, die SQL Server-Datentools enthält.
> - Visual Studio 2015: Befolgen Sie die Anweisungen unter [SQL Server Data Tools herunterladen](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt).

Das folgende Video (3:03 Min.) bietet einen kurzen Überblick über SQL Server und R:

<iframe width="560" height="315" src="https://www.youtube.com/embed/n4AYr0QIwdQ" frameborder="0" allowfullscreen></iframe>

## <a name="creating-and-running-sql-queries"></a>Erstellen und Ausführen von SQL-Abfragen

RTVS unterstützt das Hinzufügen von SQL-Abfragen in R-Projekten, wobei Sie die Möglichkeit haben, interaktiv SQL-Abfragen in einem separaten Kontext zu entwickeln, bis Sie die gewünschten Ergebnisse erhalten.

Um eine SQL-Abfragedatei hinzuzufügen, klicken Sie mit der rechten Maustaste auf das Projekt im Projektmappen-Explorer, wählen Sie **Hinzufügen > Neues Element...** und dann den Dateityp der **SQL-Abfrage** aus:

![Hinzufügen eines SQL-Abfrageelements zu einem Projekt](media/sql-add-item.png)

Die Datei wird im Transact-SQL-Editor von Visual Studio geöffnet, wobei vollständiges IntelliSense für SQL und die Möglichkeit zum Ausführen von Abfragen bereitgestellt wird. Damit diese Funktionen funktionieren, müssen Sie eine Verbindung zu einer Datenbank mithilfe der Schaltfläche „Verbinden“ auf der Symbolleiste des Editors herstellen oder einfach versuchen, eine Abfrage auszuführen (STRG+UMSCHALT+E; funktioniert auch auf einer Auswahl). Egal für welche Möglichkeit Sie sich entscheiden, es wird das Dialogfeld „Verbindung“ angezeigt:

![Dialogfeld „SQL-Verbindung“](media/sql-connection-dialog.png)

Sobald eine Verbindung hergestellt wurde, können Sie Abfragen ausführen und Ergebnisse anzeigen:

![SQL-Fenster mit Abfrageergebnissen](media/sql-query-results.png)

Der Transact-SQL-Editor unterstützt eine Vielzahl anderer Funktionen, z.B. die Darstellung des Ausführungsplans für die Abfrage, einen Abfragedebugger und auch viele andere Funktionen, die im Transact-SQL-Editor verfügbar sind. Weitere Informationen finden Sie unter [Verwenden des Transact-SQL-Editors zum Bearbeiten und Ausführen von Skripts](https://msdn.microsoft.com/library/hh272706.aspx).

## <a name="working-with-sql-server-stored-procedures"></a>Arbeiten mit gespeicherten SQL Server-Prozeduren

Durch [SQL Server-R Services](https://docs.microsoft.com/sql/advanced-analytics/r/sql-server-r-services) (SQL Server 2016 und höher) können Sie R-Code aus einer gespeicherten T-SQL-Prozedur einbetten und ausführen. Das bedeutet, dass Sie R Code auf einem SQL Server-Computer ausführen, für von einer SQL-Abfrage zurückgegebene Daten nutzen und ein SQL-Resultset generieren können, dass von SQL weiterverarbeitet oder an den Client zurückgegeben werden kann.

RTVS vereinfacht den ansonsten komplizierten und fehleranfälligen Prozess zum Kombinieren von SQL und R-Code in einer SQL-Anweisung, so wie in den folgenden Abschnitten beschrieben:

- [Hinzufügen einer Datenbankverbindung](#add-a-database-connection)
- [Schreiben und Testen einer in SQL gespeicherten Prozedur](#write-and-test-a-sql-stored-procedure)
- [Veröffentlichen einer in SQL gespeicherten Prozedur](#publish-a-sql-stored-procedure)

Das folgende Video (6:09 Min.) bietet auch eine Übersicht dieser Funktionen:

<iframe width="560" height="315" src="https://www.youtube.com/embed/dFKIT2OitWQ" frameborder="0" allowfullscreen></iframe>

### <a name="add-a-database-connection"></a>Hinzufügen einer Datenbankverbindung

1. Wählen Sie **R Tools > Daten > Datenbankverbindung hinzufügen** aus, um das Dialogfeld **Verbindungseigenschaften** anzuzeigen, indem Sie den Namen der Datenquelle (in diesem Fall SQL Server), den Namen des Servers, den Authentifizierungsmodus und den Namen der Datenbank angeben. Sie können **Testverbindung** auswählen, um Ihre Eingabe zu überprüfen, bevor Sie das Dialogfeld schließen.
 
    ![SQL-Verbindung (Dialogfeld)](media/sql-connection-string-dialog.png)

1. Sobald Sie auf **OK** geklickt haben, generiert Visual Studio mit einer gültigen Verbindung eine Verbindungszeichenfolge mit dem Namen `dbConnection` in einer neuen `settings.R`-Datei. RTVS fügt diese Datei automatisch hinzu (führt dies aus), damit Sie die Verbindung von R-Skripts sofort nutzen können:

![SQL-Datei „Settings.R“](media/sql-settings-dot-r.png)

### <a name="write-and-test-a-sql-stored-procedure"></a>Schreiben und Testen einer in SQL gespeicherten Prozedur

Um eine neue in SQL gespeicherte Prozedur hinzuzufügen, klicken Sie auf Ihr Projekt, wählen **Hinzufügen > Neues Element...**, dann **Gespeicherte SQL-Prozedur mit R** aus der Liste der Vorlagen, geben Sie der Datei einen Namen (in diesem Beispiel `StoredProcedure.R`), und klicken Sie auf **OK**.
 
RTVS erstellt drei Dateien für die gespeicherte Prozedur, eine `.R`-Datei für Ihren R-Code, eine `.Query.sql`-Datei für den SQL-Code und eine `.Template.sql`-Datei, die beide vereint. Die letzten beiden erscheinen im Projektmappen-Explorer als untergeordnete Dateien der `.R`-Datei:

![Erweiterte Projektmappen-Explorer-Ansicht der gespeicherten SQL-Prozedur mit R](media/sql-solution-explorer-expanded.png)

`StoredProcedure.R` (in diesem Beispiel) ist der Ort, an dem Sie Ihren R-Code schreiben. Der Standardinhalt ist der folgende:

```R
# @InputDataSet: input data frame, result of SQL query execution
# @OutputDataSet: data frame to pass back to SQL

# Test code
# library(RODBC)
# channel <- odbcDriverConnect(dbConnection)
# InputDataSet <- sqlQuery(channel, )
# odbcClose(channel)

OutputDataSet <- InputDataSet
```

Um es einfacher auszudrücken: Der Code erhält einen R-Datenrahmen mit dem Namen `InputDataSet` und gibt dessen Ergebnisse in `OutputDataSet` zurück. Der Vorlagencode kopiert dabei lediglich die Eingabe in die Ausgabe.

> [!Note]
> Die Namen dieser Datenrahmen werden durch die Parameter `@input_data_1_name` und `@output_data_1_name` im Aufruf der im `sp_execute_external_script`-System gespeicherten Prozedur gesteuert. Weitere Informationen zum Entwurf dieser Aufrufkonvention und einige Beispiele zum Gebrauch finden Sie unter [sp_execute_external_script (Transact-SQL)](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql).

Der andere generierte Code in den Kommentaren ist ein kleines Testskript, das das [RODBC-Paket](https://cran.r-project.org/web/packages/RODBC/index.html) zur Übermittlung einer SQL-Anweisung an SQL Server verwendet, sie ausführt und das Resultset als R-Datenrahmen abruft. Sie können die Auskommentierung dieses Testcodes aufheben, um Ihren R-Code interaktiv für das festgelegte Resultset zu schreiben, das Sie von SQL Server erhalten.

`StoredProcedure.Query.sql` ist der Ort, an dem Sie die SQL-Abfrage schreiben und testen, die die Daten für `InputDataSet` generiert. Da es sich um eine `.sql`-Datei handelt, stehen Ihnen alle Funktionen des Transact-SQL-Editors zur Verfügung.

Sobald Sie mit Ihrem SQL-Code zufrieden sind, können Sie ihn leicht mit Ihrem R-Code in `StoredProcedure.R` integrieren, indem Sie einfach die `.sql`-Datei in den offenen Editor für die `.R`-Datei ziehen. Wie unten dargestellt, wurde `StoredProcedure.Query.sql` zur Stelle nach dem Komma in `sqlQuery(channel, )` gezogen:

![Lesen einer SQL-Datei in eine R-Zeichenfolgenvariable](media/sql-reference-sql-file-from-r.png)

Wie Sie sehen können, generiert dieser einfache Schritt automatisch R-Code, um die `.sql`-Datei zu öffnen, deren Inhalt in eine Zeichenfolge zu lesen und sie an das RODBC-Paket zu übergeben, um sie an SQL Server zu senden.

Wenn dies geschehen ist, können Sie nun interaktiv R-Code schreiben, der den `InputDataSet`-Datenrahmen wie gewünscht verändert. Beachten Sie, dass Sie nur R-Code im Editor auswählen und ihn an das [interaktive Fenster](interactive-repl.md) senden können, indem Sie STRG+EINGABE drücken.

`StoredProcedure.Template.sql` enthält schlussendlich die Vorlage zum Generieren Ihrer gespeicherten SQL-Prozedur:

```sql
CREATE PROCEDURE [StoredProcedure]
AS
BEGIN
EXEC sp_execute_external_script @language = N'R'
    , @script = N'_RCODE_'
    , @input_data_1 = N'_INPUT_QUERY_'
--- Edit this line to handle the output data frame.
    WITH RESULT SETS (([MYNEWCOLUMN] NVARCHAR(max)));
END;
```

- Der Platzhalter `_RCODE_` wird durch die Inhalte von `StoredProcedure.R` ersetzt.
- Der Platzhalter `_INPUT_QUERY_` wird durch die Inhalte von `StoredProcedure.Query.sql` ersetzt.
- Sie müssen das Schema des von der gespeicherten Prozedur zurückgegebenen Resultsets beschreiben, indem Sie die `WITH RESULT SETS`-Klausel bearbeiten. Identifizieren Sie insbesondere die Spalten aus dem `OutputDataSet`-Datenrahmen, die Sie an den Aufrufer der gespeicherten Prozedur zurückgeben möchten. 

Beispielsweise für die folgende Abfrage:

```sql
SELECT TOP 100 medallion, hack_license FROM nyctaxi_sample
```

Sie verwenden die folgende `WITH RESULT SETS`-Klausel, um die Datentypen der Rückgabewerte anzugeben:

```sql
WITH RESULT SETS ((medallion NVARCHAR(max), hack_license NVARCHAR(max)));
```

### <a name="publish-a-sql-stored-procedure"></a>Veröffentlichen einer in SQL gespeicherten Prozedur

1. Wählen Sie den Menübefehl **R Tools > Daten > Mit Optionen veröffentlichen...**.
1. Ändern Sie im Dialogfeld, das erscheint, **Veröffentlichen an:** in **Datenbank**, geben Sie das Ziel an, wählen Sie **Veröffentlichen** aus, und RTVS erstellt die gespeicherte Prozedur und veröffentlicht sie:

    ![Dialogfeld „Gespeicherte Prozeduren veröffentlichen“](media/sql-publish-with-options.png)

1. Um alle gespeicherten Prozeduren in einem Projekt zu veröffentlichen, können Sie auch den Befehl **R Tools > Daten > Gespeicherte Prozeduren veröffentlichen** verwenden, der auch verfügbar ist, wenn Sie mit der rechten Maustaste auf das Projekt im Projektmappen-Explorer klicken.

> [!Tip]
> Wenn Sie den SQL Server-Objekt-Explorer in Visual Studio geöffnet haben, sehen Sie auch Ihre veröffentlichte gespeicherte Prozedur im Ordner **Programmierbarkeit > Gespeicherte Prozeduren** Ihrer Datenbank. Sie können sie auch vom Objekt-Explorer aus ausführen, indem Sie rechtsklicken, und **Execute Procedure** (Prozedur ausführen) auswählen oder sie interaktiv aus einem `.sql`-Abfragefenster aufrufen.


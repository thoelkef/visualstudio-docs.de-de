---
title: Erstellen und Konfigurieren eines TableAdapters
ms.date: 09/01/2017
ms.topic: conceptual
helpviewer_keywords:
- table adapters, creating
- creating TableAdapters
- data [Visual Studio], creating data components
- data [Visual Studio], TableAdapters
- data [Visual Studio], creating table adapters
ms.assetid: 08630d69-0d6c-4e8f-b42d-2922f45f8415
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: a363c9964b88196e31f5ba05a4244fabdf00f90f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53966874"
---
# <a name="create-and-configure-tableadapters"></a>Erstellen und Konfigurieren eines TableAdapters

TableAdapters ermöglichen die Kommunikation zwischen der Anwendung und einer Datenbank. Sie verbinden, in der Datenbank, die Abfragen ausführen oder die gespeicherten Prozeduren und entweder einen neuen Daten zurückgeben Tabellen- oder geben Sie eine vorhandene <xref:System.Data.DataTable> mit den zurückgegebenen Daten. TableAdapter-Steuerelemente können auch aktualisierte Daten aus Ihrer Anwendung an die Datenbank senden.

TableAdapters werden für Sie erstellt, wenn Sie eine der folgenden Aktionen ausführen:

- Ziehen Sie Datenbankobjekte aus **Server-Explorer** in die **Dataset-Designer**.

- Führen Sie den Konfigurations-Assistenten, und wählen Sie entweder die **Datenbank** oder **Webdienst** Datenquellentyp.

   ![Datenquellen-Assistenten in Visual Studio-Konfiguration](media/data-source-configuration-wizard.png)

Sie können auch einen neuen TableAdapter zu erstellen und konfigurieren Sie es mit einer Datenquelle durch Ziehen von einem TableAdapter unter Verwendung der **Toolbox** auf einen leeren Bereich in der **Dataset-Designer** Oberfläche.

Eine Einführung in TableAdapters, finden Sie unter [Füllen von Datasets mit TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="use-the-tableadapter-configuration-wizard"></a>Verwenden Sie den TableAdapter-Konfigurations-Assistenten

Führen Sie die **TableAdapter-Konfigurations-Assistenten** erstellen oder Bearbeiten von TableAdapters und deren zugeordnete Datentabellen. Sie können einen vorhandenen TableAdapter konfigurieren, indem Sie mit der rechten Maustaste auf die sie in der **Dataset-Designer**.

![Raddata Tabelle Konfigurations-Assistenten](../data-tools/media/raddata-table-adapter-configuration-wizard.png)

Wenn Sie einen neuen TableAdapter aus der Toolbox ziehen, wenn die **Dataset-Designer** befindet sich in zu konzentrieren, der Assistent wird gestartet und Anweisungen, die Sie angeben, welche Daten den TableAdapter Datenquelle müssen mit dem. Klicken Sie auf der nächsten Seite werden vom Assistenten gefragt, welche Art von Befehlen für die Kommunikation mit der Datenbank: SQL-Anweisungen oder gespeicherten Prozeduren verwendet werden soll. (Sie keine dieser angezeigt, wenn Sie einen TableAdapter konfigurieren, die bereits mit einer Datenquelle zugeordnet ist.)

- Sie haben die Möglichkeit, eine neue gespeicherte Prozedur in der zugrunde liegenden Datenbank zu erstellen, wenn Sie die richtigen Berechtigungen für die Datenbank verfügen. Wenn Sie diese Berechtigungen nicht haben, nicht dadurch eine Option.

- Sie können auch vorhandene gespeicherte Prozeduren für die Ausführung der **wählen**, **einfügen**, **UPDATE**, und **löschen** Befehle das TableAdapter. Die gespeicherte Prozedur, die zugewiesen ist, die **Update** Befehl ein, z. B. wird ausgeführt, wenn die `TableAdapter.Update()` Methode wird aufgerufen.

Ordnen Sie die Parameter der ausgewählten gespeicherten Prozedur den entsprechenden Spalten in der Datentabelle zu. Wenn die gespeicherte Prozedur einen Parameter, die mit dem Namen akzeptiert, z. B. `@CompanyName` , die zum Übergeben der `CompanyName` Spaltensatz in der Tabelle der **Quellspalte** von der `@CompanyName` Parameter, um `CompanyName`.

> [!NOTE]
> Die gespeicherte Prozedur, die die SELECT-Befehl zugewiesen ist, wird durch Aufrufen der Methode des TableAdapter mit den Bezeichnungen im nächsten Schritt des Assistenten ausgeführt. Die Standardmethode ist `Fill`, sodass der Code, der in der Regel, zum Ausführen der SELECT-Prozedur verwendet wird ist `TableAdapter.Fill(tableName)`. Wenn Sie den Standardnamen aus ändern `Fill`, ersetzen Sie `Fill` mit dem Namen zuweisen, und Ersetzen Sie "TableAdapter" durch den tatsächlichen Namen des TableAdapter (z. B. `CustomersTableAdapter`).

- Auswählen der **Methoden erstellen, um Updates direkt an die Datenbank senden** Option entspricht dem Festlegen der `GenerateDBDirectMethods` Eigenschaft auf "true". Die Option ist nicht verfügbar, wenn die ursprüngliche SQL-Anweisung nicht genügend Informationen bereitstellt oder die Abfrage keine aktualisierbare Abfrage darstellt. Diese Situation kann auftreten, z. B. **JOIN** Abfragen und Abfragen, die einen einzelnen (skalaren) Wert zurückgeben.

Die **erweiterte Optionen** im Assistenten können Sie:

- Generieren von INSERT-, Update- und DELETE-Anweisungen, die basierend auf der SELECT-Anweisung, die auf definiert ist die **SQL-Anweisungen** Seite
- Optimistische Nebenläufigkeit verwenden
- Gibt an, ob die Datentabelle nach EINFÜGE-zu aktualisieren und UPDATE-Anweisungen werden ausgeführt.

## <a name="configure-a-tableadapters-fill-method"></a>Konfigurieren TableAdapters-Fill-Methode

In einigen Fällen empfiehlt es sich um das Schema der Tabelle mit dem TableAdapter zu ändern. Zu diesem Zweck ändern Sie die TableAdapter primären `Fill` Methode. TableAdapter-Erstellung mit der primären `Fill` -Methode, die das Schema der zugeordneten Datentabelle definiert. Die primäre `Fill` Methode basiert auf der Abfrage oder gespeicherte Prozedur, die Sie eingegeben haben, wenn Sie den TableAdapter ursprünglich konfiguriert haben. Es ist die erste (oberste)-Methode in der Datentabelle im DataSet-Designer.

![TableAdapter mit mehreren Abfragen](../data-tools/media/tableadapter.gif)

Alle Änderungen, die Sie dem TableAdapter vornehmen Hauptthread `Fill` Methode werden in das Schema der zugeordneten Datentabelle wiedergegeben. Z. B. das Entfernen einer Spalte aus der Abfrage auf dem hauptblatt `Fill` Methode wird auch die Spalte aus der zugeordneten Datentabelle entfernt. Außerdem entfernen Sie die Spalte aus dem Hauptknoten `Fill` Methode entfernt die Spalte aus etwaigen zusätzlichen Abfragen für diesen TableAdapter.

Sie können den Konfigurations-Assistenten für TableAdapter-Abfrage verwenden, erstellen und Bearbeiten zusätzliche Abfragen für den TableAdapter. Diese zusätzlichen Abfragen müssen das Tabellenschema entsprechen, wenn sie einen skalaren Wert zurückgeben.  Jede zusätzliche Abfrage hat einen Namen, den Sie angeben.

Der folgende Beispiel zeigt, wie Sie eine weitere Abfrage, die mit dem Namen aufrufen `FillByCity`:

`CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, "Seattle")`

### <a name="to-start-the-tableadapter-query-configuration-wizard-with-a-new-query"></a>Starten Sie den Konfigurations-Assistenten für TableAdapter-Abfrage mit einer neuen Abfrage

1.  Öffnen Sie das Dataset im **DataSet-Designer**.

2.  Wenn Sie eine neue Abfrage erstellen, ziehen Sie eine **Abfrage** -Objekt aus der **DataSet** auf der Registerkarte die **Toolbox** auf eine <xref:System.Data.DataTable>, oder wählen Sie **AbfrageHinzufügen**im Kontextmenü des TableAdapter. Sie können auch ziehen eine **Abfrage** Objekt auf einen leeren Bereich, der die **Dataset-Designer**, erstellt einen TableAdapter ohne einen zugehörigen <xref:System.Data.DataTable>. Diese Abfragen können nur zur Update-, INSERT- oder einzelnen (skalaren) Wert zurück, die oder Befehle für die Datenbank zu löschen.

3.  Auf der **wählen Sie Ihre Datenverbindung** Bildschirm Wählen oder erstellen Sie die Verbindung, die die Abfrage verwendet.

    > [!NOTE]
    > Dieser Bildschirm wird nur angezeigt, wenn der Designer nicht die richtige zu verwendende Verbindung bestimmen kann, oder wenn keine Verbindungen verfügbar sind.

4.  Auf der **wählen Sie einen Befehlstyp aus** aus der folgenden Methoden zum Abrufen von Daten aus der Datenbank wählen:

    - **Verwenden von SQL-Anweisungen** ermöglicht es Ihnen, geben Sie eine SQL-Anweisung, um die Daten aus der Datenbank auszuwählen.

    - **Erstellen Sie neue gespeicherte Prozedur** können Sie den Assistenten erstellen Sie eine neue gespeicherte Prozedur (in der Datenbank) auf Grundlage der angegebenen SELECT-Anweisung.

    - **Vorhandene gespeicherte Prozeduren verwenden** können Sie eine vorhandene gespeicherte Prozedur ausführen, bei der Ausführung der Abfrage.

### <a name="to-start-the-tableadapter-query-configuration-wizard-on-an-existing-query"></a>Zum Starten des TableAdapter-Abfrage-Konfigurations-Assistenten auf eine vorhandene Abfrage

- Wenn Sie eine vorhandene TableAdapter-Abfrage bearbeiten, mit der rechten Maustaste in der Abfrage aus, und wählen Sie dann **konfigurieren** aus dem Kontextmenü.

    > [!NOTE]
    > Mit der rechten Maustaste in der Hauptabfrage des TableAdapter wird den TableAdapter und <xref:System.Data.DataTable> Schema. Mit der rechten Maustaste auf einen TableAdapter einer weiteren Abfrage, wird jedoch nur die ausgewählte Abfrage konfiguriert. Die **TableAdapter-Konfigurations-Assistenten** wird die TableAdapter-Definition, während die **Konfigurations-Assistenten für TableAdapter-Abfragen** wird nur die ausgewählte Abfrage.

### <a name="to-add-a-global-query-to-a-tableadapter"></a>Zum Hinzufügen einer globalen Abfrage einem TableAdapter

- Globale Abfragen sind SQL-Abfragen, die entweder einen einzelnen (skalaren) Wert oder keinen Wert zurückgeben. Globale Funktionen führen in der Regel Datenbankvorgänge, z. B. einfügungen, Updates und löschungen. Sie aggregiert auch Informationen, z. B. die Anzahl der Kunden in einer Tabelle oder die Gesamtbetrag der Gebühren für alle Elemente in einer bestimmten Reihenfolge.

     Hinzufügen von globalen Abfragen durch Ziehen einer **Abfrage** -Objekt aus der **DataSet** Registerkarte die **Toolbox** auf einen leeren Bereich des der **Dataset-Designer**.

- Geben Sie eine Abfrage, die die gewünschte Aufgabe, z. B. ausführt `SELECT COUNT(*) AS CustomerCount FROM Customers`.

    > [!NOTE]
    > Sie ziehen ein **Abfrage** Objekt direkt auf die **Dataset-Designer** erstellt eine Methode, die nur einen Skalarwert (Einzelwert) zurückgibt. Während die Abfrage oder gespeicherte Prozedur, die Sie auswählen, mehr als einen einzelnen Wert zurückgeben kann, gibt die Methode, die vom Assistenten erstellt wird nur einen einzelnen Wert zurück. Die Abfrage kann z. B. die erste Spalte der ersten Zeile der zurückgegebenen Daten zurückgeben.

## <a name="see-also"></a>Siehe auch

- [Füllen von Datasets mit TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)
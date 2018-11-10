---
title: Erstellen von Filterzeichenfolgen für den Tabellen-Designer | Microsoft-Dokumentation
description: Erstellen von Filterzeichenfolgen für den Tabellen-designer
author: ghogen
manager: douge
assetId: a1a10ea1-687a-4ee1-a952-6b24c2fe1a22
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/18/2016
ms.author: ghogen
ms.openlocfilehash: ff8c3dd927e81b9e131242a9a6631a8297046a6e
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "51001966"
---
# <a name="constructing-filter-strings-for-the-table-designer"></a>Erstellen von Filterzeichenfolgen für den Tabellen-Designer
## <a name="overview"></a>Übersicht
Zum Filtern von Daten in einer Azure-Tabelle, die in der Visual Studio angezeigt wird **Tabellen-Designer**, Sie muss eine Filterzeichenfolge erstellt, und geben Sie ihn in das Feld "Filter". Die Syntax der Filterzeichenfolge wird von WCF Data Services definiert und ist vergleichbar mit einer SQL-WHERE-Klausel, jedoch für den Tabellendienst über eine HTTP-Anforderung gesendet wird. Die **Tabellen-Designer** nimmt die erforderliche Codierung für Sie daher zum Filtern nach einem gewünschten Eigenschaftswert nur den Eigenschaftennamen, Vergleichsoperator, Kriterienwert und optional, boolescher Wert eingeben müssen Operator im Filterfeld. Sie müssen nicht die Option "$filter" enthalten, als würden Sie beim Erstellen einer URL zur Tabellenabfrage über die [Storage Services – REST-API-Referenz](http://go.microsoft.com/fwlink/p/?LinkId=400447).

Die WCF Data Services basieren auf der [Open Data Protocol](http://go.microsoft.com/fwlink/p/?LinkId=214805) (OData). Ausführliche Informationen über die filtersystemabfrage-Option (**$filter**), finden Sie unter den [Spezifikation zu OData URI Conventions](http://go.microsoft.com/fwlink/p/?LinkId=214806).

## <a name="comparison-operators"></a>Vergleichsoperatoren
Die folgenden logischen Operatoren werden für alle Eigenschaftentypen unterstützt:

| Logischer Operator | Beschreibung | Beispiel für Filter-Zeichenfolge |
| --- | --- | --- |
| eq |Gleich |Ort Eq 'Redmond' |
| gt |Größer als |Preis Gt 20 |
| ge |Größer oder gleich |Preis ge 10 |
| lt |Kleiner als |Preis Lt 20 |
| LE |Kleiner oder gleich |Preis le 100 |
| ne |Ungleich |Ort Ne 'London' |
| und |And |Preis le 200 and Preis Gt 3,5 |
| oder |Or |Preis le 3,5 or Preis Gt 200 |
| not |Not |nicht isAvailable |

Wenn Sie eine Filterzeichenfolge erstellen, sind die folgenden Regeln wichtig:

* Verwenden Sie die logischen Operatoren, um eine Eigenschaft auf einen Wert zu vergleichen. Beachten Sie, dass es nicht möglich, eine Eigenschaft mit einem dynamischen Wert vergleichen. eine Seite des Ausdrucks muss es sich um eine Konstante sein.
* Alle Teile der Filterzeichenfolge beachtet werden.
* Der Konstante Wert muss den gleichen Datentyp wie die Eigenschaft in der Reihenfolge für den Filter gültige Ergebnisse zurückgegeben werden. Weitere Informationen zu unterstützten Eigenschaftentypen finden Sie unter [Verständnis der Tabellendienst-Datenmodell](http://go.microsoft.com/fwlink/p/?LinkId=400448).

## <a name="filtering-on-string-properties"></a>Filtern nach Zeichenfolgeneigenschaften
Wenn Sie nach Zeichenfolgeneigenschaften filtern, schließen Sie die Zeichenfolgenkonstante in einfache Anführungszeichen ein.

Das folgende Beispiel filtert nach dem **PartitionKey** und **RowKey** Eigenschaften; zusätzliche nicht schlüsselbezogene Eigenschaften können auch der Filterzeichenfolge hinzugefügt werden:

    PartitionKey eq 'Partition1' and RowKey eq '00001'

Sie können jeden Filterausdruck in Klammern einschließen, obwohl es nicht erforderlich ist:

    (PartitionKey eq 'Partition1') and (RowKey eq '00001')

Beachten Sie, dass der Tabellendienst keine Platzhalterabfragen, und sie nicht in den Tabellen-Designer entweder unterstützt werden ein. Allerdings können Sie mithilfe von Vergleichsoperatoren für das gewünschte Präfix präfixabgleich ausführen. Im folgende Beispiel werden Entitäten mit einer LastName-Eigenschaft ab, mit dem Buchstaben "A" zurückgegeben:

    LastName ge 'A' and LastName lt 'B'

## <a name="filtering-on-numeric-properties"></a>Filtern nach numerischen Eigenschaften
Um auf eine ganze Zahl oder Gleitkommazahl zu filtern, geben Sie die Zahl ohne Anführungszeichen ein.

In diesem Beispiel gibt alle Entitäten mit einer Age-Eigenschaft, deren Wert größer als 30 ist:

    Age gt 30

In diesem Beispiel gibt alle Entitäten mit einer AmountDue-Eigenschaft, deren Wert kleiner als oder gleich 100,25 ist:

    AmountDue le 100.25

## <a name="filtering-on-boolean-properties"></a>Filtern nach booleschen Eigenschaften
Um nach einem booleschen Wert zu filtern, geben **"true"** oder **"false"** ohne Anführungszeichen ein.

Im folgende Beispiel werden alle Entitäten zurückgegeben, in denen die IsActive-Eigenschaft festgelegt ist **"true"**:

    IsActive eq true

Sie können auch diesen Filterausdruck ohne den logischen Operator schreiben. Im folgenden Beispiel der Tabellendienst werden auch alle gibt Entitäten zurück, in denen IsActive **"true"**:

    IsActive

Um alle Entitäten zurückgegeben, in denen IsActive "false", können Sie nicht Operator:

    not IsActive

## <a name="filtering-on-datetime-properties"></a>Filtern nach DateTime-Eigenschaften
Um auf einen DateTime-Wert zu filtern, geben die **"DateTime"** Schlüsselwort, gefolgt von den Datum-/uhrzeitkonstante in einfachen Anführungszeichen. Die Datum-/uhrzeitkonstante muss im kombiniertem UTC-Format vorliegen, wie in beschrieben [Formatieren von DateTime-Eigenschaftswerten](http://go.microsoft.com/fwlink/p/?LinkId=400449).

Das folgende Beispiel gibt Entitäten zurück, wenn die CustomerSince-Eigenschaft, die gleich dem 10. Juli 2008 ist:

    CustomerSince eq datetime'2008-07-10T00:00:00Z'

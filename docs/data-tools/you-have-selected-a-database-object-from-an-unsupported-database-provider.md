---
title: Sie haben ein Datenbankobjekt von einem nicht unterstützten Datenbankanbieter ausgewählt.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 0646f153149d887ce87f2688d9c28b3da502ba1c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>Sie haben ein Datenbankobjekt von einem nicht unterstützten Datenbankanbieter ausgewählt.

Der O/R-Designer unterstützt nur die .NET Framework-Datenanbieter für SQL Server (<xref:System.Data.SqlClient>). Obwohl Sie klicken können, **OK** und zum Arbeiten mit Objekten von nicht unterstützten Datenbankanbietern fortsetzen, kann unerwartetes Verhalten zur Laufzeit auftreten.

> [!NOTE]
> Es werden nur Datenverbindungen unterstützt, die den .NET Framework-Datenanbieter für SQL Server verwenden.

## <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

- Klicken Sie auf **OK**.

   Sie können weiterhin, Entwerfen der Entitätsklassen, die der Verbindung zugeordnet sind, die nicht unterstützten Datenbankanbieter verwendet. Es kann unerwartetes Verhalten auftreten, wenn nicht unterstützte Datenbankanbieter verwendet werden.

    - oder - 

- Klicken Sie auf **"Abbrechen"**.

   Die Aktion wird beendet. Erstellen oder verwenden Sie eine Datenverbindung, die .NET Framework-Anbieter für SQL Server verwendet.

## <a name="see-also"></a>Siehe auch

- [O/R-Designer-Meldungen](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL-tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
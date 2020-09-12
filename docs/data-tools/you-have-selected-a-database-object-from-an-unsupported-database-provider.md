---
title: Objekt von nicht unterstützter Anbieter
description: Sie haben ein Datenbankobjekt von einem nicht unterstützten Datenbankanbieter ausgewählt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 84841c5e0759618430f9c2e4f0146cbc2d21fae9
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036716"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>Sie haben ein Datenbankobjekt von einem nicht unterstützten Datenbankanbieter ausgewählt.

Der **O/R-Designer** unterstützt nur die .NET Framework Datenanbieter für SQL Server ( <xref:System.Data.SqlClient> ). Obwohl Sie auf **OK** klicken und die Arbeit an Objekten von nicht unterstützten Datenbankanbietern fortsetzen können, kann zur Laufzeit unerwartetes Verhalten auftreten.

> [!NOTE]
> Es werden nur Datenverbindungen unterstützt, die den .NET Framework-Datenanbieter für SQL Server verwenden.

## <a name="options"></a>Optionen

- Klicken Sie auf **OK**, um mit dem Entwerfen der Entitätsklassen fortzufahren, die der Verbindung mit dem nicht unterstützten Datenbankanbieter zugeordnet sind. Es kann unerwartetes Verhalten auftreten, wenn nicht unterstützte Datenbankanbieter verwendet werden.

- Klicken Sie auf **Abbrechen** , um die Aktion zu beenden. Erstellen oder verwenden Sie eine andere Datenverbindung, die den .NET Framework Anbieter für SQL Server verwendet.

## <a name="see-also"></a>Weitere Informationen

- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)

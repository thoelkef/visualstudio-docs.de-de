---
title: "Sie haben ein Datenbankobjekt von einem nicht unterstützten Datenbankanbieter ausgewählt | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 85a8e5883a8d78297336016ac295f9b5d76ce337
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>Sie haben ein Datenbankobjekt von einem nicht unterstützten Datenbankanbieter ausgewählt.
Der O/R-Designer unterstützt nur die .NET Framework-Datenanbieter für SQL Server (<xref:System.Data.SqlClient>). Obwohl Sie klicken können, **OK** und zum Arbeiten mit Objekten von nicht unterstützten Datenbankanbietern fortsetzen, kann unerwartetes Verhalten zur Laufzeit auftreten.  
  
> [!NOTE]
>  Es werden nur Datenverbindungen unterstützt, die den .NET Framework-Datenanbieter für SQL Server verwenden.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Klicken Sie auf **OK**.

   Sie können weiterhin, Entwerfen der Entitätsklassen, die der Verbindung zugeordnet sind, die nicht unterstützten Datenbankanbieter verwendet. Es kann unerwartetes Verhalten auftreten, wenn nicht unterstützte Datenbankanbieter verwendet werden.  
  
     - oder -   
  
- Klicken Sie auf **"Abbrechen"**.

   Die Aktion wird beendet. Erstellen oder verwenden Sie eine Datenverbindung, die .NET Framework-Anbieter für SQL Server verwendet.  
  
## <a name="see-also"></a>Siehe auch
[O/R-Designer-Meldungen](../data-tools/o-r-designer-messages.md)  
[LINQ to SQL-tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
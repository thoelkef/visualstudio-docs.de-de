---
title: Sie haben ein Datenbankobjekt von einem nicht unterstützten Datenbankanbieter ausgewählt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1027be99525081ad4df959908b856727e9ebe399
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49211697"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>Sie haben ein Datenbankobjekt von einem nicht unterstützten Datenbankanbieter ausgewählt.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]) unterstützt nur die .NET Framework-Datenanbieter für SQL Server (<xref:System.Data.SqlClient>). Obwohl Sie klicken können, **OK** und zum Arbeiten mit Objekten von nicht unterstützten Datenbankanbietern fortsetzen, treten unter Umständen unerwartetes Verhalten zur Laufzeit.  
  
> [!NOTE]
>  Es werden nur Datenverbindungen unterstützt, die den .NET Framework-Datenanbieter für SQL Server verwenden.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Klicken Sie auf **OK** weiterhin Entwerfen der Entitätsklassen, die der Verbindung zugeordnet werden soll, die den nicht unterstützten Datenbankanbieter verwendet. Es kann unerwartetes Verhalten auftreten, wenn nicht unterstützte Datenbankanbieter verwendet werden.  
  
     - oder -   
  
-   Klicken Sie auf **Abbrechen**.  
  
     Die Aktion wird beendet. Erstellen oder verwenden Sie eine Datenverbindung, die .NET Framework-Anbieter für SQL Server verwendet.  
  
## <a name="see-also"></a>Siehe auch  
 [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [.NET Framework-Datenanbieter](http://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131)   
 [Herstellen von Datenverbindungen in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)


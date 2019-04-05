---
title: 'Vorgehensweise: Aktivieren/Deaktivieren der Pluralisierung (O / R Designer) | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9ff3f206f57a544053498def16318e0ed65b64ab
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58946814"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Vorgehensweise: Aktivieren/Deaktivieren der Pluralisierung (O/R-Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Standardmäßig wird beim Ziehen Datenbankobjekte, deren Namen auf s oder ies enden, aus **Server-Explorer**/**Datenbank-Explorer** auf die [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md), die Namen der generierten Entitätsklassen sind von der plural-in die Singularform geändert. Damit soll verdeutlicht werden, dass die instanziierte Entitätsklasse einem einzigen Datensatz zugeordnet ist. Wird dem [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] beispielsweise die Tabelle Customers hinzugefügt, erhält die Entitätsklasse den Namen Customer, da die Klasse die Daten eines einzigen Kunden enthält.  
  
> [!NOTE]
>  Pluralisierung ist standardmäßig nur in der englischsprachigen Version von Visual Studio aktiviert.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-turn-pluralization-on-and-off"></a>So schalten Sie Pluralisierung ein und aus  
  
1.  Klicken Sie im Menü **Extras** auf **Optionen**.  
  
2.  Erweitern Sie im Dialogfeld **Optionen** den Knoten **Datenbanktools**.  
  
> [!NOTE]
>  Wählen Sie **Alle Einstellungen anzeigen** aus, wenn der Knoten **Datenbanktools** nicht angezeigt wird.  
  
1.  Klicken Sie auf **O/R-Designer**.  
  
2.  Legen Sie **Pluralisierung von Namen** zu **aktiviert** = **"false"** Festlegen der [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] , damit es Klassennamen nicht geändert wird.  
  
3.  Legen Sie **Pluralisierung von Namen** zu **aktiviert** = **"true"** anzuwendende Pluralisierungsregeln auf die Klassennamen von Objekten, die hinzugefügt, die [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
## <a name="see-also"></a>Siehe auch  
 [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)

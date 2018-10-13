---
title: 'Gewusst wie: Aktivieren/Deaktivieren der Pluralisierung (O / R Designer) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1f4491f25a861b8556ae5018e526349d6a17187a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49279109"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Gewusst wie: Aktivieren/Deaktivieren der Pluralisierung (O/R Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Standardmäßig wird beim Ziehen Datenbankobjekte, deren Namen auf s oder ies enden, aus **Server-Explorer**/**Datenbank-Explorer** auf die [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md), die Namen der generierten Entitätsklassen sind von der plural-in die Singularform geändert. Damit soll verdeutlicht werden, dass die instanziierte Entitätsklasse einem einzigen Datensatz zugeordnet ist. Wird dem [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] beispielsweise die Tabelle Customers hinzugefügt, erhält die Entitätsklasse den Namen Customer, da die Klasse die Daten eines einzigen Kunden enthält.  
  
> [!NOTE]
>  Pluralisierung ist standardmäßig nur in der englischsprachigen Version von Visual Studio aktiviert.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-turn-pluralization-on-and-off"></a>So schalten Sie Pluralisierung ein und aus  
  
1.  Klicken Sie im Menü **Extras** auf **Optionen**.  
  
2.  In der **Optionen** Dialogfeld erweitern Sie **Datenbanktools**.  
  
> [!NOTE]
>  Wählen Sie **alle Einstellungen anzeigen** Wenn die **Datenbanktools** Knoten ist nicht sichtbar.  
  
1.  Klicken Sie auf **O/R-Designer**.  
  
2.  Legen Sie **Pluralisierung von Namen** zu **aktiviert** = **"false"** Festlegen der [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] , damit es Klassennamen nicht geändert wird.  
  
3.  Legen Sie **Pluralisierung von Namen** zu **aktiviert** = **"true"** anzuwendende Pluralisierungsregeln auf die Klassennamen von Objekten, die hinzugefügt, die [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
## <a name="see-also"></a>Siehe auch  
 [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)


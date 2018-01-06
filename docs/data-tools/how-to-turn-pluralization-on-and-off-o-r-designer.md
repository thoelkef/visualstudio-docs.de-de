---
title: 'Vorgehensweise: Aktivieren Sie Pluralisierung ein, und deaktivieren (O-R-Designer) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: a78f38d4b02311a164e0858744b70fbc5fb0ddaa
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Vorgehensweise: Aktivieren Sie Pluralisierung ein, und deaktivieren (O/R-Designer)
Standardmäßig, wenn Sie Datenbankobjekte ziehen, deren Namen Endziffern s oder Datenreihen aus **Server-Explorer**/**Datenbank-Explorer** auf die [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md), die Namen der generierten Entitätsklassen von plural in Singular geändert werden. Damit soll verdeutlicht werden, dass die instanziierte Entitätsklasse einem einzigen Datensatz zugeordnet ist. Wird dem [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] beispielsweise die Tabelle Customers hinzugefügt, erhält die Entitätsklasse den Namen Customer, da die Klasse die Daten eines einzigen Kunden enthält.  
  
> [!NOTE]
>  Pluralisierung ist standardmäßig nur in der englischsprachigen Version von Visual Studio aktiviert.  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### <a name="to-turn-pluralization-on-and-off"></a>So schalten Sie Pluralisierung ein und aus  
  
1.  Klicken Sie im Menü **Extras** auf **Optionen**.  
  
2.  In der **Optionen** Dialogfeld erweitern Sie **Datenbanktools**.  
  
    > [!NOTE]
    >  Wählen Sie **alle Einstellungen anzeigen** Wenn die **Datenbanktools** Knoten ist nicht sichtbar.  
  
3.  Klicken Sie auf **O/R-Designer**.  
  
4.  Festlegen **Pluralisierung von Namen** auf **aktiviert** = **"false"** Festlegen der [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] , damit es Klassennamen nicht geändert wird.  
  
5.  Legen Sie **Pluralisierung von Namen** auf **aktiviert** = **"true"** anzuwendende Pluralisierungsregeln auf die Klassennamen von Objekten hinzugefügt der [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
## <a name="see-also"></a>Siehe auch  
[LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
[LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)   
[Zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
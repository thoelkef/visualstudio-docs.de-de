---
title: Diese Methode ist die dahinter liegende Methode für die folgenden standardmäßigen INSERT-, Update- oder Delete-Methoden bezogene | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 89421c61e34bf4ed98bcb8c2c8bd6ef93e1dae0b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>Diese verknüpfte Methode ist die Sicherungsmethode für die folgenden standardmäßigen Methoden zum Einfügen, Aktualisieren oder Löschen.
Diese verknüpfte Methode ist die dahinter liegende Methode für die folgenden standardmäßigen Insert-, Update- und Delete-Methoden. Wenn sie gelöscht wird, werden die entsprechenden Methoden ebenfalls gelöscht. Möchten Sie den Vorgang fortsetzen?  
  
 Die ausgewählte `DataContext`-Methode wird derzeit als eine der Insert-, Update- oder Delete-Methoden für eine der Entitätsklassen im O/R-Designer verwendet. Durch das Löschen der ausgewählten Methode greift die Entitätsklasse, die diese Methode verwendete, auf das Standardlaufzeitverhalten zurück, um die Aktionen Einfügen, Aktualisieren oder Löschen bei einem Update auszuführen.  
  
### <a name="to-delete-the-selected-method-causing-the-entity-class-to-use-runtime-updates"></a>So löschen Sie die ausgewählte Methode und bewirken, dass die Entitätsklasse Laufzeitupdates verwendet  
  
-   Klicken Sie auf **Ja**.  
  
     Die ausgewählte Methode wird gelöscht und alle Klassen, die diese Methode zum Überschreiben des Updateverhaltens verwendet hatten, greifen wieder auf das standardmäßige LINQ to SQL-Laufzeitverhalten zurück.  
  
### <a name="to-close-the-message-box-leaving-the-selected-method-unchanged"></a>So schließen Sie das Meldungsfeld, ohne die ausgewählte Methode zu ändern  
  
-   Click **No**.  
  
     Das Meldungsfeld wird geschlossen, und es werden keine Änderungen vorgenommen.  
  
## <a name="see-also"></a>Siehe auch
[O/R-Designer-Meldungen](../data-tools/o-r-designer-messages.md)  
[LINQ to SQL-tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
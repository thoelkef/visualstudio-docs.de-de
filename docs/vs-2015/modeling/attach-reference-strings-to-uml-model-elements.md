---
title: Anfügen von Referenzzeichenfolgen an UML-Modellelemente | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- UML - extending, reference strings
ms.assetid: 15dbed99-efce-42fe-a768-714a5804e7d1
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bd5a1ae4abc2e0b5c508b7b77160bbf8da3bb45e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68203226"
---
# <a name="attach-reference-strings-to-uml-model-elements"></a>Anfügen von Referenzzeichenfolgen an UML-Modellelemente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können Code schreiben, um beliebige Zeichenfolgen an Modellelemente anzufügen. Eine Zeichenfolge könnte z. B. ein URI, das zwischengespeicherte Ergebnis einer Berechnung oder ein ModelBus-Verweis auf ein Element in einem anderen Modell sein. Jede Zeichenfolge ist in einem „IReference“-Objekt enthalten. Jedem Modellelement kann eine beliebige Anzahl von „IReference“-Objekten zugeordnet werden.  
  
 Jedes „IReference“-Objekt hat einen Namen. Sie können über diesen Namen angeben, wie der Verweiswert interpretiert werden soll. Beispielsweise könnten Sie für den Namen „URI“ festlegen, um anzugeben, dass der Wert als URI interpretiert werden soll. Es gibt einige vordefinierte Verweisnamenwerte, die von den Modellierungstools verwendet werden.  
  
## <a name="attaching-a-reference-to-an-ielement"></a>Anfügen eines Verweises an ein „IElement“  
 Wenn Sie die folgenden Methoden verwenden möchten, müssen Sie einen Verweis auf Folgendes hinzufügen:  
  
 Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll  
  
 Sie sollten diese Direktive in Ihren Code einfügen:  
  
 `using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;`  
  
|Methodenaufruf|Beschreibung|  
|-----------------|-----------------|  
|`element.AddReference (nameString, valueString, duplicatesAllowed)`|Erstellt ein `IReference` mit den angegebenen Zeichenfolge für Name und Wert und verknüpft diese mit `element`. Gibt `IReference` zurück.<br /><br /> Löst eine Ausnahme aus, wenn `duplicatesAllowed` dem Wert „False“ entspricht und bereits ein `IReference` mit dem gleichen Namen zu `element` zugeordnet ist.|  
|`element.GetReferences(name)`|Gibt alle `IReference`-Objekte zurück, die mit `element` verknüpft sind und den angegebenen `name` aufweisen.|  
|`element.DeleteAllReferences(name)`|Gibt alle `IReference`-Objekte zurück, die mit dem Element verknüpft sind und den angegebenen Namen aufweisen.|  
|`reference.Delete()`|Löscht dieses `IReference`.|  
|`ReferenceConstants.WorkItem`|Der zum Benennen von Arbeitsaufgabenverweisen verwendete Wert.|  
  
## <a name="see-also"></a>Siehe auch  
 [Definieren eines linkhandlers für Arbeitsaufgaben](../modeling/define-a-work-item-link-handler.md)   
 [Definieren und Installieren einer modellierungserweiterung](../modeling/define-and-install-a-modeling-extension.md)   
 [Programmieren mit der UML-API](../modeling/programming-with-the-uml-api.md)

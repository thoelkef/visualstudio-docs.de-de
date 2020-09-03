---
title: Anweisungs Vervollständigung für Bezeichner | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense [JavaScript], statement completion
- statement completion, JavaScript IntelliSense
ms.assetid: c2cd4945-c67e-471b-8057-96cfd25f7fb2
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f5e52bf174e5a41d79fa23bfca39121db668e40e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72643859"
---
# <a name="statement-completion-for-identifiers"></a>Anweisungsvervollständigung für Bezeichner
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

JavaScript lässt keine explizite Typisierung für Variablen Deklarationen zu. Folglich kann IntelliSense nicht immer Vervollständigungs Listen für-Objekte bereitstellen. Dies kann in verschiedenen Situationen vorkommen. Im folgenden finden Sie einige gängige Beispiele.

- Ein Parameter ist deklariert, wurde jedoch nicht an anderer Stelle im aktiven Dokument aufgerufen, wie im folgenden Beispiel gezeigt.

  ```javascript
  function illuminate(light) {
           light.  // Accurate statement completion is not available
                   // unless illuminate is called elsewhere with a
                   // parameter that has a value. If it is called only
                   // in a function that is a sibling to
                   // illuminate(light) in the call hierarchy, the
                   // IntelliSense engine also cannot determine the
                   // parameter type.
       }

  // Sibling function. No statement completion for light
  // object in preceding code.
  function lightLamp() {
      var x = illuminate(1);
  }

  // Uncomment the next line to obtain statement completion for
  // light object in preceding code.
  // var x = illuminate(1);
  ```

- Ein-Objekt befindet sich in einer Funktion, die als Reaktion auf ein Ereignis aufgerufen wird. Zur Entwurfszeit kann die IntelliSense-Engine den Typ der in dieser Situation verwendeten Objekte nicht ermitteln.

   Wenn die IntelliSense-Engine bestimmen kann, dass das Ereignis aufgerufen werden soll, in der Regel durch die Verwendung von `addEventListener` für das-Ereignis im aktiven Dokument, werden genauere IntelliSense-Informationen bereitgestellt.

  Wenn IntelliSense kein Objekt identifizieren kann, füllt die IntelliSense-Engine die Vervollständigungsliste mit benannten Entitäten oder bezeichaten auf, die im aktiven Dokument vorhanden sind. Wenn die Vervollständigungsliste diese Bezeichner enthält, werden neben Ihnen Informations Symbole angezeigt. Außerdem gibt eine QuickInfo für jeden Bezeichner an, dass der Ausdruck unbekannt ist. Die folgende Abbildung zeigt Anweisungs Vervollständigungs Optionen für ein Objekt vom Typ `light` , das nicht identifiziert werden kann, da das Objekt und seine Eigenschaften nicht definiert sind. Die- `intensity` Eigenschaft ist jedoch in der bezeichnerliste verfügbar, da Sie in der- `illuminate` Funktion verwendet wurde.

  **Vervollständigungs Optionen für ein Objekt, das nicht identifiziert werden kann**

  ![JavaScript IntelliSense für Bezeichner](../ide/media/js-intellisense-identifiers.png "js_intellisense_identifiers")

  Sie können die Vervollständigungsliste für ein Objekt überschreiben, indem Sie XML-Dokumentations Kommentare oder JavaScript IntelliSense-Erweiterbarkeits Funktionen verwenden. Mit diesen Funktionen können Sie Typinformationen und aussagekräftigeren IntelliSense-Informationen bereitstellen, wenn diese andernfalls nicht verfügbar sind. Weitere Informationen finden Sie unter [Erweitern von JavaScript IntelliSense](../ide/extending-javascript-intellisense.md) und [Erstellen von XML-Dokumentations Kommentaren](../ide/create-xml-documentation-comments-for-javascript-intellisense.md).

## <a name="see-also"></a>Weitere Informationen
 [JavaScript IntelliSense](../ide/javascript-intellisense.md)

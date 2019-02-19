---
title: Best Practices für MSBuild | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
helpviewer_keywords:
- best practices, MSBuild
- MSBuild, best practices
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ad2070bb696a3ce326331d01145b3ef3b54ae5ec
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "54780665"
---
# <a name="msbuild-best-practices"></a>Best Practices für MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Es werden die folgenden bewährten Methoden zum Schreiben von MSBuild-Skripts empfohlen:  
  
-   Standardwerte für Eigenschaften werden am besten mit dem `Condition`-Attribut verarbeitet und nicht durch Deklarieren einer Eigenschaft, deren Standardwert in der Befehlszeile überschrieben werden kann. Verwenden Sie beispielsweise  
  
     `<MyProperty Condition="$(MyProperty)" == ''>`  
  
     `MyDefaultValue`  
  
     `</MyProperty>`  
  
-   Vermeiden Sie beim Auswählen von Elementen den Einsatz von Platzhaltern. Geben Sie stattdessen Dateien explizit an. Dies erleichtert das Auffinden von Fehlern, die beim Hinzufügen oder Löschen von Dateien auftreten können.  
  
## <a name="see-also"></a>Siehe auch  
 [MSBuild Advanced Concepts (Weiterführende MSBuild-Konzepte)](../msbuild/msbuild-advanced-concepts.md)

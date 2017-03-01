---
title: "Hinzufügen von Erweiterungen zu DSL-Definitionen | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 07e133be-92ab-4936-a02b-45d2012bd0a6
caps.latest.revision: 6
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: f335db9f22392c4d0293a51111efff88c25c3145
ms.lasthandoff: 02/22/2017

---
# <a name="adding-extensions-to-dsl-definitions"></a>Hinzufügen von Erweiterungen zu DSL-Definitionen
DSL-Definition-Erweiterung können Sie ein Paket von Erweiterungen für eine domänenspezifische Sprache (DSL) erstellen. Die DSL-Erweiterung, die in einem Visual Studio Integration Extension (VSIX) enthalten ist, kann auf die gleiche Weise wie eine DSL auf dem Computer eines Benutzers installiert werden. Die zusätzlichen Funktionen können dynamisch aktiviert und zur Laufzeit deaktiviert werden. DSLs müssen nicht explizit für die Erweiterung entwickelt werden, und Extensions können so gestaltet werden später oder von Dritten ohne die erweiterten DSL zu ändern.  
  
 Die zusätzlichen Funktionen können Folgendes umfassen:  
  
-   Eigenschaften-Modell und Präsentation  
  
-   Decorators für Formen und Konnektoren  
  
-   Klassen, Beziehungen, Formen und Konnektoren  
  
-   Validierungseinschränkungen  
  
-   Registerkarten und Toolboxelemente  
  
 Ein Benutzer eine erweiterte DSL erstellen kann, und speichern Sie ein Modell, Instanzen der zusätzlichen Funktionen enthält, und diese können gelesen werden, von anderen Benutzern, die die entsprechende Erweiterung installiert haben. Benutzer, die nicht die Erweiterung installiert haben nicht die zusätzlichen Funktionen verwenden, jedoch können sie aktualisieren und speichern Sie ein Modell ohne Verlust der zusätzlichen Features.  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Siehe auch  
 [Verwandte Blog-Einträge](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)


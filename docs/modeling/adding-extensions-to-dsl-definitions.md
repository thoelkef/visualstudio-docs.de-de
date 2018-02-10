---
title: "Hinzufügen von Erweiterungen zu DSL Definitionen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 1727fbc2c3a46caacb1b57c0a0f7282956daad8b
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="adding-extensions-to-dsl-definitions"></a>Hinzufügen von Erweiterungen zu DSL-Definitionen
DSL-Definition Erweiterung können Sie ein Paket von Erweiterungen für eine domänenspezifische Sprache (DSL) erstellen. Die DSL-Erweiterung, das sich in einer Visual Studio Integration Extension (VSIX) befindet, kann auf dem Computer eines Benutzers auf die gleiche Weise wie eine DSL installiert werden. Die zusätzlichen Funktionen können dynamisch aktiviert und zur Laufzeit deaktiviert werden. Konzentriert müssen nicht explizit für die Erweiterung entworfen werden, und Erweiterungen können entworfen werden später oder von Drittanbietern ohne erweiterte DSL zu ändern.  
  
 Die zusätzlichen Funktionen können Folgendes umfassen:  
  
-   Eigenschaften für das Modell und die Darstellung von Elementen  
  
-   Decorator-Elementen für Formen und Konnektoren  
  
-   Klassen, Beziehungen, Formen und Konnektoren  
  
-   Validierungseinschränkungen  
  
-   Toolboxelementen und Registerkarten  
  
 Ein Benutzer eine erweiterte DSL erstellen und speichern Sie ein Modell, das die zusätzlichen Funktionen enthält, und diese können von anderen Benutzern, die die entsprechende Erweiterung installiert haben gelesen werden. Benutzer, die nicht die Erweiterung installiert haben, können nicht die zusätzlichen Funktionen verwenden, aber sie aktualisieren können, und ein Modell speichern, ohne dass auch die zusätzlichen Funktionen.  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Siehe auch  
 [Verwandte Blogbeiträge](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)

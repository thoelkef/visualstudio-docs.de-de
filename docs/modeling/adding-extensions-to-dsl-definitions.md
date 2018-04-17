---
title: Hinzufügen von Erweiterungen zu DSL Definitionen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: a689d902a58eb747cbaec0bf7cebd740ade3e9bf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
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

---
title: Hinzufügen von Erweiterungen zu DSL-Definitionen
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: dc764df3037baeba36666ce896549018d86c2a21
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31947533"
---
# <a name="add-extensions-to-dsl-definitions"></a>Hinzufügen von Erweiterungen DSL-Definitionen

DSL-Definition Erweiterung können Sie ein Paket von Erweiterungen für eine domänenspezifische Sprache (DSL) erstellen. Die DSL-Erweiterung, das sich in einer Visual Studio Integration Extension (VSIX) befindet, kann auf dem Computer eines Benutzers auf die gleiche Weise wie eine DSL installiert werden. Die zusätzlichen Funktionen können dynamisch aktiviert und zur Laufzeit deaktiviert werden. Konzentriert müssen nicht explizit für die Erweiterung entworfen werden, und Erweiterungen können entworfen werden später oder von Drittanbietern, ohne die erweiterten DSL zu ändern.

DSL-Erweiterungen zählen die folgenden Funktionen:

-   Eigenschaften für das Modell und die Darstellung von Elementen

-   Decorator-Elementen für Formen und Konnektoren

-   Klassen, Beziehungen, Formen und Konnektoren

-   Validierungseinschränkungen

-   Toolboxelementen und Registerkarten

Ein Benutzer eine erweiterte DSL kann erstellen und speichern ein Modell, das die zusätzlichen Funktionen enthält. Das Modell kann von anderen Benutzern gelesen werden, die die entsprechende Erweiterung installiert haben. Benutzer, die nicht die Erweiterung installiert haben, können nicht die zusätzlichen Funktionen verwenden, aber sie aktualisieren können, und ein Modell speichern, ohne dass auch die zusätzlichen Funktionen.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Siehe auch

- [Verwandte Blogbeiträge](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)

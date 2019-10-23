---
title: Hinzufügen von Erweiterungen zu DSL-Definitionen
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f3e44c79783479c46247e4026788725d6ae16da7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747658"
---
# <a name="add-extensions-to-dsl-definitions"></a>Hinzufügen von Erweiterungen zu DSL-Definitionen

Die DSL-Definitions Erweiterung ermöglicht es Ihnen, ein Paket mit Erweiterungen für eine domänenspezifische Sprache (DSL) zu erstellen. Die DSL-Erweiterung, die in einer Visual Studio-Integrations Erweiterung (VSIX) enthalten ist, kann auf dem Computer eines Benutzers auf die gleiche Weise wie eine DSL installiert werden. Die zusätzlichen Features können zur Laufzeit dynamisch aktiviert und deaktiviert werden. DSLs müssen nicht explizit für Erweiterungen entworfen werden, und Erweiterungen können später oder von Drittanbietern entworfen werden, ohne die erweiterte DSL zu ändern.

DSL-Erweiterungen können folgende Features enthalten:

- Eigenschaften für Modell-und Präsentationselemente

- Decorators für Formen und Connectors

- Klassen, Beziehungen, Formen und Connectors

- Validierungs Einschränkungen

- Toolbox Elemente und Registerkarten

Ein Benutzer einer erweiterten DSL kann ein Modell erstellen und speichern, das Instanzen der zusätzlichen Funktionen enthält. Das Modell kann von anderen Benutzern gelesen werden, die die entsprechende Erweiterung installiert haben. Benutzer, die die Erweiterung nicht installiert haben, können die zusätzlichen Features nicht verwenden, aber Sie können ein Modell aktualisieren und speichern, ohne die zusätzlichen Features zu verlieren.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Siehe auch

- [Verwandte Blogbeiträge](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)

---
title: Hinzufügen von Erweiterungen zu DSL-Definitionen
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e9f39c45382fc55144f8200c3951fb4a229b7a43
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57867370"
---
# <a name="add-extensions-to-dsl-definitions"></a>Hinzufügen von Erweiterungen zu DSL-Definitionen

DSL-Definition-Erweiterung können Sie ein Paket von Erweiterungen für eine domänenspezifische Sprache (DSL) zu erstellen. Die DSL-Erweiterung, die in einem Visual Studio Integration Extension (VSIX) enthalten ist, kann auf dem Computer eines Benutzers auf die gleiche Weise wie eine DSL installiert werden. Die zusätzlichen Funktionen können dynamisch aktiviert und zur Laufzeit deaktiviert werden. DSLs müssen nicht explizit für die Erweiterung vorgesehen werden, und die Erweiterungen können entworfen werden weiter unten oder von Drittanbietern, ohne eine Änderung der erweiterten DSL.

DSL-Erweiterungen können die folgenden Features umfassen:

-   Eigenschaften für das Modell und die Darstellung von Elementen

-   Decorators für Formen und Konnektoren

-   Klassen, Beziehungen, Formen und Konnektoren

-   Validierungseinschränkungen

-   Registerkarten und Toolboxelemente

Ein Benutzer eine DSL mit der erweiterten kann erstellt, und Speichern eines Modells, das Instanzen der zusätzlichen Funktionen enthält. Das Modell kann von anderen Benutzern gelesen werden, die die geeignete Erweiterung installiert haben. Benutzer, die nicht die Erweiterung installiert haben, können nicht die zusätzlichen Funktionen verwenden können, aber zu aktualisieren und Speichern eines Modells, ohne dass Sie die zusätzlichen Funktionen verloren gehen.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Siehe auch

- [Verwandte Blogbeiträge](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)

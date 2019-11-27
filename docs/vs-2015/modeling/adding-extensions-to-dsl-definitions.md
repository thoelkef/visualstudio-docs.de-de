---
title: Hinzufügen von Erweiterungen zu DSL-Definitionen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 07e133be-92ab-4936-a02b-45d2012bd0a6
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aeeac82b27b4b5bb71ed05ba658bf9ee048bd85d
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74292156"
---
# <a name="adding-extensions-to-dsl-definitions"></a>Hinzufügen von Erweiterungen zu DSL-Definitionen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die DSL-Definitions Erweiterung ermöglicht es Ihnen, ein Paket mit Erweiterungen für eine domänenspezifische Sprache (DSL) zu erstellen. Die DSL-Erweiterung, die in einer Visual Studio-Integrations Erweiterung (VSIX) enthalten ist, kann auf dem Computer eines Benutzers auf die gleiche Weise wie eine DSL installiert werden. Die zusätzlichen Features können zur Laufzeit dynamisch aktiviert und deaktiviert werden. DSLs müssen nicht explizit für Erweiterungen entworfen werden, und Erweiterungen können später oder von Drittanbietern entworfen werden, ohne die erweiterte DSL zu ändern.

 Die zusätzlichen Features können Folgendes umfassen:

- Eigenschaften für Modell-und Präsentationselemente

- Decorators für Formen und Connectors

- Klassen, Beziehungen, Formen und Connectors

- Validierungs Einschränkungen

- Toolbox Elemente und Registerkarten

  Ein Benutzer einer erweiterten DSL kann ein Modell erstellen und speichern, das Instanzen der zusätzlichen Funktionen enthält. Diese können von anderen Benutzern gelesen werden, die die entsprechende Erweiterung installiert haben. Benutzer, die die Erweiterung nicht installiert haben, können die zusätzlichen Features nicht verwenden, aber Sie können ein Modell aktualisieren und speichern, ohne die zusätzlichen Features zu verlieren.

  Beispielcode und weitere Informationen zu diesem Feature finden Sie auf der [Visual Studio-Website zum Visualisieren und modellieren von SDK](https://go.microsoft.com/fwlink/?LinkID=186128) .

## <a name="see-also"></a>Siehe auch
 [Visual Studio-Visualisierungs-und Modellierungs-SDK](https://go.microsoft.com/fwlink/?LinkID=186128)

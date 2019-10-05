---
title: Hinzufügen von Erweiterungen zu DSL-Definitionen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 07e133be-92ab-4936-a02b-45d2012bd0a6
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bd45a2345e6e5b28b74cb27fac226514c3f92a04
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68159076"
---
# <a name="adding-extensions-to-dsl-definitions"></a>Hinzufügen von Erweiterungen zu DSL-Definitionen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DSL-Definition-Erweiterung können Sie ein Paket von Erweiterungen für eine domänenspezifische Sprache (DSL) zu erstellen. Die DSL-Erweiterung, die in einem Visual Studio Integration Extension (VSIX) enthalten ist, kann auf dem Computer eines Benutzers auf die gleiche Weise wie eine DSL installiert werden. Die zusätzlichen Funktionen können dynamisch aktiviert und zur Laufzeit deaktiviert werden. DSLs müssen nicht explizit für die Erweiterung vorgesehen werden, und die Erweiterungen können entworfen werden weiter unten oder von Drittanbietern ohne Ändern der erweiterten DSL.  
  
 Die zusätzlichen Funktionen können Folgendes umfassen:  
  
- Eigenschaften für das Modell und die Darstellung von Elementen  
  
- Decorators für Formen und Konnektoren  
  
- Klassen, Beziehungen, Formen und Konnektoren  
  
- Validierungseinschränkungen  
  
- Registerkarten und Toolboxelemente  
  
  Ein Benutzer eine DSL mit der erweiterten erstellen kann, und Speichern eines Modells, das Instanzen der zusätzlichen Features enthält, und diese können gelesen werden, von anderen Benutzern, die die geeignete Erweiterung installiert haben. Benutzer, die nicht die Erweiterung installiert haben, können nicht die zusätzlichen Funktionen verwenden können, aber zu aktualisieren und Speichern eines Modells, ohne dass Sie die zusätzlichen Funktionen verloren gehen.  
  
  Beispielcode und Weitere Informationen zu diesem Feature finden Sie in der [Visual Studio-Visualisierungs- und Modellierungs-SDK](http://go.microsoft.com/fwlink/?LinkID=186128) Website.  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio-Visualisierungs- und Modellierungs-SDK](http://go.microsoft.com/fwlink/?LinkID=186128)

---
author: dotpaul
ms.author: paulming
ms.date: 04/05/2019
ms.topic: include
ms.openlocfilehash: 054198eff46c0983a5610b29dee5e29e5ac67a70
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/09/2019
ms.locfileid: "65459363"
---
Unsichere Deserialisierer sind anfällig, wenn nicht vertrauenswürdige Daten zu deserialisieren. Ein Angreifer könnte die serialisierten Daten unerwartete Typen zum Einfügen von Objekten mit schädlichen Nebeneffekten ändern. Ein Angriff auf eine unsichere Deserialisierungsprogramm kann z. B. Befehle ausführen, auf das zugrunde liegende Betriebssystem, über das Netzwerk kommunizieren, Dateien, oder löschen.
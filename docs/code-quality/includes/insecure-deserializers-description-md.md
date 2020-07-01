---
author: dotpaul
ms.author: paulming
ms.date: 04/05/2019
ms.topic: include
ms.openlocfilehash: 054198eff46c0983a5610b29dee5e29e5ac67a70
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68147098"
---
Unsichere deserialisierungssoren sind beim Deserialisieren nicht vertrauenswürdiger Daten anfällig. Ein Angreifer könnte die serialisierten Daten so ändern, dass unerwartete Typen eingefügt werden, um Objekte mit bösartigen Nebeneffekten einzuschleusen. Ein Angriff auf ein unsicherer Deserialisierungsprogramm könnte z. b. Befehle für das zugrunde liegende Betriebssystem ausführen, über das Netzwerk kommunizieren oder Dateien löschen.
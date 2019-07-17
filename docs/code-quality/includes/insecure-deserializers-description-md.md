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
Unsichere Deserialisierer sind anfällig, wenn nicht vertrauenswürdige Daten zu deserialisieren. Ein Angreifer könnte die serialisierten Daten unerwartete Typen zum Einfügen von Objekten mit schädlichen Nebeneffekten ändern. Ein Angriff auf eine unsichere Deserialisierungsprogramm kann z. B. Befehle ausführen, auf das zugrunde liegende Betriebssystem, über das Netzwerk kommunizieren, Dateien, oder löschen.
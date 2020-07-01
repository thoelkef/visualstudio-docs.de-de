---
title: Generieren eines privaten Felds und einer privaten Eigenschaft anhand eines Konstruktors
ms.date: 06/20/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 56bd361d2bffb4ff17b03ac6743837032d1934e1
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85283722"
---
# <a name="generate-private-field-and-property-from-constructor"></a>Generieren eines privaten Felds und einer privaten Eigenschaft anhand eines Konstruktors

Dieses Refactoring gilt für: 

- C# 

**Beschreibung:** Dient zum Generieren eines privaten Felds oder einer privaten Eigenschaft anhand eines Konstruktors. 

**Hintergrund:** Sie möchten schnell ein privates Feld oder eine private Eigenschaft anhand eines Konstruktors hinzufügen und initialisieren.

**Vorteile**: Das Schreiben privater Felder und Eigenschaften kann zeitaufwändig und monoton sein. Die Verwendung dieses Refactorings ist schnell und macht das Programm stabiler.

## <a name="how-to"></a>Vorgehensweise 

1. Platzieren Sie Ihren Cursor auf dem Parameternamen im Konstruktor.

2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.
   
3. Wählen Sie als Nächstes eine der folgenden Optionen aus:

- **Feld erstellen und initialisieren** oder **Eigenschaft erstellen und initialisieren**.

   ![Generieren eines privaten Felds aus einem Konstruktor](media/generate-private-field-from-constructor.png)

## <a name="see-also"></a>Siehe auch 

- [Refactoring](../refactoring-in-visual-studio.md)

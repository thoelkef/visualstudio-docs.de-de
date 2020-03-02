---
title: Generieren eines privaten Felds aus einem Konstruktor
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 8ef4188216b669b30b7af9bd725ec432bcd0a774
ms.sourcegitcommit: 3c105990656cd509062ce60e52e776c794f6305d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2020
ms.locfileid: "77529413"
---
# <a name="generate-private-field-from-constructor"></a>Generieren eines privaten Felds aus einem Konstruktor

Dieses Refactoring gilt für: 

- C# 

**Beschreibung:** Dieses Refactoring dient zum Generieren eines privaten Felds aus einem Konstruktor. 

**Hintergrund:** Verwenden Sie dieses Refactoring, wenn Sie schnell ein privates Feld aus einem Konstruktor hinzufügen möchten.

**Vorteile**: Das Schreiben privater Felder kann zeitaufwändig und monoton sein. Die Verwendung dieses Refactorings ist schnell und macht das Programm stabiler.

## <a name="how-to"></a>Vorgehensweise 

1. Platzieren Sie Ihren Cursor auf dem Parameternamen im Konstruktor.

2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.
   
3. Wählen Sie die Option zum **Erstellen und Initialisieren des Felds** aus.

   ![Generieren eines privaten Felds aus einem Konstruktor](media/generate-private-field-from-constructor.png)

## <a name="see-also"></a>Siehe auch 

- [Refactoring](../refactoring-in-visual-studio.md)

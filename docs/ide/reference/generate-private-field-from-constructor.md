---
title: Generieren eines privaten Felds aus einem Konstruktor
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 4eb5dd39d0fb2d4cd9ba8ade0d0408d6e36a4854
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094028"
---
# <a name="generate-private-field-from-constructor"></a>Generieren eines privaten Felds aus einem Konstruktor

Dieses Refactoring gilt für: 

- C# 

- Visual Basic

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

---
title: Synchronisieren von Namespace und Ordnername
ms.date: 06/12/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: d7073edaf6ecc261c58bf1e5607323b9214c5ed0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "67160756"
---
# <a name="sync-namespace-and-folder-name"></a>Synchronisieren von Namespace und Ordnername

Dieses Refactoring gilt für:

- C#

**Beschreibung:** Synchronisieren von Namespace und Ordnername

**Hintergrund:** Sie möchten Teile Ihrer Projektmappe neu strukturieren, indem Sie eine Datei in einen neuen Ordner ziehen. 

**Vorteile**: Sie möchten sicherstellen, dass Ihr Namespace mit Ihrer neuen Ordnerstruktur auf dem neuesten Stand ist.

## <a name="how-to"></a>Vorgehensweise

1. Platzieren Sie Ihren Cursor auf dem Namespacenamen.
2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.
3. Wählen Sie **Namespace in \<folder name> ändern** aus.

   ![Synchronisieren von Namespace und Ordnername](media/sync-namespace-and-folder-name.png)

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)

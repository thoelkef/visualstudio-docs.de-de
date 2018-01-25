---
title: "Verschieben eines Typs in eine entsprechende Datei – Refactoring (C#) | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 4b7b9b1ba52bed5d2bdf042db0149d799c489a7d
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2018
---
# <a name="move-a-type-to-a-matching-file-in-c"></a>Verschieben eines Typs in eine entsprechende Datei in C# #

**Beschreibung**: Hiermit können Sie den ausgewählten Typ in eine separate Datei mit demselben Namen verschieben.

**Hintergrund**: Es sind mehrere Klassen, Strukturen, Schnittstellen usw. in der gleichen Datei vorhanden, die Sie trennen möchten.

**Vorteile**: Das Platzieren mehrerer Typen in die gleiche Datei kann die Suche nach diesen Typen erschweren.  Durch das Verschieben von Typen in Dateien mit demselben Namen wird der Code besser lesbar und ist einfacher zu navigieren.

**Vorgehensweise**:

1. Markieren Sie den Namen des zu verschiebenden Typs, oder platzieren Sie den Textcursor in den Namen:

   ![Markierter Code](media/movetype-highlight-cs.png)

1. Führen Sie dann eine der folgenden Aktionen aus:
   * **Tastatur**
     * Drücken Sie **STRG+.**, um das Menü **Schnellaktionen und Refactorings** aufzurufen. Wählen Sie dann im Popupvorschaufenster die Option **Typ in *TypeName*.cs verschieben** aus, wobei *TypeName* für den Namen des ausgewählten Typs steht.
   * **Maus**
     * Klicken Sie mit der rechten Maustaste auf den Code, und wählen Sie das Menü **Schnellaktionen und Refactorings** aus. Wählen Sie dann im Popupvorschaufenster die Option **Typ in *TypeName*.cs verschieben** aus, wobei *TypeName* für den Namen des ausgewählten Typs steht.

   Der Typ wird sofort in eine neue Datei mit diesem Namen in Ihre Projektmappe verschoben.

   ![Ergebnis des Inlinevorgangs](media/movetype-result-cs.png)

## <a name="see-also"></a>Siehe auch

[Refactoring](../refactoring-in-visual-studio.md)
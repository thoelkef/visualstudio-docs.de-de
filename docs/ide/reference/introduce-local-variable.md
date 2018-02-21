---
title: Bereitstellen einer lokalen Variable in Visual Studio | Microsoft-Dokumentation
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 997220d3b1a7305f84f61ee5fd4c205d1157f1b2
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="introduce-a-local-variable-in-visual-studio"></a>Bereitstellen einer lokalen Variable in Visual Studio

Diese Codegenerierung gilt für:

- C#

- Visual Basic

**Beschreibung**: Hiermit können Sie sofort eine lokale Variable generieren, um einen vorhandenen Ausdruck zu ersetzen.

**Hintergrund**: Sie verwenden einen Code, der bei Verwendung in einer lokalen Variable später problemlos wiederverwendet werden kann.

**Vorteile**: Sie könnten den Code für die Verwendung an verschiedenen Stellen mehrmals kopieren und einfügen. Besser wäre es jedoch, den Vorgang einmal durchzuführen, das Ergebnis in einer lokalen Variable zu speichern und durchgehend die lokale Variable zu verwenden.

## <a name="how-to"></a>Vorgehensweise

1. Markieren Sie den Ausdruck, der einer neuen lokalen Variable zugewiesen werden soll.

   - C#:

    ![Hervorgehobener Code – C#](media/local-highlight-cs.png)

   - Visual Basic:

    ![Hervorgehobener Code in Visual Basic](media/local-highlight-vb.png)

1. Führen Sie dann eine der folgenden Aktionen aus:

   - **Tastatur**
     - Drücken Sie **STRG+.**, um das Menü **Schnellaktionen und Refactorings** aufzurufen.
   - **Maus**
     - Führen Sie einen Rechtsklick durch, und klicken Sie auf das Menü **Schnellaktionen und Refactorings**.
     - Klicken Sie auf die Schaltfläche ![Glühbirnensymbol,](media/bulb-cs.png) das am linken Rand angezeigt wird, sofern der Textcursor bereits in der Zeile mit der roten Wellenlinie platziert ist.

   ![Vorschau der Aktion zum Bereitstellen eines lokalen Elements](media/local-preview-cs.png)

1. Wählen Sie **Lokales Element für (alle Vorkommen von) „*Ausdruck*“ bereitstellen** im Dropdownmenü aus.

   > [!TIP]
   > Klicken Sie im unteren Bereich des Vorschaufensters auf den Link **Vorschau der Änderungen**, um vor einer Auswahl [alle Änderungen anzuzeigen](../../ide/preview-changes.md), die vorgenommen werden.

   Die lokale Variable wird in Abhängigkeit vom angegebenen Typ erstellt. Geben Sie der neuen lokalen Variable einen neuen Namen.

   - C#:

      ![Ergebnis der Implementierung einer Schnittstelle in C#](media/local-result-cs.png)

   - Visual Basic:

      ![Ergebnis der Implementierung einer Schnittstelle in Visual Basic](media/local-result-vb.png)

   > [!NOTE]
   > Sie können die Menüoption **...alle Vorkommen von...** verwenden, um nicht nur den speziell markierten Ausdruck zu ersetzen, sondern jede Instanz des markierten Ausdrucks.

## <a name="see-also"></a>Siehe auch

[Codegenerierung](../code-generation-in-visual-studio.md)  
[Vorschau der Änderungen](../../ide/preview-changes.md)

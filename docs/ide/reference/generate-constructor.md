---
title: Generieren eines Konstruktors in Visual Studio | Microsoft-Dokumentation
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: article
author: kuhlenh
ms.author: kaseyu
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 78b1829ae6a302b7c5f71fa2c478152d0c20d1b8
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="generate-a-constructor-in-visual-studio"></a>Generieren eines Konstruktors in Visual Studio

Diese Codegenerierung gilt für:

- C#

- Visual Basic

**Beschreibung**: Hiermit können Sie sofort den Code für einen neuen Konstruktor in einer Klasse generieren.

**Hintergrund**: Sie führen einen neuen Konstruktor ein, der ordnungsgemäß automatisch deklariert werden soll, oder ändern einen vorhandenen Konstruktor.

**Vorteile**: Sie können den Konstruktor vor der Verwendung zwar deklarieren, bei diesem Feature wird dieser jedoch automatisch mit den entsprechenden Parametern generiert. Darüber hinaus müssen durch das Ändern eines vorhandenen Konstruktors alle Aufrufsites aktualisiert werden, es sei denn, Sie aktualisieren diese automatisch mithilfe dieses Features.

**Vorgehensweise**: Es gibt mehrere Möglichkeiten zum Generieren eines Konstruktors:

   - [Generieren eines Konstruktors und Auswählen von Membern](#pick)
   - [Generieren eines Konstruktors über ausgewählte Felder](#selection)
   - [Generieren eines Konstruktors aus der neuen Verwendung](#usage)
   - [Hinzufügen eines Parameters zu einem vorhandenen Konstruktor](#addparameter)
   - [Erstellen und Initialisieren eines Felds bzw. einer Eigenschaft anhand eines Konstruktorparameters](#create)

## <a id = "pick"></a> Generieren eines Konstruktors und Auswählen von Membern (nur in C#)

1. Platzieren Sie den Cursor in eine beliebige leere Zeile in einer Klasse:

   ![Cursor in einer leeren Zeile](media/constructor1-highlight-cs.png)

1. Führen Sie dann eine der folgenden Aktionen aus:

   - **Tastatur**
     - Drücken Sie **STRG+.**, um das Menü **Schnellaktionen und Refactorings** aufzurufen.
   - **Maus**
     - Führen Sie einen Rechtsklick durch, und klicken Sie auf das Menü **Schnellaktionen und Refactorings**.
     - Klicken Sie auf die Schaltfläche ![Glühbirnensymbol,](media/bulb-cs.png) das am linken Rand angezeigt wird, sofern der Textcursor bereits in der leeren Zeile in der Klasse platziert ist.

   ![Vorschau der Aktion zum Generieren eines Konstruktors](media/constructor1-preview-cs.png)

1. Wählen Sie **Konstruktor generieren...** im Dropdownmenü aus.

   Das Dialogfeld **Member auswählen** wird geöffnet.

1. Wählen Sie die Member aus, die als Konstruktorparameter enthalten sein sollen. Sie können sie mithilfe der NACH-OBEN- und NACH-UNTEN-TASTEN sortieren. Klicken Sie auf **OK**.

   ![Dialogfeld „Member auswählen“](media/constructor1-dialog-cs.png)

   > [!TIP]
   > Aktivieren Sie das Kontrollkästchen **NULL-Überprüfungen hinzufügen**, um automatisch NULL-Überprüfungen für die Konstruktorparameter zu generieren.

   Der Konstruktor wird mit den angegebenen Parametern erstellt.

   ![Ergebnis der Aktion zum Generieren eines Konstruktors](media/constructor1-result-cs.png)

## <a id="selection"></a> Generieren eines Konstruktors aus ausgewählten Feldern (nur in C#)

1. Markieren Sie die Member, die im generierten Konstruktor enthalten sein sollen:

   ![Markierte Member](media/constructor2-highlight-cs.png)

1. Führen Sie dann eine der folgenden Aktionen aus:

   - **Tastatur**
     - Drücken Sie **STRG+.**, um das Menü **Schnellaktionen und Refactorings** aufzurufen.
   - **Maus**
     - Führen Sie einen Rechtsklick durch, und klicken Sie auf das Menü **Schnellaktionen und Refactorings**.
     - Klicken Sie auf die Schaltfläche ![Glühbirnensymbol,](media/bulb-cs.png) das am linken Rand angezeigt wird, sofern der Textcursor bereits in der Zeile mit der Auswahl platziert ist.

     ![Vorschau der Aktion zum Generieren eines Konstruktors](media/constructor2-preview-cs.png)

1. Wählen Sie **Konstruktor „TypeName(...)“ generieren...** im Dropdownmenü aus.

   Der Konstruktor wird mit den ausgewählten Parametern erstellt.

   ![Ergebnis der Generierung eines Konstruktors](media/constructor2-result-cs.png)

## <a id="usage"></a> Generieren eines Konstruktors aus der neuen Verwendung (C# und Visual Basic)

1. Platzieren Sie Ihren Cursor auf der Zeile, in der eine rote Wellenlinie angezeigt wird. Die rote Wellenlinie weist auf einen Aufruf eines Konstruktors hin, der noch nicht vorhanden ist.

   - C#:

    ![Hervorgehobener Code – C#](media/constructor-highlight-cs.png)

   - Visual Basic:

    ![Hervorgehobener Code in Visual Basic](media/constructor-highlight-vb.png)

1. Führen Sie dann eine der folgenden Aktionen aus:

   - **Tastatur**
     - Drücken Sie **STRG+.**, um das Menü **Schnellaktionen und Refactorings** aufzurufen.
   - **Maus**
     - Führen Sie einen Rechtsklick durch, und klicken Sie auf das Menü **Schnellaktionen und Refactorings**.
     - Zeigen Sie auf die rote Wellenlinie, und klicken Sie auf das ![Glühbirnensymbol,](media/bulb-cs.png) das angezeigt wird.
     - Klicken Sie auf die Schaltfläche ![Glühbirnensymbol,](media/bulb-cs.png) das am linken Rand angezeigt wird, sofern der Textcursor bereits in der Zeile mit der roten Wellenlinie platziert ist.

    ![Vorschau der Aktion zum Generieren eines Konstruktors](media/constructor-preview-cs.png)

1. Wählen Sie **Konstruktor in „*TypeName*“ generieren** im Dropdownmenü aus.

   > [!TIP]
   > Klicken Sie im unteren Bereich des Vorschaufensters auf den Link **Vorschau der Änderungen**, um vor einer Auswahl [alle Änderungen anzuzeigen](../../ide/preview-changes.md), die vorgenommen werden.

   Der Konstruktor wird in Abhängigkeit von den angegebenen Parametern erstellt.

   - C#:

      ![Ergebnis der Methodengenerierung in C#](media/constructor-result-cs.png)

   - Visual Basic:

      ![Ergebnis der Methodengenerierung in Visual Basic](media/constructor-result-vb.png)

## <a id="addparameter"></a> Hinzufügen eines Parameters zu einem vorhandenen Konstruktor (nur in C#)

1. Fügen Sie einem vorhandenen Konstruktor einen Parameter hinzu.

1. Platzieren Sie den Cursor in die Zeile mit einer roten Wellenlinie, die darauf hinweist, dass Sie einen noch nicht vorhandenen Konstruktor verwendet haben.

    ![Markierung beim Generieren eines Konstruktors](media/constructor4-highlight-cs.png)

1. Führen Sie dann eine der folgenden Aktionen aus:

   - **Tastatur**
     - Drücken Sie **STRG+.**, um das Menü **Schnellaktionen und Refactorings** aufzurufen.
   - **Maus**
     - Führen Sie einen Rechtsklick durch, und klicken Sie auf das Menü **Schnellaktionen und Refactorings**.
     - Zeigen Sie auf die rote Wellenlinie, und klicken Sie auf das ![Glühbirnensymbol,](media/bulb-cs.png) das angezeigt wird.
     - Klicken Sie auf die Schaltfläche ![Glühbirnensymbol,](media/bulb-cs.png) das am linken Rand angezeigt wird, sofern der Textcursor bereits in der Zeile mit der roten Wellenlinie platziert ist.

    ![Vorschau der Aktion zum Generieren eines Konstruktors](media/constructor4-preview-cs.png)

1. Wählen Sie im Dropdownmenü **Parameter zu „TypeName(...)“ hinzufügen** aus.

   Der Parameter wird in Abhängigkeit seines Typs dem Konstruktor hinzugefügt.

   ![Ergebnis der Aktion zum Generieren eines Konstruktors](media/constructor4-result-cs.png)

## <a id="create"></a> Erstellen und Initialisieren eines Felds oder einer Eigenschaft anhand eines Konstruktorparameters (nur in C#)

1. Suchen Sie einen vorhandenen Konstruktor, und fügen Sie ihm einen Parameter hinzu:

   ![Markierung beim Generieren eines Konstruktors](media/constructor5-highlight-cs.png)

1. Platzieren Sie den Cursor in den neu hinzugefügten Parameter.

1. Führen Sie dann eine der folgenden Aktionen aus:

   - **Tastatur**
     - Drücken Sie **STRG+.**, um das Menü **Schnellaktionen und Refactorings** aufzurufen.
   - **Maus**
     - Führen Sie einen Rechtsklick durch, und klicken Sie auf das Menü **Schnellaktionen und Refactorings**.
     - Klicken Sie auf die Schaltfläche ![Glühbirnensymbol,](media/bulb-cs.png) das am linken Rand angezeigt wird, sofern der Textcursor bereits in der Zeile mit dem hinzugefügten Parameter platziert ist.

   ![Vorschau der Aktion zum Generieren eines Konstruktors](media/constructor5-preview-cs.png)

1. Wählen Sie im Dropdownmenü **Eigenschaft erstellen und initialisieren** oder **Feld erstellen und initialisieren**.

   Das Feld bzw. die Eigenschaft wird deklariert und automatisch entsprechend Ihrer Typen benannt. Zum Initialisieren des Felds bzw. der Eigenschaft im Konstruktortext, wird eine Codezeile hinzugefügt.

   ![Ergebnis der Aktion zum Generieren eines Konstruktors](media/constructor5-result-cs.png)

## <a name="see-also"></a>Siehe auch

[Codegenerierung](../code-generation-in-visual-studio.md)  
[Vorschau der Änderungen](../../ide/preview-changes.md)
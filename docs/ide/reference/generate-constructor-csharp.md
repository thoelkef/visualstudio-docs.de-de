---
title: "Generieren eines Konstruktors – Codegenerierung (C#) | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2280cfa-a9ec-4b56-9d94-c8fd384db980
author: kuhlenh
ms.author: kaseyu
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: b6e73b3b012547e98934bbcd76d1ee2eb0f3324d
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2018
---
# <a name="generate-a-constructor-in-c"></a>Generieren eines Konstruktors in C# #
**Beschreibung**: Hiermit können Sie sofort den Code für einen neuen Konstruktor in einer Klasse generieren. 

**Hintergrund**: Sie führen einen neuen Konstruktor ein, der ordnungsgemäß automatisch deklariert werden soll, oder ändern einen vorhandenen Konstruktor. 

**Vorteile**: Sie können den Konstruktor vor der Verwendung zwar deklarieren, bei diesem Feature wird dieser jedoch automatisch mit den entsprechenden Parametern generiert. Darüber hinaus müssen durch das Ändern eines vorhandenen Konstruktors alle Aufrufsites aktualisiert werden, es sei denn, Sie aktualisieren diese automatisch mithilfe dieses Features.

**Vorgehensweise**: Es gibt mehrere Möglichkeiten zum Generieren eines Konstruktors:
- [Generieren eines Konstruktors und Auswählen von Membern](#pick)
- [Generieren eines Konstruktors über ausgewählte Felder](#selection)
- [Generieren eines Konstruktors aus der neuen Verwendung](#usage)
- [Hinzufügen eines Parameters zu einem vorhandenen Konstruktor](#addparameter)
- [Erstellen und Initialisieren eines Felds bzw. einer Eigenschaft anhand eines Konstruktorparameters](#create)

## <a id = "pick"></a>Generieren eines Konstruktors und Auswählen von Membern
1. Platzieren Sie den Cursor in eine beliebige leere Zeile in einer Klasse:

   ![Cursor in einer leeren Zeile](media/constructor1-highlight-cs.png)

1. Führen Sie dann eine der folgenden Aktionen aus:
   * **Tastatur**
     * Drücken Sie **STRG+.**, um das Menü **Schnellaktionen und Refactorings** aufzurufen, und wählen Sie im Popupvorschaufenster **Konstruktor generieren...** aus.
   * **Maus**
     * Klicken Sie mit der rechten Maustaste auf den Code, und wählen Sie das Menü **Schnellaktionen und Refactorings** sowie im Popupvorschaufenster **Konstruktor generieren...** aus.
     * Klicken Sie auf die Schaltfläche ![Glühbirnensymbol,](media/bulb-cs.png) das am linken Rand angezeigt wird, sofern der Textcursor bereits in der leeren Zeile in der Klasse platziert ist.

   ![Vorschau der Aktion zum Generieren eines Konstruktors](media/constructor1-preview-cs.png)

1. Ein Dialogfeld wird angezeigt, mit dem Sie die als Konstruktorparameter zu verwendenden Elemente auswählen und (mit Pfeil nach oben und nach unten) anordnen können. Klicken Sie auf **OK**, um Ihre Änderungen zu committen.
  
   ![Dialogfeld „Member auswählen“](media/constructor1-dialog-cs.png)

   >[!TIP] 
   >Aktivieren Sie das Kontrollkästchen **NULL-Überprüfungen hinzufügen**, um automatisch NULL-Überprüfungen für die Konstruktorparameter zu generieren.

1. Der Konstruktor wird mit den ausgewählten Parametern in der angegebenen Reihenfolge erstellt.
   ![Ergebnis der Aktion zum Generieren eines Konstruktors](media/constructor1-result-cs.png)

## <a id="selection"></a>Generieren eines Konstruktors über ausgewählte Felder
1. Markieren Sie die Member, die im generierten Konstruktor enthalten sein sollen: ![Markieren von Membern](media/constructor2-highlight-cs.png)

1. Führen Sie dann eine der folgenden Aktionen aus:
   * **Tastatur**
     * Drücken Sie **STRG+.**, um das Menü **Schnellaktionen und Refactorings** aufzurufen, und wählen Sie im Popupvorschaufenster **Konstruktor "TypeName(...)" generieren** aus.
   * **Maus**
     * Klicken Sie mit der rechten Maustaste auf den Code, und wählen Sie das Menü **Schnellaktionen und Refactorings** sowie im Popupvorschaufenster **Konstruktor "TypeName(...)" generieren** aus.
     * Klicken Sie auf die Schaltfläche ![Glühbirnensymbol,](media/bulb-cs.png) das am linken Rand angezeigt wird, sofern der Textcursor bereits in der Zeile mit der Auswahl platziert ist.

     ![Vorschau der Aktion zum Generieren eines Konstruktors](media/constructor2-preview-cs.png)

1. Der Konstruktor wird mit den ausgewählten Parametern erstellt.
     ![Ergebnis der Aktion zum Generieren eines Konstruktors](media/constructor2-result-cs.png)

## <a id="usage"></a>Generieren eines Konstruktors aus der neuen Verwendung
1. Platzieren Sie den Cursor in die Zeile mit einer roten Wellenlinie, die darauf hinweist, dass Sie einen noch nicht vorhandenen Konstruktor verwendet haben.

   ![Markierter Code](media/constructor-highlight-cs.png)

1. Führen Sie dann eine der folgenden Aktionen aus:
   * **Tastatur**
     * Drücken Sie **STRG+.**, um das Menü **Schnellaktionen und Refactorings** aufzurufen, und wählen Sie im Popupvorschaufenster **Konstruktor in "*TypeName*" generieren** aus.
   * **Maus**
     * Klicken Sie mit der rechten Maustaste auf den Code, und wählen Sie das Menü **Schnellaktionen und Refactorings** sowie im Popupvorschaufenster **Konstruktor in "*TypeName*" generieren** aus.
     * Zeigen Sie auf die rote Wellenlinie, und klicken Sie auf das ![Glühbirnensymbol,](media/bulb-cs.png) das angezeigt wird.
     * Klicken Sie auf die Schaltfläche ![Glühbirnensymbol,](media/bulb-cs.png) das am linken Rand angezeigt wird, sofern der Textcursor bereits in der Zeile mit der roten Wellenlinie platziert ist.

   ![Vorschau der Aktion zum Generieren eines Konstruktors](media/constructor-preview-cs.png)

   >[!TIP]
   >Klicken Sie im unteren Bereich des Vorschaufensters auf den Link [**Vorschau der Änderungen**](../../ide/preview-changes.md), um vor einer Auswahl alle Änderungen anzuzeigen, die vorgenommen werden.

1. Der Konstruktor wird automatisch mit den aus der Verwendung abgeleiteten Parametern erstellt.

   ![Ergebnis der Aktion zum Generieren eines Konstruktors](media/constructor-result-cs.png)

## <a id="addparameter"></a>Hinzufügen eines Parameters zu einem vorhandenen Konstruktor
1. Fügen Sie einen Parameter zu einer vorhandenen Objektinstanziierung hinzu.

1. Platzieren Sie den Cursor in die Zeile mit einer roten Wellenlinie, die darauf hinweist, dass Sie einen noch nicht vorhandenen Konstruktor verwendet haben.
    
    ![Markierung beim Generieren eines Konstruktors](media/constructor4-highlight-cs.png)

1. Führen Sie dann eine der folgenden Aktionen aus:
   * **Tastatur**
     * Drücken Sie **STRG+.**, um das Menü **Schnellaktionen und Refactorings** aufzurufen, und wählen Sie im Popupvorschaufenster **Parameter zu "TypeName(...)" hinzufügen** aus.
   * **Maus**
     * Klicken Sie mit der rechten Maustaste auf den Code, und wählen Sie das Menü **Schnellaktionen und Refactorings** sowie im Popupvorschaufenster **Parameter zu "TypeName(...)" hinzufügen** aus.
     * Zeigen Sie auf die rote Wellenlinie, und klicken Sie auf das ![Glühbirnensymbol,](media/bulb-cs.png) das angezeigt wird.
     * Klicken Sie auf die Schaltfläche ![Glühbirnensymbol,](media/bulb-cs.png) das am linken Rand angezeigt wird, sofern der Textcursor bereits in der Zeile mit der roten Wellenlinie platziert ist.

    ![Vorschau der Aktion zum Generieren eines Konstruktors](media/constructor4-preview-cs.png)

1. Der Parameter wird automatisch mit seinem aus seiner Verwendung abgeleiteten Typ hinzugefügt.
   
   ![Ergebnis der Aktion zum Generieren eines Konstruktors](media/constructor4-result-cs.png)

## <a id="create"></a>Erstellen und Initialisieren eines Felds bzw. einer Eigenschaft anhand eines Konstruktorparameters
1. Fügen Sie über einen vorhandenen Konstruktor einen Parameter hinzu:

   ![Markierung beim Generieren eines Konstruktors](media/constructor5-highlight-cs.png)

1. Platzieren Sie den Cursor in den neu hinzugefügten Parameter.

1. Führen Sie dann eine der folgenden Aktionen aus:
   * **Tastatur**
     * Drücken Sie **STRG+.**, um das Menü **Schnellaktionen und Refactorings** aufzurufen, und wählen Sie im Popupvorschaufenster **Eigenschaft "YourProperty" erstellen und initialisieren** oder **Feld "YourField" erstellen und initialisieren** aus.
   * **Maus**
     * Klicken Sie mit der rechten Maustaste auf den Code, und wählen Sie das Menü **Schnellaktionen und Refactorings** sowie im Popupvorschaufenster **Eigenschaft "YourProperty" erstellen und initialisieren** oder **Feld "YourField" erstellen und initialisieren** aus.
     * Klicken Sie auf die Schaltfläche ![Glühbirnensymbol,](media/bulb-cs.png) das am linken Rand angezeigt wird, sofern der Textcursor bereits in der Zeile mit dem hinzugefügten Parameter platziert ist.

   ![Vorschau der Aktion zum Generieren eines Konstruktors](media/constructor5-preview-cs.png)

1. Das Feld bzw. die Eigenschaft wird erstellt und automatisch entsprechend Ihrer Typen benannt.

   ![Ergebnis der Aktion zum Generieren eines Konstruktors](media/constructor5-result-cs.png)

## <a name="see-also"></a>Siehe auch

[Codegenerierung](../code-generation-in-visual-studio.md)  
[Vorschau der Änderungen](../../ide/preview-changes.md)
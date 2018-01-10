---
title: Generieren Sie einen Konstruktor - Generierung von Code (c#) | Microsoft Docs
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
ms.openlocfilehash: dd5e1012c37660917d77e2643922d8a90a8e2ffe
ms.sourcegitcommit: 5f436413bbb1e8aa18231eb5af210e7595401aa6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2018
---
# <a name="generate-a-constructor-in-c"></a>Generieren Sie einen Konstruktor in c# #
**Was:** können Sie sofort den Code für einen neuen Konstruktor für eine Klasse zu generieren. 

**Wann:** führen Sie einen neuen Konstruktor und für die ordnungsgemäß automatisch deklarieren möchten, oder Sie ändern einen vorhandenen Konstruktor. 

**Grund:** konnten Sie den Konstruktor vor dem verwenden, deklarieren, aber dieses Feature, mit den entsprechenden Parametern automatisch generiert. Darüber hinaus erfordert das Ändern eines vorhandenen Konstruktors alle Aufrufsites aktualisieren, es sei denn, Sie dieses Feature verwenden, um sie automatisch zu aktualisieren.

**Vorgehensweise:** es gibt mehrere Möglichkeiten, einen Konstruktor zu generieren:
- [Generieren Sie Konstruktor, und wählen Sie Elemente](#pick)
- [Generieren Sie Konstruktor aus ausgewählten Feldern.](#selection)
- [Konstruktor von neuen Verwendung generieren](#usage)
- [Fügen Sie Parameter an vorhandenen Konstruktor hinzu.](#addparameter)
- [Erstellen Sie und initialisieren Sie Feld/Eigenschaft aus einem Konstruktorparameter](#create)

## <a id = "pick"></a>Generieren Sie Konstruktor, und wählen Sie Elemente
1. Platzieren Sie den Cursor in eine beliebige leere Zeile in einer Klasse:

   ![Cursor in die leere Zeile](media/constructor1_highlight.png)

1. Als Nächstes führen Sie eine der folgenden:
   * **Tastatur**
     * Drücken Sie **STRG +.** Trigger die **Schnellaktionen und Refactorings** Menü **Konstruktor generieren...**  im Popupmenü Fenster Vorschau.
   * **Maus**
     * Mit der rechten Maustaste, und wählen Sie die **Schnellaktionen und Refactorings** Menü **Konstruktor generieren...**  im Popupmenü Fenster Vorschau.
     * Klicken Sie auf die Schaltfläche ![Glühbirne](media/bulb.png) Symbol "wird am linken Rand angezeigt werden soll, wenn der Textcursor sich bereits in der leeren Zeile in der Klasse ist.

   ![Konstruktor Vorschau generieren](media/constructor1_preview.png)

1. Ein Dialogfeld wird angezeigt, welche Elemente auszuwählen, die als Konstruktorparameter verwendet werden sowie das Sortieren Sie sie (mit der nach-oben und nach unten weisenden Pfeil) werden sollen. Drücken Sie **Ok** um Ihre Änderungen zu übernehmen.
  
   ![Pick-Elemente-Dialogfeld](media/constructor1_dialog.png)

   >[!TIP] 
   >Sehen Sie sich die **Hinzufügen von null-Überprüfungen** Kontrollkästchen zum automatischen Generieren von null-Überprüfungen für die Parameter des Konstruktors.

1. Der Konstruktor wird mit den ausgewählten Parametern in der angegebenen Reihenfolge erstellt werden.
   ![Konstruktorergebnis generieren](media/constructor1_result.png)

## <a id="selection"></a>Generieren Sie Konstruktor aus ausgewählten Feldern.
1. Markieren Sie die Elemente in der generierten Konstruktor aufweisen sollen: ![Elemente markieren](media/constructor2_highlight.png)

1. Als Nächstes führen Sie eine der folgenden:
   * **Tastatur**
     * Drücken Sie **STRG +.** Trigger die **Schnellaktionen und Refactorings** Menü **generieren Konstruktor "TypeName(...)"**  im Popupmenü Fenster Vorschau.
   * **Maus**
     * Mit der rechten Maustaste, und wählen Sie die **Schnellaktionen und Refactorings** Menü **generieren Konstruktor "TypeName(...)"**  im Popupmenü Fenster Vorschau.
     * Klicken Sie auf die Schaltfläche ![Glühbirne](media/bulb.png) Symbol "wird am linken Rand angezeigt werden soll, wenn der Textcursor sich bereits in der Zeile mit der Auswahl ist.

     ![Konstruktor Vorschau generieren](media/constructor2_preview.png)

1. Der Konstruktor wird mit den ausgewählten Parametern erstellt.
     ![Konstruktorergebnis generieren](media/constructor2_result.png)

## <a id="usage"></a>Konstruktor von neuen Verwendung generieren
1. Platzieren Sie den Cursor in der Zeile, in dem es eine rote Wellenlinie, der angibt, Sie verwendet haben, einen Konstruktor, der noch nicht vorhanden ist.

   ![Hervorgehobene code](media/constructor_highlight.png)

1. Als Nächstes führen Sie eine der folgenden:
   * **Tastatur**
     * Drücken Sie **STRG +.** Trigger die **Schnellaktionen und Refactorings** Menü  **generieren Konstruktor in "*TypeName*" ** im Popupmenü Fenster Vorschau.
   * **Maus**
     * Mit der rechten Maustaste, und wählen Sie die **Schnellaktionen und Refactorings** , und wählen Sie im Menü  **generieren Konstruktor in "*TypeName*" ** im Popupmenü Fenster Vorschau.
     * Die rote Wellenlinie zeigen, und klicken Sie auf der ![Glühbirne](media/bulb.png) Symbol "angezeigt wird.
     * Klicken Sie auf die Schaltfläche ![Glühbirne](media/bulb.png) Symbol "wird am linken Rand angezeigt werden soll, wenn der Textcursor bereits in der Zeile mit die rote Wellenlinie vorhanden ist.

   ![Konstruktor Vorschau generieren](media/constructor_preview.png)

   >[!TIP]
   >Verwenden der [ **Vorschau der Änderungen** ](../../ide/preview-changes.md) Link am unteren Rand des Vorschaufensters, um alle Änderungen anzuzeigen, die vorgenommen wird, bevor Sie Ihre Auswahl getroffen haben.

1. Der Konstruktor wird automatisch mit allen Parametern abgeleitet aus seiner Verwendung erstellt.

   ![Konstruktorergebnis generieren](media/constructor_result.png)

## <a id="addparameter"></a>Fügen Sie Parameter an vorhandenen Konstruktor hinzu.
1. Fügen Sie einen Parameter, um eine vorhandene Objektinstanziierung.

1. Platzieren Sie den Cursor in der Zeile, in dem es eine rote Wellenlinie, der angibt, Sie verwendet haben, einen Konstruktor, der noch nicht vorhanden ist.
    
    ![Generieren von Konstruktor hervorheben](media/constructor4_highlight.png)

1. Als Nächstes führen Sie eine der folgenden:
   * **Tastatur**
     * Drücken Sie **STRG +.** Trigger die **Schnellaktionen und Refactorings** Menü **"TypeName(...)" Parameter hinzufügen**  im Popupmenü Fenster Vorschau.
   * **Maus**
     * Mit der rechten Maustaste, und wählen Sie die **Schnellaktionen und Refactorings** Menü **"TypeName(...)" Parameter hinzufügen**  im Popupmenü Fenster Vorschau.
     * Die rote Wellenlinie zeigen, und klicken Sie auf der ![Glühbirne](media/bulb.png) Symbol "angezeigt wird.
     * Klicken Sie auf die Schaltfläche ![Glühbirne](media/bulb.png) Symbol "wird am linken Rand angezeigt werden soll, wenn der Textcursor bereits in der Zeile mit die rote Wellenlinie vorhanden ist.

    ![Konstruktor Vorschau generieren](media/constructor4_preview.png)

1. Der Parameter wird mit seinem Typ abgeleitet aus seiner Verwendung automatisch hinzugefügt werden.
   
   ![Konstruktorergebnis generieren](media/constructor4_result.png)

## <a id="create"></a>Erstellen Sie und initialisieren Sie Feld/Eigenschaft aus einem Konstruktorparameter
1. Fügen Sie einen Parameter aus einem vorhandenen Konstruktor hinzu:

   ![Generieren von Konstruktor hervorheben](media/constructor5_highlight.png)

1. Platzieren Sie den Cursor in der neu hinzugefügten Parameter.

1. Als Nächstes führen Sie eine der folgenden:
   * **Tastatur**
     * Drücken Sie **STRG +.** Trigger die **Schnellaktionen und Refactorings** Menü **erstellen und Initialisieren von Eigenschaft "YourProperty"** oder **erstellen und Initialisieren von Feld "YourField"** aus der Vorschau-Fenster-Popupfenster.
   * **Maus**
     * Mit der rechten Maustaste, und wählen Sie die **Schnellaktionen und Refactorings** Menü **erstellen und Initialisieren von Eigenschaft "YourProperty"** oder **erstellen und Initialisieren von Feld 'YourField'**im Popupmenü Fenster Vorschau.
     * Klicken Sie auf die Schaltfläche ![Glühbirne](media/bulb.png) Symbol "wird am linken Rand angezeigt werden soll, wenn der Textcursor sich bereits in der Zeile mit dem hinzugefügten Parameter ist.

   ![Konstruktor Vorschau generieren](media/constructor5_preview.png)

1. Die Feldeigenschaft wird erstellt und automatisch Ihre Typen entsprechend benannt werden.

   ![Konstruktorergebnis generieren](media/constructor5_result.png)
  
## <a name="see-also"></a>Siehe auch  
[Codegenerierung (C#)](../code-generation-csharp.md)  
[Vorschau der Änderungen](../../ide/preview-changes.md)
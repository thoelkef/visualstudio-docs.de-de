---
title: Gehe zu | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 509b2107-23d1-4fb3-987f-ab99ef45b72e
author: BrianPeek
ms.author: brpeek
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 3b812629bf0f655f39c35a56eb1b3ca9113303a6
ms.openlocfilehash: 8bf6d49b21d128d15f5312fb230d4a8e7a8195af
ms.lasthandoff: 03/01/2017

---

# <a name="go-to"></a>Gehe zu
Es bieten sich viele Möglichkeiten zur komfortablen Navigation im Code innerhalb der Visual Studio IDE, sowohl mit der Tastatur als auch mit der Maus.

<!-- VERSIONLESS -->
## <a name="go-to-all"></a>Gehe zu allen
Dieses Funktion ist in Visual Studio 2017 und höher vorhanden.  Dies ermöglicht es Ihnen durch Ihren Code zu navigieren, um die bestimmten Bits zu finden, nach denen Sie suchen.  Sie können auf einer einfachen, einheitlichen Oberfläche nach einer bestimmten Zeile, einem Typ, einem Symbol, einer Datei und mehr suchen.

### <a name="how-to-use"></a>Verwendung
* **Tastatur**
  * Drücken Sie **STRG+,** oder **STRG+T**.  (Beachten Sie, dass Ihre Tastenkombination je nach dem gewählten Profil möglicherweise abweicht.)
* **Maus**
  * Wählen Sie **Bearbeiten > Gehe zu > Gehe zu allen** aus.

Standardmäßig wird dadurch oben rechts in Ihrer IDE ein kleines Fenster angezeigt.

![Gehe zu allen](~/ide/media/gotoall.png)

An diesem Punkt bieten sich verschiedene Wege an:
* Geben Sie Text für die Suche ohne Präfix mithilfe der [Filtersymbole](#filtered-searches) ein, die unter dem Textfeld ausgewählt sind.
* Geben Sie ein [Präfix](#filtered-searches) ein, gefolgt von dem zu suchenden Text.
* Geben Sie ein Fragezeichen (?) ein, um weitere Hilfe anzufordern.
  ![Gehe zu allen – Hilfe](~/ide/media/gotoall_help.png)

### <a name="filtered-searches"></a>Gefilterte Suchvorgänge
Um Ihre Suche auf einen bestimmten Typ einzugrenzen, können Sie entweder während der Eingabe ein Präfix oder die Schaltfläche unterhalb des Suchfensters verwenden, wie unten dargestellt.

Präfix | Symbol | Verknüpfung | Beschreibung
:----: | ---- | -------- | ---
#      | ![Zeichensymbol](~/ide/media/gotoall_symbolicon.png) | STRG+1, STRG+S | Suchen von übereinstimmenden Symbolen
f      | ![Dateisymbol](~/ide/media/gotoall_fileicon.png)     | STRG+1, STRG+F | Übereinstimmende Dateinamen suchen
m      | ![Membersymbol](~/ide/media/gotoall_membericon.png) | STRG+1, STRG+M | Übereinstimmende Elemente suchen
t      | ![Typsymbol](~/ide/media/gotoall_typeicon.png)     | STRG+1, STRG+T | Übereinstimmende Typen suchen
:      | ![Zeilensymbol](~/ide/media/gotoall_lineicon.png)     | Strg+G         | Zu der eingegebenen Zeilennummer gehen

### <a name="search-locations"></a>Speicherorte für die Suche
Um die Suche auf bestimmte Speicherorte einzugrenzen, verwenden Sie die zwei Dokumentsymbole.

Symbol | Beschreibung
---- | ---
![Aktuelles Dokument](~/ide/media/gotoall_currentdocument.png) | Nur im aktuellen Dokument suchen
![Externe Dokumente](~/ide/media/gotoall_external.png) | In externen Dokumenten suchen, zusätzlich zu den unter Projekt/Projektmappe gespeicherten

### <a name="settings"></a>Einstellungen
Klicken auf das Zahnradsymbol ![Zahnradsymbol](~/ide/media/gotoall_gear.png) unten rechts ermöglicht Ihnen, die Funktionsweise diese Features zu ändern.

Einstellung | Beschreibung
------- | ---
Vorschauregisterkarte verwenden | Das ausgewählte Element sofort auf der Vorschauregisterkarte der IDE anzeigen
Details anzeigen    | Zeigt Projekt-, Datei-, Zeilen- und Zusammenfassungsinformationen aus Dokumentationskommentaren im Fenster an
Fenster zentrieren   | Das Fenster in die Mitte der IDE verschieben, statt an die Standardposition oben rechts
<!-- END VERSIONLESS -->

## <a name="go-to-definition"></a>Gehe zu Definition
Zur Quelle eines Typs navigieren und das Ergebnis auf einer neuen Registerkarte öffnen:

Eingabe        | Funktion 
------------ | ---
**Tastatur** | Platzieren Sie den Textcursor an einer beliebigen Position innerhalb des Typnamens, und drücken Sie **F12**
**Maus**    | Klicken Sie mit der rechten Maustaste auf den Typnamen, und wählen Sie **Gehe zu Definition** aus

## <a name="peek-definition"></a>Peek-Definition
Vorschau der Definition eines Typs in einem Popupfenster statt auf einer neuen Registerkarte:

Eingabe        | Funktion 
------------ | ---
**Tastatur** | Platzieren Sie den Textcursor an einer beliebigen Position innerhalb des Typnamens, und drücken Sie **ALT+F12**
**Maus**    | Klicken Sie mit der rechten Maustaste auf den Typnamen, und wählen Sie **Definition einsehen** aus

Wenn Sie im Popupfenster eine andere Definition einsehen möchten, können Sie einen Brotkrumenpfad beginnen, in dem Sie mithilfe der Kreise und Pfeile navigieren können, die oberhalb des Popups angezeigt werden.  Weitere Informationen finden Sie unter [Gewusst wie: Anzeigen und Bearbeiten von Code mithilfe von „Definition einsehen“ (Alt+F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md).

## <a name="go-to-implementation"></a>Gehe zu Implementierung
Navigieren von einer Basisklasse oder einem Typ zu deren bzw. seinen Implementierungen.  Wenn mehrere Implementierungen vorhanden sind, sind sie im Fenster **Ergebnisse der Symbolsuche** aufgelistet:

Eingabe        | Funktion 
------------ | ---
**Tastatur** | Platzieren Sie den Textcursor an einer beliebigen Position innerhalb des Typnamens, und drücken Sie **STRG+F12**
**Maus**    | Klicken Sie mit der rechten Maustaste auf den Typnamen, und wählen Sie **Gehe zu Implementierung** aus

## <a name="find-all-references"></a>Alle Verweise suchen
Alle Orte finden, an denen eine Methode/Eigenschaft/Variable verwendet wird.  Sie können dies verwenden, um auf toten Code zu prüfen und mögliche Nebenwirkungen eines umfangreichen Refactorings zu überprüfen.  Drücken Sie **F8**, um zwischen den Ergebnissen zu wechseln.

Eingabe        | Funktion 
------------ | ---
**Tastatur** | Platzieren Sie den Textcursor an einer beliebigen Position innerhalb des Typnamens, und drücken Sie **STRG+K, R**
**Maus**    | Klicken Sie mit der rechten Maustaste auf den Typnamen, und wählen Sie **Alle Verweise suchen** aus

## <a name="navigating-results"></a>Navigieren in den Ergebnissen
Mithilfe der Navigationsfunktionen von Visual Studio können Sie im Stapel vorwärts und rückwärts suchen:

Eingabe        | Funktion 
------------ | ---
**STRG+-**          | Rückwärts durch den Stapel navigieren
**STRG+UMSCHALT+-**    | Vorwärts durch den Stapel navigieren

Sie können außerdem die Menüelemente **Ansicht > Rückwärts navigieren** und **Ansicht > Vorwärts navigieren** verwenden.

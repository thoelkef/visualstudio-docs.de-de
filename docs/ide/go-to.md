---
title: Suchen von Code mithilfe von Gehe-zu-Befehlen | Microsoft-Dokumentation
ms.custom: 
ms.date: 09/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 509b2107-23d1-4fb3-987f-ab99ef45b72e
helpviewer_keywords:
- code editor, go to
- code editor, go to line
- go to line
- go to
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 15b222eaa3e03a44f99f64e86f9c88d125e41f98
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="find-code-using-go-to-commands"></a>Suchen von Code mithilfe von Gehe zu-Befehlen  
Die **Gehe zu**-Befehle von Visual Studio führen eine zielgerichtete Suche in Ihrem Code aus, damit Sie angegebene Elemente schneller finden. Sie können über eine einfache und einheitliche Oberfläche zu einer bestimmten Zeile, einem bestimmten Typ, einem bestimmten Symbol oder einer bestimmten Datei gehen. Dieses Funktion ist in Visual Studio 2017 und höher vorhanden.  

### <a name="how-to-use-it"></a>Verwendungsweise  

Eingabe        | Funktion 
------------ | ---
**Tastatur** | Drücken Sie **STRG+T** oder **STRG+,**.     
**Maus**    | Klicken Sie auf **Bearbeiten** > **Gehe zu** > **Go To All** (Gehe zu allen).  

Dadurch wird oben rechts in Ihrem Code-Editor ein kleines Fenster angezeigt.  

![Gehe zu allen](media/gotoall.png)

Während der Eingabe in das Textfeld werden die Ergebnisse in einer Dropdownliste unterhalb des Textfelds angezeigt. Um zu einem Element zu wechseln, wählen Sie es in der Liste aus.    

![Fenster „Navigieren zu“](../ide/media/vside_navigatetowindow.png "Fenster „Navigieren zu“")  

Sie können auch ein Fragezeichen (?) eingeben, um weitere Hilfe anzufordern.  

  ![Gehe zu allen: Hilfe](media/gotoall_help.png)

### <a name="filtered-searches"></a>Gefilterte Suchvorgänge  
Standardmäßig wird das angegebene Element in allen Projektmappenelementen gesucht. Sie können jedoch die Codesuche auf bestimmte Elementtypen einschränken, indem Sie den Suchbegriffen bestimmte Zeichen voranstellen. Sie können auch schnell Suchfilter ändern, indem Sie Schaltflächen auf der Symbolleiste des Dialogfelds „Gehe zu“ auswählen. Schaltflächen zum Ändern der Typfilter befinden sich auf der linken Seite, und die Schaltflächen zum Ändern des Suchbereichs auf der rechten.  

![Go to members (Elemente von „Gehe zu“)](../ide/media/vside_navigation_toolbar.png)

#### <a name="filter-to-a-specific-type-of-code-element"></a>Filtern eines bestimmten Codeelementtyps  
Um Ihre Suche auf einen bestimmten Typ von Codeelement einzugrenzen, können Sie entweder ein Präfix in das Suchfeld eingeben oder eines der fünf Filtersymbole auswählen:  

Präfix | Symbol | Verknüpfung | Beschreibung
:----: | ---- | -------- | ---
\#      | ![Zeichensymbol](media/gotoall_symbolicon.png) | STRG+1, STRG+S | Zum angegebenen Symbol wechseln
f      | ![Dateisymbol](media/gotoall_fileicon.png)     | STRG+1, STRG+F | Zur angegebenen Datei wechseln
m      | ![Membersymbol](media/gotoall_membericon.png) | STRG+1, STRG+M | Zum angegebenen Member wechseln
t      | ![Typsymbol](media/gotoall_typeicon.png)     | STRG+1, STRG+T | Zum angegebenen Typ wechseln
:      | ![Zeilensymbol](media/gotoall_lineicon.png)     | STRG+G         | Zur angegebenen Zeilennummer wechseln

#### <a name="filter-to-a-specific-location"></a>Filtern an einem bestimmten Speicherort    
Um die Suche auf bestimmte Speicherorte einzugrenzen, wählen Sie eines der zwei Dokumentsymbole aus:  

Symbol | Beschreibung
---- | ---
![Aktuelles Dokument](media/gotoall_currentdocument.png) | Nur im aktuellen Dokument suchen
![Externe Dokumente](media/gotoall_external.png) | In externen Dokumenten suchen, zusätzlich zu den unter Projekt/Projektmappe gespeicherten  

### <a name="camel-casing"></a>Camel-Case-Schreibweise  
Wenn Sie die [Camel-Case-Schreibweise](https://en.wikipedia.org/wiki/Camel_case) in Ihrem Code verwenden, können Sie Codeelemente schneller finden, indem Sie nur die Großbuchstaben des Codeelementnamens eingeben. Wenn Ihr Code beispielsweise über einen Typ namens `CredentialViewModel` verfügt, können Sie die Suche eingrenzen, indem Sie den Typfilter („t“) auswählen und anschließend nur die Großbuchstaben des Namens (`CVM`) in das „Gehe zu“-Dialogfeld eingeben. Diese Funktion ist nützlich, wenn der Code lange Namen aufweist.  

![Fenster „Navigieren zu“ - Suchvorgänge mit Großbuchstaben](../ide/media/vside_capitalsearch.png)

### <a name="settings"></a>Einstellungen  
Über das Zahnradsymbol ![Zahnradsymbol](media/gotoall_gear.png) können Sie die Funktionsweise dieser Funktion ändern:  

Einstellung | Beschreibung
------- | ---
Vorschauregisterkarte verwenden | Das ausgewählte Element sofort auf der Vorschauregisterkarte der IDE anzeigen
Details anzeigen    | Zeigt Projekt-, Datei-, Zeilen- und Zusammenfassungsinformationen aus Dokumentationskommentaren im Fenster an
Fenster zentrieren   | Verschieben Sie dieses Fenster in die Mitte des Code-Editors, statt an die Standardposition.   

## <a name="see-also"></a>Siehe auch  
[Navigieren im Code](../ide/navigating-code.md)  
[Go To Definition and Peek Definition („Gehe zu Definition“ und „Definition einsehen“)](../ide/go-to-and-peek-definition.md)  
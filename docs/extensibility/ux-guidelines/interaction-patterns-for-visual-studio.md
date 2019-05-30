---
title: Interaktionsmuster für Visual Studio | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 306c729c8c908d6d065155fcbfc9cf64adb4f4a1
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66335309"
---
# <a name="interaction-patterns-for-visual-studio"></a>Interaktionsmuster für Visual Studio
## <a name="overview"></a>Übersicht
 Ein Entwurfsmuster, ist im Allgemeinen den Kern eines Entwurfs, die in bestimmten Situationen zum Lösen von Problemen mit ähnlichen Sätzen von Einschränkungen angewendet werden können. Feature und System-Designer verwenden Sie diese Entwurfsmuster als Ausgangspunkt, die dann an ihre spezifische Situation angepasst werden können.

 Visual Studio verfügt über eine Bibliothek mit häufige Interaktionsmuster von, die beim Erstellen von neuer Funktionen berücksichtigt werden sollten. Es gibt zwei Core-Kontexte für unsere Entwurfsmuster: Visual Studio-Clients (Devenv) und Visual Studio Online. Bei bestimmten Problemen entwerfen ein allgegenwärtig Muster vorliegt, die in allen Fällen gut funktioniert. In vielen Fällen kann jedoch die Lösung für die Benutzeroberfläche unterscheiden, die in einem Browser und, die auf eine Client-Anwendung gehostet wird präsentiert wird.

### <a name="visual-studio-client-pattern-types"></a>Visual Studio-Client-Mustertypen

|Mustertyp|Beschreibung|Beispiele|
|------------------|-----------------|--------------|
|**Anwendungsebene-Muster**|Allgemeine Muster für die Anwendung bestimmen oder Anwendungskontext angezeigt und enthält, die Zusammensetzung und Steuerelementmuster, die darin enthaltenen|-Toolfenster<br />-Dokumentfenster|
|**Zusammengesetzte Muster**|Allgemeine Muster, die über Anwendungsmuster hinweg erstrecken oder einem erkannten Muster setzt sich aus mehreren Steuerelementen in einer Konfiguration mit distinct|-Ansicht wechseln<br />-List-Generatoren<br />– Anzeigen von Daten<br />-Benachrichtigungen<br />-Überprüfung<br />-Auswahl Modelle|
|**Steuerelementmuster**|Einzelheiten dazu, wie Low-Level-Steuerelemente werden Verhalten erwartet|-Strukturansichten<br />-Bearbeitung in einem Grid-Steuerelement|

## <a name="application-patterns"></a>Anwendungsmuster
 Auf einer hohen Ebene besteht aus Visual Studio-Benutzeroberfläche, Windows, Dialogfelder, Befehle und Symbolleisten in einer einzigen IDE. Die Visual Studio-Hierarchie bestimmt Kontext und Laufwerken-Menüs. Der wichtige Integrationspunkte in der Benutzeroberfläche der IDE werden Dokumentfenster, Toolfenster, Projekte, die Befehlsstruktur, die Text-Editor, der Toolbox, die Fenster "Eigenschaften" und Tools > Optionen.

 Es gibt grundlegende Verwendungsmuster für jede der in der Benutzeroberfläche der IDE die wichtige Integrationspunkte:

- [Menüs und Befehle für Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)

- [Anwendungsmuster für Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)

    - [Fenster-Interaktionen](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)

    - [Toolfenster](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)

    - [Dokument-Editor-Konventionen](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)

    - [Dialogfelder](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)

    - [Projekte](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)

## <a name="common-control-patterns"></a>Allgemeine Steuerelementmuster
 Steuerelementmuster sind vor allem an, zu den Steuerelementen wie erwartet Verhalten. Dies ist ein Bereich, in denen Konsistenz wichtigsten ist.

 Am häufigsten verwendeten Steuerelemente in Visual Studio sollte es sich um die Desktop-Windows-Richtlinien einhalten. Unsere Richtlinien beziehen sich ausschließlich auf Bereiche, in denen wir häufig verwendete Konventionen mit Visual Studio-spezifischer Aktivitäten oder stellen Sie in denen wir die Richtlinien vollständig ersetzen zum Anpassen von Visual Studio, um die Anforderungen unserer Benutzer anspruchsvolle erweitern müssen.

- [Allgemeine Steuerelementmuster für Visual Studio](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)

    - [Allgemeine Steuerelemente](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)

    - [Textsteuerelemente](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

    - [Schaltflächen und Links](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

## <a name="composite-patterns"></a>Zusammengesetzte Muster
 Es gibt eine Reihe von Möglichkeiten, die Benutzer erwarten, um Aufgaben auszuführen. Nach Möglichkeit sollten Funktionen entworfen werden, verwenden Sie diese Muster sowohl für die Interaktion und den visuellen Entwurf.

 Es gibt viele zusammengesetzte Muster in Visual Studio, einige der wichtigsten im Hinblick auf die Konsistenz sind:

- [Zusammengesetzte Muster für Visual Studio](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)

    - [Objektgebundenen Benutzeroberfläche und einsehen](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

    - [Auswahlmodelle](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

    - [Persistenz und Einstellungen werden gespeichert.](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

    - [Touch-Punkts](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)
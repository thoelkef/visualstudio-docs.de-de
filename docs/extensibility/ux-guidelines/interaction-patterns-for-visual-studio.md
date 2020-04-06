---
title: Interaktionsmuster für Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac917aeb2530570b755e7f1e6fc6de00714a54b0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698377"
---
# <a name="interaction-patterns-for-visual-studio"></a>Interaktionsmuster für Visual Studio
## <a name="overview"></a>Übersicht
 Ein Entwurfsmuster ist im Allgemeinen der Kern eines Entwurfs, der in bestimmten Situationen angewendet werden kann, um Probleme mit ähnlichen Einschränkungen zu lösen. Feature- und Systemdesigner nutzen diese Designmuster als Ausgangspunkte, die dann an ihre jeweilige Situation angepasst werden können.

 Visual Studio verfügt über eine Bibliothek mit allgemeinen Interaktionsmustern, die beim Erstellen neuer Features berücksichtigt werden sollten. Es gibt zwei Hauptkontexte für unsere Entwurfsmuster: Visual Studio Client (devenv) und Visual Studio Online. Bei einigen Designproblemen gibt es ein allgegenwärtiges Muster, das in allen Situationen gut funktioniert. In vielen Fällen kann die Lösung jedoch für die Benutzeroberfläche, die in einem Browser angezeigt wird, und für die in einer Clientanwendung gehostete Benutzeroberfläche unterschiedlich sein.

### <a name="visual-studio-client-pattern-types"></a>Visual Studio Client-Mustertypen

|Mustertyp|Beschreibung|Beispiele|
|------------------|-----------------|--------------|
|**Muster auf Anwendungsebene**|High-Level-Muster, die der Anwendung gemeinsam sind, den Anwendungskontext bestimmen oder anzeigen und zusammengesetzte und Steuerelementmuster enthalten|- Werkzeugfenster<br />- Dokumentfenster|
|**Zusammengesetzte Muster**|Häufige Muster, die sich über Anwendungsmuster erstrecken können, oder ein erkanntes Muster, das aus mehreren Steuerelementen in einer unterschiedlichen Konfiguration besteht|- Ansichtsschaltung<br />- Listenbauer<br />- Anzeige von Daten<br />- Benachrichtigungen<br />- Validierung<br />- Auswahlmodelle|
|**Steuerungsmuster**|Einzelheiten dazu, wie sich Kontrollen auf niedriger Ebene verhalten sollen|- Baumansichten<br />- Bearbeiten innerhalb eines Rastersteuerelements|

## <a name="application-patterns"></a>Anwendungsmuster
 Auf hoher Ebene umfasst die Visual Studio-Schnittstelle mehrere Fenster, Dialogfelder, Befehle und Symbolleisten innerhalb einer einzelnen IDE. Die Visual Studio-Hierarchie bestimmt den Kontext und steuert Menüs. Die wichtigsten Integrationspunkte in der Benutzeroberfläche der IDE sind Dokumentfenster, Toolfenster, Projekte, die Befehlsstruktur, der Texteditor, die Toolbox, das Eigenschaftenfenster und Tools > Optionen.

 Es gibt grundlegende Verwendungsmuster für jeden der wichtigsten Integrationspunkte in der Benutzeroberfläche der IDE:

- [Menüs und Befehle für Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)

- [Anwendungsmuster für Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)

  - [Fensterinteraktionen](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)

  - [Toolfenster](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)

  - [Dokumenteditor-Konventionen](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)

  - [Dialogfelder](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)

  - [Projekte](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)

## <a name="common-control-patterns"></a>Gemeinsame Steuerungsmuster
 Bei den Steuerungsmustern geht es vor allem darum, wie sich einzelne Steuerelemente verhalten sollen. Dies ist ein Bereich, in dem Die Konsistenz am kritischsten ist.

 Die häufigsten Steuerelemente in Visual Studio sollten den Desktop-Windows-Richtlinien folgen. Unsere Richtlinien umfassen nur Bereiche, in denen wir allgemeine Konventionen durch Visual Studio-spezifische Interaktionen erweitern müssen, oder Orte, an denen wir die Richtlinien vollständig ablösen, um Visual Studio an die Anforderungen unserer anspruchsvollen Benutzer anzupassen.

- [Allgemeine Steuerelementmuster für Visual Studio](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)

  - [Allgemeine Steuerelemente](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)

  - [Textsteuerelemente](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

  - [Schaltflächen und Hyperlinks](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

## <a name="composite-patterns"></a>Zusammengesetzte Muster
 Es gibt eine Reihe von Möglichkeiten, mit denen Benutzer Aufgaben ausführen möchten. Wo immer möglich, sollten Features so konzipiert werden, dass diese Muster sowohl für Interaktionals als auch für visuelles Design verwendet werden.

 Obwohl es in Visual Studio viele zusammengesetzte Muster gibt, sind einige der wichtigsten in Bezug auf Konsistenz:

- [Zusammengesetzte Muster für Visual Studio](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)

  - [On-Object-Benutzeroberfläche und Gucken](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

  - [Auswahlmodelle](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

  - [Persistenz- und Speichereinstellungen](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

  - [Touch-Eingang](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)
